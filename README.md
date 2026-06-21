# Open Weather Station

## Integrantes

| Nome                                           | Matrícula |
| ---------------------------------------------- | --------- |
| [Laís Soares](https://github.com/Laisczt)      | 211029512 |
| [Bruna Lima](https://github.com/libruna)       | 211041105 |
| [José Augusto](https://github.com/JAugustoM)   | 231026429 |
| [Ana Catarina](https://github.com/an4catarina) | -         |

## 1) Descrição do produto

Open Weather Station (OWS) é uma solução de monitoramento de fatores climáticos (e.g. velocidade do vendo, termperatura, precipitação, etc.) utilizando um arduíno e um dispositivo móvel, criada com o intuito de sermais barata, compacta, e amigável ao usuário que outras opções existentes no mercado. OWS é capaz de enviar telemetria sem fio ao servidor local ou integrar diretamente à serviços como Wunderground, Thingspeak, Windguru ou OpenWeatherMap.

### 1.1) Funções principais, público-alvo e contexto de uso

| Funcionalidade                    | Descrição                                                                                                   |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Comunicação sem fio               | O OWS é capaz de transmitir suas informações por meio de wi-fi ou rede móvel, a partir do dispositivo móvel |
| Visualização de dados/diagnóstico | O aplicativo móvel permite também a visualização dos dados em gráficos, e o diagnóstico do sistema arduino  |

**Informações coletadas**

- Velocidade do vento(m/s)
- Direção do vento (ângulo)
- Rajada de vento (m/s)
- Direção da rajada de vento (ângulo)
- Chuva(mm)
- Temperatura(ºC)
- Pressão atmosférica(Pascal)
- Humidade relativa(%)
- Iluminação Ambiente(lux)

### 1.2) Componentes e sensores utilizados

Abaixo está a lista dos principais componentes e sensores utilizados na OWS, o BoM completo do projeto pode ser visto neste [link](https://github.com/panchazo/open-weather-station#list-of-materials)

| Componente            | Quantidade | Uso                                                                         |
| :-------------------- | :--------: | :-------------------------------------------------------------------------- |
| Sensor BH1750         |     1      | Utilizado para medir a iluminição ambiente                                  |
| Sensor BME280         |     1      | Utilizado para medir a temperatura, pressão atmosférica e humidade ambiente |
| Anemômetro WS 1080    |     1      | Utilizado para medir a velocidade do vento                                  |
| Veleta WS 1080        |     1      | Utilizado para medir a direção do vento                                     |
| Pluviômetro WS 1080   |     1      | Utilizado para medir o volume de chuva                                      |
| Arduino Uno R3        |     1      | Microcontrolador utilizado como unidade de processamento                    |
| Módulo Bluetooth HC05 |     1      | Provê conectividade bluetooth ao dispositivo                                |

### 1.3) Tecnologias de comunicação e controle embarcadas

A comunicação com os sensores BH1705 e BME280 é feita utilizando comunicação I2C no mesmo barramento. O pluviômetro, a veleta e o anemômetro utilizam comunicação serial via conector RJ11.

O envio de informações do sistema para o aplicativo é feita via bluetooth, utilizando o módulo HC05.

## 2) Análise técnica do funcionamento

### 2.1) Principais módulos do sistema

O sistema original da OpenWeatherStation foi projetado em torno de componentes de fácil acesso e focava na comunicação local via Bluetooth. Ele é dividido nos seguintes módulos principais:

1. **Módulo de Processamento Central**: Responsável por ler os sensores e formatar os dados. No projeto original, isso é feito utilizando um Arduino Uno.
2. **Módulo de Sensoriamento Atmosférico**: Composto pelo sensor BME280 (para medição de temperatura, umidade e pressão) e pelo sensor BH1750 (para medição da luminosidade), ambos comunicando-se via barramento I2C.
3. **Módulo de Sensoriamento Eólico e Pluviométrico**: Utiliza as peças mecânicas de reposição da estação comercial WS1080, lendo os contatos magnéticos (reed switches) do anemômetro (velocidade do vento) e pluviômetro (chuva), além dos resistores da biruta (direção do vento).
4. **Módulo de Comunicação Local**: Baseado no módulo Bluetooth HC05, que transmite os dados lidos pelo microcontrolador para um dispositivo próximo.
5. **Módulo de Interface e Armazenamento (App Android)**: Um aplicativo de smartphone que pareava com a estação via Bluetooth para coletar, exibir e armazenar os dados climáticos.

### 2.2) Identificação de tecnologias críticas

Para o funcionamento adequado da versão original da **OpenWeatherStation**, as seguintes tecnologias e conceitos de hardware/software são considerados críticos para a arquitetura do projeto:

- **Comunicação Serial sem Fio (Bluetooth):** No projeto original, a estação meteorológica não possui uma tela para mostrar os dados ou conexão com a Internet. O módulo HC05, operando através do _Serial Port Profile (SPP)_, atua como a única ponte de saída de dados. Sem esta tecnologia, a estação estaria limitada a recolher os dados localmente, sem a capacidade de envia-los ao celular para serem exibidas.

- **Barramento I2C:** É o protocolo de comunicação que viabiliza a leitura dos sensores digitais do projeto (BME280 para métricas atmosféricas e BH1750 para luminosidade). O I2C é considerado crítico porque permite interligar múltiplos sensores de alta precisão utilizando apenas dois pinos do microcontrolador (SDA e SCL), preservando as demais portas digitais e analógicas para outras aplicações.

- **Interrupções de Hardware:** O anemómetro (velocidade do vento) e o pluviómetro (volume de chuva) geram pulsos digitais rápidos a cada fecho dos seus contactos magnéticos. Se o microcontrolador tentasse ler estes pulsos através de _polling_, poderia perder contagens importantes durante rajadas de vento ou precipitação intensa.

- **Conversão Analógico-Digital (ADC) e Divisores de Tensão:** A biruta (direção do vento) do kit original funciona como um divisor de tensão variável, onde diferentes posições ativam diferentes resistores internos gerando variações de voltagem. A capacidade do microcontrolador de ler este sinal analógico de forma precisa através do seu conversor ADC, mapeando a tensão para um valor numérico, é a tecnologia crítica que permite descodificar a origem direcional do vento.

- **Tratamento de _Debounce_:** Os sensores baseados _reed switches_ sofrem do fenómeno de _bouncing_, que o microcontrolador pode interpretar como múltiplos acionamentos simultâneos. A implementação de filtros de _debounce_ é crítica para realizar medições precisas de volume de chuva e velocidade do vento.

- **Aplicação Mobile Datalogger:** Uma vez que as placas baseadas na arquitetura Arduino clássica (como o Uno ou Nano) possuem uma memória extremamente limitada para guardar o histórico climático, o projeto original delega as funções de armazenamento de dados, relógio de tempo real (RTC) e interface gráfica para uma aplicação Android. O desenvolvimento desta aplicação é uma tecnologia crítica, pois atua como a unidade de processamento de alto nível do sistema, recebendo as _strings_ de dados brutos via Bluetooth, processando-as e exibindo-as no aplicativo mobile.

## 3) Proposta de reprodução com ESP32

### 3.1) Descrição conceitual de como as funcionalidades poderiam ser implementadas usando a ESP32 e componentes compatíveis com o ecossistema ESP-IDF;

A reprodução do sistema substituirá a arquitetura original baseada em Arduino/Bluetooth por uma solução baseada no ESP32, utilizando os sensores disponíveis.
Sem a necessidade de uma interface visual local, o ESP32 operará como um módulo de sensoriamento, enviando dados diretamente para a rede.

- **Leitura I2C (Atmosfera)**: Utilizando a API `driver/i2c.h` do ESP-IDF, o sistema configurará o ESP32 como mestre I2C para ler o sensor BMP180 ou BMP280. Uma Task do FreeRTOS será responsável por buscar essas leituras em intervalos regulares.
- **Leitura Analógica (Luminosidade e Direção do Vento)**: O ADC do ESP32, configurado via `esp_adc/adc_oneshot.h`, será usado para ler os valores de tensão. Um pino será conectado ao sensor LDR configurado em um divisor de tensão para estimar a luz solar.
- **Comunicação IoT (Wi-Fi, HTTP ou MQTT):**: Será utilizada a conectividade Wi-Fi nativa da ESP32 via `esp_wifi.h`. O processamento de dados consolidará as variáveis climáticas e o sistema poderá ser configurado para duas abordagens de envio:
  1. **Integração em Nuvem (HTTP)**: Usando a biblioteca `esp_http_client.h`, o ESP32 montará as requisições POST formatadas de acordo com a API do WeatherUnderground, permitindo que os dados da estação sejam visíveis na plataforma.
  2. **Integração Local (MQTT)**: Usando a biblioteca nativa `mqtt_client.h`, o ESP32 empacotará os dados em uma string no formato JSON e publicará em um tópico de um broker MQTT local.

### 3.2) Diagrama conceitual do sistema

(pode ser esquemático ou em diarama de blocos);

### 3.3) Limitações e desafios esperados

- **Falta de Medição de Umidade Relativa**: A restrição aos sensores da lista implica a ausência de um sensor capaz de medir a umidade relativa do ar (como os comumente usados DHT11 ou BME280 completo), limitando os dados providos pela estação.
- **Dependência de Wi-Fi**: Como a estação enviará dados via HTTP para o WeatherUnderground ou via MQTT localmente, e não possui um display próprio para apresentar os dados, qualquer instabilidade na rede local irá impedir o envio das informações. Será necessário implementar no código uma lógica de reconexão robusta e, possivelmente, uma fila no FreeRTOS para não perder dados durante quedas curtas.
- **Não Linearidade e Ruído no ADC**: A estimativa de luminosidade via LDR pode ser prejudicada pela não-linearidade do ADC do ESP32. O desafio será implementar curvas de calibração via software ou utilizar as APIs de calibração (`esp_adc_cal.h`) para amenizar esta limitação.

## 4) Pesquisa bibliográfica e tecnológica

### 4.1) Artigos sobre tecnologia do produto

#### Artigo 1: Análise Comparativa do Consumo de Energia entre os Protocolos MQTT e HTTP em uma Plataforma IoT

- **Autores:** Heriberto J. Jara Ochoa, Raul Peña, Yoel Ledo Mezquita, Enrique Gonzalez, Sergio Camacho-Leon
- **DOI e Acesso:** [10.3390/s23104896](https://www.mdpi.com/1424-8220/23/10/4896)

- **Resumo:** O artigo apresenta uma análise comparativa entre os protocolos MQTT e HTTP em uma plataforma IoT destinada ao monitoramento remoto em tempo real no setor de transportes. Os autores desenvolveram e validaram um sistema embarcado baseado em NodeMCU para avaliar o impacto dos protocolos no consumo energético, considerando diferentes níveis de QoS do MQTT. Os resultados demonstraram que o MQTT apresentou maior eficiência energética, proporcionando uma economia de 6,03% com QoS 0 e 8,33% com QoS 1 em relação ao HTTP, o que contribui para o aumento da autonomia de dispositivos alimentados por bateria. Este trabalho foi selecionado porque analisa exatamente as duas abordagens de conectividade propostas para a nossa ESP32: a integração em nuvem com requisições POST via HTTP e a publicação em rede local via MQTT.

### 4.2) Artigos sobre a aplicação / uso do produto

#### Artigo 1: Estação Meteorológica Automática com Previsões Inteligentes

- **Autores:** Thomas Alexandre da Silva, Andre L. M. Serrano, Erick R. C. Figueiredo, Geraldo P. Rocha Filho, Fábio L. L. de Mendonça, Rodolfo I. Meneguette 3 and Vinícius P. Gonçalves
- **DOI e Acesso:** [10.3390/s25113432](https://www.mdpi.com/1424-8220/25/11/3432)

- **Resumo:** O artigo apresenta o desenvolvimento de uma estação meteorológica automática de baixo custo baseada em um sistema embarcado alimentado por energia solar. A solução utiliza um microcontrolador integrado a diversos sensores ambientais para monitorar variáveis como temperatura, umidade, radiação ultravioleta, precipitação e qualidade do ar. Os dados coletados são processados e transmitidos em tempo real por meio de conexão Wi-Fi para uma plataforma Web, onde são armazenados e utilizados por um modelo de aprendizado de máquina capaz de gerar previsões meteorológicas para as próximas 24 horas. Os resultados demonstraram elevada estabilidade operacional, autonomia energética e boa concordância com os dados de estações meteorológicas oficiais. Como aplicação em sistemas embarcados, o trabalho evidencia a utilização de hardware de baixo custo, comunicação sem fio, sensoriamento distribuído e processamento inteligente de dados para monitoramento ambiental.

## 5) Comparativo com produtos similares

# Open Weather Station

## Integrantes

| Nome                                           | Matrícula |
| ---------------------------------------------- | --------- |
| [Laís Soares](https://github.com/Laisczt)      | 211029512 |
| [Bruna Lima](https://github.com/libruna)       | -         |
| [José Augusto](https://github.com/JAugustoM)   | 231026429 |
| [Ana Catarina](https://github.com/an4catarina) | -         |

## Descrição do produto

Open Weather Station (OWS) é uma solução de monitoramento de fatores climáticos (e.g. velocidade do vendo, termperatura, precipitação, etc.) utilizando um arduíno e um dispositivo móvel, criada com o intuito de sermais barata, compacta, e amigável ao usuário que outras opções existentes no mercado. OWS é capaz de enviar telemetria sem fio ao servidor local ou integrar diretamente à serviços como Wunderground, Thingspeak, Windguru ou OpenWeatherMap.

### Funções principais, público-alvo e contexto de uso

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

### Componentes e sensores utilizados

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

### Tecnologias de comunicação e controle embarcadas

A comunicação com os sensores BH1705 e BME280 é feita utilizando comunicação I2C no mesmo barramento. O pluviômetro, a veleta e o anemômetro utilizam comunicação serial via conector RJ11.

O envio de informações do sistema para o aplicativo é feita via bluetooth, utilizando o módulo HC05.

## Análise técnica do funcionamento

### Principais módulos do sistema

(sensores, atuadores, controle, interface, conectividade);

### Identificação de tecnologias críticas

A seguir está a lista das tecnologias críticas para o funcionamento da OWS:

- Comunicação bluetooth para comunicação sem fio;
- Watchdog timer utilizado para reinicializar o sistema em caso de falha;

<!-- (por exemplo, protocolos sem fio, sistemas operacionais embarcados, técnicas de economia de energia). -->

## Proposta de reprodução com ESP32

### Descrição conceitual de como as funcionalidades poderiam ser implementadas usando a ESP32 e componentes compatíveis com o ecossistema ESP-IDF;

### Diagrama conceitual do sistema

(pode ser esquemático ou em diarama de blocos);

### Limitações e desafios esperados.

## Pesquisa bibliográfica e tecnológica

## Comparativo com produtos similares

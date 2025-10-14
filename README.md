# Trabalho 2 - 2025-2

## 1. Objetivos

Este trabalho tem como objetivo a realização de um estudo teórico-exploratório sobre um produto embarcado existente, identificando como suas principais funcionalidades poderiam ser total ou parcialmente recriadas utilizando uma ESP32 e sensores simples disponíveis no ecossistema ESP32.

A proposta é que o grupo compreenda as tecnologias envolvidas, levante a bibliografia acadêmica e técnica relacionada, e proponha um modelo conceitual de implementação que possa servir de base para um projeto prático em uma etapa posterior da disciplina.

O trabalho deve ser realizado em grupos de 4 integrantes.

## 2. Seleção do sistema embarcado

Cada grupo deve selecionar um produto embarcado de uso cotidiano ou industrial, que utilize sensores e atuadores passíveis de reprodução com componentes simples (por exemplo: sensores de temperatura, umidade, luminosidade, movimento, motores DC, relés, displays, etc.).

Exemplos de categorias possíveis:
	•	Termostatos inteligentes, estações meteorológicas, smart locks, dispositivos vestíveis (wearables);
	•	Sistemas de irrigação automatizada;
	•	Mini robôs móveis com sensores de distância;
	•	Medidores ambientais ou de energia;
	•	Dispositivos de automação residencial (smart home).

**Sugestão**: Pesquisem a documentação dos produtos e dêem preferência para produtos mais antigos ou com documentação mais aberta. Produtos muito fechados tem documentação muito restrita.

## 3. Informações a serem levantadas sobre o sistema

Descreva, de modo resumido, o produto em estudo com suas principais funções, aplicações e segmento no mercado bem como documente com fotos ou ilustrações.

O relatório deve conter os seguintes tópicos:  

1.	Descrição do produto selecionado.  
	•	Funções principais, público-alvo e contexto de uso;  
	•	Componentes e sensores utilizados;  
	•	Tecnologias de comunicação e controle embarcadas.  

2.	Análise técnica do funcionamento
	•	Principais módulos do sistema (sensores, atuadores, controle, interface, conectividade);
	•	Identificação de tecnologias críticas (por exemplo, protocolos sem fio, sistemas operacionais embarcados, técnicas de economia de energia).
	3.	Proposta de reprodução com ESP32
	•	Descrição conceitual de como as funcionalidades poderiam ser implementadas usando a ESP32 e componentes compatíveis com o ecossistema Arduino;
	•	Diagrama conceitual do sistema (pode ser esquemático, em blocos ou simulado com Fritzing);
	•	Limitações e desafios esperados.
	4.	Pesquisa bibliográfica e tecnológica
	•	4 artigos científicos sobre as tecnologias envolvidas (sensores, protocolos, RTOS, consumo de energia, conectividade, etc.);
	•	2 artigos sobre produtos ou aplicações similares em sistemas embarcados;
	•	Resumo de cada artigo destacando sua contribuição e relação com o produto estudado.
	5.	Comparativo com produtos similares
	•	Tabela comparativa de 3 a 5 produtos de mercado da mesma categoria.


Em seguida, faça um detalhamento de suas características específicas conforme a listagem abaixo. Cada produto pode ou não possuir todas as características listadas. Será necessário incluir todas as características encontradas.

**Obs**.: Para cada um dos detalhes será necessário incluir uma referência bilbiográfica podendo ser uma nota técnica do fabricante, um site de especificações do fabricante, manual do produto ou outras fontes de informações verificadas mostrando as características levantadas. Para cada característica aponte a fonte da informação.

### **Listagem de características**:

1. **Unidade de processamento**: Microcontrolador (MCU) ou Microprocessador (MPU): incluir características como arquitetura, fabricante, frequência de clock.

2. **Memória**: RAM (Memória Volátil), ROM / Flash (Memória Não-Volátil), Memória EEPROM (separada ou embutida).

3. **Sistema Operacional**:

   3.1 GPOS, RTOS, sem sistema operacional.

4. **Sensores e Atuadores**:

   4.1 **Sensores**: Detectam variáveis do ambiente como temperatura, umidade, pressão, luz, proximidade, etc., e enviam esses dados ao processador.

   4.2 **Atuadores**: São dispositivos que recebem comandos do processador para realizar ações físicas, como motores, LEDs, relés e válvulas.
   4.3 Conexão com a MCU/MPU: Normalmente conectados via GPIOs, barramentos de comunicação como I2C, SPI, ou mesmo comunicação sem fio em dispositivos IoT.

5. **Interfaces de Comunicação com fio**:

   5.1 I2C, SPI, UART, CAN, Ethernet, etc.

6. **Interfaces de Comunicação sem fio**:

   6.1 Wi-Fi, Bluetooth, Cat-M, NB-IoT, Zigbee, LoRaWAN, UWB, NFC.

7. **Unidades de Entrada/Saída (I/O)**:

   7.1 GPIO (General Purpose Input/Output): Entradas e saídas programáveis para interagir com sensores e atuadores.
   7.2 ADC/DAC (Conversor Analógico-Digital e Digital-Analógico): Converte sinais analógicos de sensores para digitais e vice-versa.
   7.3 PWM (Pulse Width Modulation): Utilizado para controlar dispositivos analógicos, como motores ou LEDs, modulando o sinal de saída.

8. **Fonte de Energia e Sistema de Alimentação**:

   8.1 **Tipos**: Baterias (Li-ion, NiMH) para portáteis, alimentação direta em sistemas automotivos ou industriais.
   8.2 **Gerenciamento de Energia** (PMIC): Controla e regula a distribuição de energia para componentes.
   8.3 **Backup de Energia**: Capacitores ou baterias de backup em sistemas que precisam de armazenamento de dados seguro.
   8.4 **Circuitos de reset** garantem que o sistema inicialize corretamente e permite o reset automático em caso de falha.
   8.5 **Supervisores de Energia**: Monitoram a voltagem de alimentação e reiniciam o sistema caso uma queda de tensão comprometa a integridade.

9. **Firmware e Atualizações**:

   9.1 Firmware: Código de baixo nível que controla o hardware e gerencia as operações básicas do dispositivo.  
   9.2 Atualizações Over-the-Air (OTA): suporte a atualizações de firmware remotamente.

10. **Unidade de Proteção e Segurança**:

    10.1 **Criptografia**: Hardware de criptografia embutido para proteger dados.
    10.2 **Hardware Security Module (HSM)**: Armazena chaves e credenciais com segurança.
    10.3 **Outras caracteísticas de Segurança**: Autenticação, controle de acesso, e uso de VPNs ou TLS para comunicação segura.

11. **Armazenamento Externo**:

    11.1 Cartões SD, NAND flash, HDD (em sistemas maiores).

12. **Interface com o Usuário (UI)**:

    12.1 **Displays**: OLED, LCD, LED segmentados para feedback visual.
    12.2 **Botões e Sensores de Toque**: Usados para entrada de comandos.

## 4. Artigos acadêmicos relacionados

Realizar uma pesquisa em publicações acadêmicas sobre:
1. 4 artigos científicos que detalhem uma ou mais de uma das principais tecnologias que viabilizam a existência do produto.
2. 4 artigos científicos sobre aplicação / uso do produto.

Obs.: Pesquise em bases de pesquisas acadêmicas (Periódicos Capes, Scopus, IEEExplore, etc.), **artigos científicos publicados em revistas científicas** (Journals).

Exemplos: Artigos sobre uma arquitetura de processador, sobre um protocolo de comunicação, sistemas operacionais, etc.

Para cada artigo faça um breve resumo dos aspectos mais importantes do trabalho e sua aplicação relacionada à sistemas embarcados.

## 5. Produtos relacionados

Liste pelo menos 5 produtos de mercado relacionados (mesma categoria) seja da mesma geração (época) ou de gerações diferentes na história do produto.

Faça uma tabela que compare as principais especificações e características de cada um dos produtos relacionados com o produto sendo estudado.

## 6. Formato da Entrega

O trabalho deve ser todo elaborado em um repositório (git) como fork deste repositório e todo o conteúdo deve estar em Markdown.

O trabalho deve ser todo desenvolvido em uma pasta com o nome do produto para que possa ser submetido como MR a este repositório.

**Data de Entrega: 24/04/2025**

### Orientações específicas

1. **Identificação**:

- No corpo do texto do projeto deve constar o Nome Completo e Matrícula de cada integrante do grupo.

2. **Formato dos arquivos**:
    - Todos os arquivos devem ser inseridos em uma pasta do repositório criado à partir do FORK do repositório original do trabalho;
    - A Pasta principal deve ser nomeado com o nome Abreviado do Produto (sem acento ou espaços);
    - Arquivos de texto devem estar em Markdown;
    - O arquivo principal em Markdown dentro da pasta do produto deve ter o nome padrão `README.md`. O trabalho pode ser estruturado em mais de um arquivo mas o principal deve seguir este padrão para poder ser indexado externamente;
    - Arquivos auxiliares de imagens podem ser usados em qualquer formato padrão que possa ser renderizado pelo Gitlab (JPG, PNG, PDF);

3. **Descrição do produto**: insiram uma ou mais fotos do produto escolhido na descrição do mesmo.

4. Na **listagem das características** insiram link da referência bibliográfica onde constam os detalhes documentados além de inserir ao final do trabalho a referência bibliográfica.

5. **Artigos acadêmicos**:
    - Cada artigo deve ser apresentado com um resumo sobre o que o mesmo contribui ou como se relaciona com o produto apresentado.
    - Insiram o link do PDF do artigo original no arquivo markdown.
    - **Atenção**: Não façam upload do PDF para o repositório.

## Critérios de Avaliação

| Item                                                                   | Peso |
| ---------------------------------------------------------------------- | ---- |
| Descrição geral do produto                                             | 15%  |
| Descrição de dalhada incluíndo referências bibliográficas de cada item | 40%  |
| Artigos acadêmicos                                                     | 30%  |
| Produtos relacionados                                                  | 15%  |
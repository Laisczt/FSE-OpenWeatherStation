# Trabalho 2 - 2026-1

## 1. Objetivos

Este trabalho tem como objetivo a realização de um estudo teórico-exploratório sobre um produto embarcado existente, identificando como suas principais funcionalidades poderiam ser total ou parcialmente recriadas utilizando uma ESP32 e sensores simples disponíveis no ecossistema ESP32.

A proposta é que o grupo compreenda as tecnologias envolvidas, levante a bibliografia acadêmica e técnica relacionada, e proponha um modelo conceitual de implementação que possa servir de base para um projeto prático em uma etapa posterior da disciplina.

O trabalho deve ser realizado em grupos de no máximo 4 integrantes.

## 2. Seleção do sistema embarcado

Cada grupo deve selecionar um produto embarcado de uso cotidiano ou industrial, que utilize sensores e atuadores passíveis de reprodução com componentes simples (por exemplo: sensores de temperatura, umidade, luminosidade, movimento, motores DC, relés, displays, IMUs, etc.).

Exemplos de categorias possíveis:  
	•	Termostatos inteligentes, estações meteorológicas, smart locks, dispositivos vestíveis;  
	•	Sistemas de irrigação automatizada;  
	•	Mini robôs móveis com sensores de distância;  
	•	Medidores ambientais ou de energia;  
	•	Dispositivos de automação residencial.  

**Sugestão**: Pesquisem a documentação dos produtos e dêem preferência para produtos mais antigos ou com documentação mais aberta. Produtos muito fechados tem documentação muito restrita.

## 3. Informações a serem levantadas sobre o sistema

Descreva, de modo resumido, o produto em estudo com suas principais funções, aplicações e segmento no mercado bem como documente com fotos, ilustrações e diagramas.

O relatório deve conter os seguintes tópicos:  

1.	**Descrição do produto selecionado:**  
	•	Funções principais, público-alvo e contexto de uso;  
	•	Componentes e sensores utilizados;  
	•	Tecnologias de comunicação e controle embarcadas.  

2.	**Análise técnica do funcionamento:**   
	•	Principais módulos do sistema (sensores, atuadores, controle, interface, conectividade);  
	•	Identificação de tecnologias críticas (por exemplo, protocolos sem fio, sistemas operacionais embarcados, técnicas de economia de energia).  

3.	**Proposta de reprodução com ESP32:**  
	•	Descrição conceitual de como as funcionalidades poderiam ser implementadas usando a ESP32 e componentes compatíveis com o ecossistema ESP-IDF;  
	•	Diagrama conceitual do sistema (pode ser esquemático ou em diarama de blocos);  
	•	Limitações e desafios esperados.  

4.	**Pesquisa bibliográfica e tecnológica:**  

	Realizar uma pesquisa em publicações acadêmicas sobre:
	- 4 artigos científicos que detalhem uma ou mais de uma das principais tecnologias que viabilizam a existência do produto.
	- 4 artigos científicos sobre aplicação / uso do produto.

	Obs.: Pesquise em bases de pesquisas acadêmicas (Periódicos Capes, Scopus, IEEExplore, etc.), **artigos científicos publicados em revistas científicas** (Journals).

	Exemplos: Artigos sobre uma arquitetura de processador, sobre um protocolo de comunicação, sistemas operacionais, etc.

	Para cada artigo faça um breve resumo dos aspectos mais importantes do trabalho e sua aplicação relacionada à sistemas embarcados.

5.	**Comparativo com produtos similares:**  

	Liste pelo menos 5 produtos de mercado relacionados (mesma categoria) seja da mesma geração (época) ou de gerações diferentes na história do produto.

	Faça uma tabela que compare as principais especificações e características de cada um dos produtos relacionados com o produto sendo estudado.

## 4. Formato da Entrega

O trabalho deve ser todo elaborado em um repositório (git) como fork deste repositório e todo o conteúdo deve estar em Markdown.

O trabalho deve ser todo desenvolvido em uma pasta com o nome do produto para que possa ser submetido como MR a este repositório.

**Data de Entrega: 11/06/2026**

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
| Descrição geral do produto                                             | 10%  |
| Descrição de dalhada incluíndo referências bibliográficas de cada item | 25%  |
| Proposta de implementação                                              | 25%  |
| Artigos acadêmicos                                                     | 30%  |
| Produtos relacionados                                                  | 10%  |


## Links dos Trabalhos de Semestres anteriores:

- [Lista de Sensores e Atuadores Disponíveis](/Lista_de_Sensores.md)

- [Trabalho 2025/2](https://gitlab.com/fse_fga/trabalhos-semestres-anteriores/trabalhos-2025_2/trabalho-2-2025-2)   
- [Trabalho 2025/1](https://gitlab.com/fse_fga/trabalhos-semestres-anteriores/trabalhos-2025-1/trabalho-1-2025-1)  
- [Trabalho 2024/2](https://gitlab.com/fse_fga/trabalhos-semestres-anteriores/trabalhos-2024_2/trabalho-1-2024-2)  

# Fabric-End-to-End-Data-Engineering-Project-Bing
### Projeto que pega dados de noticias da API Bing
Título do Projeto: Pipeline de Dados com Microsoft Fabric: Ingestão, Análise de Sentimento e Visualização de Notícias da Bing API

### Visão Geral:
Este projeto implementa um pipeline de dados end-to-end utilizando o Microsoft Fabric para coletar, processar e analisar notícias da Bing News API. O fluxo inclui ingestão, transformação incremental, análise de sentimento com Machine Learning, orquestração de pipelines e alertas em tempo real, finalizando com visualizações interativas no Power BI.

# Solution Architecture Overview
![Solution](https://github.com/Felipe30chaves/Fabric-End-to-End-Data-Engineering-Project-Bing/blob/main/Arquitetura.jpg)


### 1. Azure Data Factory (ADF)
Função Principal:
Orquestração de pipelines e ingestão de dados.

Recursos-Chave:

Copy Activity: Move dados entre fontes (HTTP, Blob Storage) e destinos (Data Lake, SQL DB).

Data Flows: Transformações visuais (join, pivot, filtro) sem código.

Triggers Agendados: Automação de execuções (ex.: coleta diária de dados da ECDC).

Monitoramento: Rastreamento de falhas em tempo real via Azure Monitor.

Caso de Uso:
Ingestão de dados da Bing API/ECDC para o Data Lake.

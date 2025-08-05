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


### 2. Microsoft Fabric
Visão Geral:
Plataforma unificada que integra ADF, Synapse, Power BI e Data Activator em um único workspace.

Vantagens:

OneLake: Camada única de armazenamento (sem duplicação de dados).

Experiência Coesa: Transição fluida entre ingestão, transformação e análise.

Governança Simplificada: Metadados centralizados e controle de acesso unificado.


### 3. Synapse Data Engineering
Função Principal:
Transformação de dados em escala usando Spark.

Recursos-Chave:

Notebooks Spark (Python/Scala): Processamento distribuído de grandes volumes.

Spark Pools: Clusters sob demanda com autoscaling.

Integração com Delta Lake: Suporte a transações ACID e time travel.

Caso de Uso:
Limpeza e enriquecimento de dados de COVID-19 (ex.: pivotamento de indicadores).


### 4. Synapse Data Science
Função Principal:
Desenvolvimento e operacionalização de modelos de ML.

Recursos-Chave:

Notebooks Integrados: Compatíveis com PyTorch, scikit-learn e MLflow.

Serviços Conectados: Azure Machine Learning para experimentação.

Previsão em Tempo Real: Deploy direto em pipelines.

Caso de Uso:
Modelos de previsão de propagação da COVID-19.

### 5. Delta Lake
Função Principal:
Camada de armazenamento confiável sobre Data Lakes.

Recursos-Chave:

ACID Transactions: Garantia de integridade em escritas concorrentes.

Schema Enforcement: Validação de estrutura dos dados.

Time Travel: Recuperação de versões históricas dos dados.

Benefícios:
Base para análises consistentes no Synapse/Power BI.

### 6. OneLake
Função Principal:
Repositório unificado de dados no Microsoft Fabric.

Características:

Estrutura Hub-and-Spoke: Organiza dados em "domínios" (ex.: Health, Finance).

Formato Delta Lake: Todos os dados são armazenados como Delta Tables por padrão.

Acesso Aberto: Compatível com Spark, SQL e ferramentas de terceiros.

Vantagem:
Elimina a fragmentação de dados entre Data Lake, Data Warehouse e BI.

### 7. Data Activator
Função Principal:
Detecção proativa de eventos em fluxos de dados.

Recursos-Chave:

Alertas em Tempo Real: Monitora métricas (ex.: picos de mortes por COVID).

Gatilhos Automatizados: Ações como e-mail, Teams ou reinício de pipelines.

Integração com Power BI: Ativa alertas diretamente de dashboards.

Caso de Uso:
Notificar equipes se ocupação de UTIs ultrapassar 90%.


### 8. Power BI
Função Principal:
Visualização e análise de dados.

Recursos-Chave:

Direct Lake Mode: Acesso direto a dados no OneLake (sem cópias).

DAX/M Language: Cálculos complexos e transformações em tempo real.

Data Activator Embed: Botões de alerta incorporados em relatórios.

Caso de Uso:
Dashboards de tendências de casos, mortes e testes na UE.

# Pipeline de Dados Telegram

## 1. Introdução

### 1.1 Objetivo

Neste projeto, será realizada a captação de dados provenientes de um bot do Telegram, o qual irá captar todas as mensagens digitadas pelos membros do grupo ao qual o bot está instalado. O objetivo é transferir esses dados para um Datalake, realizar o processamento dos dados em lote na nuvem e então fazer a análise dos dados tratados. Com isso, é possível utilizar essas informações para extrair insights valiosos, abrindo possibilidades para aprimorar serviços e explorar oportunidades de monetização.

### 1.2 O que é Pipeline?

Um pipeline de dados é um conjunto de processos que automatizam a coleta, transformação, armazenamento e análise de dados. Ele permite que os dados sejam transferidos de uma fonte de origem para um destino final de forma eficiente e organizada. Aqui estão os componentes principais de um pipeline de dados:

- **Ingestão de Dados:** Coleta de dados de diversas fontes, como bancos de dados, arquivos, APIs, sensores, entre outros. Isso pode incluir dados estruturados, semiestruturados ou não estruturados.

- **Transformação de Dados:** Limpeza, transformação e enriquecimento dos dados para que eles estejam no formato adequado para análise ou armazenamento. Isso pode incluir normalização, agregação, filtragem, e combinação de diferentes fontes de dados.

- **Armazenamento de Dados:** Armazenamento dos dados transformados em um local adequado para consulta e análise. Isso pode ser feito em bancos de dados relacionais, data warehouses, data lakes, ou outras soluções de armazenamento.

- **Processamento de Dados:** Execução de análises e processos sobre os dados armazenados. Isso pode incluir a execução de algoritmos de machine learning, análises estatísticas, relatórios e visualizações.

- **Orquestração e Automação:** Gestão e automação de todo o fluxo de trabalho do pipeline de dados, garantindo que os processos sejam executados na ordem correta e que os dados sejam processados de forma eficiente e confiável.

- **Monitoramento e Manutenção:** Monitoramento contínuo do pipeline para garantir que ele esteja funcionando corretamente, além de realizar a manutenção e ajustes necessários para lidar com problemas ou mudanças nas fontes de dados.

Os pipelines de dados são fundamentais em ambientes de big data e ciência de dados, pois permitem que grandes volumes de dados sejam processados de maneira consistente e escalável.

### 1.3 Pipeline do projeto

O pipeline de dados deste projeto começa com a captação de dados fornecidos pelos usuários do grupo do Telegram onde há um bot instalado. O bot foi configurado para captar as informações e por meio de uma API, conectar as fontes de dados à nuvem da Amazon Web Services (AWS).

Na plataforma da AWS, os dados são recebidos por uma função Lambda, que os organiza por dias no AWS S3. Diariamente, um AWS Event Bridge aciona um processo em lote no serviço Lambda, que transforma os dados brutos, extrai apenas as informações relevantes (data da mensagem, nome e número do contato, e a mensagem) e os armazena de maneira organizada no AWS S3. No processo de visualização, tabelas criadas a partir dos arquivos Parquet gerados no passo anterior possibilitam a realização de análises variadas usando a linguagem SQL. É possível extrair esses dados para um dashboard posteriormente.

![Texto Alternativo](https://github.com/vanessamo88/PipelineDadosTelegram/blob/main/Profissao%20Analista%20de%20dados%20M42%20Material%20de%20apoio%20arch.png?raw=true)

# 1. Descrição do Projeto

Este projeto open-source implementa uma arquitetura de DataLakehouse utilizando contêineres Docker para facilitar a integração, o armazenamento e a análise de grandes volumes de dados em formato distribuído. A solução permite centralizar dados de um banco de dados PostgreSQL (com a base Northwind carregada via script SQL) em um repositório escalável na nuvem, possibilitando consultas e visualizações rápidas para insights de negócios. Este pipeline de dados é ideal para ambientes de big data e análises avançadas, integrando ferramentas modernas de forma eficiente e acessível. Confira o repositório para mais detalhes sobre o código e configurações.

# 2. Objetivo do Projeto

O ojetivo deste projeto é colocar em prática os conhecimentos adquiridos no curso de Machine Learning e IA em ambientes distribuídos da Data Science Academy (DSA). Ele serve como uma solução totalmente open-source para que usuários de dados possam implementar uma arquitetura robusta e distribuída para processar e analisar grandes conjuntos de dados.

# 3. Arquitetura do Projeto

![Arquitetura do Projeto DataLakehouse](images/Arquitetura_projeto.png)

# 4. Tecnologias Utilizadas

- Git
- SQL
- PostgresSQL
- Airbyte
- Amazon S3
- Dremio
- Docker

## 4.1 Descrição de como as Tecnologias foram utilizadas

1. <strong> 🐘 PostgreSQL </strong>

   Utilizei o PostgreSQL como banco de dados transacional para armazenar e gerenciar os dados de origem do projeto. Foi também a fonte de dados para o Airbyte, permitindo fácil acesso aos dados do banco Northwind, que foram carregados via script SQL para uso e análise no pipeline.

2. <strong> 🐳 Docker Desktop </strong>

   O Docker Desktop foi a base para a criação dos contêineres que rodaram todos os serviços necessários para a solução. Com ele, criei contêineres para o PostgreSQL, Airbyte e Dremio, garantindo um ambiente controlado e eficiente para todos os processos de integração, armazenamento e análise de dados.

3. <strong> 🪼 Airbyte </strong>

   O Airbyte foi utilizado como ferramenta de integração de dados. Ele foi responsável por conectar à fonte de dados (neste caso, o PostgreSQL), onde os dados do banco Northwind foram carregados via script SQL. O Airbyte então carregava esses dados para o destino apropriado, mantendo-os atualizados e prontos para serem consumidos.

4. <strong> ☁️ Amazon S3 </strong>

   Para o armazenamento dos dados, utilizei o Amazon S3 como DataLake, garantindo um repositório centralizado, seguro e de alta disponibilidade na nuvem. O S3 foi escolhido devido à sua escalabilidade, facilidade de integração e baixo custo, permitindo armazenar dados em qualquer formato (como Parquet, CSV, JSON) sem complicações.

5. <strong> 🛠️ Dremio </strong>

   A peça chave para transformar esse projeto em um DataLakehouse foi o Dremio. O Dremio é uma plataforma poderosa que permite consultar dados armazenados no DataLake diretamente através de SQL, sem a necessidade de mover ou transformar fisicamente os dados. No meu projeto, os dados eram armazenados no S3 em formato Parquet, e o Dremio automaticamente reconhecia o formato dos arquivos, convertendo-os para tabelas relacionais, permitindo consultas rápidas e eficientes, além de insights prontos para o negócio.

# 5. Exibição do Projeto

1. Cônteires do PostgreSQL, Airbyte e do Dremio em execução no Docker Desktop

<br>

![Docker Desktop](images/Docker.png)

<br>

2. Dados carregados no PostgreSQL via script SQL. O script foi extraído do repositório do GitHub chamado northwind_psql do autor pthom.

<br>

![Schema do Banco de Dados](images/Schema_db.png)

<br>

![Tabelas no Banco de Dados PostgreSQL](images/tabelas_postgres.png)

3. Configurações de Source, Destination e Connection do Airbyte

<br>

![Tela de Source do Airbyte](images/Source_airbyte.png)

<br>

![Tela de Source do Airbyte](images/Source_config_airbyte.png)

<br>

![Tela de Source do Airbyte](images/Source_config_2_airbyte.png)

<br>

![Tela de Destination do Airbyte](images/Destination_airbyte.png)

<br>

![Tela de Destination do Airbyte](images/Destination_config_airbyte.png)

<br>

![Tela de Destination do Airbyte](images/Destination_config_2_airbyte.png)

<br>

![Tela de Connection do Airbyte](images/Connection_airbyte.png)

<br>

![Tela de Connection do Airbyte](images/Connection_config_airbyte.png)

<br>

![Tela de Connection do Airbyte](images/Connection_config_2_airbyte.png)

4. Bucket S3 criado e com os arquivos em parquet carregados através da carga do Airbyte

<br>

![Tela da Amazon S3](images/Bucket_s3.png)

<br>

![Tela da Amazon S3](images/Bucket_s3_pasta_dados.png)

<br>

![Tela da Amazon S3](images/Bucket_s3_pasta_dados_schema_transacional_prod.png)

<br>

![Tela da Amazon S3](images/Bucket_s3_pasta_schema_transacional_prod.png)

<br>

![Tela da Amazon S3](images/Bucket_s3_pasta_todas_as_tabelas.png)

<br>

![Tela da Amazon S3](images/Bucket_s3_arquivo_carregado.png)

5. Processamente e Análise no Dremio

<br>

![Tela do Dremio](images/Dremio_source.png)

<br>

![Tela do Dremio](images/Dremio_source_arquivo.png)

<br>

![Tela do Dremio](images/Dremio_source_arquivo_config.png)

<br>

![Tela do Dremio](images/Dremio_source_tabelas.png)

<br>

![Tela do Dremio](images/Dremio_source_arquivo_tratado.png)

<br>

![Tela do Dremio](images/Dremio_resultado_final.png)

<br>

![Tela do Dremio](images/Dremio_resultado_query_1.png)

<br>

![Tela do Dremio](images/Dremio_resultado_query_2.png)

## Análise Rápida de Resultado:

1. A categoria que mais vendeu foi a de Beverages com 9.532 produtos vendidos e somando um valor total de R$ 267.890,00. Já a categoria que menos vendeu foi a de Grains/Cereals (Grãos e Cereais) com 4.562 itens vendidos e um valor de R$ 95.754,00, tendo uma diferença de R$ 172.136 entre ambos os produtos;

2. A categoria Beverages representa 21% do Faturamento Total, enquanto a de Grains/Cereals representa somente 8%;

3. O produto com maior valor vendido do catálogo foi o Côte de Blaye com 623 unidades vendidas e o um valor total de R$ 141.399. Já o produto com menor valor vendido é o Chocolade com apenas 138 unidades vendidas e um total de R$ 1.370;

4. Apesar do produto Côte de Blaye ter sido o produto com maior valor vendido, o produto mais vendido foi o Camembert Pierrot com 1.577 unidades vendidas, porém com somente 4% do valor total vendido entre todos os produtos. Para efeitos de comparação, o produto Côte de Blaye tem 11% do total vendido.

# 6. Instalação e Configuração

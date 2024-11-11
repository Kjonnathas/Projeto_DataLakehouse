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

5. Processamento e Análise no Dremio

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

- Pré-requisitos:

  1. Instalar o Docker Desktop;

     Link para download: https://www.docker.com/

  2. Instalar o PgAdmin (Client do PostgreSQL);

     Link para download: https://www.pgadmin.org/download/

  3. Instalar o Airbyte;

     Link para download: https://docs.airbyte.com/using-airbyte/getting-started/oss-quickstart

  4. Instalar o Git;

     Link para download: https://git-scm.com/downloads

  5. Criar uma conta na AWS;

     Link do site: https://aws.amazon.com/pt/console/

  6. Criar uma conta no Dremio;

     Link do site: https://www.dremio.com/get-started/

<br>

- Passo a passo:

1. Após ter instalado os softwares informados e criado as contas, o primeiro passo é criar os contêineres no Docker. Abra o seu prompt de comando ou o terminal do Git e digite:

```

docker run --name <conteiner_name> -p 5432:5432 -e POSTGRES_DB=<db_name> -e POSTGRES_USER=<username> -e POSTGRES_PASSWORD=<password> -d postgres
```

1.1 Após rodar este comando, o Docker criará o volume, a imagem e o contêiner do PostgreSQL.

1.2 Em seguida, abra o PgAdmin (se não instalou ainda, precisará instalar agora). Após abrir o PgAdmin, siga as seguintes etapas:

<br>

![Criando o Servidor no PostgreSQL](images/Postgres_criar_servidor.png)

<br>

![Criando o Servidor no PostgreSQL](images/Postgres_criar_servidor_2.png)

<br>

![Criando o Servidor no PostgreSQL](images/Postgres_criar_servidor_3.png)

<br>

![Criando o Servidor no PostgreSQL](images/Postgres_criar_servidor_4.png)

1.3 Após criar o schema, clique com o botão direito sobre o objeto
tables e selecione query tool. Em seguida irá abrir uma tela para criar códigos em SQL. Vá até a pasta src/scripts e copie o código em SQL e cole no query tool e depois aperte F5 ou clique no botão de executar disponível para que seja feita a criação das tabelas no seu schema;

1.4 Com as tabelas criadas, podemos prosseguir com a criação do contêiner do Airbyte. É preciso fazer o download do arquivo disponível no site do Airbyte através do link disponibilizado. Feito o download, o arquivo será baixado zipado. Faça a descompactação do arquivo. Basta clicar com o botão direito e extrair tudo. Após isso, será necessário criar uma variável de ambiente para o que o sistema operacional entenda o comando do airbyte. Entre na pasta do airbyte e copie o caminho. Em seguida, vá até as variáveis de ambiente, clique no Path, editar e novo. Cole o caminho e depois clique em ok para salvar. Agora o sistema operacinal já deve reconhecer os comandos que vamos precisar digitar:

```
abctl version
```

Obs: Se o comando acima não funcionar significa que algo de errado ao salvar a variável de ambiente ocorreu. Revise essa etapa! Se o prompt devolver a versão é porque funcionou normalmente e o sistema já identifica o comando.

1.5 Com o Docker Desktop aberto, digite o comando abaixo no seu prompt de comando:

```
abctl local install
```

Essa etapa costuma demorar pela primeira vez, então tenha paciência! É importante verificar na documentação a exigência mínima de hardware, pois o Airbyte é pesado e consome bastante memória. Se seu computador não for muito bom, é provável que vá ter problemas com travamento.

1.6 Se tudo der certo e a instalação concluir com sucesso, digite o comando:

```
abctl local credentials
```

O comando acima lhe dará um ID e uma senha, que serão necessários para logar no Airbyte via navegador. Teste a sua conexão indo até o navegador e acesse "localhost:8000", digite as credenciais e resolvido.

1.7 Depois que estiver funcionando, vamos precisar colocar o contêiner do Airbyte e do PostgreSQL na mesma rede para que eles possam se comunicar. Caso contrário, ao tentar realizar a conexão da fonte de dados no Airbyte resultará em erro. Sendo assim, vá ao prompt de comando e digite:

```
docker network inspect bridge
```

Este comando apresentará uma estrutura json e na chave Containers tanto o PostgreSQL quanto o Airbyte precisam aparecer. Acredito que por padrão o PostgreSQL já vai para a rede Bridge, mas no caso do Airbyte não. Mas para evitar problemas você pode incluir o parâmetro "--network bridge" ao criar o contêiner do PostgreSQL. Caso já tenha criado, basta excluir o contêiner no Docker Desktop e criar novamente com a inclusão deste parâmetro. Em seguida, vamos incluir o contêiner do Airbyte na rede Bridge. Para isso, digite o seguinte comando:

```
docker network disconnect <rede_atual> <container_name>
```

Obs: Para saber em que rede o contêiner do Airbyte está digite: docker inspect -f '{{.NetworkSettings.Networks}}' container_name. Sabendo o nome da rede substitua no código fornecido acima. Em seguida, continue com o comando:

```
docker network connect bridge <container_name>
```

O código acima irá incluir o contêiner do Airbyte na rede Bridge e com isso os dois contêineres estarão se comunicando.

1.8 Agora é a parte de configurar o source, o destination e a connection no Airbyte. Visualizando as imagens disponibilizadas acima é possível fazer as configurações da source sem grandes problemas. Não seguirei com o destination pois a Amazon faz cobrança e não quero que algo acabe não saindo como o esperado e gere custos não planejados. Isso quer dizer que, vou ficar devendo a parte da Amazon e do Dremio. Porém, há vários tutoriais e vídeos gratuitos sobre o assunto. Caso queira muito seguir, procure por esse material e siga em frente!

<br>

## Licença

Este projeto está licenciado sob os termos da licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

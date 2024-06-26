# ETL_API_cervejas
O objetivo do teste é consumir dados de uma API, persisti-los em uma arquitetura de data lake com três camadas, sendo a primeira de dados brutos, a segunda selecionada e particionada por localização, e a terceira contendo dados analíticos agregados.

Camada Bronze: Dados brutos/dados não curados geralmente persistem em seu formato nativo (mas depende de você) Prata: Transformados em um formato de armazenamento colunar, como Parquet ou Delta, particionado por localização da cervejaria Ouro: Crie uma visualização agregada com o número de lojas por tipo e localização

# Arquitetura
![Diaga_cerveja](https://github.com/RobertMaklyn/Engenharia_de_Dados_Projeto-/assets/147719579/598ceea0-d8ee-472e-95cb-5b675bf22a63)

1 – Na sua conta do Microsoft Azure, crie um grupo de recursos contendo os seguintes recursos:

Azure Data Lake Storage: como datalake

Azure Data Factory: como orquestrador do projeto

Azure Databricks: como ambiente/plataforma de desenvolvimento para código Python/PySpark/SQL

Azure Key Vault: para armazenamento seguro de senhas/credenciais, cadeias de conexão por meio de "segredos"

![recursos3](https://github.com/RobertMaklyn/Engenharia_de_Dados_Projeto-/assets/147719579/d68bf351-bb61-46fd-9551-4fdd9de3cf24)

2 – Crie um contêiner cervejas no Azure Data Lake Storage com diretórios bronze, prata e ouro para armazenamento de dados em suas respectivas camadas

3 – Use o Azure Key Vault para armazenar o token de acesso da instância do Azure Databricks e as senhas e a cadeia de conexão do Azure Data Lake Storage.

4 - Crie uma política de acesso no Key Vault para o Data Factory acessar os segredos do Key Vault.

5 – Inicie a instância do Azure Databricks e crie um escopo para acessar os arquivos do Azure Data Lake Storage e gerar o token de acesso para ser armazenado no Azure Key Vault.

6 – Faça um ponto de montagem para acessar os diretórios do seu contêiner no Azure Data Lake Storage.

7 - Crie 3 notebooks utilizando Python e PySpark para realizar as transformações, cada notebook referente a uma camada: bronze, prata, ouro.

8 – Acesse a instância do Azure Data Factory, crie um pipeline, no painel de atividades, expanda a opção databricks, selecione os notebook. Configure serviços vinculados, configure os caminhos do notebook e vincule a execução sequencial de notebooks em caso de execução bem-sucedida.

![datafactory](https://github.com/RobertMaklyn/Engenharia_de_Dados_Projeto-/assets/147719579/55184165-a428-4f47-9276-e4969248b118)

9 - Valide o pipeline, salve e debug.

10 - Você pode verificar se os dados foram salvos em cada respectivo diretório no Azure Data Lake Storage.

![lakehouse](https://github.com/RobertMaklyn/Engenharia_de_Dados_Projeto-/assets/147719579/63dab03f-0c54-4ab1-ae8e-54ee8683a49c)

Você pode verificar o código clicando [aqui](https://github.com/RobertMaklyn/ETL_API_cervejas/tree/main/azure_databricks_notbooks)
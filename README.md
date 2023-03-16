# Projeto final - Academia Mulheres em Tech Data Engineer da parceria Gama Academy e Accenture

## Grupo 1: The last of Us!
<table align="center">
  <tr>
    <td align="center">
      <a href="https://github.com/alinetsbarreto">
        <img src="https://avatars.githubusercontent.com/u/124752253?v=4" width="100px;" alt="Foto Aline Barreto"/><br>
        <sub style="color: purple;">
          <b>Aline Barreto </b>
        </sub><br>
         <a href="https://www.linkedin.com/in/alinetsbarreto/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" height="15px"></a>
      </a>
    </td>
    <td align="center">
      <a href="https://github.com/gabieng">
        <img src="https://avatars.githubusercontent.com/u/103044907?v=4" width="100px;" alt="Gabriela Silva"/><br>
        <sub style="color: purple;">
          <b> Gabriela Silva </b>
        </sub><br>
         <a href="https://www.linkedin.com/in/gabriela-ssilva/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" height="15px"></a>
      </a>
   </td>
    <td align="center">
      <a href="https://github.com/paulacapuano">
        <img src="https://avatars.githubusercontent.com/u/61557397?v=4" width="100px;" alt="Paula Capuano"/><br>
        <sub style="color: purple;">
          <b> Paula Capuano </b>
        </sub><br>
         <a href="https://www.linkedin.com/in/paulacapuano/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" height="15px"></a>
    </td>
  </tr>
</table>


# Desafio

Desenvolver uma aplicação em Python para carga de arquivos em um banco de dados SQL e gerar relatórios estatísticos visando a descoberta de fraudes bancárias.

## Objetivo inicial 

O objetivo inicial é analisar estes arquivos criando uma base de dados relacional para fazer a carga e depois analisá-la. 
O cartão fraudado, será aquele que tiver movimentações abaixo de 2 minutos de espaçamento entre as transações


## Estratégia 

Fazer um processo de ETL dos dados recebidos utilizando Spark e fazer análise de fraudes pelo banco SQL Server e análises estatísticas e relatórios pelo PowerBI.

<img src="https://github.com/paulacapuano/gama-accenture-grupo1/blob/main/imagem/estrategia.png">
</p>

 
 ## Execução
1. Criar VM no portal Azure e conectar via chave SSH com a máquina local
2. Transformar os dados com Spark
3. Carregar o dados resultantes no banco de dados SQL Server
4. Analisar os dados de clientes e fraudes por SQL
5. Fazer análises estatíticas e gerar relatório no PowerBI

## 1. Criar VM no portal Azure e criar ambiente para o Spark
https://user-images.githubusercontent.com/103044907/225511989-9ac6143c-978c-40c9-bc8b-dda9973e0ef2.mp4

* Conectar com a máquina local via chave SSH
* Conectar VM com VS code
* Instalar jupyter notebook e preparar o ambiente:
```shell
sudo apt update
sudo apt upgrade
sudo apt install python3-pip
sudo apt install unixodbc-dev 
pip install pyodbc
sudo apt install default-jre
sudo apt-get install jupyter-notebook

```
* Criar o ambiente do Spark
* Transferir os arquivos csv com os dados para a VM

## 2. Transformação dos dados com Spark

[Script com a transformação dos dados com Spark:](https://github.com/paulacapuano/gama-accenture-grupo1/blob/main/scriptSpark-notebook.ipynb)

* Código para juntar csvs da mesma entidade ([clientes](https://github.com/paulacapuano/gama-accenture-grupo1/tree/main/Dados/Clientes), [transação_in](https://github.com/paulacapuano/gama-accenture-grupo1/tree/main/Dados/Transacao-I) e [transação_out](https://github.com/paulacapuano/gama-accenture-grupo1/tree/main/Dados/Transacao-Out)) em um dataframe.
* Código para juntar os dataframes de transação_in e transação_out em um dataframe de transações.
* Código para verificar se tem colunas de ID repetidos no dataframe de transação.
* Código para verificar os tipos dos dados nas colunas nos dataframes.


## 3. Carregar os dados resultantes no banco de dados SQL Server

### 3.1 Criar banco de dados:
https://user-images.githubusercontent.com/103044907/225514324-97985f7c-6efb-4e3f-a7bc-934a000db8f1.mp4

### 3.2 Script conexão:
[Script de conexão com o banco de dados e migração:](https://github.com/paulacapuano/gama-accenture-grupo1/blob/main/script-Spark-conexao-banco.ipynb)

* Instalação do ODBC 18 e pyodbc para conexão com banco de dados.
* Criação de tabelas no banco de dados.
* Inserção dos dados no banco de dados.


## 4. Analisar os dados de clientes e fraudes por SQL
[Script com as análises em SQL:](https://github.com/paulacapuano/gama-accenture-grupo1/blob/main/analise_SQL_clientes_fraudes.sql)

* Cria uma tabela que une todos os clientes cadastrados e não cadastrados que estão apenas na tabela de transações.
* Cria uma tabela com a análise de fraude pela diferença de 2 min, nessa tabela é inserido uma coluna "Fraude" que indica se a transação é fraudulenta ou não.

### Modelo de entidades e relacionamentos
<img src="https://github.com/paulacapuano/gama-accenture-grupo1/blob/main/imagem/relacionamento.png">
</p>


## 5.Fazer análises estatíticas e gerar relatório no PowerBi

<img src="https://github.com/paulacapuano/gama-accenture-grupo1/blob/main/imagem/powerbi.png">
</p>

## 6. Modelo de Machine Learning com DecisionTreeClassifier (usando Py script)
![ml](https://user-images.githubusercontent.com/103044907/225615442-73b16da4-2adc-4263-8664-83f78481ba90.jpg)

###Para construir um modelo de machine learning capaz de prever se uma transação é uma fraude ou não com base nas variáveis selecionadas no Powerbi, deve-se seguir os seguintes passos:

1. Juntar as informações das duas tabelas, clientes cadastro e fraudes, usando a coluna "id" como chave para unir as tabelas. A tabela consolidada com as informações está em:
[Tabela ML](https://github.com/paulacapuano/gama-accenture-grupo1/blob/main/Dados/Resultado/tabml.xlsx)

2. Transformar as variáveis categóricas em variáveis numéricas, usando a técnica de one-hot encoding. Para isso, você pode usar a função get_dummies() do pandas.

3. Dividir o conjunto de dados em conjunto de treinamento e conjunto de teste usando a função train_test_split() do scikit-learn.

4. Treinar um modelo de classificação usando a árvore de decisão (DecisionTreeClassifier) do scikit-learn.

5. Resultado:

![Capturar](https://user-images.githubusercontent.com/103044907/225618177-eca7cf5a-8bfc-44b2-a23a-17f13c1050bc.JPG)



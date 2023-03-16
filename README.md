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

Analisar arquivos de clientes e transações, criando uma base de dados relacional para fazer a carga e depois analisá-la.


## Estratégia 

Fazer um processo de ETL dos dados recebidos utilizando Spark, fazer análise de fraudes pelo banco SQL Server e análises estatísticas e relatórios pelo PowerBI.

<img src="https://github.com/paulacapuano/gama-accenture-grupo1/blob/main/imagem/estrategia.png">
</p>

 
 ## Execução
1. Criar VM no portal Azure e conectar via chave SSH com a máquina local
2. Transformar os dados com Spark
3. Carregar o dados resultantes no banco de dados SQL Server
4. Analisar os dados de clientes e fraudes por SQL
5. Fazer análises estatíticas e gerar relatório no PowerBI

## 1. Criar VM no portal Azure e criar ambiente para o Spark
* Conectar com a máquina local via chave SSH
* Conectar VM com VS code
* Instalar jupyter notebook
* Criar o ambiente do Spark
* Transferir os arquivos csv com os dados para a VM

## 2. Transformação dos dados com Spark

[Script com a transformação dos dados com Spark:](https://github.com/paulacapuano/gama-accenture-grupo1/blob/main/scriptSpark.ipynb)

* Código para juntar csvs da mesma entidade ([clientes](https://github.com/paulacapuano/gama-accenture-grupo1/tree/main/Dados/Clientes), [transação_in](https://github.com/paulacapuano/gama-accenture-grupo1/tree/main/Dados/Transacao-I) e [transação_out](https://github.com/paulacapuano/gama-accenture-grupo1/tree/main/Dados/Transacao-Out)) em um dataframe.
* Código para juntar os dataframes de transação_in e transação_out em um dataframe de transações.
* Código para verificar se tem colunas de ID repetidos no dataframe de transação.
* Código para verificar os tipos dos dados nas colunas nos dataframes.


## 3. Carregar o dados resultantes no banco de dados SQL Server
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



## Bibliotecas


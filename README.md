# Credit Data Exploration and Analysis with SQL
 Credit Data Exploration and Analysis with SQL


# **Exploração e análise de dados de crédito com SQL**

*Esse notebook faz parte do curso SQL para análise de dados da EBAC.*

## Os dados: 

Os dados representam informações de clientes de um banco e contam com as seguintes colunas: 

* idade = idade do cliente
* sexo = sexo do cliente (F ou M)
* dependentes = número de dependentes do cliente
* escolaridade = nível de escolaridade do clientes
* salario_anual = faixa salarial do cliente
* tipo_cartao = tipo de cartao do cliente
* qtd_produtos = quantidade de produtos comprados nos últimos 12 meses
* iteracoes_12m = quantidade de iterações/transacoes nos ultimos 12 meses
* meses_inativo_12m = quantidade de meses que o cliente ficou inativo
* limite_credito = limite de credito do cliente
* valor_transacoes_12m = valor das transações dos ultimos 12 meses
* qtd_transacoes_12m  = quantidade de transacoes dos ultimos 12 meses

A tabela foi criada no **AWS Athena** junto com o **S3 Bucket** com uma versão dos dados disponibilizados em: https://github.com/andre-marcos-perez/ebac-course-utils/tree/main/dataset


## **Exploração de dados:**

A primeira fase da análise é entender o que tem na nossa matéria prima. Vamos a exploração de dados:

**Qual a quantidade de informações temos na nossa base de dados?**

Query: SELECT count(*) FROM credito
> Reposta: 2564 linhas

**ps.:** A base de dados do link acima contém mais linhas do que a seleção utilizada. Você pode utilizar todas as linhas ou considerar apenas uma fração dos dados. Na prática, quanto maior a quantidade de dados utilizada, mais confiável a análise! Mas existem limites computacionais e financeiros na qual a redução de dados para análise para fins de estudo se torna interessante. 

**Como são os dados** 

Query: SELECT * FROM credito LIMIT 10;
![Dez primeiras linhas do dataset](https://github.com/marianeneiva/sqlEBAC/blob/main/limit10.png?raw=true)

> É possível reparar que existem algumas informações nulas na tabela (valor na), vamos olhar mais de perto para os valores de cada coluna! 

**Quais os tipos de cada dado**

**Query:** DESCRIBE credito

![Descrição dos tipos de dados](https://github.com/marianeneiva/sqlEBAC/blob/main/describe.png?raw=true)


Agora que ja entendemos quais são os tipos de dados, vamos olhar mais atentamente para as varíaveis que não são numéricas.

**Quais são os tipos de escolaridade disponíveis no dataset?**

**Query:** SELECT DISTINCT escolaridade FROM credito

![Tipos de escolaridade](https://github.com/marianeneiva/sqlEBAC/blob/main/escolaridade.png?raw=true)

> Os dados contam com vários níveis de escolaridade e é possível perceber que temos valores nulos (na) no dataset, trataremos isso mais tarde!

Será que temos mais valores nulos?

**Quais são os tipos de estado_civil disponíveis no dataset?**

**Query:** SELECT DISTINCT estado_civil  FROM credito

![Tipos de estado civil](https://github.com/marianeneiva/sqlEBAC/blob/main/escolaridade.png?raw=true)

> Novamente encontramos valores nulos nos dados de estado civil!

**Quais são os tipos de salario_anual disponíveis no dataset?**

**Query:** SELECT DISTINCT salario_anual  FROM credito

![Tipos de salario anual](https://github.com/marianeneiva/sqlEBAC/blob/main/salario_anual.png?raw=true)

> Os salários nesse dataset não estão expostas com o valor exato que o cliente ganha. O que está informado é a faixa salarial de cada um. Também contem dados nulos. 


**Quais são os tipos de cartão disponíveis no dataset?**

**Query:** SELECT DISTINCT tipo_cartao  FROM credito

![Tipos de cartão](https://github.com/marianeneiva/sqlEBAC/blob/main/cartao.png?raw=true)

> Aqui vemos que não há necessidade de tratar valores nulos.


# Conclusão

Essas foram **algumas** análises extraídas do dataset de crédito.  

Alguns insights interessantes:

- a maior parte dos clientes possui renda até 40K 
- a maior parte dos clientes é masculino!
- a escolaridade não parece influenciar no limite nem no tipo do cartão
- os clientes com maiores limites são em sua maioria homens 
- os clientes com menores limites são em sua maioria mulheres
- dentre os menores limites não há presença de cartão platinum
- a faixa salarial impacta diretamente no limite de crédito
- nao existem clientes com salário anual acima de 60K do sexo feminino

**Uma exploração maior dos dados pode explicar porque as mulheres tem menor crédito. Isso também pode ser um problema cultural que pode ser repensado!**





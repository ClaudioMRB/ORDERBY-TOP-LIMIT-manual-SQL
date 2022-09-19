# ORDERBY-TOP-LIMIT-manual-

## ---------------A ORDEM SQL POR Palavra-Chave----------------------

A palavra-chave é usada para classificar o conjunto de resultados em ordem ascendente ou descendente.`ORDER BY`

A palavra-chave classifica os registros em ordem ascendente por padrão. Para classificar os registros em ordem decrescente, use a palavra-chave.`ORDER BY`` DESC`

### ORDEM POR SintaxE

SELECT *column1*, *column2, ...*
FROM *table_name*

###### ORDER BY *column1, column2, ...* ASC|DESC;

------

## Banco de dados de demonstração

Abaixo está uma seleção da tabela "Clientes" no banco de dados de amostras northwind:

| CustomerID | CustomerName                       | PostalCode | ContactName        | Address                       | City        | Country |
| :--------- | :--------------------------------- | :--------- | :----------------- | :---------------------------- | :---------- | :------ |
| 1          | Alfreds Futterkiste                | 12209      | Maria Anders       | Obere Str. 57                 | Berlin      | Germany |
| 2          | Ana Trujillo Emparedados y helados | 05021      | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | Mexico  |
| 3          | Antonio Moreno Taquería            | 05023      | Antonio Moreno     | Mataderos 2312                | México D.F. | Mexico  |
| 4          | Around the Horn                    | WA1 1DP    | Thomas Hardy       | 120 Hanover Sq.               | London      | UK      |
| 5          | Berglunds snabbköp                 | S-958 22   | Christina Berglund | Berguvsvägen 8                | Luleå       | Sweden  |

------

## ORDEM POR EXEMPLO

A seguinte instrução SQL seleciona todos os clientes da tabela "Clientes", classificada pela coluna "País":

### Exemplo

SELECT * FROM Customers
ORDER BY Country;

------

## ORDEM POR EXEMPLO DESC

A seguinte instrução SQL seleciona todos os clientes da tabela "Clientes", classificados DESCENDO pela coluna "País":

### Exemplo

SELECT * FROM Customers
ORDER BY Country DESC;

------

## PEDIDO POR Várias colunas Exemplo

A seguinte declaração SQL seleciona todos os clientes da tabela "Clientes", classificada pela coluna "País" e pela coluna "CustomerName". Isso significa que ele encomenda por País, mas se algumas linhas têm o mesmo País, ele as encomenda pelo CustomerName:

### Exemplo

SELECT * FROM Customers
ORDER BY Country, CustomerName;

------

## ORDEM POR Várias Colunas Exemplo 2

A seguinte instrução SQL seleciona todos os clientes da tabela "Clientes", classificada ascendente pela coluna "País" e descendente pela coluna "CustomerName":

### Exemplo

SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;



### **EXEMPLOS**

* Ordernardo por preço na ordem crescente

**SELECT** * **FROM** tb_sale **ORDER BY** price

OU 

**SELECT** * **FROM** tb_sale **ORDER BY** price **ASC**

* Ordernardo por preço na ordem  descrescente

**SELECT** * **FROM** tb_sale **ORDER BY** price **DESC**

OU 

**SELECT** * **FROM** tb_sale **ORDER BY** seller_id,  price **DESC**



# -----------SQL TOP, LIMITE, BUSCAR CLÁUSULA PRIMEIRO OU ROWNUM-----------------------------

[❮ Anterior](https://www.w3schools.com/sql/sql_delete.asp)[Próxima ❯](https://www.w3schools.com/sql/sql_min_max.asp)

------

## A cláusula top de seleção sql

A cláusula é usada para especificar o número de registros a serem devolvidos.`SELECT TOP`

A cláusula é útil em grandes mesas com milhares de registros. O retorno de um grande número de registros pode impactar o desempenho.`SELECT TOP`

**Nota:** Nem todos os sistemas de banco de dados suportam a cláusula. O MySQL suporta a cláusula para selecionar um número limitado de registros, enquanto o Oracle usa e .` SELECT TOP``LIMIT`` FETCH FIRST *n* ROWS ONLY``ROWNUM`

**Grade de acesso SQL Server / MS:**

SELECT TOP *number*|*percent* *column_name(s)*
FROM *table_name
*WHERE *condition*;

**Sintaxe MySQL:**

SELECT *column_name(s)*
FROM *table_name
*WHERE *condition*
LIMIT *number*;

**Oráculo 12 Sintaxe:**

SELECT *column_name(s)*
FROM *table_name
*ORDER BY *column_name(s)*
FETCH FIRST *number* ROWS ONLY;

**Sintaxe oracle mais antiga:**

SELECT *column_name(s)*
FROM *table_name*
WHERE ROWNUM <= *number*;

**Sistribução oracle mais antiga (com ORDEM BY):**

SELECT *
FROM (SELECT *column_name(s)* FROM *table_name* ORDER BY *column_name(s)*)
WHERE ROWNUM <= *number*;

------

## Banco de dados de demonstração

Abaixo está uma seleção da tabela "Clientes" no banco de dados de amostras northwind:

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| :--------- | :--------------------------------- | :----------------- | :---------------------------- | :---------- | :--------- | :------ |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |

------

## SQL TOP, LIMIT and FETCH FIRST Examples

A seguinte instrução SQL seleciona os três primeiros registros da tabela "Clientes" (para SQL Server/MS Access):

### Exemplo

SELECT TOP 3 * FROM Customers;

A seguinte instrução SQL mostra o exemplo equivalente para MySQL:

### Exemplo

SELECT * FROM Customers
LIMIT 3;

A seguinte instrução SQL mostra o exemplo equivalente para Oracle:

### Exemplo

SELECT * FROM Customers
FETCH FIRST 3 ROWS ONLY;

------

## EXEMPLO DE PERCENTUAL SQL

A seguinte instrução SQL seleciona os primeiros 50% dos registros da tabela "Clientes" (para SQL Server/MS Access):

### Exemplo

SELECT TOP 50 PERCENT * FROM Customers;

A seguinte instrução SQL mostra o exemplo equivalente para Oracle:

### Exemplo

SELECT * FROM Customers
FETCH FIRST 50 PERCENT ROWS ONLY;

------

## ADICIONE UMA CLÁUSULA ONDE

A seguinte instrução SQL seleciona os três primeiros registros da tabela "Clientes", onde o país é "Alemanha" (para SQL Server/MS Access):

### Exemplo

SELECT TOP 3 * FROM Customers
WHERE Country='Germany';

A seguinte instrução SQL mostra o exemplo equivalente para MySQL:

### Exemplo

SELECT * FROM Customers
WHERE Country='Germany'
LIMIT 3;

A seguinte instrução SQL mostra o exemplo equivalente para Oracle:

### Exemplo

SELECT * FROM Customers
WHERE Country='Germany'
FETCH FIRST 3 ROWS ONLY;

### **EXEMPLO**

SELECT * FROM tb_sale ORDER BY price DESC LIMIT 2 OFFSET 4
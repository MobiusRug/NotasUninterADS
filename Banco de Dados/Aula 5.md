# SUBQUERIES
- a declaração de uma query dentro de outra query
- O select de uma subquery é sempre declarado entre parênteses;
- As cláusulas para tratamento de subconsultas são os operadores relacionais not in, any, all e not exists.

## Operadores Relacionais

### In
- Verifica se um ou mais valores, presentes em uma coluna, possuem correspondência em uma lista ou em um resultado de uma subconsulta

`where expressao [not] in (subconsulta);`

Consulta com valores predefinidos:

```sql
select nome,cidadeId from cliente where cidadeId in (1,5);
```

Consulta dinâmica:

```sql
select nome, cidadeId from cliente where cidadeId
in (select id from cidade where nomeCidade = ‘Curitiba’
or nomeCidade = ‘Imperatriz’);
```

### Exists

- é responsável pela realização de um teste de existência, retornando um valor booleano
- palavra-chave exists não é precedida por um nome de coluna, constante ou qualquer outra expressão.

`where [not] exists (subconsulta);`

```sql
SELECT Nome
FROM Clientes
WHERE EXISTS (
    SELECT 1
    FROM Pedidos
    WHERE Pedidos.ClienteID = Clientes.ID
);
--a consulta retorna os nomes dos clientes que têm pelo menos um pedido na tabela de pedidos
```

-  Retorna verdadeiro ou falso;
-  Possui como argumento um select;
- A subquery não devolve nenhuma tabela resultante
- Exists pode ser negado por um not.

### Any 

- recuperar registros da consulta principal que satisfaçam a condição de comparação com qualquer outro registro recuperado na subconsulta.

`valor operador ANY (subconsulta)`

- Suponha que você queira encontrar todos os produtos que têm um preço maior do que qualquer preço dos produtos de uma determinada categoria. Você pode usar o operador `ANY` para realizar essa consulta:

```sql
SELECT Nome
FROM Produtos
WHERE Preco > ANY (
    SELECT Preco
    FROM Produtos
    WHERE Categoria = 'Eletrônicos'
);

--a subconsulta retorna uma lista de preços dos produtos da categoria 'Eletrônicos'. O operador `ANY` compara o preço de cada produto na tabela principal com a lista de preços da subconsulta e retorna os produtos cujos preços são maiores do que pelo menos um dos preços da subconsulta.
```

### All

- comparar um valor com todos os valores retornados por uma subconsulta
- `valor operador ALL (subconsulta)`

```sql
SELECT Nome
FROM Produtos
WHERE Preco > ALL (
    SELECT Preco
    FROM Produtos
    WHERE Categoria = 'Roupas'
);
--a subconsulta retorna uma lista de preços dos produtos da categoria 'Roupas'. O operador `ALL` compara o preço de cada produto na tabela principal com todos os preços da subconsulta e retorna os produtos cujos preços são maiores do que todos os preços da subconsulta.
```

### Subquery correlacionada

- é uma subconsulta em SQL na qual os resultados da subconsulta dependem dos valores da consulta externa à qual está associada

```sql
SELECT id
	,nome
	,genero
	,salario
FROM cliente c
WHERE salario > ANY (
		SELECT salario
		FROM cliente
		WHERE genero = c.genero
		);
```

-  **INTERSECT**: O operador `INTERSECT` retorna os registros que estão presentes em ambas as consultas. Ele retorna a interseção dos conjuntos de resultados das duas consultas.

Exemplo no SQL padrão (que não funciona no MySQL):

```SQL
SELECT column1, column2
FROM table1
INTERSECT
SELECT column1, column2
FROM table2;

```

-  **EXCEPT**: O operador `EXCEPT` retorna os registros da primeira consulta que não estão presentes na segunda consulta. Em outras palavras, ele retorna os elementos exclusivos da primeira consulta.

Exemplo no SQL padrão (que não funciona no MySQL):

```SQL
SELECT column1, column2
FROM table1
EXCEPT
SELECT column1, column2
FROM table2;

```

- podemos resolver as limitações do MySQL simulando a função do except com o in e o intersect utilizando o in ou o exists.
- Intersect:
```sql
SELECT column1, column2
FROM table1
WHERE (column1, column2) IN (
    SELECT column1, column2
    FROM table2
);

```

```sql
select distinct cidadeId from cliente
where cidadeId in (select id from cidade);
```

- Except:

```sql
SELECT column1, column2
FROM table1
WHERE (column1, column2) NOT IN (
    SELECT column1, column2
    FROM table2
);

```

```sql
select distinct id from cidade
where id not in (select cidadeId from cliente);
```

### Commont table Expressions

```mysql
WITH average AS (
	SELECT AVG(quantity) AS average_quantity
	FROM order_details
)

SELECT order_details.\*
FROM order_details, average
WHERE quantity > average.average_quantity
```
# FORMATAÇÃO DE DADOS TEXTUAIS

## Length()
- Retorna o número de caracteres em uma string
- pode ser aplicada em uma coluna de uma tabela para calcular o comprimento das strings armazenadas nessa coluna para cada registro da tabela

```sql
select length(coluna) from <tabela>
where <condição>;
```

```sql
SELECT nome
	,length(nome)
	,dataNascimento
	,length(dataNascimento)
	,salario
	,length(salario)
FROM cliente;
```

![[Pasted image 20230811091004.png]]

## Upper() e Lower()

- A função `upper` tem como objetivo converter para letras maiúsculas um valor de um tipo char ou varchar, `lower` faz o inverso

```sql
select upper(coluna) from <tabela> where <condição>;
select lower(coluna) from <tabela> where <condição>;
```

## ltrim(), rtrim(), trim()
- remoção de espaços vazios presentes em colunas de cadeia de caracteres
- com `trim` Podemos usar os parâmetros both (retira os espaços das duas extremidades), leading (retira somente os espaços da esquerda) e trailing (retira somente os espaços da direita, isto é, do final).

```sql
select ltrim(coluna) from <tabela> where <condição>;
select rtrim(coluna) from <tabela> where <condição>;
select trim([parametro]coluna)
from <tabela> where <condição>;
```

## Substring()

- permite a pesquisa e a seleção de parte de uma string.

```sql
substring(expressão, inicio, tamanho);

substring(expressão FROM inicio FOR tamanho);
```

• **expressão:** indica a string a ser pesquisada;
• **início:** índice inicial da pesquisa na expressão fornecida;
• **tamanho**: comprimento da string do resultado.

- extrair somente as três primeiras letras das placas dos veículos dos clientes.

```sql
select placaVeiculo,
substring(placaVeiculo, 1, 3) from cliente;
```

```sql
select placaVeiculo,
substring(placaVeiculo from 1 for 3)
from cliente;
```

- Ao usarmos um número negativo, significa que a extração começará pela direita, ou seja, pelo final da string.

```sql
 select placaVeiculo, substring(placaVeiculo, -2) from cliente;
```

## Replace()
- Baseado em uma expressão definida, a função replace realiza uma busca em uma determinada string e, ao encontrar, substitui o valor da string pelo valor especificado no argumento.

```sql
replace(‘expressao’ ou coluna,
‘string a consultar’, ‘substituir’);
```

```sql
select email, replace(email, ‘#’, ‘@’) from cliente;
```

![[Pasted image 20230811092019.png]]

## Cast()

- Permite a conversão de um tipo de dado em outro tipo de dado.

```sql
cast(value as datatype);
```

```sql
select cast(‘2000-01-01’ as date),
cast(‘1000.00’ as decimal), cast(‘20:15’ as time);
```

![[Pasted image 20230811092158.png]]


## FORMATAÇÃO DE DADOS NUMÉRICOS E TEMPORAIS 

## Round()

- Arredondamento de valores numéricos com casas decimais.

```sql
select round(coluna, casas decimais)
from <tabela> where <condição>;
```

```sql
select salario, round(salario), round(salario, 1),
round(salario, 2) from cliente;
```

![[Pasted image 20230811092332.png]]

-  valores que apresentaram a última casa decimal igual ou superior a 5 tiveram o valor arredondado para mais, caso contrário, o valor foi arredondado para menos.

## Truncate()

- Retorna o número truncado em N casas decimais. Se a definição do número de casas decimais for igual a zero (0), não haverá ponto decimal.

```sql
select truncate(coluna, casas decimais)
from <tabela> where <condição>;
```

```sql
select salario, truncate(salario,0), truncate(salario,1),
truncate(salario, 2) from cliente;
```

![[Pasted image 20230811092502.png]]

## Mod() e Div()

- A função `mod()` retorna o resto da divisão
- Já a função `div()` retorna o quociente (parte inteira) da divisão.

```sql
select mod(dividendo, divisor);
select dividendo div divisor;
```

```sql
select mod(4, 2) as ‘resto divisão’,
mod(5,2) as ‘resto divisão’,
4 div 2 as ‘quociente’,
5 div 2 as ‘quociente’;
```

![[Pasted image 20230811092627.png]]

## Curdate(), Curtime() e Now()

- A função `curdate()` retorna a data corrente, sendo a função `current_date()` sinônimo da curdate().
- A função `curtime()` retorna a hora corrente, sendo a função `current_time()` sinônimo na função curtime().
- Já a função `now()` retorna a data e a hora corrente.

```sql
 select curdate(), curtime(), now();
```

![[Pasted image 20230811092815.png]]

## Date()

- A função` date(expressão)` realiza a extração de uma data de um tipo *date* ou *datetime*.

```sql
select now(), date(curdate()), date(now());
```

![[Pasted image 20230811092923.png]]


## Day() e suas variações 

• `day(date)`: retorna o dia de uma data, sendo sinônimo da função `dayofmonth()`;
•`dayname(date)`: retorna o nome do dia da semana;
• `dayofweek(date)`: retorna o dia da semana;
• `dayofyear(date)`: retorna o dia do ano;
• `last_day(date)`: retorna o último dia do mês.

```sql
SELECT curdate()
	,day(curdate())
	,dayname(curdate())
	,dayofweek(curdate())
	,dayofyear(curdate())
	,last_day(curdate());
```


![[Pasted image 20230811093330.png]]

## Week() e Weekday()

- `week(date[model])`: retorna a semana do ano de um tipo date, sendo a função `weekofyear(date) `semelhante à função week. O model indica se a semana começa no domingo (0) ou na segunda (1).
- `weekday(date)`: retorna o dia da semana, sendo: 0 = monday, 1 = tuesday, ..., 6 = sunday.

![[Pasted image 20230811093646.png]]


## Month(), Monthname() e Year()

- A função `month(date)` retorna o número do mês correspondente a uma data.
- A função `monthname(date)`, por sua vez, retorna o nome do mês de uma data. 
-  função `year(date)` retorna o ano de uma data.

```sql
SELECT month(curdate())
	,monthname(curdate())
	,year(curdate());
```

![[Pasted image 20230811093831.png]]

## Adddate()

- Adiciona a uma data um intervalo predefinido, gerando uma nova data

```sql
adddate(data, intervalo_data expressão unidade);
```

```sql
SELECT curdate()
	,adddate(curdate(), interval 31 day)
	,adddate(curdate(), interval 1 month)
```

![[Pasted image 20230811094011.png]]

## Datediff()

- A função `datediff(data1, data2)` calcula a diferença em dias (inteiro) do intervalo entre duas datas informadas.

```sql
SELECT curdate()
	,datediff(‘2022 - 01 - 01 ’, curdate())
	,datediff(curdate(), ‘2022 - 01 - 01 ’);
```

![[Pasted image 20230811094112.png]]

## Date_Format()

- A função `date_format(date, format)` formata a data de acordo com o formato especificado.

```sql
SELECT curdate()
	,date_format(curdate(), '%w %m %y')
	,date_format('2022-01-01 20:15:00', '%h:%i:%s');
```

## Timediff()

- A função `timediff(expressão 1, expressão  2)` retorna a diferença entre dois tempos definidos.

```sql
SELECT timediff('2021-12-31 23:59:59.000001', '2021-12-30 01:01:01.000002');
```

![[Pasted image 20230811094544.png]]

## Time() e suas Subdivisões

- `time(expressão)`: extrai a hora de um tipo `datetime`;
- `hour(time)`: extrai somente a hora de um tempo;
- `minute(time)`: extrai somente os minutos de um tempo;
- `second(time)`: extrai somente os segundos de um tempo;
- `microsecond(expressão)`: extrai somente os microssegundos de um tempo.

```sql
SELECT curtime()
	,TIME(curtime())
	,hour(curtime())
	,minute(curtime())
	,second(curtime())
	,microsecond(curtime());
```

![[Pasted image 20230811094800.png]]

## Addtime() e Timestamp()

- A função `addtime(expressão 1, expressão 2)` adiciona um intervalo de tempo a um tipo *date* ou *datetime*.
- Já as funções `timestamp(expressão)` e` timestamp(expressão 1, expressão 2)` adicionam a um tipo *date* ou *datetime* a quantidade de tempo informada.

```sql
SELECT ADDTIME('01:00:00.999999', '02:00:00.999998');
SELECT TIMESTAMP('2003-12-31');
SELECT TIMESTAMP('2003-12-31 12:00:00', '12:00:00');
```

![[Pasted image 20230811095429.png]]

## Timestampadd()

- Adiciona uma fração de tempo a um tipo *datetime*

```sql
 timestampadd(unit, interval, datetime_expr);
```

```sql
SELECT curdate()
	,curtime()
	,timestampadd(minute, 30, curdate())
	,timestampadd(week, 1, ‘curtime() ’);
```

![[Pasted image 20230811095557.png]]

## Time_Format()

- Formata um valor do tipo time.
- `time_format(time, format);`

```sql
select time_format(‘100:00:00’, ‘%h %k %h %i %l’);
```

![[Pasted image 20230811095715.png]]

# AGREGAÇÃO/EXTRAÇÃO DE DADOS

- Cinco funções de agregação - Contagem, soma, média, máximo, mínimo
## Count()

- Retorna a quantidade de registros correspondentes a uma pesquisa.
- `select count(*) from <tabela> where <coluna>;`

```sql
SELECT count(*)
	,count(generoFunc)
FROM funcionario;
```

![[Pasted image 20230811095941.png]]
- não contabiliza null

```sql
SELECT count(*)
FROM funcionario
WHERE generoFunc = ‘m’;
```

## Sum()

- Retorna o somatório dos valores de uma coluna.
- `select sum(coluna) from <tabela> [where <coluna>];`

```Sql
SELECT sum(salarioFunc)
FROM funcionario;
```

## Min()

- Retorna o menor valor encontrado em uma coluna.
- `select min(coluna) from <tabela> [where <coluna>];`

```sql
SELECT min(salarioFunc)
	,min(NascFunc)
FROM funcionario;
```

## Max()

- Retorna o maior valor encontrado em uma coluna.
- `select max(coluna) from <tabela> [where <coluna>];`

```sql
SELECT max(salarioFunc)
	,max(NascFunc)
FROM funcionario;
```

## Avg()

- Realiza a média dos valores de uma coluna.
- ` select avg(coluna) from <tabela> [where < coluna >];`

```sql
SELECT avg(salario)
FROM funcionario;
```

## Group By()

- Agrupa todas as linhas do retorno de uma pesquisa que possuem o valor de suas colunas iguais.

```sql
SELECT (< coluna_agrupamento > e / ou < função_agrupamento >)
FROM < tabela > [where <condição>]
GROUP BY < coluna_agrupamento > [having <condição>};]
```

```sql
SELECT departamento
	,count(*)
FROM funcionario
GROUP BY departamento
ORDER BY departamento;
```

- não podemos aplicar uma função de agregação (min, max, sum, avg e count) em conjunto com outras colunas sem a declaração do group by.

## Having()

- Realiza um filtro sobre o group by.

```sql
SELECT (< coluna_agrupamento > e / ou < função_agrupamento >)
FROM < tabela > [where <condição>]
GROUP BY < coluna_agrupamento >
HAVING < condição >;
```

- quantos departamentos possuem mais de dois funcionários?

```sql
SELECT departamento
	,count(*)
FROM funcionario
GROUP BY departamento
HAVING count(departamento) > 2;
```

# INTEGRIDADE E SEGURANÇA DE DADOS

## Segurança Lógica

- assegurar que cada operação executada no banco de dados seja efetuada somente por usuários que possuem privilégios para tal fim
- uso de técnicas de autenticação ou autorização  e mascaramento dos dados no carregamento, além de armazenar os dados criptografados na base de dados.
-  Para realizar esses procedimentos, fazemos uso dos comandos *grant* e *revoke*, os quais pertencem a **Data Control Language (DCL)**

- **Grant**

```mysql
GRANT PRIVILÉGIOS
	ON [banco_dados].tabela
	TO usuário_1 [identified by ‘senha_1’]
		,usuário_n [identified by ‘senha_n’]
	WITH GRANT OPTION;
```

```sql
GRANT SELECT
	TO nome_usuario;
```

- **Revoke**

```mysql
REVOKE PRIVILÉGIOS
	ON objeto
	FROM usuário_1
		,usuário_2
		,...;
```

```mysql
REVOKE CREATE TABLE
	TO nome_usuario;
```

Retirando todas as permissões do usuário ‘aluno’.
revoke all, grant option from aluno@localhost;

- No MySQL, os privilégios são atribuídos em quatro níveis diferentes:

	-  *Global* – acesso a todas as tabelas de todos os Bancos de Dados;
	- *Database* – acesso a todas as tabelas de um Banco de Dados específico;
	- *Table* – acesso a uma tabela específica com todas as suas colunas;
	- *Column* – acesso apenas às colunas especificadas de uma determinada tabela

- Os privilégios podem ser atribuídos ou retirados, sendo:
	- **Trabalhar com os dados** – *Insert, update, delete, select e execute;*
	- **Estrutura do Banco de Dados** – *Create, alter e drop.*

- Tabelas utilizadas para gerenciar permissões (MySQL)
	- *user* – armazena nomes e senhas dos usuários, assim como os privilégios globais empregados a todos os Bancos de Dados;
	- *db* – armazena privilégios dos Bancos de Dados;
	- *tables_priv* – armazena privilégios das tabelas;
	- *columns_priv* – armazena privilégios de colunas;
	- *procs_priv* – armazena privilégios de acesso às funções e stored procedures.

### Principais comandos

- *Create user*

```mysql
CREATE USER 'nomeUsuario'@'servidor' IDENTIFIED BY 'senha' PASSWORD EXPIRE;
```

- *Drop user* – exclui um usuário do Banco de Dados.

```mysql
DROP USER [IF EXISTS] nomeusuario;
```

-  *Flush privileges* – atualiza os dados de privilégios nas tabelas do MySQL.

```mysql
FLUSH PRIVILEGES;
```

-  *Show grants* – visualiza os privilégios de um usuário.

```mysql
SHOW GRANTS FOR usuario@localhost;
```

## Segurança física

-  proteger os dados de qualquer situação que possa provocar danos físicos
- a forma como ocorrerá o armazenamento físico, como as rotinas de backup serão realizadas, protocolo de acesso ao servidor, medidas contra o uso indevido de informações, perda acidental ou intencional, degradação e destruição dos dados, entre outros.

## Integridade de Dados

- aplicação de regras e protocolos que visam garantir a consistência e a confiabilidade dos dados contidos no Banco de Dados. 
- parâmetros de validação, restrições e controle de redundâncias

### Integridade declarativa
- baseia-se nos comandos da Data Definition Language (DDL), aplicando restrições a:
	- **Chave primária** – que não contenha valores duplicados ou valor nulo;
	- **Chave estrangeira** ou **integridade referencial** – 
		- impedindo que uma chave estrangeira receba um valor que não possui correspondência (não existe) com a tabela de origem (pai) 
		- ou que uma linha da tabela de origem seja excluída sem levar em consideração as tabelas filhas (que contém a declaração de chave estrangeira)
	- **Domínio** – limitando o tipo de valor válido a ser recebido por uma coluna.
- Comando: PRIMARY KEY, NOT NULL, CHECK, UNIQUE, FOREIGN KEY

### Integridade procedural

- Fornece uma solução para as validações ou restrições que não são cobertas pela integridade declarativa
- declaração de estruturas que encapsulam as instruções em bloco, sendo
	- **Trigger** – comandos que disparam automaticamente ações quando um outro comando SQL é executado
	- **Stored procedures** – são programas propriamente ditos que executam tarefas e, inclusive, podem chamar funções definidas pelo usuário;
	- **Funções definidas pelo usuário** – conjunto de instruções que retornam um valor.

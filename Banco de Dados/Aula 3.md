#  SQL DATA TYPES

- Todo objeto que tem a função de armazenamento de dados sempre terá um tipo de dado associado ao mesmo

1. Tipo numérico.
2. Tipo cadeia de caracteres ou valor string.
3. Tipo valor temporal.

- O tipo do dado define as características da coluna
	- O tipo de dado contido pelo objeto;
	- O comprimento ou tamanho do valor a ser armazenado (bits ou bytes)
	- A precisão e a escala do número
		- Precisão – Refere-se ao total de dígitos em um número;
		-  Escala – É o número de dígitos à direita da casa decimal.

## Tipo Numérico

- Podem assumir os valores inteiros, ponto flutuante ou ponto fixo 
- Os tipos de dados considerados **inteiros** são: *bit, tinyint(1), smallint(2), int(4), mediumint e bigint(8)*. - tamanho em bytes entre parenteses
- os tipos numéricos ocupam um comprimento de 1 a 8 bytes,
- do tipo **bit** apresenta um armazenamento diferenciado, abrangendo um comprimento de 0 (zero) a 64 bits por valor armazenado.
- **ponto flutuante**, não possuem definição do número de dígitos, são representados pelo *float* e *double*, requerem 4 a 8 bytes, respectivamente, para cada lado do valor
- **ponto fixo**, possui definição do máximo de dígitos presentes, representados pelo tipo *decimal*, o qual necessita de 4 bytes de armazenamento para cada lado do valor

## Tipo Cadeia de Caracteres ou Valor String

- São subdividos em duas categorias:

1. Valores binários – *Binary, varbinary e blo*b (16 bits, mais 2 de controle).
2. Valores não binários – Representados pelos tipos de dados *char, nchar, varchar, nvarchar e text.*

- os valores não binários, geralmente, ocupam o equivalente ao número de caracteres definidos na coluna
- *varchar* ocupa o tamanho realmente utilizado acrescido de um caractere de controle para identificar o fim da cadeia de caracteres, já o char ocupa todo o tamanho
- Os tipos *nchar* e *nvarchar* possuem a capacidade de armazenar caracteres Unicode

## Tipo Valor Temporal

- Utilizados no armazenamento de dados do tipo data e hora
- eles requerem um tamanho de armazenamento de 1 a 8 bytes.
-  tipos:
	- *Date* - datas sem declaração de hora. Formato padrão: YYYY-MM-DD 
	- *Time* - Apenas para hora. Formato padrão: hh:mm:ss
	- *Datetime* – Utilizado para valores de data e hora. Não considera o fuso horário. Formato padrão: YYYY-MM-DD hh:mm:ss.
	- *Timestamp* – Semelhante ao datetime, porém baseado no fuso horário. É um número sequencial começando em 01/01/1970 00:00 de Londres
	- *Year* – Armazena apenas o ano, podendo utilizar 2 ou 4 dígitos.

# SQL NA PRÁTICA

## Comandos Úteis para Iniciar

- **Apresentando os Bancos de Dados Existente**

`show databases;`


- **Acessando um Banco de Dados**

`use bdados;`

- **Descobrindo o Banco de Dados que você está conectado**

`select database()`

- **Apresentando as tabelas existentes dentro de um Banco de Dados**
- para executar esse comando é necessário estar dentro do Banco de Dados desejado, utilizando o comando use.

`show tables;`

- **Apresentando o dicionário de dados de uma tabela**
O dicionário de dados contém a estrutura lógica da tabela, ou seja, o nome da coluna, o tipo de dado, a chave, entre outros.
`describe tabela;`

-- comentario de uma linha
/\*\*/ comentario de varias linhas 

## Principais Comandos 

### Criando um Banco de Dados 
`CREATE DATABASE nome_bd;`

- Podemos incrementar a query para realizar uma pré-verificação da existência de um Banco de Dados com o mesmo nome.
`CREATE DATABASE IF NOT EXISTS bdados;`

### Criando tabelas (create)
comando create, declarando o nome da tabela juntamente com a definição de todas as colunas.
restrições - Definição de chaves, not null, unique, default e check.

```SQL
 create table ntabela (
	coluna1 tipodado(tam) restrições, ...,
	colunan tipodado(tam) restrições); 
```

```SQL
CREATE TABLE usuario (
    id INTEGER,
    email VARCHAR(100),
    senha VARCHAR(20)
);
```

### Incluindo dados na tabelas (insert)
```SQL
insert into ntabela (
	coluna1, ..., colunan) values
	(valor1, ..., valorn);
```

- No que se refere aos valores com exceção dos valores numéricos, os demais serão declarados dentro de aspas simples.
- Datas são declaradas entre aspas simples e no formato AAAA-MM-DD;
- O insert permite a escrita de uma query mais simples, omitindo o nome das colunas. Porém, apenas se todos os dados forem declarados na mesma sequência que foram definidos na criação da tabela

```sql
insert into ntabela values
	(valor1, ..., valorn);
```

```sql
insert into usuario (id, email, senha) values
	(1, ‘maria.lopes@email.com’, ‘M1256779@’);
```

- O comando insert também permite a inserção de dados em colunas específicas de uma tabela,

```sql
insert into usuario (id, senha) -- Exceto a coluna email
	values (2, ‘JJ886645@’);
```

### Consultando dados na tabela (select)
`select * from ntabela;`

- *select* possibilita solicitar diversos tipos de consultas - m determinadas colunas, ordenar o resultado em ordem crescente ou decrescente, realizar filtros, entre outras.

```sql
select email, senha from usuario order by email; -- consulta colunas específicas e ordenando por email
```

- Se houver algum valor NULO dentro da coluna que será ordenada, o mesmo será apresentado antes que os demais
- o padrão de apresentação é ascendente, mas é possível apresentar os dados de forma descendente 
- `order by` deve ser sempre a última cláusula da instrução select

```sql
select * from usuario order by id desc;
```

- Para realizar um filtro no select, utiliza-se a cláusula where, a qual permite a definição de condições para realizar a consulta.

```sql
select * from usuario where email is null;
```

- Na cláusula where, também podemos aplicar os operadores lógicos, relacionais e booleanos

### Excluindo objetos em SQL (DROP):

- **Excluindo uma tabela**
`DROP TABLE ntabela;`

- **Excluindo um Banco de Dados**
`DROP DATABASE bdados;`

# SQL PK, FK E UK

## Declarando uma chave primária (PK) em uma tabela

- quando criamos uma restrição de chave primária, todas as colunas incluídas na chave primária devem possuir a restrição *not null* declarada

`coluna tipodado restrição,
	`primary key(coluna)`

```sql
create table estado (
	id integer not null,
	descricao varchar(100),
	sigla char(02),
	primary key(id));
```

![[Pasted image 20230728203817.png]]

## Declarando chaves estrangeiras (FK) em uma tabela:

`coluna tipodado restrição,
	`foreign key(coluna)
	`references tabOrigem (colOrigem)`
	`comportamento`


- comportamento - On delete no action on update no action.
- comportamentos referem-se à ação que será executada pelo Banco de Dados quando o usuário tentar excluir ou alterar o valor de uma chave primária que está sendo utilizada em outra tabela como chave estrangeira

```Sql
create table cidade (
	id integer not null,
	estado_id integer not null,
	descricao varchar(150),
	primary key(id),
	foreign key(estado_id) references estado(id)
	on delete no action on update no action);
```

```sql
CREATE TABLE cliente(
	id INT PRIMARY KEY,
    nome VARCHAR(100),
    idCidade INT, constraint fkclienteCidade -- , the foreign key constraint is explicitly named as `fkclienteCidade`. 
    FOREIGN KEY(idCidade) REFERENCES cidade(id));
```

## Declaração de chaves únicas (Unique Key – UK) em uma tabela

- Chaves candidatas
`coluna tipodado(tamanho) unique`

```SQL
create table entregador (
	id integer not null,
	cidade_id integer not null,
	cnh integer unique,
	nome varchar(150),
	endereco varchar(150),
	telefone varchar(30),
	primary key(id),
	foreign key(cidade_id) references cidade(id)
		on delete no action on update no action);
```

## Declaração de chaves compostas em uma tabela

- Declaração de uma PK composta de várias colunas

`constrant nomeRestricao primary key (col1,...coln)`

```sql
create table pedidoProduto (
	pedido_id integer not null,
	produto_id integer not null,
	quantidadeProduto integer,
	valorUnitario decimal,
	desconto decimal,
	primary key(pedido_id, produto_id),
	foreign key(pedido_id) references pedido(id)
		on delete no action on update no action,
	foreign key(produto_id) references produto(id)
		on delete no action on update no action);
```

# SQL CONSTRAINTS

- toda restrição é uma regra com a qual os dados devem estar em conformidade
- evitar que dados inválidos sejam inseridos no banco

## Restrição *not null*

- impedirá que uma coluna aceite um valor nulo 
`coluna tipo de dado(tamanho) not null`

```sql
 create table usuario (
	id integer not null,
	email varchar(100) not null,
	senha varchar(20) not null,
	primary key(id));
```

## Restrição *check*

- A restrição check específica regras para os valores da coluna, validando a mesma
`coluna tipodado(tamanho) check(coluna in (valor1,...valorn))`

Dentro da restrição check é necessário informar a coluna, que receberá a validação, a cláusula in e os valores correspondentes (todos entre parênteses).

```sql
genero char(01) check(genero in(‘M’, ‘F’))
```

## Restrição *default*

- Definição de um valor padrão associado a uma coluna
`coluna tipodado(tamanho) default valorpadrao`

```sql
create table cliente (
	id integer not null,
	nome varchar(150),
	dataNascimento date,
	genero char(01),
	estadoCivil char(01) default 'S',
	primary key(id));
```

- podemos aplicar várias restrições em uma mesma coluna

```sql
genero char(01) check(genero in(‘M’,‘F’)) default ‘M’
```

restrições  podem também serem aplicadas em tabelas existentes utilizando o comando *alter table* 

# ALTERAÇÕES, AUTO INCREMENT, ENTRE OUTROS

## *Alter Table*

- Comando que permite ao usuário alterar uma tabela

### add
- Adiciona uma coluna em uma tabela existente;
`alter table ntabela`
	`add ncoluna tipodado(tamanho);`

```sql
alter table cidade add ddd char(3);

ALTER TABLE CIDADE ADD COLUMN(DDD CHAR (3)) --MAIS CLARO 
```

- na inclusão de novas colunas não possível adicionar a restrição not null em uma tabela existente que já possua dados armazenados - as linhas existentes não poderiam fornecer valores a nova coluna e, obrigatoriamente, não pode permanecer vazia.
- é possível indicar posição que coluna será inserida com comando `after`

```sql
ALTER TABLE aluno ADD ddd INT ZEROFILL AFTER email 
```


### modify
- Modifica as definições de uma coluna existente, mas não permite alterar o seu nome

`alter table ntabela`
	`modify colunaatual tipodado(tam);`

```sql
alter table cidade modify ddd char(02);
```

### change
- Renomeia e altera as definições de uma coluna existente (nome, tipo da coluna, entre outros);

`alter table ntabela`
	`change colunaatual colunanova tipo(tamanho);`

```sql
alter table cidade
	change ddd codigoArea char(02);
```

### drop
- Exclui uma coluna pertencente a uma tabela

`alter table ntabela drop column ncoluna;`

```sql
alter table cidade drop codigoArea;
```

- não é possível a exclusão de uma coluna que é chave primária e que está sendo referenciada como chave estrangeira em outras tabelas.

### Adicionando uma chave primária

```sql
ALTER TABLE nome_tabela ADD PRIMARY KEY(coluna);
```

### Adicionando uma chave estrangeira em uma tabela

`alter table ntabela add constraint nRestricao`
	`foreign key ncoluna`
	`references ntabela(ncoluna);`


- Exemplo: Criar um relacionamento entre as tabelas Produto e TipoProduto, sabendo que na tabela Produto não existe a coluna que representará a ligação entre as duas tabelas
- antes de criarmos a chave estrangeira, devemos adicionar a coluna ‘tipoProduto_id’ na tabela Produto.

```sql
alter table produto
	add tipoProduto_id integer not null;
```

- Agora que a coluna foi adicionada na tabela Produto, vamos adicionar a restrição de chave estrangeira.

```sql
alter table produto add constraint fk_prodTipo
	foreign key (tipoProduto_id)
	references tipoProduto(id);
```

### Renomeando uma table - rename 

`alter table tabelaantiga rename to tabelanova;`

```sql
alter table cidade rename to cidades;
```

##  Propriedades Especiais

- ***Unsigned***
	- não permite o recebimento de valores negativos para colunas do tipo de dado inteiro
	- Uma coluna que não possua essa propriedade declarada assumirá por padrão *signed*, permitindo a atribuição de valores negativos.
- ***Zerofill***
	- Insere o autopreenchimento com zeros nos espaços ociosos
	-  automaticamente torna a coluna *unsigned*
- ***Auto_increment***
	- gerar automaticamente um número inteiro e incrementá-lo a partir da inclusão de uma nova linha, não havendo a inclusão manual desse valor na coluna
	- deverá ser declarada com o tipo de dado inteiro (integer), possuir a restrição *not null* e a definição de *primary key* ou *unique*
	-  só poderá haver uma coluna utilizando essa propriedade
	- sempre *unsigned* por padrão

```sql
create table estado (
	id integer unsigned zerofill,
	descricao varchar(100));

insert into estado values (1, 'Paraná');
insert into estado values (2, 'São Paulo');
select * from estado;
```


![[Pasted image 20230729090610.png]]

```sql
create table estado (
	id integer unsigned zerofill
	primary key auto_increment,
	descricao varchar(100));

insert into estado (descricao) values ('Paraná');
insert into estado (descricao) values ('São Paulo');
select * from estado;
```

![[Pasted image 20230729090733.png]]

## Detalhando uma Query ou script
![[Pasted image 20230729090855.png]]
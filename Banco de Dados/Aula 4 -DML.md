
#  INCLUSÃO DE REGISTROS

- comando *INSERT*
- **inclusão de várias linhas em uma tabela** -  inclusão de parênteses para cada linha separados por vírgula.
- **Copiar dados de outra tabela**

```sql
insert into cliente 
(nome, genero, dataNascimento, salario, email, cidadeId)
select nomeFunc, sexoFunc, nascFunc, salarioFunc, emailFunc, cidadeId from funcionario;
--as colunas da tabela Funcionário, obrigatoriamente, devem estar em concordância com o tipo de dado existente em cada coluna da tabela Cliente
```

## Trabalhando com chaves estrangeiras
- Para incluirmos novas linhas em uma tabela que possui chave(s)  estrangeira(s), é necessário que o valor exista em sua tabela de origem
- É possível otimizar a inserção de registros que possuem chaves estrangeiras com a utilização de *subqueries*

```sql
insert into cliente values
(3, 'Nair Verne', 'F', '1986-04-21', 6400.66, 'nair.verne@email.com', (select id from cidade where nome = 'São Paulo'));
```

- neste exemplo não é necessário consultar a tabela cidade para buscar o id específico 

## Erros na inclusão de linhas em uma tabela

- tentativa de inclusão de uma linha sem declarar uma coluna que possui a restrição *not null*.
-  tentativa de inclusão de linha sem a declaração do valor da chave primária.
	- em chaves primárias a restrição not null é padrão
- tentativa de inclusão do mesmo valor da chave primária de forma repetida.
- tentativa de inclusão de valor em coluna não especificada (sem correspondência).
-  tentativa de inclusão de valor inexistente em chave estrangeira

# EXCLUSÃO E MODIFICAÇÃO DE REGISTROS

##  Removendo linhas da tabela - DELETE

- `DELETE FROM ntabela WHERE condição;`

```SQL
DELETE FROM cliente WHERE id = 5;
DELETE FROM cliente WHERE nome = 'Helena Magalhaes'
```

- A aplicação de subqueries, em conjunto com o comando delete, também pode ser utilizada com o intuito de otimizar o processo.

```sql
DELETE FROM cliente WHERE cidadeId IN 
	(SELECT id FROM cidade WHERE nome = 'Curitiba');
```

- Fazendo o uso dos operadores lógicos, em conjunto com a cláusula where, podemos ampliar o uso de filtros com a adição de mais uma condição

```SQL
DELETE FROM funcionario 
	WHERE departamento =1 AND sexoFunc = 'M';
```

-  Uma alternativa é utilizar o comando `truncate` que exige menos recursos do sistema, porém  não permite o uso de triggers, nem de cascade e, também, não dá suporte a replicações no Banco de Dados

### Comportamento do DELETE
-  a definição do comportamento do comando delete está presente no momento de criação das tabelas que possuem chaves estrangeiras
- `on delete no action` - não permite a exclusão de linhas na tabela pai que estejam associadas a outra tabela (filha)
- `on delete cascade` - quando é feita a exclusão na tabela pai, é realizada todos os registros que fazem referência na tabela filha

```sql
create table cidade (
	 -- Tabela pai
	id int,
	nome varchar(100) not null
	uf char(02),
	constraint pkCidade primary key (id));

create table cliente (
	 -- Tabela filha
	id int auto_increment,
	-- Demais colunas foram suprimidas
	cidadeId int not null,
	constraint pkcliente primary key (id),
	constraint fkClienteCidade
	foreign key (cidadeId)references cidade(id)
		on delete no action on update no action);

create table funcionario (
	 -- Tabela filha
	matricula int not null,
	-- Demais colunas foram suprimidas
	cidadeId int not null,
	constraint pkfuncionario primary key (matricula),
	constraint fkFuncCidade
	foreign key (cidadeId) references cidade(id)
		on delete cascade on update no action);
```

## Alterando as linhas da tabela - UPDATE

-  o comando `update` é o responsável por manter a base de dados atualizada, realizando alterações no conteúdo 
-  é sempre acompanhado pelo argumento `SET` e, geralmente, pela cláusula `WHERE`.

```SQL
--SINTAXE
update ntabela
	set coluna1 = valor1, ..., colunan = valorn
	where ncoluna = valorfiltro;
```

```sql
update funcionario set salarioFunc = salarioFunc * 1.15;
```

```sql
update funcionario 
	set nomeFunc = 'Ana Rosa Silva Vieira', emailFunc = 'anavieira@email.com' 
	where matricula = 1;
```

```sql
update funcionario 
	set salarioFunc = salarioFunc * 1.05
	where sexoFunc = 'M' and departamento = 1;
```

```sql
update funcionario
	set cidadeId = (select id from cidade where nome = 'Imperatriz')
	where matricula = 2;
```

### Comportamento do UPDATE

- `on update no action` - não é possível alterar o valor de uma chave estrangeira que está sendo utilizada em outra tabela (integridade referencial)
- o comando update também permite o uso do `cascade.`

# RESTRIÇÃO DE CONSULTAS 

- Operadores lógicos - **or, and, not**
- Operadores relacionais tradicionais
	- =
	- <> ou !=
	- >,<,>=,<=
	- in
	- not in
- o igual não funciona apropriadamente para comparar float
- outros operadores relacionais
	- **like** - compatível
	- **between** intervalo (BETWEEN MIN AND MAX)
	- **is null**
	- **exists**
	- **any** - Comparação com qualquer elemento do conjunto
	- **all** - Comparação com todos os elementos do conjunto
- aritméticos - +,-,\*, \/

```sql
select nome, genero, salario from cliente
	where salario >= 5000 and salario <= 8000;
```

```sql
select * from cidade where uf is not null;
```

- selecionar os clientes que possuem o termo Silva no nome.
```sql
select * from cliente where nome like '%Silva%';
```

- O operador `%`  tem como função substituir uma cadeia de caracteres

```sql
select nome, salario, genero, cidadeId
	from cliente where cidadeId in (1, 2, 4);
```

```sql
select nome, salario, genero, cidadeId
	from cliente where cidadeId between 1 and 4;
```

## Order By
- A cláusula order by tem por objetivo ordenar o resultado de um select.
- poderá ser apresentada de forma ascendente (asc) ou descendente (desc), sendo que a declaração asc é padrão, podendo ser omitida.
- será sempre a última cláusula a ser declarada.

```sql
select nome, salario from cliente
	where genero = 'F' order by nome;
```

- Também é possível realizar a ordenação por mais de uma coluna ao mesmo tempo, simplesmente separando as colunas por vírgula e definindo a ordem desejada (asc ou desc).

```sql
select nome, salario from cliente
	where genero = 'F' order by nome desc, salario asc;
```

- O order by ainda permite que possamos ordenar a consulta sem declararmos o nome da coluna, usando apenas a sua posição no select.

```sql
select nome, salario, email from cliente order by 3 asc;
```

## DATA

- pode-se utilizar os operadores relacionais para comparação (>,< = etc)
- pode-se utilizar as funções auxiliares YEAR, MONTH, DAY
```SQL
SELECT * FROM tbcliente WHERE YEAR(DATA_NASCIMENTO) = 1995;
```

# JUNÇÃO DE TABELAS 

## INNER JOIN

- combinação de linhas de duas tabelas e retorna apenas as que satisfazem a condição definida no join.

```sql
--sintaxe
SELECT colunas
FROM tabela1
INNER JOIN tabela2 ON tabela1.coluna = tabela2.coluna;
```

- `on` - Cláusula onde é definida a condição de ligação. A condição normalmente envolve a igualdade de valores entre colunas nas duas tabelas. Por exemplo, `tabela1.coluna = tabela2.coluna` indica que as linhas são combinadas quando os valores na coluna da tabela1 são iguais aos valores na coluna da tabela2.
- `tabela_A.tabela_B_id` Nome da tabela e da coluna que possui dados em comum com a segunda tabela (B).
- `tabela_B.id` Tabela e nome coluna que possui dados em comum com a coluna da primeira tabela (A).

```sql
select nomecidade, nomeEstado, sigla from cidade
	inner join estado on cidade. estadoID = estado.id;
```

![[Pasted image 20230731091420.png]]


![[Pasted image 20230731091431.png]]

- podemos utilizar o join implícito dentro da condição where. O resultado será o mesmo, sendo a query correspondente:

```sql
select nomecidade, nomeEstado, sigla from cidade, estado
	where cidade.estadoID = estado.id;
```

- É recomendado usar o join para fazer a convergência de tabelas e o where para aplicar filtros

## OUTER JOIN
- Apresenta todas as linhas de uma tabela, mesmo quando elas não satisfazem a condição definida.

### LEFT JOIN

- Satisfazendo ou não a condição de junção entre as tabelas, todas as linhas da tabela à esquerda do join serão incluídas no resultado.
- left join *inclusive*
```SQL
SELECT coluna1, coluna2
FROM tabela_A
LEFT JOIN tabela_B ON tabelaA.tabela_B_id = tabela_B.id;
```

```sql
select nomecidade, nomeEstado, sigla from cidade
left join estado on cidade. EstadoID = estado.id;
```

![[Pasted image 20230731092602.png]]

- left join *exclusive*

```SQL
SELECT coluna1, coluna2
FROM tabela_A
LEFT JOIN tabela_B
ON tabela_A.tabela_B_id = tabela_B.id
WHERE tabela_B.id is null;
```

```sql
select nomecidade, nomeEstado, sigla from cidade
left join estado on cidade. EstadoID = estado.id
where estado.id is null;
```

![[Pasted image 20230731092624.png]]

### RIGHT JOIN

- retorna todas as linhas da tabela da direita e apenas as linhas correspondentes da tabela da esquerda.
- right join *inclusive*
```SQL
SELECT coluna1, coluna2 
FROM tabela_A RIGHT JOIN tabela_B
ON tabela_A.tabela_B_id = tabela_B.id
```

```sql
select nomecidade, nomeEstado, sigla from cidade
right join estado on cidade. EstadoID = estado.id;
```

![[Pasted image 20230731093101.png]]

- right join *exclusive*
```sql
SELECT coluna1, coluna2 
FROM tabela_A RIGHT JOIN tabela_B
ON tablea_A.tabela_B_id = tabela_B.id
WHERE tabela_A.id IS null;
```

### FULL OUTER JOIN

- Apresenta todas as linhas de ambas as tabelas envolvidas no join, mesmo as que não estão relacionadas com a outra tabela.

```sql
SELECT coluna1, coluna2
FROM tabela_A FULL JOIN tabela_B
ON tabela_A.tabela_B_id = tabela_B.id
```

![[Pasted image 20230731093258.png]]

 - o MySQL não possui suporte ao full join. Como alternativa, pode-se realizar um left join combinado com o right join exclusive.

```sql
SELECT nomecidade
	,nomeEstado
	,sigla
FROM cidade
LEFT JOIN estado ON cidade.EstadoID = estado.id

UNION

SELECT nomecidade
	,nomeEstado
	,sigla
FROM cidade
RIGHT JOIN estado ON cidade.EstadoID = estado.id
WHERE cidade.EstadoID IS NULL;
```

## CROSS JOIN

-  gera um resultado formado por todas as combinações possíveis de uma linha da primeira tabela com uma linha da segunda tabela
- resulta  um produto cartesiano das duas tabelas

```sql
SELECT coluna1
	,coluna2
FROM tabela_A
CROSS JOIN tabela_B;
```

```sql
SELECT nomefunc
	,pergunta
FROM pergunta
CROSS JOIN funcionario;
```

![[Pasted image 20230731093847.png]]

## SELF JOIN

- operação de junção no SQL em que uma tabela é combinada com ela mesma.
- Isso significa que você está usando a mesma tabela em ambos os lados da operação de junção, mas com alias (apelidos) diferentes para diferenciá-las no contexto da consulta.
```SQL
SELECT colunas
FROM tabela AS alias1
JOIN tabela AS alias2 ON condição_de_correspondência;
```

- `tabela`: É o nome da tabela que você deseja fazer a autojunção.
- `alias1` e `alias2`: São os alias (apelidos) que você dá à mesma tabela para diferenciá-la no contexto do "join".
- `colunas`: São as colunas que você deseja selecionar na consulta final.
- `condição_de_correspondência`: É a condição pela qual as linhas da tabela são combinadas. Geralmente, envolve colunas correspondentes entre os aliases da mesma tabela.

```SQL
SELECT funcionario.nomefunc
	,gerente.nomeFunc AS ‘gerenteNome’ --utiliza o alias gerente para a tabela funcionairo e renomeia a coluna nome como gerenteNome
FROM funcionario
INNER JOIN funcionario AS gerente --cria um novo nome para a 'réplica' da tabela
ON funcionario.gerente = gerente.matricula
ORDER BY funcionario.nomefunc;
```

- `SELECT funcionario.nomefunc ,gerente.nomeFunc ‘Gerente’`
	- para uma tabela referenciar a sim mesma é necessário criar uma alias para a sua cópia, nesse caso é utilizado o alias gerente para a cópia da tabela, além disso a coluna nomeFunc é renomeada como Gerente na apresentação
- `INNER JOIN funcionario AS gerente` ao fazer inner join é criado um alias para a tabela 

| id  | nome  | gerente_id |
| --- | ----- | ---------- |
| 1   | João  | NULL       |
| 2   | Maria | 1          |
| 3   | Pedro | 1          |
| 4   | Ana   | 2          |

```SQL
SELECT f1.nome AS funcionario, f2.nome AS gerente
FROM funcionarios AS f1
LEFT JOIN funcionarios AS f2 ON f1.gerente_id = f2.id;

```

| funcionario | gerente |
| ----------- | ------- |
| João        | NULL    |
| Maria       | João    |
| Pedro       | João    |
| Ana         | Maria   |
## JUNÇÃO COM VÁRIAS TABELAS

```sql
SELECT nomeFunc, nomecidade, nomeEstado 
FROM funcionario
INNER JOIN cidade ON funcionari.cidadeID = cidade.id
INNER JOIN estado ON cidade.EstadoID = estadoi.id
ORDER BY moveFunc;
```

![[Pasted image 20230731203839.png]]

![[Pasted image 20230731204124.png]]


# OUTROS COMANDOS E RECOMENDAÇÕES 

## ALIAS

- usado para atribuir um nome temporário ou alternativo a uma tabela ou a uma coluna de uma tabela.
- Na maior parte dos casos é opcional e utilizado para melhorar a qualidade das consultas 
- Em algumas situações o uso do alias é obrigatório, como, por exemplo, no autorrelacionamento (self join) e em subconsultas correlacionadas.

```sql
-- Sem alias
select nomeFunc, salarioFunc, salarioFunc * 1.10
from funcionario;
-- Com alias
select nomeFunc 'Nome do Funcionário',
salarioFunc as 'Salário atual',
salarioFunc * 1.10 as 'Novo salário' from funcionario;
```

![[Pasted image 20230731204904.png]]

## LIMIT

-  determinar o número de linhas que devem ser retornadas na consulta

```SQL
--SINTAXE
select colunas from nomeTabela
	limit deslocamento, nroLinhas;
```

- deslocamento- Indica o número de linhas que serão ignoradas. Se omitido, assume o valor 0.
- nroLinhas -  Quantidade de linhas que serão retornadas na consulta.

```sql
select * from funcionario LIMIT 3, 2;
```

## DISTINCT

- elimina as linhas repetidas
- Essa cláusula deve aparecer logo após o *select.*
- compara linhas inteiras, é possível ter colunas iguais e ainda aparecer no resultado, caso outras sejam diferentes 

```SQL
select distinct nome from cliente order by nome;
```

## CASE

- permite realizar operações condicionais em consultas.
- Forma Simples: A forma simples é usada quando você deseja avaliar uma única expressão e retornar um valor correspondente com base em diferentes condições. A sintaxe é a seguinte:

```sql
CASE expressao
    WHEN valor1 THEN resultado1
    WHEN valor2 THEN resultado2
    ...
    ELSE resultado_padrao
END
```

```SQL
SELECT nome,
       CASE tipo
          WHEN 'A' THEN 'Ativo'
          WHEN 'I' THEN 'Inativo'
          ELSE 'Desconhecido'
       END AS status
FROM usuarios;
```

Forma Pesquisada: A forma pesquisada é usada quando você precisa avaliar várias condições separadas. Cada condição é verificada individualmente, e a primeira condição verdadeira encontrada retorna o resultado correspondente. A sintaxe é a seguinte:

```SQL
CASE
    WHEN condicao1 THEN resultado1
    WHEN condicao2 THEN resultado2
    ...
    ELSE resultado_padrao
END

```

```SQL
SELECT nome,
       CASE
          WHEN idade < 18 THEN 'Menor de idade'
          WHEN idade >= 18 AND idade < 65 THEN 'Adulto'
          ELSE 'Idoso'
       END AS faixa_etaria
FROM pessoas;

```

## UNION E UNION ALL

- operadores usados para combinar os resultados de duas ou mais consultas em uma única saída.
- a quantidade e os tipos de colunas selecionadas devem ser os mesmos em todas as consultas unidas pelo `UNION`.
- O operador `UNION` combina os resultados de duas ou mais consultas, mas remove as duplicatas resultantes.
- O operador `UNION ALL`, por outro lado, combina os resultados de duas ou mais consultas, incluindo todas as linhas, inclusive as duplicadas
- Sempre que você precisar usar o order by, deve declará-lo no último select do union

```SQL
SELECT coluna1, coluna2, ...
FROM tabela1
WHERE condicao1
UNION
SELECT coluna1, coluna2, ...
FROM tabela2
WHERE condicao2;

```

```SQL
SELECT nome, idade
FROM alunos
WHERE curso = 'Matemática'
UNION
SELECT nome, idade
FROM alunos
WHERE curso = 'Ciências da Computação';

```

```SQL
SELECT nome, curso
FROM alunos
WHERE curso = 'Matemática'
UNION ALL
SELECT nome, curso
FROM alunos
WHERE curso = 'Ciências da Computação';

```
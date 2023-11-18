# ÍNDICE

- Ao executarmos um select com a declaração de um filtro (where) o SGBD realiza uma ação denominada table scan ou full scan, a qual faz uma varredura em toda a tabela
- tabela *heap* - não possui nenhum índice
- A própria SQL cria índices implícitos automaticamente para colunas PK e FK
- a utilização de índices agilizam a velocidade do tempo de resposta de uma consulta.

>[!Boas Pŕaticas em Consultas]
>- Selecione apenas colunas necessárias
>- Na cláusula where, procure usar filtros nesta ordem: números, datas e horas, textos e, por último, textos extensos;
>-  Quando possível, use a comparação por igualdade e não por faixa de valores
>- Utilize índices


## Balanced Binary Tree 

- é uma árvore de pesquisa binária em que um nó não pode possuir mais que dois filhos e, além disso, por ser uma árvore balanceada, significa que um lado da árvore não pode ter mais nós que o outro lado.

![[Pasted image 20230816092239.png]]

![[Pasted image 20230816092402.png]]
- figura anterior - todos nós a esquerda são menores que o nó pai e a direita maiores

![[Pasted image 20230816092437.png]]

- essa árvore está desequilibrada, perdendo todas as vantagens oferecidas pela b-tree
-  *B-Tree clustered* – A tabela de dados é organizada pela coluna indexada
	- Um índice clusterizado reorganiza fisicamente as linhas da tabela com base nas colunas definidas como índice clusterizado. Isso significa que as próprias linhas de dados na tabela são organizadas de acordo com a ordem das chaves primárias (ou do índice definido como clusterizado). Uma tabela pode ter apenas um índice clusterizado, pois a organização física dos dados depende diretamente desse índice.
- *B-Tree non-clustered* -  os índices non-clustered contém apenas a indicação (ponteiros) para as páginas de dados onde estão as informações, ou seja, não há uma organização por ordem do índice
	- Um índice não-clusterizado é uma estrutura separada que armazena um mapeamento entre as chaves de índice e as localizações físicas das linhas na tabela. As linhas de dados na tabela não são reorganizadas fisicamente, independentemente do índice não-clusterizado. Uma tabela pode ter vários índices não-clusterizados.
- Em resumo, a principal diferença entre um índice clusterizado e um índice não-clusterizado está na forma como os dados são armazenados fisicamente. O índice clusterizado organiza as linhas da tabela, enquanto o índice não-clusterizado cria uma estrutura separada que aponta para as linhas na tabela

## Criando um índice

- é possível criar um índice na própria declaração de uma tabela, mas, geralmente, a necessidade de criação de um índice surge na medida que as tabelas crescem

1. **Na criação da tabela** – Usa-se a palavra reservada index, seguida do nome da coluna que será indexada.

```mysql
CREATE TABLE nomeTabela (
	nomeColuna1 tipo_dado
	,...
	,nomeColunaN tipo_dado
	,INDEX (nomeColuna)
	);
```

```mysql
CREATE TABLE cliente (
	codigo INTEGER
	,nome VARCHAR(100)
	,email VARCHAR(100)
	,INDEX (codigo)
	);
```

2.  **Alteração da tabela** – Na definição de um índice em uma tabela existente usamos o comando *create index.*

```mysql
CREATE INDEX nomeIndice ON tabela (colunas);
```

```mysql
CREATE INDEX idxContatoNome ON Contatos (nome);
```

# VIEW

- é uma representação virtual de um conjunto de dados armazenados em tabelas
- Em vez de armazenar os dados fisicamente, uma view é uma consulta salva que pode ser tratada como uma tabela ou entidade em si mesma.

```mysql
CREATE [or replace] [algorithm = algorithm_type] VIEW nomeView [(listaColuna)] AS

SELECT [with [cascaded | local] CHECK option];
```

```mysql
CREATE VIEW mostraFuncionario
AS
SELECT nomeFunc AS ‘Nome’
	,generoFunc AS ‘Genero’
	,salarioFunc AS ‘Salario’
	,emailFunc AS ‘Email’
FROM funcionario;
```

- comandos:
-  Excluir uma view através do comando drop view:

```mysql
drop view nome_da_view;
```

- Consultar as views existentes:

```mysql
show FULL tables IN nome_banco
WHERE table_type LIKE ‘view’;

SELECT table_schema
	,table_name
FROM information_schema.tables
WHERE table_type LIKE ‘view’;
```

# TRANSAÇÕES

- conjunto de operações em sequência, as quais são executadas como um bloco único e indivisível, com início e fim (término)
- principal objetivo é manter a integridade das informações armazenadas no Banco de Dados.
- *Commit* – Confirma a execução em definitivo do bloco de instruções executado, finalizando a transação com sucesso;
- *Rollback* – Descarta todas as instruções executadas, indicando que ocorreu um erro.

## Tipos
- **Implícitas** – Ocorrem automaticamente quando enviamos os comandos insert, update ou delete;
- **Explícitas** – Seguem o conceito formal de transações, onde se deve indicar o início e o término.

## Propriedades

- **Atomicidade** 
	- Bloco único (indivisível), sempre apresentando início e fim
- **Consistência**
	- Mantém a integridade dos dados, assegurando que uma transação leva o banco de dados de um estado válido para outro, mantendo as regras e restrições do sistema.
- **Isolamento**
	- Garante que as operações de uma transação sejam isoladas de outras transações em execução concorrente
- **Durabilidade**
	- uma vez que uma transação tenha sido confirmada (comitada), suas alterações sejam permanentemente armazenadas no banco de dados, mesmo em caso de falhas do sistema.

```mysql
start TRANSACTION
[comandos]
[commit / rollback]
SET autocommit = {0 ou 1 } ou {OFF ou ON};
```

## Problemas de concorrência

- **Leitura Suja (Dirty Read):** Uma transação lê dados modificados por outra transação que ainda não foi confirmada (comitada). Se a segunda transação for revertida, a primeira transação terá lido dados inválidos.
    
- **Leitura Não Repetível (Non-Repeatable Read):** Uma transação lê um valor, outro processo modifica esse valor e, em seguida, a primeira transação tenta lê-lo novamente, obtendo um valor diferente. Isso pode levar a inconsistências nas análises baseadas nos dados.
    
- **Leitura Fantasma (Phantom Read):** Uma transação executa uma consulta que retorna um conjunto de linhas, outra transação insere, atualiza ou exclui algumas linhas e, em seguida, a primeira transação executa a mesma consulta novamente, encontrando linhas adicionais ou diferentes.

- **Escrita Fantasma (Phantom Write):** Duas transações executam uma consulta similar, inserindo, atualizando ou excluindo registros que não interferem entre si. No entanto, quando as duas transações são confirmadas, uma delas é revertida devido a conflitos de bloqueio, resultando em uma alteração não esperada.

- **Perda de Atualização (Lost Update):** Duas transações tentam atualizar o mesmo dado simultaneamente. Se não houver mecanismos adequados para controlar a concorrência, uma atualização pode ser sobrescrita por outra, levando a uma perda de dados.

## Níveis de isolamento

- Para evitar os problemas de concorrência, pode ser definido um nível de isolamento para as transações

- **READ UNCOMMITTED (Leitura não confirmada):** Nesse nível, as transações podem ler dados não confirmados por outras transações. Isso pode resultar em leituras sujas, leituras não repetíveis e leituras fantasmas. É o nível de isolamento mais permissivo, mas também o menos consistente.
- **READ COMMITTED (Leitura confirmada):** Nesse nível, as transações só podem ler dados que foram confirmados por outras transações. Isso evita leituras sujas, mas ainda permite leituras não repetíveis e leituras fantasmas. É mais consistente do que o nível READ UNCOMMITTED, mas não totalmente livre de problemas de concorrência.
- **REPEATABLE READ (Leitura repetível):** Nesse nível, as transações garantem que, uma vez que tenham lido um conjunto de dados, esses dados permanecerão consistentes até o término da transação. Isso resolve o problema das leituras não repetíveis, mas leituras fantasmas ainda podem ocorrer.
- **SERIALIZABLE (Serialização):** Nesse nível, as transações são executadas de forma serializada, uma após a outra. Isso garante a máxima consistência, evitando todos os problemas de concorrência, incluindo leituras fantasmas. No entanto, isso pode levar a um desempenho reduzido devido à limitação da concorrência.

- **Declarando o nível de isolamento da transação**: a definição do nível de isolamento deverá ser declarada antes do início da transação.

```mysql
SET TRANSACTION ISOLATION LEVEL {read uncommited
	,READ commited
	,REPEATABLE READ
	,serializable};
```

```mysql
SET TRANSACTION ISOLATION LEVEL READ COMMITED;

start TRANSACTION...-- Início da transação
```

# TRIGGER 

- objeto de banco de dados que é definido para ser acionado automaticamente quando ocorre um evento específico em uma tabela
- Esse evento pode ser uma ação de inserção (INSERT), atualização (UPDATE) ou exclusão (DELETE) de dados em uma tabela.
- Os triggers podem ser úteis para implementar regras de negócios, fazer auditorias, manter registros de histórico, entre outras tarefas.
## Tipos

1.  **Triggers em Nível de Linha (Row-Level Triggers):** Esses triggers são acionados para cada linha individual afetada pelas instruções SQL que acionam o trigger. Ou seja, se uma instrução SQL afetar várias linhas, o trigger em nível de linha será acionado para cada uma dessas linhas separadamente. Esses triggers podem acessar e manipular dados específicos da linha atual.
	Por exemplo, se você tiver um trigger "AFTER INSERT" em nível de linha e inserir várias linhas em uma tabela, o trigger será acionado uma vez para cada linha inserida, permitindo que você execute ações personalizadas com base nos dados de cada linha.
2.**Triggers em Nível de Instrução (Statement-Level Triggers):** Esses triggers são acionados uma vez para cada instrução SQL que ativa o trigger, independentemente do número de linhas afetadas por essa instrução

- MySQL implementa somente trigger em nível de linha

## Sintaxe

```mysql
CREATE
	OR [replace] TRIGGER nomeTrigger {momentoDisparado}{eventoDisparado} ON nomeTabela
FOR each row

BEGIN
	/* Código da trigger */
END;
```

exemplo
```mysql
DELIMITER //
CREATE TRIGGER TG_CALCULA_FATURAMENTO_INSERT 
AFTER INSERT ON ITENS_NOTAS
FOR EACH ROW 
BEGIN
	DELETE FROM TAB_FATURAMENTO;
	INSERT INTO TAB_FATURAMENTO
	SELECT A.DATA_VENDA, SUM(B.QUANTIDADE * B.PRECO) AS TOTAL_VENDA FROM
	NOTAS A INNER JOIN ITENS_NOTAS B
	ON A.NUMERO = B.NUMERO
	GROUP BY A.DATA_VENDA;
END //

```
- **momentoDisparado** - `BEFORE` ou `AFTER`
	- Triggers "BEFORE" podem ser usados para validar ou modificar os dados antes que eles sejam realmente gravados na tabela.
	- Triggers "AFTER" são usados para executar ações após a conclusão da operação.
- **eventoDisparado** - `INSERT`, `UPDATE` ou `DELETE`

## Referências NEW e OLD

- palavras-chave especiais usadas para se referir aos valores de dados das linhas afetadas durante as operações de inserção, atualização ou exclusão.
- **`NEW`:** A referência `NEW` é usada para se referir aos novos valores que serão inseridos ou atualizados em uma tabela. Em um trigger de INSERT ou UPDATE, você pode usar `NEW` para acessar os valores que estão sendo adicionados ou modificados.
- **`OLD`:** A referência `OLD` é usada para se referir aos valores antigos que estão prestes a ser atualizados ou excluídos de uma tabela. Em um trigger de UPDATE ou DELETE, você pode usar `OLD` para acessar os valores que estão sendo modificados ou removidos.

## Comandos úteis

- Visualizar as triggers do Banco de Dados

```mysql
show triggers [{from | in} nomeBancoDados] [where = condição];
```

- Exclusão de um trigger:

```mysql
DROP TRIGGER nomeTrigger;
```

## Exemplo
- INSERT
```mysql
CREATE TABLE auditoria (
	acao CHAR(10)
	,matricula INT
	,salarioAntigo DECIMAL(10, 2)
	,salarioNovo DECIMAL(10, 2)
	,dataOperacao DATE
	);

-- Triger disparada na inclusão
delimiter $$ -- Declaração de um delimitador de comandos

CREATE TRIGGER funcionarioInclusao
AFTER INSERT ON funcionario
FOR each row

BEGIN
	INSERT INTO auditoria
	VALUES (
		‘inclusao’
		,new.matricula
		,NULL
		,new.salarioFunc
		,curdate()
		);

END$$ 
delimiter; -- volta utilizar delimitador ;

-- Incluir funcionário
INSERT INTO funcionario
VALUES (
	1
	,‘Ana Rosa Silva’
	,‘F’
	,‘1996 - 12 - 31 ’
	,8500
	,1
	,1
	,‘ana.rosa@email.com’
	,1
	);

-- Mostra os dados da tabela Auditoria
SELECT *
FROM auditoria;
```

![[Pasted image 20230817083444.png]]
- UPDATE

```mysql
DELIMITER $$
CREATE TRIGGER funcionarioAlteracao AFTER UPDATE ON funcionario
FOR EACH ROW
BEGIN
    INSERT INTO auditoria
    VALUES ('Alteracao', NEW.matricula, OLD.salarioFunc, NEW.salarioFunc, CURDATE());
END $$
DELIMITER ;

UPDATE funcionario
SET salarioFunc = 10500
WHERE matricula = 1;

-- Mostrar os dados da tabela Auditoria
select * from auditoria;

```

![[Pasted image 20230817083908.png]]

- DELETE

```MYSQL
DELIMITER $$
CREATE TRIGGER funcionarioExclusao AFTER DELETE ON funcionario
FOR EACH ROW
BEGIN
    INSERT INTO auditoria
    VALUES ('Exclusao', OLD.matricula, OLD.salarioFunc, OLD.salarioFunc, CURDATE());
END $$
DELIMITER ;

DELETE FROM funcionario WHERE matricula = 1;

-- Mostrar os dados da tabela Auditoria
SELECT * FROM auditoria;
```

![[Pasted image 20230817084023.png]]

- TRIGGER BEFORE 

```MYSQL
DELIMITER $$
CREATE TRIGGER funcionarioNovoID BEFORE INSERT ON funcionario
FOR EACH ROW
BEGIN
    SET NEW.matricula = (SELECT MAX(matricula) + 1 FROM funcionario);
END $$
DELIMITER ;

INSERT INTO funcionario
    (nomeFunc, generoFunc, NascFunc, salarioFunc,
    departamento, cargo, emailFunc, cidadeId)
VALUES
    ('Tales Heitor Souza', 'M', '2000-10-01', 7689,
    1, 2, 'tales.heitor@email.com', 1);

```

![[Pasted image 20230817084326.png]]

```MYSQL
-- Mostra as triggers do Banco de Dados aula
SHOW TRIGGERS FROM aula;
```

![[Pasted image 20230817084349.png]]


# STORED PROCEDURE 

- Conjunto de instruções SQL a serem executadas pelo  SGBD para realizar uma determinada tarefa 
- Em seu interior, são declaradas instruções de seleção, controle e repetição, podendo realizar alterações nos dados armazenados nas tabelas, porém sem retorno de valores
- Podem ou não receber parâmetros de entrada.

## Sintaxe

- **Criando**
```mysql
DELIMITER $$
CREATE OR REPLACE PROCEDURE nomeProcedimento(
    [tipo] parametro tipoDado,
    ...,
    [tipo] parametroN tipoDadoN
)
BEGIN
    /* Bloco de comandos */
END $$
DELIMITER ;

```

- **Executando**
```mysql
CALL nomeProcedimento(parâmetro);
```

- **Mostrar procedures**

```mysql
SHOW PROCEDURE STATUS
WHERE definer = 'root@localhost';

-- ou

SELECT *
FROM information_schema.routines
WHERE routine_schema = 'nomeBancoDados'
AND routine_type = 'PROCEDURE';
```

- **Excluir procedures**

```mysql
DROP PROCEDURE nomeProcedure;
```

- **Declarar variáveis**
- **Atribuir valor a variavel**
## Comandos condicionais e de repetição

### IF 
```mysql
IF condição THEN
    comandos;
ELSEIF condição THEN
    comandos;
    -- Pode haver mais blocos ELSEIF conforme necessário
ELSE
    comandos;
END IF;

```

### CASE

```MYSQL
CASE valor
    WHEN condição THEN
        comandos;
    WHEN condição THEN
        comandos;
        -- Pode haver mais blocos WHEN conforme necessário
    ELSE
        comandos;
END CASE;
```

### LOOP

```MYSQL
[identificador:] LOOP
    /* Bloco de comandos */
    IF condição THEN
        ITERATE [identificador];
    END IF;
    LEAVE [identificador];
END LOOP [identificador];
```

- A estrutura `LOOP` é usada para criar loops em SQL.
- O `ITERATE` é usado para pular a iteração atual do loop e passar para a próxima.
- O `LEAVE` é usado para sair do loop. 
- Se você não desejar usar um identificador para o loop, pode omiti-lo.

### WHILE-DO

```MYSQL
[identificador:] WHILE condição DO
    /* Bloco de comandos */
END WHILE [identificador];

```

### REPEAT-UNTIL 

```MYSQL
[identificador] REPEAT
    /* Bloco de comandos */
UNTIL condição;
END REPEAT [identificador];

```
- Similar a do-while

## Exemplo

-  procedure para gerar aleatoriamente 6 números para uma aposta de loteria. O intervalo dos números será informado como parâmetro na procedure. Os números gerados serão armazenados em uma tabela juntamente com o número do concurso da loteria.
```mysql
-- Tabela que armazena o concurso e os números gerados
CREATE TABLE cartela (
    concurso INT,
    numero INT
);

DELIMITER $$
CREATE PROCEDURE geraCartela(
    nroInicial INT,
    nroFinal INT,
    nroConcurso INT
)
BEGIN
    DECLARE nroGerado INT DEFAULT 0;
    DECLARE i INT DEFAULT 0;
    
    geraNumero: LOOP
        SET nroGerado = (SELECT FLOOR(RAND() * nroFinal) + nroInicial);
        
        IF NOT EXISTS (SELECT * FROM cartela WHERE numero = nroGerado) THEN
            INSERT INTO cartela VALUES (nroConcurso, nroGerado);
            SET i = i + 1;
        END IF;
        
        IF i < 6 THEN
            ITERATE geraNumero;
        END IF;
        
        LEAVE geraNumero;
    END LOOP geraNumero;
END $$
DELIMITER ;

```

utilizando repeat until:

```mysql
-- Tabela que armazena o concurso e os números gerados
CREATE TABLE cartela (
    concurso INT,
    numero INT
);

DELIMITER $$
CREATE PROCEDURE geraCartela(
    nroInicial INT,
    nroFinal INT,
    nroConcurso INT
)
BEGIN
    DECLARE nroGerado INT DEFAULT 0;
    DECLARE i INT DEFAULT 0;
    
    REPEAT
        SET nroGerado = (SELECT FLOOR(RAND() * nroFinal) + nroInicial);
        
        IF NOT EXISTS (SELECT * FROM cartela WHERE numero = nroGerado) THEN
            INSERT INTO cartela VALUES (nroConcurso, nroGerado);
            SET i = i + 1;
        END IF;
        
    UNTIL i >= 6 
    END REPEAT;
END $$
DELIMITER ;

```

utilizando while

```mysql
-- Tabela que armazena o concurso e os números gerados
CREATE TABLE cartela (
    concurso INT,
    numero INT
);

DELIMITER $$
CREATE PROCEDURE geraCartela(
    nroInicial INT,
    nroFinal INT,
    nroConcurso INT
)
BEGIN
    DECLARE nroGerado INT DEFAULT 0;
    DECLARE i INT DEFAULT 0;
    
    WHILE i < 6 DO
        SET nroGerado = (SELECT FLOOR(RAND() * nroFinal) + nroInicial);
        
        IF NOT EXISTS (SELECT * FROM cartela WHERE numero = nroGerado) THEN
            INSERT INTO cartela VALUES (nroConcurso, nroGerado);
            SET i = i + 1;
        END IF;
        
    END WHILE;
END $$
DELIMITER ;

```

- Chamando a procedure;

```mysql
CALL geraCartela(1, 60, 200);
SELECT * FROM cartela;
```

![[Pasted image 20230817091625.png]]

# FUNCTION

- semelhante a uma stored procedure, porém, ao final da execução, sempre retornará um valor
-  tem como objetivo suprir tarefas específicas enquanto uma procedure é mais abrangente 
- existem dois tipos de funções definidas pelo usuário:
	1. **Escalares** – Que retornam apenas um valor.
	2. **Composta** – Que retorna um conjunto de valores como resultado.

## Sintaxe

```mysql
DELIMITER $$
CREATE FUNCTION funçãoNome(
    parâmetro1 tipo_dados,
    ...,
    parâmetroN tipo_dados
) RETURNS tpDadoRetorno [NOT] DETERMINISTIC
BEGIN
    -- instruções
    RETURN valor;
END $$
DELIMITER ;
```

-  Uma função **determinística** retorna o mesmo resultado para os mesmos parâmetros de entrada. Já uma função **não determinística** retorna resultados diferentes para os mesmos parâmetros.

**Apresentando funções**

```mysql
SHOW FUNCTION STATUS WHERE db = 'nomeBancoDados';

-- Mostrar informações sobre as funções no banco de dados
SELECT *
FROM information_schema.routines
WHERE routine_schema = 'nomeBancoDados'
AND routine_type = 'FUNCTION';

```

**Executando uma função**

Uma função implementada por um usuário pode ser utilizada com qualquer comando (select, insert, update, delete, entre outros) em conjunto com o nome da função desejada e a declaração dos parâmetros de entrada necessários, 

```mysql
-- Chamada de função com um parâmetro
SELECT nomeFunção(parâmetro);

-- Chamada de função com múltiplos parâmetros e referência a uma tabela
SELECT nomeFunção(parâmetro1, ..., parâmetroN)
FROM nomeTabela;
```

## Exemplo

- função que retorne se um número é par ou ímpar

```mysql
DELIMITER $$
CREATE FUNCTION parImpar(numero INT)
RETURNS CHAR(5) DETERMINISTIC
BEGIN
    DECLARE tipo CHAR(5) DEFAULT NULL;
    SET tipo = 'impar';
    
    IF numero % 2 = 0 THEN
        SET tipo = 'par';
    END IF;
    
    RETURN tipo;
END $$
DELIMITER ;

```

```sql
SELECT parImpar(10), parImpar(5);
```

![[Pasted image 20230817092831.png]]

-  função que retorne a idade de um funcionário.

```mysql
DELIMITER $$
CREATE FUNCTION CalculaIdade(nascimento DATE)
RETURNS INT DETERMINISTIC
BEGIN
    DECLARE dataAtual DATE;
    DECLARE idade INT DEFAULT 0;
    
    SET dataAtual = (SELECT CURDATE());
    SET idade = YEAR(dataAtual) - YEAR(nascimento);
    
    RETURN idade;
END $$
DELIMITER ;

-- Executando a função desenvolvida:
SELECT nomeFunc, nascFunc, CalculaIdade(nascFunc) AS idade
FROM funcionario;
```

![[Pasted image 20230817092957.png]]

## Função dentro de procedure
- podemos chamar uma função dentro de uma procedure
- Criando a função de número aleatório:

```mysql
DELIMITER $$
CREATE FUNCTION numeroAleatorio(inicio INT, final INT)
RETURNS INT DETERMINISTIC
BEGIN
    DECLARE numero INT DEFAULT 0;
    
    SET numero = (SELECT FLOOR(RAND() * final) + inicio);
    
    RETURN numero;
END $$
DELIMITER ;
```

- procedure

```mysql
-- Tabela que armazena o concurso e os números gerados
CREATE TABLE cartela (
    concurso INT,
    numero INT
);

DELIMITER $$
CREATE PROCEDURE geraCartela(
    nroInicial INT,
    nroFinal INT,
    nroConcurso INT
)
BEGIN
    DECLARE i INT DEFAULT 0;
    
    WHILE i < 6 DO
        DECLARE nroGerado INT;
        SET nroGerado = numeroAleatorio(nroInicial, nroFinal);
        
        IF NOT EXISTS (SELECT * FROM cartela WHERE numero = nroGerado) THEN
            INSERT INTO cartela VALUES (nroConcurso, nroGerado);
            SET i = i + 1;
        END IF;
        
    END WHILE;
END $$
DELIMITER ;
```

# CURSOR 

- um cursor é uma estrutura que permite percorrer e manipular resultados de consultas SQL de forma individual, semelhante a um ponteiro em linguagens de programação
- Um cursor é particularmente útil quando você deseja processar linhas de um conjunto de resultados um por um. Isso é especialmente útil quando você precisa executar operações complexas ou aplicar lógica personalizada em cada linha de resultado.
- Um cursor é somente para leitura
-  A leitura dos dados por meio do cursor ocorre sequencialmente na ordem definida pelo select
-  No MySQL, o cursor pode carregar os dados na memória criando uma tabela temporária (cópia) ou, ainda, apontar diretamente para o conjunto de dados obtido na consulta (asensitive).
- Normalmente, o cursor é declarado dentro de uma procedure

## Etapas para utilização do cursor

1. Declaração do cursor (`DECLARE`, alocação de memória);
2. Abertura do cursor (`OPEN`);
3. Execução do cursor (`FETCH`);
4. Fechamento e liberação do cursor (`CLOSE`).

### Declarando um cursor
- Antes de usar um cursor, você precisa declará-lo. A declaração de cursor inclui a consulta SQL que será usada para buscar os registros e quaisquer parâmetros necessários.

```mysql
DECLARE cursorNome CURSOR FOR expressãoSelect;
```

### Abrindo um cursor
- Após declarar um cursor, você precisa abrir o cursor. Isso executa a consulta SQL e cria um conjunto de resultados temporário.

```mysql
OPEN cursorNome;
```

### Executando um cursor
- Você pode usar comandos como `FETCH` para ler registros do cursor um por um.
- Você pode aplicar lógica personalizada aos registros enquanto os lê. Isso pode incluir cálculos, atualizações em outras tabelas, ou qualquer outra operação desejada.

```mysql
FETCH cursorNome INTO listaVariáveis;
```

### Fechando um cursor
- Depois de terminar de usar o cursor, é importante fechá-lo para liberar os recursos. Isso também encerra a leitura dos registros.

```mysql
CLOSE cursorNome;
```

### Tratamento de erros

- Erros podem ocorrer durante a execução de um cursor devido a várias razões, como registros ausentes, divisão por zero ou violação de restrições. Para lidar com esses erros de forma eficaz, é comum usar construções chamadas "handlers de erro".

```mysql
DECLARE ação HANDLER FOR NOT FOUND
SET varFinal = TRUE;
```

- A ação pode assumir dois estados, isto é, manter a execução com a ação `CONTINUE` ou finalizar a execução com a ação `EXIT`;
-  A variável final define que o cursor chegou ao final do conjunto de resultados

## Exemplo

- A empresa solicitou uma simulação de reajuste para salários dos funcionários e, sendo assim, criaremos um cursor que possibilite fazer essa simulação, cujas regras são
	• Funcionários do departamento 1 terão 10% de aumento;
	• Funcionários do departamento 2 terão 12% de aumento;
	• Demais funcionários terão 8% de aumento.

```mysql
-- Tabela para armazenar a simulação do reajuste
CREATE TABLE simulacao (
    nome VARCHAR(100),
    salario DECIMAL(10, 2),
    novoSalario DECIMAL(10, 2)
);

-- Procedure para calcular o reajuste
DELIMITER $$
CREATE PROCEDURE simulaReajuste()
BEGIN
    -- Variável para identificar o final do cursor
    DECLARE done BOOLEAN DEFAULT FALSE;
    DECLARE vnome VARCHAR(100);
    DECLARE vsalario DECIMAL(10, 2);
    DECLARE vnovoSalario DECIMAL(10, 2);
    DECLARE vdepartamento INT;

    DECLARE cursorFuncionario CURSOR FOR
        SELECT nomeFunc, departamento, salarioFunc
        FROM funcionario;
        
    -- Altera o status da variável de fim do cursor
    -- Após a leitura linha a linha, quando chegar ao final do cursor, o handler irá alterar o valor da variável ‘done’ para verdadeiro.
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
    
    OPEN cursorFuncionario;
    
    leCursor: LOOP
        FETCH cursorFuncionario INTO vnome, vdepartamento, vsalario;
        
        IF done THEN -- Testa se o cursor chegou ao final
            LEAVE leCursor; -- Sai do loop no final
        END IF;
        
        IF vdepartamento = 1 THEN
            SET vnovoSalario = vsalario * 1.10;
        ELSEIF vdepartamento = 2 THEN
            SET vnovoSalario = vsalario * 1.12;
        ELSE
            SET vnovoSalario = vsalario * 1.08;
        END IF;
        
        INSERT INTO simulacao VALUES (vnome, vsalario, vnovoSalario);
    END LOOP;
    
    CLOSE cursorFuncionario;
END $$
DELIMITER ;

```

```mysql
SELECT * FROM simulacao;
```

![[Pasted image 20230817102355.png]]

---
# Outros materiais SQL

## Window funtions
- ranquamento, agregação ou posição
northwind database
```postgresql
select 
	employee_id,
	order_date,
	first_value (order_date) over (partition by employee_id order by order_date) -- mostra a data da primeira orderm por funcionṕario id
	order_dae,
	product_id
from orders
inner join order_details on 
	orders.order_id = order_details.order_id
inner joint products on
	products.product_id = order_details.product_id
```

é uma função que gera um valor dentro de um janela e repete esse valor na janela inteira - transcrição literal video 

![[Pasted image 20231110225338.png]]

![[Pasted image 20231110225445.png]]


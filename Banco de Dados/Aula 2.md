# MODELO LÓGICO OU RELACIONAL 

- Todos os dados estão armazenados em tabelas
- Linguagem Padrão utilizada é o SQL
- Se baseia no conceito de matrizes
	- linhas - tuplas
	- colunas - atributos
- BD relacional é composto de - Atributos, domínio, tuplas e relações

## COMPONENTES DO MODELO
### ATRIBUTO

- Identifica o dado que está armazenado em um Banco de Dados
- nome de cada coluna presente na tabela

![[Pasted image 20230724083056.png]]

### DOMÍNIO

- Refere-se ao tipo de dado -  define o tamanho e os valores que cada atributo poderá receber.
- Definição de padrões de validação

![[Pasted image 20230724083223.png]]

### TUPLA

- conjunto horizontal de dados presentes nos atributos -  registro ou linha presente em uma tabela

![[Pasted image 20230724083306.png]]


### RELAÇÃO

- Conjunto de tuplas relacionadas 
- Cada relação está vinculada a um objeto específico dentro do Bancos de Dados.
-  tabelas são uma divisão lógica do Bancos de Dados, pois, fisicamente, o Bancos de Dados é um arquivo único.

![[Pasted image 20230724083836.png]]


## REGRAS DE CODD

- **Regra Fundamental (Regra 0):** Um banco de dados relacional deve usar recursos relacionais para gerenciamento.
    -
- **Regra de Informação (Regra 1):** As informações devem ser representadas em tabelas usando colunas e linhas.
    
- **Regra de Acesso Garantido (Regra 2):** Cada dado é acessado usando o nome da tabela, chave primária e nome da coluna.
    
- **Regra de Tratamento de Valores Nulos (Regra 3):** Valores nulos são suportados de forma sistemática para representar informações ausentes.
    
- **Regra de Catálogo On-line Dinâmico (Regra 4):** Metadados são tratados como dados e acessíveis usando a mesma linguagem usada para dados.
    
- **Regra de Sublinguagem Ampla dos Dados (Regra 5):** Há suporte para várias linguagens, mas uma linguagem principal deve abranger consultas e manipulação.
    
- **Regra de Atualização de Visualizações (Regra 6):** Visualizações atualizáveis também podem ser atualizadas pelo sistema.
    
- **Regra de Inserção, Atualização e Exclusão de Alto Nível (Regra 7):** Conjuntos de dados podem ser manipulados por comandos simples de inclusão, atualização e exclusão.
    
- **Regra de Independência Física de Dados (Regra 8):** Alterações físicas não devem afetar programas e consultas.
    
- **Regra de Independência Lógica de Dados (Regra 9):** Mudanças nas relações e visões não devem impactar as aplicações.
    
- **Regra de Independência de Integridade (Regra 10):** Mudanças nas regras de integridade não afetam as aplicações.
    
- **Regra de Independência de Distribuição (Regra 11):** Mudanças geográficas dos dados não devem afetar as aplicações.
    
- **Regra de Não Transposição das Regras (Regra 12):** Linguagens de baixo nível não podem burlar regras de integridade e restrições.

## ALGEBRA RELACIONAL 

- todos os dados são representados como relações matemáticas
- O tratamento dos dados é feito pelo cálculo relacional ou pela álgebra relacional.

### Operadores Relacionais

- atuar nas relações, com o objetivo de manipular uma ou mais relações como entrada e produzir uma nova relação como saída (resultado).

#### Operador de Atribuição (Assignment) - $\leftarrow$
-  redirecionar o resultado da operação para uma nova relação

#### Operador de seleção (Where) $\sigma$
- Seleciona os dados de acordo com uma condição pré-estabelecida, conhecida como predicado

![[Pasted image 20230724085542.png]]


#### Operador de Projeção(Select) $\pi$
- Retorna determinadas *colunas* de uma relação
- Ex.: $\pi$ nome (cliente):

![[Pasted image 20230724085818.png]]

## RESTRIÇÕES DE INTEGRIDADE

- **Integridade de Domínio**
- **Integridade de Vazio**
- **Integridade de Entidade**
- **Integridade Referencial** - O valor que é chave estrangeira em uma tabela destino, deve ser chave primária de algum registro na tabela origem
- **Restrição de unicidade (unique)** -  Garante a unicidade do valor da chave primária em cada uma das tuplas de uma relação
- Restrições de atributos e padrões
	- Nenhuma chave primária ou estrangeira poderá conter valor nulo
	- Valor padrão (default): definição de um valor pré-definido quando não for informado
	- Validação (check): aplicação de regras de validação
- **Integridade da chave**: toda tupla apresenta um conjunto de atributos que a identifica de maneira única na relação
- **Integridade Semântica** -  descreve as regras de negócio da organização através da utilização de assertions ou triggers

### CHAVES 
- Uma relação (tabela) deve ter a capacidade de identificar cada uma das tuplas separadamente - chaves
- As relações (tabelas) interagem umas com as outras por meio de chaves.

#### Chave composta
- conter mais de um atributo em sua composição. Normalmente, a chave composta deriva de uma relação n:n 
- É bastante comum usar a chave Surrogate Key (chave artificial)

![[Pasted image 20230724100843.png]]


- Exemplo de caso
![[Pasted image 20230724101153.png]]

# NORMALIZAÇÃO

-  **anomalia de modificação** é um efeito colateral inesperado que ocorre quando se alteram os dados de uma tabela com redundâncias excessivas.
-  A **normalização de dados** é uma técnica de **decomposição** utilizada no projeto de banco de dados com objetivo de prover um armazenamento consistente, evitando redundância de dados e anomalias de atualização.
- O **processo de normalização** sujeita um esquema de relação a uma série de testes para certifica-se de que ele satisfaça certa forma normal
- quando aplicamos a normalização sobre um conjunto de tabelas, é normal que surjam novas colunas ou relações para que os dados possam ser mais bem distribuídos pelas tabelas

## DEPENDÊNCIA FUNCIONAL 

- A dependência funcional (DF) é uma restrição de duas ou mais colunas de uma tabela
- X determina Y (X →Y) se existe no máximo um valor de Y para cada valor de X
	- (EX. para cada CPF de cliente existe apenas um endereço, porém para o mesmo endereço pode existir mais de um CPF, logo Y->X não é necessariamente válido quando X->Y)
- as dependências funcionais identificam potenciais chaves candidatas. (X -> Y, X é chave candidata)
- Se não houver outras chaves candidatas, um determinante se tornará a chave primária se ele não permitir valores nulos.

>[!Definição]
> uma dependência funcional, denotada por X → Y entre dois conjuntos de atributos X e Y, que são subconjunto de R, especifica uma restrição nas possíveis tuplas que formam um estado da relação r de R. A restrição é que, para quaisquer duas tuplas t1 e t2 em r que tenha t1[X] = t2[X], elas também têm de ter t1[Y] = t2[Y].

- se duas tuplas tiverem o mesmo valor para X, então elas também terão o mesmo valor de Y. X é chamando de *determinante* e Y de *determinado*.
- Uma dependência funcional pode ser considerada *trivial*, neste caso se X → Y e X contém (Ↄ) Y.

## CHAVES

- **SUPERCHAVE** -  uma superchave de um esquema de relação $R = {A 1, A2, ..., An}$ é um conjunto de atributos $S \subset R$ na qual não haverá duas tuplas t1 e t2, em qualquer estado válido da relação r de R, cuja $t1[S] = t2[S]$
 - uma superchave é um conjunto de atributos que tem a característica de restringir o conjunto de tuplas de uma relação a apenas uma linha.
 -  a chave é defendida como uma **superchave mínima** (vou chamar ela de K), onde qualquer remoção de atributo de K fará com que K deixe de ser superchave da relação
 - Uma chave mínima é  chave candidata
 - uma das chaves candidatas é escolhida para ser **chave primária**. As demais se tornam **chaves secundárias**
 -  **atributo primário** - atributo que faz parte de uma chave candidata

## PRIMEIRA FORMA NORMAL (1FN)

-  Sua definição prevê que todos os atributos de uma relação devem ter seus valores definidos sobre domínios **atômicos ou indivisíveis** - ou seja, os campos  não devem ser compostos ou multivalorados
- para resolver o problema de atributos compostos, separamos os valores em várias colunas
-  Já, para resolver o problema de atributos multivalorados, criamos uma tabela com a chave da relação original e uma coluna atômica que representa os diversos/múltiplos valores em linhas distintas.
- Evita-se a redundância e atributos repetidos 

Tabela não normalizada:

![[Pasted image 20230725081020.png]]

- Cria-se uma nova relação para os atributos multivalorados, a chave será uma chave composta da chave original e do atributo
![[Pasted image 20230725081108.png]]

- Na relação original separa-se o atributo composto em vários atributos atômicos

![[Pasted image 20230725081149.png]]

>[!Primeira forma Normal]
>- Uma relação R existe na primeira forma normal (1FN) se, e somente se, todos os **domínios subjacentes** contiverem apenas **valores atômicos**.
>- No modelo relacional, um domínio é atômico se os elementos do domínio são considerados **unidades indivisíveis**. Um esquema de relação R está na primeira forma normal se **todos os atributos de R são atômicos**. 
>- A primeira forma normal afirma que o **domínio** de um atributo deve incluir **apenas valores atômicos (simples e indivisíveis)** e que o valor de qualquer atributo em uma tupla deve ser um único valor do domínio desse atributo.
>- A primeira forma normal **evita** as chamadas relações aninhadas, essas relações contêm vários atributos em uma única coluna e não são permitidas no modelo relacional.


## SEGUNDA FORMA NORMAL (2FN)

- relação R está na 2FN se todo atributo não primário A em R tem dependência funcional total de uma chave candidata.
- ou seja, **não existe dependência parcial**
- a 2FN refere-se às relações com chave primária composta.

![[Pasted image 20230725082332.png]]


>[!Segunda Forma Normal]
>- Um esquema de relação R está na 2FN se cada atributo não primário A em R for total e funcionalmente dependente da chave primária de R.
>- Uma tabela está na segunda forma normal (2FN) se estiver na primeira forma normal (1FN), e seus atributos não chaves forem totalmente dependentes da chave primária.

## TERCEIRA FORMA NORMAL (3FN)

- Conformidade com a 2FN; e
- Não possuir nenhum atributo dependente de outros atributos que não sejam chaves da relação.

>[!Terceira forma normal]
>Um esquema de relação R está na terceira forma normal (3FN) sempre que uma dependência funcional não trivial X → A for determinada em R, qualquer
(a) X é superchave de R; ou
(b) A é atributo primário de R;

-  todo atributo não primário da relação não ser transitivamente dependente de uma chave da relação

![[Pasted image 20230725083103.png]]

- para que exista necessidade de normalizar utilizando a terceira forma normal temos que ter 3 atributos, vamos supor A, B e C, de forma que A seja primário e B e C não primários. Além disso, temos que ter uma dependência transitiva onde A → B e B→ C.

## RESUMO
Para chegarmos até a terceira forma normal temos que cumprir alguns requisitos. As relações do modelo não podem ter atributos compostos ou multivalorados (1FN), não pode existir em cada uma das relações dependência parcial (2FN) nem dependência transitiva (3FN).


# CONVERSÃO PARA O MODELO FÍSICO 

- deve-se levar em consideração as limitações do Sistema Gerenciador de Bancos de Dados (SGBD) escolhido 
- os objetos (relações) podem ser definidos e agrupados em **esquemas**
- As tabelas e as colunas são criadas de acordo com as definições do modelo lógico.
-  criadas restrições, visualizações, índices, gatilhos e procedimentos.

## ARQUIVO FÍSICO

-  as tabelas de um Bancos de Dados implicam um agrupamento lógico dos dados. Fisicamente, no disco, o Bancos de Dados é normalmente um arquivo único,
- é armazenado também o dicionário de dados, que é uma descrição da forma como os dados devem ser apresentados e manipulados
- , existem SGBDs que armazenam outros tipos de arquivos, como o arquivo de log das transações
-  o gerenciamento do Bancos de Dados fica a cargo do DBA

## Terminologias e Equivalências

| Modelo conceitual | Modelo Relacional | Modelo Físico |
| ---------------- | ----------------- | ------------- |
| Entidade         | Relação           | Tabela        |
| Campo            | Atributo          | Coluna        |
| Registro         | Tupla             | Linha              |


- Após a conversão do modelo relacional para o modelo físico, resta apenas executar o script em SQL para a criação do Bando de Dados
- Ferramentas oferecem a geração de forma automática do script a partir do modelo 

# SCHEMAS

- Além do modelo relacional também existe a **modelagem dimensional**, usada na criação de Data Warehouse e Data Mart, que são a base para o Business Intelligence (BI).
- Um **Data Warehouse** (armazém de dados) consiste em um Bancos de Dados que reúne informações de várias fontes
-  um **Data Mart** é uma divisão lógica de um Data Warehouse, que atende a uma área específica de negócio

## MODELAGEM DIMENSIONAL 

- os modelos dimensionais abarcam um conjunto de dados desnormalizados, projetados para a recuperação de dados de um Data Warehouse
- permite a visualização das mesmas informações a partir de ângulos distintos
-  dois pilares: dimensões e fatos.

### Tabela Dimensão
- Conjunto de objetos que descrevem e classificam os fatos por meio de seus atributos.
- Normalmente, as dimensões apresentam atributos com dados textuais
-  contêm a descrição dos fatos que serão analisados

### Tabela Fato
- Os fatos são as medidas do negócio
- Geralmente englobam dados numéricos e aditivos

## MODELOS

A modelagem dimensional tem três tipos de modelos:
	- Estrela (Star Schema);
	- Floco de neve (Snow Flake)
	- Constelação (Fact Constellation)

### Modelo estrela – Star Schema

-  todas as dimensões se relacionam diretamente com a tabela fato
- as dimensões devem conter todas as descrições necessárias para definir os fatos que vão ser analisados
- as dimensões não são normalizadas

![[Pasted image 20230725092703.png]]

### Modelo Floco de Neve 
-  as dimensões não se relacionam necessariamente com a tabela fato, pois podem se relacionar com outras dimensões

![[Pasted image 20230725092753.png]]

### Modelo constelação - Fact Constellation
- apresenta mais de uma tabela fato
- várias “estrelas”, formando uma constelação

![[Pasted image 20230725092924.png]]


# STRUCTURED QUERY LANGUAGE (SQL)

- a comunicação com o Bancos de Dados será realizada com o SQL.
- A IBM foi a primeira empresa a desenvolver um modelo de Bancos de Dados relacional, consequentemente, o SQL, na década de 1970.
- Oracle e Microsoft, criaram Bancos de Dados relacionais – consequentemente, os seus SQLs
- Padronização - em 1986 a ANSI lançou a primeira versão do SQL ANSI
- Existência de interfaces gráficas para facilitar interface entre BD e SGBD

## DIVISÃO DO SQL 

- **Data Definition Language (DDL)** -  comandos para criação, alteração ou exclusão dos objetos. Tais comandos são: *create, drop, alter e truncate*.
- **Data Manipulation Language (DML)** - atua na manipulação de tabelas, através de inserções, exclusões e alterações em linhas (registros) armazenadas em tabelas. Os comandos pertencentes a essa subdivisão são: *insert, update, delete e merge.*
- **Data Query Language (DQL)** -  possibilita a consulta dos dados. O comando é o *select*.
- **Data Control Language (DCL)** -  controle de acesso dos usuários aos objetos e dados, através dos comandos *grant* e *revoke*.
-  **Data Transation Language (DTL)** - os comandos *commit, rollback e savepoint* permitem, respetivamente, a confirmação ou o cancelamento de uma transação

![[Pasted image 20230725093904.png]]

## QUERY (SCRIPT)

- uma query é uma instrução SQL
- Cada instrução SQL deverá ser finalizada com ponto e vírgula (;)
- Outro detalhe é que você pode inserir comentários em uma query, englobando apenas uma linha (--) ou várias linhas (/\* ... \*/).

## DIALETOS

- cada empresa que desenvolve SGBDs (Oracle, Microsoft, IBM, entre outras), além de usar o padrão do SQL ANSI, também utiliza uma linguagem adicional para o desenvolvimento de códigos mais avançados no Bancos de Dados, o que chamamos de dialeto

• PL/SQL é a linguagem de programação utilizada pelo Oracle e MySQL;
• Transact-SQL (T-SQL) é propriedade da Microsoft e Sybase;
• SQL/PL, DB2 da IBM;
• PL/pgSQL, PostgreSQL (variação do PL/SQL); e
• PSQL, Firebird. 
CHA#  CONCEITOS DEFINIÇÕES E MODELOS

-  Conjunto de dados inter-relacionados representando informações de um domínio específico;
-  é o local onde são armazenados os dados de uma aplicação.

## Modelos de Banco de Dados 

 - Hierárquico;
 - Rede;
 - Orientado a objetos;
 - Relacional;
 - NoSQL ou não-relacional.

### Modelo hierárquico
- surgiu na década de 1960 com a primeira linguagem de Banco de Dados, conhecida como DL/I
-  os dados são armazenados em estruturas no formato de árvore. 
- A desvantagem está na rigidez da estrutura de dados, em que, no caso de alterações da classe principal ou de classes dependentes, obrigaria que fosse refeito todo o Banco de Dados

![[Pasted image 20230720081130.png]]

### Modelo em Redes
- surgiu entre as décadas de 1960 e 1970 como uma extensão do modelo hierárquico
- Permite que nós filhos tenham mais de um pai
- ainda apresenta problemas de flexibilidade na atualização dos dados 

![[Pasted image 20230720081534.png]]

### Modelo orientado a objetos 

- Incorpora as características da metodologia de desenvolvimento orientado a objetos com os conceitos de Sistema Gerenciador de Banco de Dados (SGBD)
- a informação é organizada  e, consequentemente, armazenada sob a forma de objetos
-  manipulação é feita por meio de métodos.

### Modelo Relacional

-  criado na década de 1970 por Dr. Edgar Frank Codd
- O Banco de Dados relacional está estruturado em relações (tabelas) relacionadas entre si, relações essas que possuem atributos. 

### Modelo NoSQL
- projetados para armazenar e manipular grandes volumes de dados não estruturados ou semi-estruturados.
- maior flexibilidade na modelagem dos dados, permitindo que as informações sejam armazenadas em diferentes formatos, como documentos, grafos, pares chave-valor ou colunas

#  SISTEMA GERENCIADOR DE BANCO DE DADOS (SGBD)

- é a interface entre os dados de baixo nível, armazenados em um Banco de Dados, e os usuários e as aplicações, que desejam acessar e manipular esses dados.
- Possibilita a realização de diversas operações
	- Adição, remoção e atualização de tabelas no Banco de Dados;
	- Inserção de novos dados;
	- Recuperação, atualização e exclusão de dados.
- Como objetivos, o SGBD deve:
	-  Ocultar dos usuários os detalhes mais técnicos de funcionamento do Banco de Dados - *abstração de dados*
	- Prover independência de dados às aplicações 

## Características de um SGBD

- Controle de redundância
- Compartilhamento dos dados e concorrência
- Controle de acesso
- Controle de transações
- Possibilidade de múltiplas interfaces
- Restrições de integridade
- Backup e recuperação de dados
- Independência de dados
- Eliminação de inconsistências
- Padronização dos dados

## Sistema de Banco de Dados

- é um ecossistema que engloba quatro componentes principais:
	- Hardwares
	- SGBD
	- Aplicações
	- Usuários
- Os usuários podem ser classificados como:
	- Programador de aplicações
	- Administrador de Banco de Dados ou DBA
	- Usuário final 

![[Pasted image 20230720091922.png]]


## Administrador de Bando de Dados (DBA)

-  um ou mais responsáveis pela tarefa de gerenciamento do Banco de Dados
-  responsáveis pela autorização de acesso ao Banco de Dados para os demais usuários, coordenação e monitoração do uso
- Funções:
	- Definição do Banco de Dados;
	- Estrutura de armazenamento e definição de acesso aos dados;
	- Esquema físico e organização dos dados
	- Conceder acesso aos usuários;
	- Cuidar da integridade dos dados;
	- Acompanhar o desempenho do Banco de Dados;
	- Atividades de manutenção e backups.

# MODELAGEM DE DADOS

- Os modelos ajudam a demonstrar graficamente o Banco de Dados que será construído.
- pode ser descrito ou modelado em vários níveis de abstração
	- Modelo conceitual
	- Modelo lógico
	- Modelo físico 

## Projeto de Bando de dados 

- Etapas
	1. Análise de Requisitos
	2. Modelagem conceitual
	3. Modelo lógico 
	4. Modelo físico
- todo e qualquer projeto é guiado do início ao fim pelas regras de negócio

![[Pasted image 20230720093111.png]]

## Modelo Conceitual 

- Define quais os dados que precisam estar presentes no Banco de Dados, sem se importar com a implementação do modelo físico.
- Independente do SGBD
- Usado para envolver o cliente 
- Somente as entidades e campos principais
- Uma das técnicas mais utilizadas entre os profissionais da área é a abordagem Entidade-Relacionamento (ER)
![[Pasted image 20230720093435.png]]

## Modelo Lógico

- descrevemos o Banco de Dados no nível do SGBD - depende do SGBD
-  considerará as limitações e as características particulares do tipo de tecnologia presente no Banco de Dados escolhido
- Define as chaves primárias das entidades;
-  Adequação ao padrão de nomenclatura;
- definir quais as relações (tabelas) e quais os atributos que compõem as relações, bem como os tipos de dados  que serão armazenados nesses atributos.
![[Pasted image 20230720093922.png]]

## Modelo Físico

- Considera os limites impostos pelo SGBD e pelos requisitos não funcionais dos programas que acessam os dados.
- Descrição detalhada de como a base de dados está armazenada internamente

![[Pasted image 20230720094151.png]]

# MODELO ENTIDADE RELACIONAMENTO - MER 

-  desenvolvido pelo professor Peter Chen (1990)
-  modelo de dados conceitual de alto nível
- Conceitos fundamentais:
	- **Entidade**: representação abstrata de um objeto do mundo real que desejamos armazenar informações - irão formar tabelas
	- **Campo**: características particulares de cada entidade
		- O conjunto de informações contidas nos campos formam o que chamamos de *registro*
	- **Relacionamento:** associação entre duas ou mais entidades.

## ENTIDADE

### TIPOS DE ENTIDADE

#### ENTIDADE FUNDAMENTAL
- Possui chave primária simples
- não necessita da existência de qualquer outra entidade para existir - é independente 

#### ENTIDADE ASSOCIATIVA
- entidade definida a partir da simplificação de um relacionamento de muitos para muitos entre duas ou mais entidades

#### ENTIDADE FRACA
- caracteriza-se pela dependência existencial
- Tanto o relacionamento quanto a entidade deverão serem representados com borda dupla.
- ![[Pasted image 20230720095328.png]]
### INSTÂNCIA DE UMA ENTIDADE

- São as informações armazenadas nos campos de uma entidade

![[Pasted image 20230720095554.png]]


### REGRAS PARA NOMEAR UMA ENTIDADE

- Deve ser única no modelo
- O nome não pode conter espaços em branco
- O nome não pode conter caracteres especiais
-  Preferencialmente, opte por nomes curtos e significativos.

### REPRESENTAÇÃO
- São representadas por um retângulo com o nome da entidade
- ![[Pasted image 20230720095825.png]]
### CAMPOS
- as propriedades que caracterizam uma entidade

#### TIPOS
- Os campos podem ser:
	- Obrigatório/Opcional
	- Simples/Composto
	- Monovalorado/Multivalorado
	- Derivado

![[tmp3_wz0pt2.png]]


##### OBRIGATORIEDADE

- **Campo obrigatório** - deve possuir obrigatoriamente um valor
- **Campo opcional ou nulo** - seu preenchimento não é obrigatório

##### ESTRUTURA
- **Campo Simples** - Não podem ter o seu conteúdo divido
- **Campo composto** - Podem ser divididos em partes menores que podem inclusive gerar novos campos (ex. nome pode ser divido em nome e sobrenome)

##### QUANTIDADE DE VALORES
- **Campo monovalorado** - possui um único valor para a entidade (CPF)
- **Campo multivalorado** - podem possuir mais de um valor para uma entidade (telefone)

##### ARMAZENAMENTO
- **Campo armazenado** - efetivamente armazenado no BD
- **Campo derivado** - Derivado de outros campos ou entidades relacionados a ele (idade da data de nascimento)

#### DOMÍNIO
- Conjunto de todos os valores possíveis para determinado campo 

#### REGRAS DE NOMEAÇÃO

- únicos na entidade
- sem espaços em branco
- sem caracteres especiais
- Utilizar nomes significativos que identifiquem o seu conteúdo
- Preferencialmente nomes curtos

#### FORMAS DE REPRESENTAÇÃO

- presentado por meio de uma linha que o liga a uma determinada entidade, possui uma ponteira que representa a prioridade que o campo exerce dentro da entidade
	- campo principal (chave primária), secundária, estrangeira ou campo comum

![[Pasted image 20230720102404.png]]


#### TIPOS DE CHAVE 

##### CHAVE PRIMÁRIA OU PRIMARY KEY

- conjunto de campos que permite identificar unicamente uma instância da entidade
- Identificada pela sigla *PK (Primary Key)*;
- O valor contido nesse campo deve ser único para cada instância da entidade -> não poderá sofrer alteração
- Não poderá receber valores duplicados ou nulos
- Chave primária que apresente mais de um campo é denominada de *chave primária composta*
-  **Chave primária não natural**: existem situações em que não temos um campo “natural”, ou seja, próprio da entidade que possa ser a chave primária. Neste caso utilizamos uma *Surrogate Key*, geralmente um campo numérico sequencial 

##### CHAVE ESTRANGEIRA OU FOREIGN KEY

- campo ou um conjunto de campos presentes em uma entidade, mas que pertencem a outra entidade
- Identificada pela sigla *FK (Foreign Key*);
- Utilizada para referenciar o relacionamento com outra entidade
- Sempre será uma chave primária de outra entidade associada
- O valor da chave estrangeira poderá se repetir


## RELACIONAMENTO OU ASSOCIAÇÃO 

- Um relacionamento pode ser entendido como uma associação entre as entidades devido as regras de negócio
- Ele se manifesta pelos campos em comum nas tabelas
- utilizamos um losango que estabelece a ligação entre as entidades envolvidas, conectando-as por meio de uma linha.

![[Pasted image 20230721091230.png]]

### AUTORRELACIONAMENTO

- Relacionamento entre instâncias da mesma entidade
- Normalmente há diferenciação pelo papel 

![[Pasted image 20230721091435.png]]

### ESPECIALIZAÇÃO E GENERALIZAÇÃO

- A *especialização* ocorre quando existe a presença de propriedades particulares em uma entidade, provocando uma subdivisão 
-  *generalização* é o inverso da especialização, isto é, agrega as similaridades

![[Pasted image 20230721091801.png]]

# CARDINALIDADE

- Expressa o número de instâncias da entidade A que podem ser associadas a uma outra determinada instância da entidade B relacionada.

## Um para um (1:1)

- UMA instância da entidade está associada a apenas UMA instância de outra entidade e, de forma inversa, o mesmo acontece.
- a chave estrangeira poderá ficar em qualquer uma das entidades

![[Pasted image 20230721092314.png]]

- quando ocorrer um relacionamento 1:1, sua existência é opcional, sendo possível transformar uma entidade em um campo da outra

##  Um para muitos / muitos para um (1:n / n:1)

- Uma entidade está associada a várias instâncias de outra entidade, mas de forma inversa, uma entidade apenas pode estar associada a no máximo UMA instância da entidade
-  a cardinalidade n sempre terá precedência sobre a cardinalidade 1.

![[Pasted image 20230721092857.png]]

-  a chave estrangeira deverá ficar sempre na entidade do lado n do relacionamento.

![[Pasted image 20230721093109.png]]

## Muitos para muitos (n:n / n:m)

-  uma entidade está associada a várias instâncias de outra entidade e o inverso ocorre da mesma maneira.

![[Pasted image 20230721093235.png]]

- Relacionamentos cuja cardinalidade resulte em n:n sempre gerarão uma nova entidade -> *entidade associativa*
- Nela adicionaremos a chave primária das entidades envolvidas no relacionamento
- o relacionamento torna-se automaticamente 1:n.
- A chave primária da entidade associativa pode ser:
	-  composta pelas chaves estrangeiras das entidades Conta e Cliente.
	- Criar uma chave artificial, denominada Surrogate Key

![[Pasted image 20230721093741.png]]

## Cardinalidades mínima e máxima

- restringe a quantidade de ocorrências que podem existir entre as entidades que participam do relacionamento.
- **Cardinalidade mínima**:  define se o relacionamento entre duas entidades é obrigatório ou não.  
	- **Opcional:** indica que o relacionamento é opcional. Representa-se pelo *número 0*.  
	- **Obrigatória:** indica que o relacionamento é obrigatório. Representa-se pelo *número 1*.
- **Cardinalidade máxima:** define a quantidade máxima de ocorrências da Entidade que pode participar do Relacionamento. Deve ser maior que zero.  
	- cardinalidade máxima 1
	- cardinalidade máxima “muitos”, referida pela letra “n”

![[Pasted image 20230721094338.png]]

-  a notação da cardinalidade é sempre apresentada no lado oposto

![[Pasted image 20230721094400.png]]


## NOTAÇÃO

![[Pasted image 20230721094425.png]]


# EXEMPLO DE DIAGRAMA

![[Pasted image 20230721094511.png]]
# ANÁLISE DE PONTOS DE FUNÇÃO

- técnica de medição do tamanho funcional de um software - estimar o esforço para implementação de um sistema
- medir o que o software faz e não como ele foi construído - independente de tecnologia
- avaliação padronizada dos requisitos lógicos do usuário. - medição a partir do ponto de vista do usuário
- Pode ser usada para derivar produtividade, custo e estimar esforço, mas não mede essas quantidade diretamente
- **Ponto de função** - unidade de medida que procura definir o tamanho de um aplicativo (software)
- Processo de contagem:

![[Pasted image 20231117100701.png]]

1. determinar o tipo de contagem;
2. identificar o escopo da contagem e a fronteira da aplicação;
3. contar funções:
	a. tipo dados;
	b. tipo transação;
4. determinar a contagem de pontos de função não ajustados;
5. determinar o valor do fator de ajuste;
6. calcular o número dos pontos de função ajustados (AFP).

## Passo 1 - Determinar o tipo de contagem

1. **Projeto de desenvolvimento**: contagem de pontos de função associados à criação de um novo projeto.
2. **Projeto de melhoria**: contagem de pontos de função de funções adicionadas, modificadas ou eliminadas de um projeto existente.
3. **Aplicação**: contagem de pontos de função de um projeto finalizado.

## Passo 2 - Identificar o escopo de contagem e a fronteira da aplicação

- Determinar se a contagem estará concentrada em um ou mais sistemas ou mesmo em partes de um ou mais sistemas.
- Define quais funções serão incluídas na contagem
- **Fronteira da aplicação**: divisor entre os componentes do aplicativo e os componentes de outros aplicativos

## Passo 3 - Contagem das funções 

-  Identificar cinco componentes básicos, identificados como *arquivos lógicos internos (ALI)*, *arquivos de interface externa (AIE), entrada externa (EE), saída externa (SE) e consulta externa (CE)* e quantificar a complexidade de cada um

### Funções tipos dados
-  funcionalidades fornecidas para o armazenamento de dados da aplicação
- **Arquivos Lógicos Internos (ALI)** -  mantidos dentro da fronteira da aplicação
- **Arquivos Lógicos Externos (ALE)** - mantidos fora da aplicação ou lidos de outra

-  o processo de contagem consiste em identificar os **registros lógicos referenciados (RLR) e seus dados lógicos referenciados (DER**) para cada ALI ou AIE e, com base nisso, atribuir um grau de complexidade e um correspondente número de pontos de função. 
	- **Dados lógicos referenciados (DER)** - campo único, reconhecido pelo usuário, não repetido (ex. atributo)
		- chaves estrangeiras não são contadas como DER
	- **Registros Lógicos Referenciados (RLR)** -  é um subgrupo de DER, reconhecido pelo usuário (ex. tabela)

- Complexidade das funções tipos dados

| -              | 1 a 19 DER | 20 a 50 DER | Acima de 50 DER |
| -------------- | ---------- | ----------- | --------------- |
| 1 RLR          | Simples    | Simples     | Média           |
| 2 a 5 RLR      | Simples    | Média       | Complexa        |
| Acima de 5 RLR | Média      | Complexa    | Complexa        |


- Pontos de função das funções tipo dados 

| -   | Simples  | Média     | Complexa  |
| --- | -------- | --------- | --------- |
| ALI | 7 pontos | 10 pontos | 15 pontos |
| AIE | 5 pontos | 7 pontos  | 10 pontos |

### Funções tipo transação

- representam as funcionalidades de processamento de dados do sistema
- formada por **processos elementares** -  menor unidade de uma função disponível ao usuário. 
- **Entrada Externa (EE)** 
	- manipula dados ou informações de controle originados fora da fronteira de uma aplicação
	- principal intenção manter (incluir, alterar ou excluir dados) um ou mais ALI e/ou alterar a forma como o sistema se comporta
- **Saída Externa (SE)** 
	- envia dados ou informações de controle para fora da fronteira da aplicação com algum processamento adicional
	- intenção apresentar informação ao usuário, por meio de lógica de processamento,
- **Consulta Externa (CE)** 
	- envia dados ou informações de controle para fora da fronteira da aplicação sem processamento adicional
	- apresentar informação ao usuário por meio de uma simples recuperação de dados ou informação de controle

-  o processo consiste em identificar o ALR e seus DER para cada EE, SE ou CE e, com base nisso, atribuir- lhe(s) um grau de complexidade e um correspondente número de pontos de função. 
	-  **Arquivo Lógico Referenciado (ALR)** é um ALI/AIE que foi acessado por uma função de transação

- Complexidade das EE

| -              | 1 a 4 DER | 5 a 15 DER | Acima de 15 DER |
| -------------- | ---------- | ----------- | --------------- |
| 1 ALR          | Simples    | Simples     | Média           |
| 2 ALR      | Simples    | Média       | Complexa        |
| Acima de 2 RLR | Média      | Complexa    | Complexa        |

- Complexidade das SE e CE

| -              | 1 a 4 DER | 5 a 19 DER | Acima de 19 DER |
| -------------- | --------- | ---------- | --------------- |
| 1 ALR          | Simples   | Simples    | Média           |
| 2 a 3 ALR      | Simples   | Média      | Complexa        |
| Acima de 3 RLR | Média     | Complexa   | Complexa        |


- Pontos de função das funções tipo transação

| -   | Simples  | Média    | Complexa |
| --- | -------- | -------- | -------- |
| EE  | 3 pontos | 4 pontos | 6 pontos |
| SE  | 4 pontos | 5 pontos | 7 pontos |
| CE  | 3 pontos | 4 pontos | 6 pontos |

### Determinar a contagem de pontos de função não ajustados

- a pontuação correspondente a cada função, que deve ser multiplicada pela quantidade de funções daquela complexidade.
- Após obtermos o total de pontos de função das funções tipo dados e das funções tipo transação, basta somarmos os dois resultados para obtermos o total de pontos de função não ajustados, que representam o tamanho funcional da aplicação.

$$
PFNA = [QT(ALI)\times CP(ALI)] + [QT(AIE)\times CP(AIE)] + [QT(EE) \times CP(EE)] 
+ [QT(SE)\times CP(SE)] +
[QT(CE)\times CP(CE)]
$$

## Passo 4 - Determinar o valor do fator de ajuste

- características intrínsecas a um aplicativo afetam o seu tamanho funcional
- o fator de ajuste se baseia na avaliação de 14 características
- Cada um desses itens recebe uma nota de 0 a 5, conforme análise do analista do projeto

![[Pasted image 20231117110012.png]]

$$
VFA = (SNI \times 0,01) + 0,65
$$
sendo SNI o Somatório do Nível de Inluência

-  as características gerais do sistema podem influenciar no seu tamanho variando no intervalo de -35% a +35%
- uso do fator de ajuste tornou-se opcional no final de 2002, dado que várias características estão desatualizadas ou sujeitas a interpretações diversas

## Passo 5 - Calcular o número dos pontos de função ajustados (AFP)

$$
PFA = PFNA \times VFA
$$

## Duração e custo de um projeto 

- **Esforço (E)** -  quantos pontos de função são produzidos por hora multiplicado pela quantidade de pontos totais a serem implementados, desta forma teremos a estimativa da quantidade em horas para desenvolver o sistema

$$
E = h/PF  \times PFT
$$
- possuir um histórico de projetos, de modo a se estimar esse esforço de desenvolvimento com maior precisão.
- A partir do Esforço é possível determinar o **Custo**, dado pelo esforço total multiplicado pelo custo médio da hora do desenvolvedor

$$
C = E \times C_{horaDev}
$$

# PONTOS DE CASOS DE USO

- surgiu em 1993 como um modelo relativamente mais simples do que a análise de pontos de função
- análise da quantidade e complexidade dos *atores* e *casos de uso*, o que gera os **UUCP, ou pontos de caso de uso não ajustados**

## Pontos de casos de uso não ajustados (UUCP)
### Definição da complexidade dos atores

- cada ator é contado uma única vez
- **Pontuação:**
	- Atores humanos que interagem com o sistema por meio de interface gráfica: alta complexidade – 3 pontos de caso de uso.
	- Sistemas que interagem por protocolo de controle de transmissão/protocolo de internet (TCP/IP) e atores humanos que interagem com o sistema apenas por linha de comando: média complexidade – 2 pontos de caso de uso.
	- Sistemas que são acessados por interfaces de programação (API): baixa complexidade – 1 ponto de caso de uso.
- Após a identificação e pontuação dos atores, basta somente realizar a soma de todos os valores para obter-se o peso não ajustado dos atores.

### Definição da complexidade dos casos de uso

-  os casos de uso também devem ser contados uma única vez
- somente casos de uso completos devem ser contados

#### Complexidade por transações
a. casos de uso simples: com até 3 transações, valem 5 pontos;
b. casos de uso médios: com 4 a 7 transações, valem 10 pontos;
c. casos de uso complexos: com acima de 7 transações, valem 15 pontos.

#### Complexidade por classes necessárias
a. casos de uso simples: com 5 classes ou menos.
b. casos de uso médios: com 6 a 10 classes;
c. casos de uso complexos: com mais de 10 classes.

#### Complexidade por análise de risco
a. casos de uso simples: casos de uso como relatórios que têm apenas 1 ou 2 transações e baixo risco, pois não alteram dados.
b. casos de uso médios: casos de uso padronizados que têm um número conhecido e limitado de transações, pois, embora a sua lógica de funcionamento seja conhecida, neles, regras de negócio obscuras podem existir;
c. casos de uso complexos: casos de uso não padronizados que têm um número desconhecido de transações e alto risco

## Pontos ajustados de casos de uso (UCP)
-  para a definição dos pontos ajustados são aplicados 13 fatores técnicos, que recebem uma pontuação de 0 a 5
- cada fator técnico recebe inicialmente um valor predefinido
![[Pasted image 20231117114948.png]]

- Cálculo do **fator de complexidade técnica (TCF)**

$$
TCF = 0,6 + (0,01 \times TFT)
$$
TFT -  total da soma dos pontos de fatores técnicos
-  também são aplicados mais 8 fatores ambientais - específicos às características da equipe de desenvolvimento

![[Pasted image 20231117115210.png]]

- Cálculo do **fator ambiental total (EF)**
$$
EF = 1,4 - (0,03 \times TFA)
$$

TFA - total da soma dos fatores ambientais
- o total de pontos de casos de uso ajustados (UCP), basta multiplicarmos o total de UUCP por TCF e EF

$$
UCP = UUCP \times TCF \times EF
$$

# PONTOS DE HISTÓRIAS

- estimativa de esforço preferida de métodos ágeis
- **história de usuário** uma explicação informal e geral sobre um recurso de software, escrita sob a perspectiva do usuário final
-  a metodologia consiste em identificar de forma subjetiva quanto tempo um número qualquer de pessoas que se dedicasse unicamente a uma história de usuário levaria para terminá-la, com uma versão executável do sistema - pontuação = n. de pessoas x quantidade de dias
- Método comum é utilizar a série de Fibonacci para a pontuação das histórias, os pontos são uma unidade relativa de medida que ajuda a estimar o esforço necessário para implementar uma determinada funcionalidade.
	- não correspondem diretamente a horas, dias ou outras unidades de tempo; em vez disso, eles refletem a dificuldade percebida da tarefa.
	- A equipe de desenvolvimento, em colaboração com os membros responsáveis pela definição de requisitos (por exemplo, analistas de negócios, proprietários de produtos), atribui pontos de história a cada história de usuário durante uma reunião de planejamento.

# SLOC E KSLOC

- **SLOC** - Número de linhas de código implementadas em um sistema
	-  uma das primeiras técnicas de estimativas
- **KSLOC** - Kilo Source Lines of Code - mil unidades SLOC, também são utilizados os termos MSLOC e GSLOC
1. **Ksloc otimista**: número mínimo de linhas que se espera desenvolver se todas as condições forem favoráveis.
2. **Ksloc pessimista**: número máximo de linhas que se espera desenvolver em condições desfavoráveis.
3. **Ksloc esperado**: número de linhas que efetivamente se espera desenvolver em uma situação de normalidade.

$$
KSLOC = \frac{4 \times KSLOC_{esperado} +KSLOC_{otimista} +KSLOC_{pessimista}}{6}
$$

- estimativas obtidas devem ser comparadas com a informação real, ao final do projeto, para a equipe ter um feedback para ajustar futuras previsões

# COCOMO - Constructive Cost Model

- Modelo de estimativa de esforço para produção de software baseado em Ksloc.
- Existem três versões do modelo: COCOMO Básico, COCOMO Intermediário e COCOMO Detalhado

1. **Implementação básica**: quando a única informação sobre o sistema efetivamente disponível é o número estimado de linhas de código.
2. **Implementação intermediária**: quando fatores relativos a produto, suporte computacional, pessoal e processo são conhecidos.
3. **Implementação avançada**: quando for necessário subdividir o sistema em subsistemas e distribuir as estimativas de esforço por fases e atividades.

- para o cálculo do esforço todas as implementações consideram também o tipo de projeto a ser desenvolvido

1. **Modo orgânico**: projetos de software relativamente simples, bem compreendidos e desenvolvidos por equipes experientes.
	1. a=2.4 e b=1.05.
2. **Modo Semi-Destacado:** Esses projetos estão entre os extremos de simplicidade e complexidade. Pode haver algum grau de novidade no projeto, e a equipe pode ter uma combinação de membros experientes e menos experientes. 
	1. a=3.0 e b=1.12
3. **Modo Embutido:** projetos complexos, muitas vezes associados a sistemas críticos ou incorporados em outros sistemas maiores. Esses projetos podem envolver requisitos rigorosos, restrições específicas e interfaces complexas.
	1.  a=3.6 e 0b=1.20

## Modelo básico
### Esforço estimado 

$$
E = a \times (KSLOC)^b 
$$

![[Pasted image 20231117124244.png]]

### Tempo linear de desenvolvimento

$$
T = c \times E^d
$$

### Número médio de pessoas recomendado para a equipe:

$$
P = \frac{E}{T}
$$

## Modelo Intermediário

- o modelo intermediário considera, além das linhas de código, 15 fatores influenciadores de custo

![[Pasted image 20231117125026.png]]

- Cálculo do fator de ajuste de esforço EAF:
$$
EAF = Rely \times Data \times CPLX \times Time \times ... \times Sced.
$$

- Estimativa do esforço:
$$
E = a \times (KLOC)^b \times EAF
$$

![[Pasted image 20231118091413.png]]
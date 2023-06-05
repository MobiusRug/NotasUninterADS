# Análise de Sistemas - A história

- No século XX iniciou-se um período que chamamos de  Era da Informação
-  A informação flui com velocidade cada vez maior e em volumes espantosos.
- Faz-se necessários mecanismos para filtrar informações úteis das irrelevantes
	- O sistemas de informação computacionais surgiram com o objetivo de solucionar esse problema
- A **Tecnologia da Informação (TI)** é composta por um conjunto de recursos de hardware e de software dedicados ao armazenamento, processamento e utilização da informação
- a TI define a maneira como os recursos de hardware e software estão organizados num sistema capaz de executar um conjunto de tarefas para manter e evoluir o negócio.
- O  uso cada vez mais intenso dos sistemas computacionais e com a evolução constante da tecnologia, foi necessário estruturar a construção de software
	- [[UNINTER/Fundamento de Desenvolvimento de Software/Aula 2#CRISE DO SOFTWARE]]
- A análise de sistemas surgiu e foi definindo formas mais efetivas de desenvolver softwares

## ANÁLISE DE SISTEMAS
- Prática baseada em modelos , com o objetivo de obter um melhor entendimento da entidade real a ser construída.
- O modelo precisa representar:
	- a entidade física
	- a informação referente a essas entidades que o software precisa processar
	- a arquitetura e as funcionalidades que o software precisa entregar 
- A modelagem do software precisa mostrar a solução a ser construída em diferentes níveis de abstração
	- ponto de vista do cliente e técnico
- Duas classes de modelos:
	**Modelos de Análise**: representam os requisitos do software, mostrando três domínios diferentes
	- domínio das informações que precisam ser tratadas
	- domínio das funcionalidades a serem atendidas
	- domínio comportamental que deve ser seguido

	**Modelos de Projetos**: representam as características que ajudam tecnicamente a entender o funcionamento do software
	 - arquitetura
	 - interface do usuário/camada visual
	 - camada física

### PRINCÍPIOS 
- O domínio de informação relacionado com o software a ser construído precisa ser representado e entendido
	- envolve dados que transitam dentro do sistema e para fora do sistema

- As funcionalidades a serem desenvolvidas pelo software devem ser detalhadamente definidas

- O comportamento do software precisa ser representado e deve ser guiado pelas:
	- interações com o ambiente externo
	- contexto de negócio no qual o cliente está inserido
	- pelo uso que o usuário dará para o software

- **Particionamento**: Um problema complexo ou grande é dividido em partes menores - Os modelos que mostram informações, funcionalidade e comportamento devem ser particionados de modo que revelem os detalhes em forma de camadas

- **Análise x Projeto**
	- ANÁLISE:
		- Foco em entender o problema do cliente - O QUE deve ser resolvido
		- Não se preocupa com a solução de software 
	- PROJETO:
		- Foca nos detalhes de implementação da solução - COMO será resolvido

### MÉTODOS DE MODELAGEM DE SISTEMAS

- **ANÁLISE ESTRUTURADA**
	-  Fundamentada na decomposição funcional do problema
	-  Foco nas  funcionalidades que o software deve entregar
	-  DFD e o Dicionário de Dados (DD) as principais ferramentas.

- **ANÁLISE ESSENCIAL**
	- Identifica inicialmente os eventos externos que acionam o software -> ações (funções ) em resposta
	- Posteriormente identifica os eventos gerados internamente e também as respectivas ações

- **ANÁLISE ORIENTADA A OBJETOS**
	- Procura compreender o problema a ser resolvido por meio de simples objetos do mundo real.
	- **Objeto** é uma entidade real ou abstrata que modela um conceito presente na realidade humana, ocupando espaço físico ou lógico.
	- [[Aula 1 - paradigmas e Java#PARADIGMA ORIENTADO A OBJETOS]]

## O ANALISTA DE SISTEMAS 
[[UNINTER/Fundamento de Desenvolvimento de Software/Aula 2#ANALISTA DE SISTEMA]]

É o profissional que, por meio do trabalho do analista de requisitos, **projeta uma solução**, baseada na arquitetura definida pelo arquiteto de software, gerando **modelos e documentos** que serão utilizados pelos programadores na construção do software.

# ANÁLISE ESTRUTURADA 

- **Objetivo principal** - construção de um modelo lógico
- Utiliza técnicas gráficas
- A especificação baseada na análise estruturada é composta de diagrama de fluxo de dados, de dicionário de dados e de especificações dos processos.


## BENEFÍCIOS

- Uso de diagrama e fluxo de dados fornece mais clareza sobre o sistema proposto
- apresentação dos requisitos em termos de fluxo lógico consegue mostrar mal- entendidos e pontos controversos
- interfaces entre o novo sistema e outros sistemas já existentes são mostrados de modo bem mais claro
- O uso de dicionário de dados cria um padrão de nomenclatura

## PROBLEMAS

- O esforço, a formalidade e o grau de detalhe necessários, especialmente na construção do dicionário de dados, muitas vezes, geram resistência por parte dos analistas de sistemas - o valor agregado da documentação vale o esforço
- Preocupação por parte dos programadores de que ao obterem especificações detalhadas da lógica no português estruturado, acabarão “retirando todo o prazer da programação, tornando-os meros codificadores
- Necessária capacitação dos usuários e analistas 

# DIAGRAMA DE FLUXO DE DADOS (DFD)

- uma das ferramentas mais utilizadas na análise estruturada
-  objetivo de um DFD é mostrar de onde os dados surgem, para onde vão, quando são armazenados e qual processo os transforma
-  possui uma representação em rede que mostra as funcionalidades que o sistema deve entregar e os dados que interligam essas funcionalidades
- utilizada no momento da análise
- A criação de um DFD envolve os seguintes pontos:
	- Escolha de nomes significativos para os seus componentes,
	- Numerar os processos
	- Criar o diagrama e ajustá-lo visando uma boa estética e comunicação adequada
	- Caso necessário, utilizar o particionamento em níveis
- O diagrama é composto por vários elementos ou componentes, chamados de processos, fluxos de dados, depósitos de dados e entidades.

## PROCESSOS

- Mostra as funcionalidades ou processos que o software deve executar - *coração do DFD*
- são conhecidos como **bolha, função ou transformação**, pois representam as transformações de fluxos de dados de entrada em fluxos de dados de saída
- O nome do processo deve descrever o que ele faz - ex.: *cadastrar cliente* - uso de verbos + especificação a que o processo se refere no contexto do software
- Podem ser manuais ou automatizados
![[Pasted image 20230427093756.png]]

## FLUXO DE DADOS 

- são os componentes capazes de interligar os processos
- representam caminhos pelos quais passam os dados:  transportam dados entre os componentes do DFD
- Representados por meio de setas que indicam a origem e o destino do dado.
- Cada fluxo deve ter um único nome, o qual deve identificar os dados transportados pelo fluxo. ex.: *pedido*
- o fluxo de dados mostra também o estado em que o dado se encontra, baseado no processo executado, mas ele não modifica o dado durante o transporte
- Podem ser classificados como: 
	- **Fluxo externo:** entre entidade e processo. 
	- **Fluxo interno**: entre dois processos;
	- **Fluxo de acesso à memória**: entre processo e depósito de dados;
	- **Fluxo de erro ou rejeição**: para fora de um Processo.

![[Pasted image 20230427094537.png]]

## DEPÓSITO DE DADOS

- Armazena dados para uso posterior
- Independente de implementação - não confundir com BD
- Nome deve estar no plural, representando que, no depósito, existem vários dados do mesmo contexto.
![[Pasted image 20230427095749.png]]

## ENTIDADES

- Representam partes do mundo real - são a origem ou o destino das transações
- Podem ser chamadas de *Terminadores*
- Podem representar outro sistema - quando representar um sistema externo, deve ser incluída a palavra 'sistema' ao seu nome
- Deve estar no plural

![[Pasted image 20230427100308.png]]

# NÍVEIS DE UM DFD

O DFD deve ser modelado em uma série de níveis, de modo que, a cada nível, ofereça sucessivamente mais detalhes sobre uma parte do nível que lhe seja superior.

## DFD DE CONTEXTO

- Nível mais alto - dá uma visão das principais funções do sistema 
- é macro, contendo um processo que representa o sistema como um todo
- explica o objetivo do software, os principais dados trafegados e as entidades mais importantes
![[Pasted image 20230427100827.png]]

## DFD DE NÍVEL ZERO

- Nesse nível de DFD, é possível encontrar detalhes sobre as principais funcionalidades do software.
- contém as macrofunções do sistema.
- mostram quais são os relacionamentos das principais funcionalidades
- é possível criar um entendimento, mesmo que primário, sobre o funcionamento do software

![[Pasted image 20230427101215.png]]

## DFD DE NÍVEIS INTERMEDIÁRIOS

- mostram a decomposição, ou seja, o detalhamento ou explosão de cada processo de nível mais alto
- cada nível detalha mais o nível imediatamente anterior.
- A quantidade de níveis depende de fatores como complexidade e porte do sistema
- a numeração dos processos ajuda na identificação do detalhamento 

![[Pasted image 20230427101509.png]]


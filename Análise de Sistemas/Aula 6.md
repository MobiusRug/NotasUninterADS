# DIAGRAMA DE ESTADO 
- um diagrama dinâmico, pois mostra a evolução de estados em um objeto, ao longo da sua vida no software e quais eventos geram a mudança de estado
- sua construção é recomendada apenas quando existir um certo grau de complexidade na transição de um estado para outro 

## ELEMENTOS BÁSICOS DE UM DIAGRAMA DE ESTADO 

- **EVENTO** - é uma ocorrência que gera uma mudança de estado
	- *Externo*  - é causado por algo fora do limite do sistema 
	- *Interno* - é causado por algo dentro do limite do sistema
	- *Temporal*- causado pela ocorrência de uma data ou hora específica, ou pela passagem do tempo.

- **ESTADO** - condição de um objeto em determinado momento no tempo – o tempo entre os eventos.

- **TRANSIÇÃO** -  é um relacionamento entre dois estados

-  **Objeto** - é o elemento que sofre a mudança de estado a partir de um evento.

![[Pasted image 20230514174255.png]]

# DIAGRAMA DE ATIVIDADES 

-  O Diagrama de Atividades descreve lógica de procedimento, processo de negócio e fluxos de trabalho.

## ELEMENTOS

- **Estado Inicial e Final** - início e fim do processo
![[Pasted image 20230514174821.png]]

- **Atividades** - são ações que devem ser executadas 
- Quando uma atividade é finalizada, a execução do fluxo do processo é transferida para a próxima atividade. Essa transferência é chamada de transição

![[Pasted image 20230514174931.png]]

- **Transição** -  é o caminho a ser seguido ao longo de todo o fluxo do processo, até a sua conclusão do processo
![[Pasted image 20230514175031.png]]

- **Decisões** - controlar os desvios ao longo do fluxo do processo de negócio 
![[Pasted image 20230514175144.png]]

- **Bifurcação e União** -  a junção ou a separação de atividades executadas ao longo de um fluxo de negócio 
![[Pasted image 20230514175259.png]]

- **Raias**: são uma forma de organização lógica das atividades. Essa organização pode estar associada a objetos, a usuários ou atores ou a outra organização lógica que agregue valor para compreender o fluxo das atividades em um Diagrama de Atividades.

![[Pasted image 20230514175351.png]]


![[Pasted image 20230514175424.png]]

# DIAGRAMA DE SEQUÊNCIA 

- consiste em um grupo de objetos relacionados por linhas de vida e apresenta, de maneira visual, as mensagens que eles trocam durante uma transação.
- representa uma funcionalidade descrita em um caso de uso 
- mostra a sequência de mensagens trocadas entre objetos, além disso, um diagrama de sequência também mostra as estruturas de controle entre objetos do software.
- dimensão horizontal, que representa o conjunto de objetos e uma dimensão vertical, que representa o tempo de vida de um objeto,

## ELEMENTOS

- **Ator**: é o usuário que inicia a interação e a troca de mensagens
-  **Linha de Vida**: é uma instância ou uma ocorrência de um componente, em que chegam mensagens, e de onde partem mensagens. E o tempo de vida de um componente desde o momento em que ele é chamado até quando ele é finalizado, concluindo seu objetivo.
- **Fragmento**: é onde tratamos as estruturas condicionais que fazem parte do fluxo de vida da mensagem em um objeto
-  **Mensagem**: é a mensagem “de fato” que trafega pela linha de vida

![[Pasted image 20230514180642.png]]

# DIAGRAMA DE COMPONENTES 

- tem como objetivo apresentar a visão dos pacotes que compõe o sistema e suas dependências
-  **componente** é um módulo do software com identidade e interface bem definida. É um pedaço do software
	- módulo de classes, que representa sistemas ou subsistemas independentes com capacidade de interagir com o restante do sistema.
-  *representa o modelo físico dos componentes de software. Um componente é composto por um conjunto de interfaces e classes.*

## BENEFÍCIOS

-  a equipe de desenvolvedores consegue visualizar a estrutura física do sistema, além de conhecer os componentes do sistema e o relacionamento entre eles
- mostrar visualmente o comportamento dos serviços criados para o software e suas interfaces.

![[Pasted image 20230514182455.png]]



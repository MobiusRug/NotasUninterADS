# ENGENHARIA DE REQUISITOS

- **Requisitos** - Determinar o que as partes interessadas necessitam e o que o sistema deve fazer para satisfazer essas necessidades
- Quatro passos principais:
	-  **Estudo de viabilidade da construção do software**
		- Verificar se a funcionalidade é viável de codificar considerando os aspectos técnicos, financeiros e prazos
	-  **Coleta de requisitos:** 
		-  Os analistas de requisitos entrevistam clientes e usuários finais para conhecer as suas ideias e necessidades sobre quais funcionalidades o software deve executa
	-  **Especificação de requisitos:**
		- documentação e o detalhamento de cada um dos requisitos necessários para o software
	-  **Validação dos requisitos:**
		- garantir o entendimento

## CICLO DE VIDA DA ENGENHARIA DE REQUISITOS POR PRESSMAN

- **CONCEPÇÃO**: compreender o problema a ser resolvido, entendendo o cenário de atuação e as necessidades do cliente no nível macro
- **LEVANTAMENTO**: os analistas de requisitos começam a entrevistar os usuários e a compreender, em detalhes, como os requisitos deverão funcionar. Pode-se utilizar de técnicas de modelagem
- **ELABORAÇÃO:**  desenvolver um modelo técnico refinado das funcionalidades, características principais a serem atendidas e restrições do software. Definidos *cenários de uso*
- **NEGOCIAÇÃO:** 
	- validação dos requisitos levantados
	- possibilidade de novos requisitos e alterações
	- negociação de custo, prazo e escopo
	- gerenciar e conciliar conflitos - priorização dos requisitos mais importantes
- **ESPECIFICAÇÃO:** 
	- O projeto de construção de software pode ser desenvolvido 
	- São definidas as tecnologias e a arquitetura que será empregada
	- Entra na fase de projeto técnico
- **VALIDAÇÃO:** 
	- Garantir que os requisitos estão corretos segundo os processos da empresa e que foram especificados e projetados de uma forma viável para implementação
- **GESTÃO DE REQUISITOS:** 
	- conjunto de atividades que ajudam na identificação, controle, rastreamento e modificação dos requisitos ao longo do tempo.
	- Necessária devido a volatilidade dos requisitos 
	- também se ocupa com a rastreabilidade entre os requisitos de um software. 

## O ANALISTA DE REQUISITOS

Resumidamente faz a ponte entre o negócio a parte técnica, deve saber portanto navegar nestes dois mundos, abstrair as necessidades de negócio e converter em planejamento técnicos viáveis e facilitar a comunicação entre as áreas. 

## O DOCUMENTO DE ESPECIFICAÇÃO DE REQUISITOS

- Uma **especificação de requisitos de software (SRS – Software Requirements Specification)** é uma descrição de um sistema de software a ser desenvolvido. Ele estabelece requisitos funcionais e não funcionais e pode incluir um conjunto de casos de uso que descrevem as interações do usuário que o software deve fornecer.
- Tão importante quanto descrever o que fará, é fundamental deixar claro o que o software não fará

# REQUISITOS FUNCIONAIS E REQUISITOS NÃO FUNCIONAIS

- Após conhecer e modelar o processo de negócio do nosso cliente, é possível automatizá-lo por meio do desenvolvimento de um software - o software é reflexo do processo
-  Requisitos são, além de funções, objetivos, propriedades, restrições que o sistema deve possuir para satisfazer contratos, padrões ou especificações de acordo com as necessidades dos usuário - foco no cliente 
- **REQUISITOS FUNCIONAIS:**
	- Um requisito funcional define uma função particular de um sistema ou algum dos seus componentes; eles representam “o que o software faz”, em termos de tarefas e serviços (funcionalidades). - O QUE o software faz 
- **REQUISITOS NÃO FUNCIONAIS:**
	- referem-se aos critérios que qualificam os requisitos funcionais.
	- Esses critérios podem ser de **qualidade para o software**, ou seja, os requisitos de performance, usabilidade, confiabilidade, robustez etc.
	- os critérios podem ser quanto à **qualidade para o processo de software**, ou seja, requisitos de entrega, implementação, entre outros.
	- O plano para implementar requisitos funcionais é detalhado no design do sistema. O plano de implementação de requisitos não funcionais é detalhado na arquitetura do sistema
	- ex.: o sistema deve imprimir o relatório em até 5s, o sistema deve utilizar a linguagem x, deve ser utilizada fonte y

# CASOS DE USO

- O documento de casos de uso modela os requisitos funcionais do sistema.
-  documentar um caso de uso significa descrever *fluxos de eventos,* listando todos os passos seguidos para se chegar a um resultado.
- **FLUXO PRINCIPAL(FP):**
	- *Caminho feliz* -  É o fluxo no qual todas as informações estão corretas e o caso de uso faz o que deveria ser feito, conforme o requisito - atinge objetivo principal
- **FLUXO ALTERNATIVO (FA):** 
	- são funções que não fazem parte do fluxo principal, mas estão disponíveis para o usuário executar, ou seja, sua execução não é obrigatória
- **FLUXO DE EXCEÇÃO (FE):**
	 -  é o tratamento de tudo o que não é o caminho normal ou esperado

![[Pasted image 20230503103107.png]]


## REGRAS DE ESCRITA EM UM CASO DE USO

- Todo caso de uso deve indicar uma ação
- Utilizar uma numeração sequencial para se referenciar ao caso de uso
- podemos utilizar uma identificação e um sequencial numérico para organizar os passos que devem ser seguidos para executar a funcionalidade
-  No caso de uso, para facilitar o entendimento do mesmo, é importante inserir as seguintes informações:
	- Nome do caso de uso
	- Descrição breve
	- Pré-condições
	- Fluxo Principal
	- Fluxos Alternativos
	- Fluxos de Exceção
	- Regras de Negócios
	- Mensagens

# HISTÓRIAS DE USUÁRIO

- forma como descrevemos o funcionamento esperado para o software no conceito das metodologias ágeis.
- curta e simples descrição de uma funcionalidade ou parte de uma funcionalidade
- Ela pode ser contada por meio da perspectiva da pessoa que deseja a funcionalidade, usualmente de um usuário ou cliente do sistema
-  formato: *Como/Sendo (quem), eu quero/gostaria/devo/posso (o que), para que/de/para (porque/resultado).*
- quem é o usuário, o que o usuário quer fazer e para que ele quer
- Para compor um requisito, é preciso descrever as estórias de todos os usuários que vão usar a funcionalidade
- Um épico é uma grande história ou um conjunto de história

## BENEFÍCIOS
- mantêm foco no usuário
- permitem a colaboração entre a equipe técnica e os usuários.
- impulsionam soluções criativas.
-  criam ritmo. 

- Princípio **INVEST** -   Independente, Negociável, Valiosa, Estimável, Pequena (Small) e Testável
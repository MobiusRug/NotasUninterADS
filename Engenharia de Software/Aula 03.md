# Projeto de Arquitetura de Software

 - Para desenvolver um software, partimos do contexto geral desse sistema, para depois separarmos os processos em cada fase, de acordo com o modelo de processos (prescritivos ou ágeis) escolhido - ex. planta construção civil
 - **Projeto** é: “
	 - ... um esforço temporário empreendido para criar um produto, serviço ou resultado único” (PMI, 2017) “
	 - ... um empreendimento planejado, orientado a resultados, possuindo atividades com início e término, para atingir um objetivo claro e definido” (Brasil, 2011)
- **Projeto de software**:
	- um processo em várias etapas em que as representações de dados e a estrutura do programa, as características de interfaces e os detalhes procedurais são sintetizados com base nos requisitos de informação - Pressman, 2011
- **Projeto da arquitetura de software**
	- representa a estrutura de dados e os componentes de programa necessários para construir um sistema computacional. Ele considera o estilo de arquitetura que o sistema assumirá, a estrutura e as propriedades dos componentes que constituem o sistema, bem como as inter-relações que ocorrem entre todos os componentes da arquitetura de um sistema
- Conforme Pressman (2011), as **etapas de um projeto de arquitetura** são: 
	1. Projeto de dados 
	2. Derivação da estrutura da arquitetura do sistema
	3. Análise de estilos ou padrões de arquitetura alternativos 
	4. Implementação da arquitetura utilizando-se um modelo de processos

 **Projeto de dados**
- Levantamento de requisitos 
- Definição das entidades externas com as quais o software irá interagir 
	- Diagrama entidade-relacionamento

**Derivação da estrutura da arquitetura do sistema**
- Identificação de arquétipos arquiteturais 
- Abstrações de elementos do sistema 
- Definição de classes e objetos
	- Linguagem UML -  Diagrama de classes

**Análise de estilos ou padrões de arquitetura alternativos** 
Define-se o padrão de arquitetura de software a ser implementado

**Implementação da arquitetura utilizando-se um modelo de processos** 
Implementação da arquitetura

- Pfleeger (2004) destaca que o projeto é um processo iterativo composto por: Projeto conceitual e projeto técnico
1. **Projeto conceitual** 
	- Apresenta ao cliente exatamente o que o sistema fará 
	- Sendo aprovado, é traduzido, dando origem ao projeto técnico 
		- Linguagem UML -  Diagramas de casos de uso
2. **Projeto técnico** 
	- Determinar hardware necessário
	- Determinar software necessário 
	- Descrever a forma que o sistema terá

# Padrões de Arquitetura de Software

- descrição abstrata, estilizada, das práticas recomendadas que foram testadas e aprovadas em diferentes subsistemas e ambientes.
- é muito comum identificarmos projetos de sistemas que são desenvolvidos em conformidade com mais de uma arquitetura

## Arquitetura centralizada em dados

-  um repositório de dados, tal como um banco de dados, reside no centro dessa arquitetura
-  componentes de alguma forma, modificam dados contidos nesse repositório

![[Pasted image 20231110093546.png]]

## Arquitetura de fluxo de dados
- Também conhecida como arquitetura de duto e filtro
- dados de entrada devem ser transformados por meio de uma série de componentes computacionais ou de manipulação em dados de saída
- representação por meio de diagramas de atividades da linguagem UML.

![[Pasted image 20231110093650.png]]

## Arquitetura em camadas
- o sistema é organizado em camadas com a funcionalidade relacionada associada a cada camada
- camada mais externa, os componentes atendem operações de interface do usuário. 
- Na camada mais interna, os componentes realizam a interface com o sistema operacional
- nas camadas intermediárias, são fornecidos serviços utilitários e funções de software de aplicação

![[Pasted image 20231110093743.png]]

## Arquitetura cliente-servidor
- muito utilizada para sistemas distribuídos e sistemas web
- sistema é apresentado como um conjunto de serviços, e cada serviço é fornecido por um servidor separado
- Os clientes são usuários desses serviços e acessam os servidores para usá-los.

![[Pasted image 20231110093824.png]]

## Arquitetura orientada a objetos
- aproximar as estruturas de um programa das coisas do mundo real
- componentes de um sistema encapsulam dados e as operações que devem ser aplicadas para manipular os dados
- A comunicação e a coordenação entre componentes são realizadas por meio da passagem de mensagens.
- **Classes**: é um conjunto de características e comportamentos que definem o conjunto de objetos pertencentes à classe;
- **Objetos**: uma ou várias instâncias de uma classe 

![[Pasted image 20231110093940.png]]

## Arquitetura Modelo, Visão e Controlador – MVC
-  separar a apresentação e a interação dos dados do sistema
 - **Modelo**: gerencia o sistema de dados e as operações associadas a esses dados;
 - **Visão**: define e gerencia como os dados são apresentados ao usuário.;
 - **Controlador**: gerencia a interação do usuário e passa essa interação para a Visão e o Modelo.
- ![[Pasted image 20231110094039.png]]
# Levantamento de Requisitos

- são as descrições **do que o sistema deve faze**r, os serviços que oferecem e as **restrições** a seu funcionamento. Esses requisitos refletem as necessidades dos clientes para um sistema que serve a uma finalidade determinada
- são classificados como requisitos funcionais e não funcionais

## Requisitos funcionais
- Declarações dos serviços que o sistema deve fornecer 
- Como o sistema deve agir com relação a determinadas entradas 
- Como o sistema deve se comportar em determinadas situações
- O que o sistema não deve fazer

## Requisitos não funcionais
- Restrições sobre os serviços ou funções oferecidas pelo sistema
	- Restrições de tempo 
	- Restrições sobre o processo de desenvolvimento 
	- Restrições impostas por padrões 
- Aplicam-se ao sistema como um todo, em vez de às características individuais ou aos serviços

## Técnicas para elicitação de requisitos

**Entrevistas**
- Formais ou informais, com usuários e demais partes envolvidas no sistema

**Cenários**
- Podem ser escritos como texto, suplementados por diagramas, telas, entre outros

**Casos de uso** 
- Abordagem mais estruturada de cenários. Identifica os atores envolvidos em uma iteração e dá nome ao tipo de iteração

**Etnografia**
- Técnica de observação que pode ser usada para compreender os processos operacionais e ajudar a extrair os requisitos de apoio para esses processos

## Especificação de requisitos

**Sentenças em linguagem natural**
- Frases numeradas em linguagem natural
- Cada frase deve expressar um requisito

**Linguagem natural estruturada**
- Linguagem natural em um formulário ou template
- Cada campo fornece informações sobre um aspecto do requisito,

**Notações gráficas**
- Modelos gráficos suplementados por anotações em texto
- Diagramas de casos de uso e de sequência da UML

**Especificações matemáticas**
- Conceitos matemáticos como as máquinas de estados finitos ou conjuntos

# Gerenciamento de Configuração e Mudança
- é um conjunto de atividades destinadas a gerenciar as alterações identificando os artefatos que precisam ser alterados, estabelecendo relações entre eles, definindo mecanismos para gerenciar diferentes versões desses artefatos, controlando as alterações impostas e auditando e relatando alterações feitas
- Para Sommerville (2018), o gerenciamento de
configuração envolve quatro atividades
1. **Controle de versão**
	- Controlar as várias versões dos componentes do sistema
	-  Garantir que as mudanças feitas não interfiram nas outras
2. **Construção de sistema**
- Reunir componentes, dados e bibliotecas do programa, compilando-os e ligando-os para criar um sistema executável
3. **Gerenciamento de mudanças**
	- Manter o controle das solicitações de mudança de clientes e desenvolvedores no software já entregue
	- Elaborar os custos e o impacto dessas mudanças, bem como decidir se e quando as alterações devem ser implementadas
4. **Gerenciamento de lançamentos**
- Preparar o software para o lançamento externo e acompanhar as versões lançadas para uso do cliente

# Manutenção e Evolução de Software 

- uma vez desenvolvido, um software terá um valor necessariamente decrescente com o passar do tempo
	- Falhas são descobertas
	- Requisitos mudam
	- Produtos menos complexos, mais eficientes ou tecnologicamente mais avançados são disponibilizados
- “independentemente do domínio de aplicação, tamanho ou complexidade, o software continuará a evoluir com o tempo
- São corrigidos erros 
	- Quando há adaptação a um novo ambiente
	- Quando o cliente solicita novas características ou funções
	- Quando a aplicação passa por um processo de reengenharia
- três diferentes tipos de manutenção
	- Correção de defeitos
	- Adaptação ambiental
	- Adição de funcionalidade
# ARQUITETURA DE SOFTWARE

O sucesso do desenvolvimento de um sistema depende de formas de **documentar** todos os seus aspectos de forme bem definida que possa ser entendida pelos interessados no sistema. Isso facilita a comunicação entre a equipe de desenvolvimento permitindo que aplicação atenda a padrões necessários para funcionar de forma assertiva.

## PADRÃO ARQUITETURAL

- Um padrão arquitetural tem o objetivo atender uma visão orientada aos negócios.
- O modelo ajuda a tomada de decisões do projeto de software, como e quais serão suas utilidades, linguagens, tecnologias no relacionamento de cada subsistema para a construção de soluções para a aplicação.

## HISTÓRICO

- No fim dos anos 60, cientistas começaram a discutir formas de estruturar um sistema antes do seu desenvolvimento.
- Apenas nos anos 90 foi escrito o livro “Software Architecture: Perspectives on a Emerging Discipline” por Mary Shaw e David Garlan, da Carnegie Mellon University.
- Devido a importância do tema para o desenvolvimento a norma **ISO/IEC/IEEE 42010:2011** foi estabelecida com o objetivo de criar, analisar e descrever arquiteturas de software.

# ESTILO ARQUITETURAL

- considera o sistema por completo, permitindo determinar como o sistema está organizado, caracterizando os requisitos, componentes e suas interações.
- Possibilita a:
	- Identificação de componentes
	- Identificação do mecanismo de interação
	- Identificação de propriedades 

## VANTAGENS;
- Suporte a atributos de qualidade 
- Diferenciação entre arquiteturas;
- Menos esforço para entender o projeto;
- Reuso de arquitetura e conhecimento em novos projetos;
- Suporte ao planejamento e a gerenciamento da manutenção e integridade da solução.

# DOCUMENTAÇÃO

- Define as atividades que serão realizadas;
- É o primeiro artefato a agregar artefatos de qualidade;
- É o melhor artefato nas primeiras fases do desenvolvimento;
- Elemento chave para posterior manutenção do sistema.

## Princípios de uma Boa Documentação

- Princípio 1: Documentar sob o ponto de vista de quem irá utilizar a documentação.
- Princípio 2: Evitar ambiguidade.
- Princípio 3: Usar uma organização padrão para o documento a ser criado, isto é, um modelo ou template.
- Princípio 4: Evitar repetições desnecessárias. Entretanto redundância é aceitável ou desejável se:
	- Uma informação está definida em um local X da documentação e uma elaboração ou refinamento da mesma informação aparece em um local Y. Neste caso, repetir a informação (ou parte dela) no local Y é comum.
	- Duas informações são mapeadas uma para outra. É difícil fazer isso sem repetir parte delas.
	- A repetição é conveniente por motivos práticos, quando trocar de página constantemente para entender o texto fica inviável.
- Princípio 5: Documentar as razões para as decisões tomadas. - e as alternativas rejeitadas
- Princípio 6: Manter a documentação atualizada.
- Princípio 7: Revisar a documentação criada.
- Princípio 8: Tornar a documentação acessível a todos os participantes relacionados ao projeto.

## ISO/IEC/IEEE 42010:2011
- A norma oferece o modelo conceitual para a documentação de uma arquitetura de software.
- **VIEWS**:
	- **Visão Lógica**: Funcionalidade do sistema
	- **Visão Física**: Funcionalidade para o usuário final
	- **Visão de Desenvolvimento**: integração de componentes
	- **Visão do processo**: gestão da implementação
	- **Visão de casos de uso**: Validação do design de arquitetura

# OS DIFERENTES MODELOS ARQUITETURAIS

## Arquitetura em camadas (Layered pattern)

- Organiza um sistema de conjunto em camadas que podem ser desconstruídas em diferentes serviços, trazendo um modelo incremental de desenvolvimento
- Os casos mais comuns para o uso desse padrão são em software de e-commerce e desktop.
- ![[Pasted image 20230417102802.png]]

## Arquitetura cliente-servidor (Client-server pattern)

- Estilo organizado em serviços combinando dados do cliente e do servidor.
- Primordial que o cliente disponibilize uma rede de acesso às informações.

![[Pasted image 20230417103101.png]]


## Arquitetura MVC (Model-view-controller pattern)
- Distribuído em três camadas *(Modelo, Visão e Controle)*, este padrão é um dos mais comuns para o online, porque traz um modelo interativo de sistema.

![[Pasted image 20230417103205.png]]

## Arquitetura de microserviços (Microservices pattern)

- Utiliza múltiplos serviços e componentes para desenvolver uma estrutura modular favorecida.
- Possibilita a escalabilidade e independência dos módulos - ou até podem utilizar diferentes linguagens e programações

![[Pasted image 20230417103400.png]]

# O FUTURO DA ARQUITETURA DE SOFTWARE

- Computação em nuvem
- Inteligência artifical
- microsserviços
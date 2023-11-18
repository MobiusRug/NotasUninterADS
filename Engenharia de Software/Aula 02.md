# DESENVOLVIMENTO ÁGIL

- Métodos ágeis surgiram para corrigir falhas na engenharia de software convencional.
- Agilidade no desenvolvimento de software envolve responder a mudanças de forma rápida e eficaz.
- A partir de 1990, começam a surgir os métodos ágeis para desenvolvimento de software
- Em 2001, é criado o Manifesto para o Desenvolvimento Ágil de Software (Agile Alliance), que busca valorizar:
	- *Indivíduos e interações* mais que processos e ferramentas;
	- *Software em funcionamento* mais que uma documentação abrangente;
	- *Colaboração com o cliente* mais que negociação de contratos;
	- *Responder a mudanças* mais que seguir um plano.
- A agilidade promove estruturas de equipe que facilitam a comunicação, entrega rápida de software operacional e envolve o cliente no processo de desenvolvimento.
- Para obter agilidade, o processo deve ser adaptável, fluído, enxuto e enfatizar a entrega incremental.
- Um processo ágil deve se adaptar incrementalmente com feedback constante do cliente.

## Princípios do processo ágil 

1 - Nossa maior prioridade é **satisfazer o cliente** através da entrega contínua e adiantada de software com valor agregado.

2 - **Aceitar mudanças** de requisitos, mesmo no fim do desenvolvimento. Processos ágeis se adequam a mudanças, para que o cliente possa tirar vantagens competitivas.

3 - **Entregar frequentemente software** funcionando, de poucas semanas a poucos meses, com preferência à menor escala de tempo.

4 - Pessoas de negócio e desenvolvedores devem trabalhar diariamente em conjunto por todo o projeto.

5 - Construir projetos em torno de **indivíduos motivados**, dando a eles o ambiente e o suporte necessário e confiando neles para fazer o trabalho.

6 - O método mais eficiente e eficaz de transmitir informações para e entre uma equipe de desenvolvimento é por meio de **conversa face a face.**

7 - **Software funcionando é a medida primária de progresso.**

8 - Os processos ágeis promovem **desenvolvimento sustentável**. Os patrocinadores, desenvolvedores e usuários devem ser capazes de manter um ritmo constante indefinidamente.

9 - Contínua atenção a **excelência técnica** e bom design aumenta a agilidade.

10 - **Simplicidade**: a arte de maximizar a quantidade de trabalho não realizado é essencial.

11 - As melhores arquiteturas, requisitos e designs emergem de **times auto-organizáveis.**

12 - Em intervalos regulares, a equipe reflete sobre como se tornar mais eficaz e então refina e ajusta seu comportamento de acordo.


# EXTREME PROGRAMMING - XP

- surgiu nos EUA no final dos anos 1990.
- Valoriza mudanças incrementais e feedback rápido, considerando a mudança positiva.
- Adequado para equipes pequenas e médias,
- Enfatiza a qualidade a curto, médio e longo prazo, evitando comprometer a qualidade em troca de ganhos a curto prazo.
- Práticas do XP relacionadas a cliente, gerência de projeto, programação e testes incluem:
	a. **Jogo de planejamento** para priorizar funcionalidades com o cliente. - semanal
	b. **Metáfora**: é preciso conhecer a linguagem do cliente e seus significados.
	c. **Equipe coesa:** Cliente faz parte da equipe de desenvolvimento para eliminar barreiras de comunicação. 
	d. **Reuniões em pé** para eficiência.
	e. **Design simples**, atendendo às necessidades do cliente.
	f. **Versões pequenas** para testes contínuos. 
	g. **Ritmo sustentável** com não mais de oito horas de trabalho por dia.
	h. **Posse coletiva do código.** 
	i. **Programação em pares** para verificação de código por pelo menos duas pessoas.
	j. **Padrões de codificação** para consistência.
	k. **Testes de aceitação** planejados com o cliente. 
	l. **Desenvolvimento orientado a teste**, definindo e implementando testes antes da programação. 
	m. **Refatoração** quando necessária para gerenciar a complexidade do código.
	n. **Integração contínua** para evitar surpresas no final do ciclo.
- Ciclo de lançamentos de releases do método XP:

![[Pasted image 20231107100141.png]]

-  Desvantagens incluem práticas não consensuais, falta de escalabilidade para equipes maiores e a programação em pares pode ser cansativa.
- O desenvolvimento em pares pode aumentar o custo de desenvolvimento, mas pode economizar custos na fase de testes.

# FEATURE DRIVEN-DEVELOPMENT -- FDD

- Método ágil enfatiza o uso de orientação a objetos e foi apresentado em 1997 por Peter Coad e Jeff de Luca como evolução de um processo mais antigo.
- Foca no desenvolvimento por funcionalidades
- Dividido em duas fases: 
	a. **Concepção e planejamento**: pré-construção do software, geralmente de uma a duas semanas. 
	b. **Construção**: desenvolvimento iterativo do produto em ciclos de uma a duas semanas.

- Na fase de concepção e planejamento, existem três disciplinas (processos):
	a) **DMA - Desenvolver Modelo Abrangente**: utiliza modelagem orientada a objetos.
	b) **CLF - Construir Lista de Funcionalidades**: aplica decomposição funcional para identificar as funcionalidades do sistema.
	c) **PPF - Planejar por Funcionalidade**: planeja os ciclos iterativos com base nas funcionalidades identificadas.

- A fase de construção incorpora duas disciplinas (processos):
	a) **DPF - Detalhar por Funcionalidade**: realiza o design orientado a objetos do sistema. 
	b) **CPF - Construir por Funcionalidad**e: constrói e testa o software com linguagem e técnica de teste orientadas a objetos.

- Comparação com XP e Scrum: a fase de concepção do FDD tem semelhanças com a construção do "Backlog do Produto" no Scrum. A fase de construção do FDD se assemelha às práticas de Jogo de Planejamento no XP e à definição de Sprints no Scrum.
- A fase de concepção e planejamento está relacionada à elicitação e especificação de requisitos, resultando em modelos de software e planos de desenvolvimento.

![[Pasted image 20231107101903.png]]

# Dynamic Systems Development Method - DSDM

- Modelo ágil baseado em desenvolvimento iterativo e incremental, com participação ativa do usuário.
- Composto por três fases: **Pré-projeto, Ciclo de Vida e Pós-projeto.**
- Fundamentado no Princípio de Pareto (Princípio 80/20), abordando inicialmente os 20% dos requisitos mais determinantes para o sistema.
- Princípios fundamentais do DSDM incluem: 
	- a) *Envolvimento do usuário* no projeto o tempo todo.
	- b) *Autonomia dos desenvolvedores* para tomar decisões sem consultar comitês superiores. 
	- c) *Entregas frequentes de releases* de alta qualidade são essenciais para garantir um produto final satisfatório. 
	- d) *Efetividade das entregas na solução de problemas de negócio*, focando nos requisitos mais importantes. 
	- e) *Feedback dos usuários* para realimentar o processo de desenvolvimento iterativo e incremental.
	- f) *Reversibilidade de ações* durante o desenvolvimento. 
	- g) *Previsibilidade* para definir o escopo e objetivos das iterações antes do início.
	- h) *Ausência de testes no escopo*, tratando os testes como atividade externa ao ciclo de vida.
	- i) *Comunicação de alta qualidade* entre todos os envolvidos é fundamental para o sucesso do projeto.

![[Pasted image 20231107103513.png]]

- Na fase do **Pré-Projeto**, atividades de Estudo de Viabilidade e Exploração se concentram na análise das características do projeto, necessidades dos usuários e requisitos.
- A fase do **Ciclo de Vida** inclui atividades de Exploração, Engenharia e Desenvolvimento em diversos ciclos iterativos que incorporam os princípios do DSDM.
- A fase de **Pós-Projeto** ocorre após a conclusão de cada ciclo iterativo e entrega ao cliente, com o objetivo de verificar o funcionamento correto do software, realizar manutenção e aprimoramentos, se necessário.

# Método Crystal Clear

- Criado por Alistair Cockburn em 1997.
- Adequado para equipes pequenas (até oito pessoas) trabalhando juntas.
- Composta por um designer líder e de dois a sete programadores.
- Propõe o uso de radiadores de informação, acesso fácil a especialistas de domínio, eliminação de distrações, cronograma de desenvolvimento e ajuste do método quando necessário.

Ciclo de vida do método Crystal Clear:

1. Iteração: estimação, desenvolvimento e celebração (dura poucas semanas).
2. Entrega: várias iterações, entregando funcionalidades úteis ao cliente em até dois meses.
3. Projeto: conjunto de todas as entregas.

Os sete pilares do método Crystal Clear:

1. Entregas frequentes (no máximo a cada dois meses).
2. Melhoria reflexiva (discussão frequente sobre o rumo do projeto e descobertas).
3. Comunicação osmótica (trabalho em uma sala única, programadores trabalham individualmente, mas próximos).
4. Segurança pessoal (falar sem medo de repreensões).
5. Foco (membros da equipe têm dois ou três tópicos de alta prioridade).
6. Acesso fácil a especialistas (disponibilidade de especialistas de domínio, usuários e clientes).
7. Ambiente tecnologicamente rico (suporte a testes automáticos, gerenciamento de configuração e integração frequente).

# Adaptive Software Development - ASD

- Baseado em ideias da área de sistemas adaptativos complexos.
- Considera o processo de desenvolvimento de software como um sistema complexo com *agentes* (desenvolvedores, clientes, etc.), *ambientes* (organizacional, tecnológico e de processo) e *saídas emergentes* (produtos sendo desenvolvidos).

Três grandes fases do modelo ASD:

1. **Especular**:
    
    - Planejamento de ciclos adaptáveis.
    - Determinação do tempo de duração do projeto, quantidade de ciclos, objetivos de cada ciclo, componentes a serem desenvolvidos, tecnologias necessárias e listas de tarefas.
2. **Colaborar**:
    
    - Equilíbrio entre atividades previsíveis e incertas.
    - Desenvolvimento de componentes de forma concorrente.
3. **Aprender**:
    
    - Revisões de qualidade e testes de aceitação com a presença do cliente e especialistas do domínio.
 
Comparação com o método DSDM (Método de Desenvolvimento de Sistemas Dinâmicos):

- Fase de Especulação do ASD é similar à fase de Pré-Projeto do DSDM.
- Fase de Colaboração do ASD é comparável ao Ciclo de Vida do DSDM.
- Fase de Aprender do ASD, envolvendo revisão de qualidade, testes e manutenção, é equivalente à fase de Pós-Projeto do DSDM.

Ciclo de execução do ASD:

- Iterativo, envolvendo as três fases, desde o início do projeto até a entrega.
- Mantém peculiaridades em relação ao DSDM, especialmente na execução independente de cada fase no DSDM e o ciclo iterativo entre as três fases no ASD.

![[Pasted image 20231107105416.png]]

# SCRUM

- Modelo ágil para a gestão de projetos de software.
- *Sprint* é um conceito importante, sendo um ciclo de desenvolvimento com duração geralmente de duas semanas a um mês.
- Pode ser integrado a outros métodos ágeis e aplicado a qualquer ambiente de trabalho.
    

## Fases do Scrum

1. **Planejamento Geral**:
    
    - Estabelecimento dos objetivos gerais do projeto e da arquitetura do software.
2. **Ciclos de Sprint**:
    
    - Desenvolvimento de incrementos do sistema em ciclos.
3. E**ncerramento do Projeto**:
    
    - Conclusão do projeto, documentação e avaliação das lições aprendidas.

## Papéis importantes no Scrum:

1. **Scrum Master**:
    - Responsável por manter o time Scrum em um ambiente propício para o sucesso do projeto.
    - Facilitador e solucionador de conflitos, não um gerente ou líder.

1. **Product Owner** (dono do produto):
    - Representa a voz do cliente e coordena as necessidades dos clientes.
    - Responsável por indicar requisitos importantes em cada sprint.

1. **Scrum Team** (Time Scrum):
    - Responsável pelo desenvolvimento das entregas e pela compreensão dos requisitos.
    - Não necessariamente dividido em papéis específicos.

### Outros papéis no Scrum:

- **Stakeholders**: Pessoas com interesse no projeto, como cliente, usuários e patrocinadores.
- **Scrum Guidance Body**: Grupo de especialistas que orientam o Product Owner, Scrum Master e Time Scrum.
- **Chief Product Owner**: Papel em projetos maiores com vários times Scrum.
- **Chief Scrum Master**: Gerencia mais de um time Scrum.

## Product Backlog e Sprints:

- Funcionalidades a serem implementadas mantidas em uma lista chamada de Product Backlog.
- O Product Backlog não precisa ser completo no início e pode ser atualizado à medida que o projeto avança.
- Transferência de elementos do Product Backlog para o Sprint Backlog no início de cada Sprint.
- Mantém-se o sprint backlog atualizado, indicando as tarefas já concluídas e aquelas ainda por concluir


## Reuniões 
- **Reuniões diárias (Stand Up Meetings)**
	- realizadas para atualização dos membros do Time Scrum.
	-  duração limitada de 15 minutos, em que todos os membros do Time Scrum devem participar
		1. O que eu fiz ontem?
		2. O que farei hoje?
		3. Quais impedimentos ou obstáculos estou enfrentando atualmente?
- **Reunião de Revisão** 
	- avalia o produto do Sprint e os processos de trabalho.
	- Reunião de Retrospectiva analisa os Sprints concluídos e identifica melhorias para o processo.

O Product Owner é fundamental na avaliação das entregas e requisitos.

![[Pasted image 20231107112128.png]]
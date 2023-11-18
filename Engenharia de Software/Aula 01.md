# INTRODUÇÃO 

- não há notações, métodos ou técnicas universais para o desenvolvimento de uma variedade completamente heterogênea de sistemas de software.
- “A engenharia de software se destina a apoiar o desenvolvimento de software profissional em vez da programação individua
- É a relacionada a todos os aspectos da produção de software
- estudar, criar e otimizar os processos de trabalho para os desenvolvedores de software.

## Processos de software
- conjunto de *atividades* interdependentes, com *responsáveis* e com *entradas* e *saídas* definidas que levam à produção de um sistema de software
- Quatro atividades fundamentais de acordo com Sommerville
	1. **Especificação**: a funcionalidade do software e as restrições sobre sua operação devem ser definidas.
	2. **Desenvolvimento**: o software deve ser produzido para atender à especificação.
	3. **Validação**: o software deve ser validado para garantir que atenda ao que o cliente deseja.
	4. **Evolução**: o software deve evoluir para atender às mudanças nas necessidades dos clientes.

## Modelos de Processos de Software
- **Processos prescritivos**:  propósito de organizar e direcionar as atividades inerentes ao desenvolvimento de software.
- **Processos ágeis**:  possuem iterações curtas, em que o resultado é medido por meio do produto pronto

# Modelo em Cascata
- Desenvolvido na década de 1970
- Apresenta o processo de desenvolvimento de software como uma série de fases 

![[Pasted image 20231030094605.png]]

1. **Definição dos Requisitos:** Nesta fase, os requisitos do sistema são coletados e documentados de forma detalhada.
    
2. **Projeto:** A partir dos requisitos definidos, é criado um projeto que descreve como o sistema será estruturado e quais componentes serão desenvolvidos.
    
3. **Implementação e teste de unidade:** Nesta fase, o código-fonte é escrito com base no projeto, transformando a concepção em um sistema de software funcional.
    
4. **Integração e Teste de Sistema:** O sistema é submetido a testes rigorosos para garantir que ele atenda aos requisitos e funcione corretamente.
    
5. **Operação e Manutenção:** Após a implantação, o sistema é mantido e atualizado conforme necessário para corrigir defeitos e atender a novos requisitos.


- ***Vantagens***
	- Fases bem definidas ajudam a detectar erros mais cedo
	- Procura promover a estabilidade dos requisitos
	- Funciona bem quando os requisitos são conhecidos e estáveis
	- É adequado para equipes tecnicamente fracas ou inexperientes 

- ***Desvantagens***
	- Não produz resultados tangíveis até a fase de codificação
	- É difícil estabelecer requisitos completos antes de começar a codificar
	- Desenvolvedores sempre reclamam que os usuários não sabem expressar aquilo que precisam
	- Não há flexibilidade com requisitos

## Modelo em V
- Trata-se de uma variação do Modelo Cascata e prevê uma fase de validação e de verificação para cada fase de construção.
- À medida que a equipe de software desce em direção ao lado esquerdo do V, os requisitos básicos do problema são refinados em representações cada vez mais detalhadas e técnicas do problema e de sua solução
- Uma vez que o código tenha sido gerado, a equipe se desloca para cima, no lado direito do V, realizando basicamente uma série de testes (ações de garantia da qualidade) que validem cada um dos modelos criados à medida que a equipe se desloca para baixo, no lado esquerdo do V.

![[Pasted image 20231030100919.png]]

• **fase de requisitos** – a equipe e o cliente eliciam e elaboram o documento de requisitos, que é aprovado conjuntamente, na forma de um contrato de desenvolvimento;
• **fase de design arquitetural** – a equipe organiza os requisitos em unidades funcionais coesas, definindo como as diferentes partes arquiteturais do sistema vão se interconectar e colaborar;
• **fase de design detalhado** – a equipe vai aprofundar a descrição das partes do sistema e tomar decisões sobre como elas serão implementadas;
• **fase de implementação** – o software é implementado de acordo com a especificação detalhada;
• **Fase de teste de unidade** – tem como objetivo verificar se todas as unidades se comportam como especificado na fase de design detalhado.
• **fase de teste de integração** – tem como objetivo verificar se o sistema se comporta conforme a especificação do design arquitetural;
• **fase de teste de sistema** – verifica se o sistema satisfaz os requisitos especificados.

## Modelo em W
-  incorpora o teste nas atividades de desenvolvimento desde seu início, e não apenas nas fases finais
- Planejamento dos testes em cada uma das fases de construção

- **Fase de requisitos**: apenas requisitos que possam ser testados são aceitáveis ao final dessa fase
- **Fase de design arquitetural**: arquiteturas simples devem ser fáceis de testar
- **Design detalhado**: Unidades coesas são mais fáceis de testar 

![[Pasted image 20231030103009.png]]


# Modelo em Espiral

- Proposto em 1988 por Boehm - combinação do modelo em cascata com a prototipação
- Processo de software **orientado a riscos**
- Cada loop representa uma fase do processo de software
- Cada subprojeto aborda um ou mais elementos de alto risco, até que todos os riscos identificados tenham sido tratados 
- Pressman diz que é iterativo, mas, não, incremental – sendo, então, evolucionário 

## Setores do modelo em espiral 

1. **Planejamento**:Determinar objetivos, alternativas e restrições
    
2. **Análise de Risco**: Avaliar alternativas, identificar e resolver riscos
    
3. **Engenharia e Construção**: Desenvolver e testar
    
4. **Avaliação e Planejamento da Próxima Iteração**: Planejar as próximas fases

## VANTAGENS
- Suporta mecanismos de redução de riscos.
- Obtêm-se versões do sistema a cada iteração.
- Entregando produtos cada vez mais refinados e de melhor qualidade.
- Reflete as práticas reais de engenharia atual.
- Apresenta uma abordagem sistemática.
- Apresenta estimativas realistas.

## DESVANTAGENS
- Exige analistas de risco bastante experientes.
- Exige uma equipe de desenvolvimento extremamente qualificada.
- Exige um gerenciamento de processo mais complexo.
- Não é recomendado resolver problemas mais simples e pequenos.

## Outras características
- As primeiras iterações são as mais baratas do ponto de vista de investimento de tempo e de recursos 
- Também são as que resolvem os maiores problemas do projeto
- Esse modelo não provê a equipe com indicações claras sobre a quantidade de trabalho esperada a cada ciclo
- Pode tornar o tempo de desenvolvimento nas primeiras fases bastante imprevisível

![[Pasted image 20231031083450.png]]

# Desenvolvimento por fases

- Tem como premissa diminuir o tempo de desenvolvimento e entrega do produto de software ao cliente
-  o sistema é projetado de modo que possa ser entregue em partes, possibilitando aos usuários dispor de alguns recursos enquanto o restante do sistema está sendo desenvolvido.
	- **sistema em produção**: é o sistema que está sendo atualmente utilizado pelo cliente;
	- **sistema em desenvolvimento**: é a versão seguinte que está sendo desenvolvida para substituir o sistema em produção.

![[Pasted image 20231031084706.png]]

## Desenvolvimento incremental x Desenvolvimento iterativo

- **Desenvolvimento incremental** - o sistema é dividido por funcionalidades e cada versão entregue corresponde a uma ou um conjunto dessas funcionalidades - os *builds*

![[Pasted image 20231031084849.png]]

- **Desenvolvimento iterativo** - : a primeira versão entregue corresponde ao sistema completo, porém, com funcionalidades limitadas. Cada versão posterior corresponde a mudanças realizadas nas funcionalidades limitadas.

![[Pasted image 20231031084950.png]]

## Vantagens
- O custo de acomodar as mudanças nos requisitos do cliente é reduzido
-  É mais fácil obter feedback dos clientes 
-  É possível obter entrega e implementação rápida de um software útil ao cliente

## Desvantagens
-  O processo não é visível: se os sistemas são desenvolvidos rapidamente, não é viável economicamente produzir documentos para cada versão do sistema.
- Os sistemas são frequentemente mal estruturados: mudanças contínuas tendem a corromper a estrutura do software e tornar mudanças difíceis e caras.

# Prototipação Evolucionária

- De acordo com Roger Pressman  o modelo incremental sempre apresenta uma funcionalidade operacional ou um produto de trabalho a cada iteração. Já o modelo evolucionário, durante as primeiras iterações, pode gerar versões compostas apenas por modelos em papel, documentação ou produtos não operacionais para o usuário
-  quando os requisitos estão obscuros, o paradigma da prototipação auxilia os interessados a compreender melhor o que está para ser construído.
- Um protótipo é uma versão inicial de um sistema de software utilizado para demonstrar conceitos, experimentar opções de projeto e, geralmente, conhecer mais sobre o problema e suas possíveis soluções

## Tipos de prototipação
- **Throw-away** -  para levantar os requisitos do sistema junto aos usuários e depois ser efetivamente descartado
- **Cornerstone (evolucionário)** - para ser refinado até chegar ao sistema final desejado pelos usuários.

![[Pasted image 20231031091758.png]]

![[Pasted image 20231031091816.png]]


![[Pasted image 20231031091829.png]]

# RUP - Rational Unified Process
- Framework iterativo e incremental de desenvolvimento de software, centrado na arquitetura, planejado por riscos, guiado por casos de uso e orientado a objetos

## Boas práticas
1. Desenvolvimento iterativo
2. Gerenciamento de requisitos
3. Uso da Arquitetura de Componentes
4. Modelagem visual (UML)
5. Contínua verificação de Qualidade
6. Gerenciamento de Mudanças

## Perspectivas
- **Dinâmica** - Também conhecido como temporal ou horizontal, mostra as *fases* do modelo ao longo do tempo, além de *iterações* e *marcos* do projeto.
- **Estática** - Também conhecido como funcional ou vertical, mostra as *atividades* realizadas no processo, componentes, *disciplinas*, *artefatos* e papeis de processo.
- **Prática** - Segue boas práticas

## Conceitos
- **Papel (Role)** -  Definição abstrata dos comportamentos e responsabilidades de um indivíduo (ou um conjunto de indivíduos) que trabalham como uma equipe em uma organização.
- **Atividades** - Trata-se de uma unidade de trabalho que fornece um resultado significativo dentro do contexto de um projeto. Tem um propósito claro e envolve criar ou atualizar artefatos.
- **Artefato** - Trata-se de um pedaço de informação que é produzido e/ou utilizado durante a execução do processo – são os produtos tangíveis do processo.
- **Fluxo de Trabalho** -Trata-se de um pedaço de informação que é produzido e/ou utilizado durante a execução do processo – são os produtos tangíveis do processo.
- uma disciplina pode ter vários artefatos, mas um artefato só é produzido por uma disciplina.
- existe um relacionamento N:N entre artefatos e fases


## Fases

- Uma passagem pelas quatro fases se chama ciclo de desenvolvimento e uma passagem pelas nove disciplinas se chama Iteração, podendo haver mais de uma iteração por fase, 
### Iniciação/concepção
- Tem o objetivo de estabelecer um caso de negócio para o sistema. Deve-se identificar as entidades externas, que irão interagir com o sistema, e definir essas interações. Depois você usa essas informações para avaliar a contribuição do sistema com o negócio.
- **marco**: Escopo ou objetivos do ciclo de vida.
- Artefatos importantes: Documento de Visão; Casos de Negócio; Plano de Desenvolvimento do Software; Modelo de Casos de Uso; Glossário.

### Elaboração
-  desenvolver um entendimento do domínio do problema, estabelecer um framework de arquitetura para o sistema
- Ao concluir, deve-se ter um modelo de requisitos para o sistema, uma descrição de arquitetura e um plano de desenvolvimento para o software.
- **marco**: Arquitetura estabilizada.
- Artefatos importantes: Protótipos; Lista de Riscos; Documento de Arquitetura de Software; Modelo de Projeto; Modelo de Dados.

### Construção
- desenvolver partes do sistema paralelamente e integradas durante esta fase.
- Ao concluir esta fase, você deve ter um sistema de software em funcionamento e a documentação associada pronta para ser liberada para os usuários.
- **marco**: Capacidade operacional inicial.
- Artefatos importantes: o próprio sistema executável e suas bibliotecas; conjunto de testes do software; materiais de treinamento; material de suporte do usuário.

### Transição
- colocar o sistema em funcionamento no ambiente real de uso.
- **marco**: Lançamento (ou Release) do produto.
- Artefatos importantes: Notas de Release; Artefatos de Instalação; entre outros.


## Disciplinas

### Modelagem de negócios
- Entender os problemas atuais da organização-alvo e identificar as possibilidades de melhoria.

### Requisitos
- Definir as fronteiras do sistema (ou delimitar o sistema).
- e o que sistema deve fazer 
- Fornecer uma base para estimar o custo e o tempo de desenvolvimento do sistema.

### Análise de Projeto/Design
- Transforma os requisitos em um projeto do sistema a ser criado

### Implementação
- Implementar classes e objetos em termos de componentes
- Testar os componentes desenvolvidos como unidades.
- Integrar os resultados produzidos por implementadores individuais (ou equipes) ao sistema executável.

### Teste
- Validar as suposições feitas nas especificações de design e requisito através de demonstração concreta
- Validar as funções do software conforme projetadas.
- Verificar se os requisitos foram implementados de forma adequada.

### Implantação
- Desenvolver artefatos de instalação e materiais de treinamento.
- Liberar o sistema em produção para os usuários finais.

### Gerenciamento de Configuração e Mudanças
- Restringir as mudanças nesses itens de configuração.
- Auditar as mudanças nesses itens de configuração.

### Gerenciamento de Projetos
- Fornecer diretrizes práticas para planejar, montar a equipe, executar e monitorar os projetos.
- Fornecer um framework de gerenciamento de risco.

### Ambiente
- Oferecer processos e ferramentas que darão suporte à equipe de desenvolvimento.

![[Pasted image 20231031095352.png]]

![[Pasted image 20231031095444.png]]
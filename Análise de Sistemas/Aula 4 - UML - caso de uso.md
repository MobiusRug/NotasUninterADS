# O QUE É UML

- Começou a ser criada em 1994, por J*ames Rumbaugh, Grady Booch e Ivar Jacobson* (The Three Amigos) na *Rational Software Corporation*
- consolidaram seus métodos com as informações obtidas e padronizaram tudo em uma linguagem de modelagem não-proprietária: Unified Modeling Language (UML).
-  **UML é uma linguagem ou notação de diagramas que serve para especificar, visualizar e documentar modelos de software desenvolvidos sob os preceitos da orientação por objetos**
-  A UML é controlada pelo **OMG** e considerada como a norma da indústria de software para descrevê-lo graficamente.

## MODELOS

- representação ou abstração dos objetos e atividades envolvidas no processo de criação de um software.
- ajudam a visualizar o sistema como ele é ou como desejamos que seja
- permitem especificar a estrutura ou o comportamento de um sistema
- proporcionam um guia para a construção do sistema
- documentam as decisões de projeto tomadas e apoiam a tomada de uma melhor decisão 
- permitem visualizar o sistema em diversos níveis de abstração.
- Facilitam a comunicação entre os membros da equipe de formulação do software
- Expressam duas visões diferentes
	- **visão estrutural**: capturam a estrutura do sistema - quais elementos compõem a estrutura do sistema e como eles se relacionam;
	- **visão comportamental**: capturam a dinâmica do sistema -  como os elementos que compõem o sistema se comunicam e como se comportam e respondem a diversos estímulos.

## MODELOS DE UML

- a UML é a linguagem mais conhecida no mundo da TI para fazer modelagem de softwares. 
- Os **elementos** UML são usados para criar diagramas que representam uma determinada parte ou um ponto de vista do sistema
- Os **diagramas** mostram visualmente a solução definida para a construção do software.
- A versão atual é a 2.0

### DIAGRAMAS ESTRUTURAIS OU ESTÁTICOS

- **Diagrama de classes:** principal diagrama de análise de projeto OO. São mostradas as classes do sistema, seus relacionamentos, seus atributos e seus métodos
- **Diagrama de componentes**: modela as partes do software no ambiente onde ele está sendo implementado
- **Diagrama de implantação:** modela o hardware de cada um dos ambientes utilizado
- **Diagrama de objetos:** modela instâncias reais das classes e seus relacionamentos
- **Diagrama de pacotes:** mostra como os elementos estão organizados em pacotes e as dependências entre esses pacotes.
- **Diagrama de estrutura da composição**
- **Diagrama combinado componentes/implantação**: como os componentes de software estão distribuídos nos componentes do hardware.

### DIAGRAMAS COMPORTAMENTAIS OU DINÂMICOS

- **Diagrama de caso de uso:**  são especificados e detalhados os requisitos funcionais, com descrição dos cenários nos quais os atores interagem com o sistema
- **Diagrama de sequência:** apoia a visão dinâmica, modela  a interação entre os diversos objetos de uma linha de tempo.
- **Diagrama de atividades:** normalmente usado para modelagem de processos de negócio ou para detalhamento da lógica de negócio, permite a modelagem de fluxo de controle e de dados
- **Diagrama de estados:** modela como os estímulos ou eventos externos causam mudanças no estado de um objeto, no decorrer do seu ciclo de vida.
- **Diagrama de comunicação:**
- **Diagrama de visão geral da interação:**  são modelados blocos de interação associados ao diagrama de sequência, visão macro
- **Diagrama de tempo:** modela mudanças no estado de um objeto, com ênfase na questão do tempo 

# MODELO ORIENTADO A OBJETOS

- A orientação a objetos é um processo conceitual independente de uma linguagem de programação, pois tem como foco visualizar o domínio do problema a ser automatizado como uma coleção de objetos e métodos associados
- Um objeto uma entidade, real ou abstrata, que *modela um conceito presente na realidade humana*, ocupando espaço físico ou lógico
- Um objeto denota uma entidade de natureza *física, conceitual ou de software:*
- Um objeto possui : *identidade, atributos e métodos* (comportamentos)

## PILARES DA ORIENTAÇÃO A OBJETOS

- São eles **abstração, encapsulamento e herança**
- **Abstração**: concentrar nos aspectos essenciais, próprios de uma entidade
- **Encapsulamento:** separação dos aspectos externos de um objeto, acessíveis por outros objetos, dos detalhes internos da implementação daquele objeto, que ficam ocultos dos demais objeto
- **Herança:** é o compartilhamento de atributos e operações entre objetos, com base em um relacionamento hierárquico.

# DIAGRAMAS DE CASO DE USO

- normalmente é o primeiro diagrama a ser construído, após o levantamento de requisitos do software
- permite analisar o relacionamento de cada uma das **funcionalidades** que o software deve executar - foco em mostrar o comportamento externo do software
- Essas funcionalidades do sistema são apresentadas do **ponto de vista do usuário**.
- é representado por **atores, casos de uso e relacionamentos** entre esses elementos. 
- Inicia-se  com a descoberta dos atores ou dos casos de uso do sistema, com base nos seus requisitos iniciais
- Para cada caso de uso, deve-se descrever os **cenários principais e os alternativos relevantes**
- atores, representados pelos bonecos; os casos de uso, representados pelas elipses; e os relacionamentos, representados por setas
- É uma boa prática colocar os casos de uso do diagrama de caso de uso dentro de um retângulo, que irá representar os limites do software - a visão total do escopo do software

![[UML_use_case_example-800x707.png]]


## ELEMENTOS DE UM DIAGRAMA DE CASO DE USO

### ATORES
- Um ator representa um **papel** exercido por um usuário ao interagir com determinado caso de uso.
- Usuários podem desempenhar mais de um papel no sistema.
- o ator interage com o sistema, mas ele não faz parte do sistema.
- é representado por um boneco e um rótulo com o nome do ator
- Podem ser classificados como:
	- **primário:**  interessado que acessa o sistema para utilizar diretamente um serviço.
	- **secundário (ou de suporte):**  interage com o sistema fornecendo algum tipo de serviço ou informação
- Podem ser divididos em diferentes categorias como: *Usuários, Aplicações, Dispositivos, Eventos externos*
- Uma boa dica para identificar os atores é analisar as fontes e os destinos das informações a serem processadas e as áreas da organização que serão afetadas ou utilizarão o sistema

![[Pasted image 20230511091715.png]]

### CASO DE USO 

- A representação gráfica do caso de uso é feita por meio de um ícone que é uma elipse contendo seu nome
- define uma função do sistema.

![[Pasted image 20230511092048.png]]

### RELACIONAMENTO

- Representam a ligação dos atores com os casos de uso e dos casos de uso entre si

#### RELACIONAMENTO ENTRE ATORES - GENERALIZAÇÃO

- O único relacionamento possível entre os atores é a **generalização.**
- é usada para representar a relação de herança de comportamento entre atores.
- permite que um ator herde os casos de uso de outro ator, ou seja, um ator especializado (subator) pode realizar todos os casos de uso de um ator mais genérico (superator), além de ter seus próprios casos de uso específicos.
- é representado por uma linha sólida com um triângulo vazio apontando para o ator mais genérico (superator)![[generalização.png]]
#### RELACIONAMENTO ENTRE UM ATOR E UM CASO DE USO: ASSOCIAÇÃO

- ator se comunica com o sistema por meio do envio e recebimento de mensagens

![[Pasted image 20230512073343.png]]

#### RELACIONAMENTOS ENTRE CASOS DE USO

##### INCLUSÃO
Um relacionamento include de um caso de uso A para um caso de uso B indica que B é essencial para o comportamento de A, ou seja, sempre que A for executado, B também será, é um relacionamento obrigatório 

![[Pasted image 20230512073723.png]]

##### EXTENSÃO
quando o caso de uso B estende o caso de uso A, significa que quando o caso de uso A for executado o caso de uso B poderá (poderá – talvez não seja) ser executado também. A direção do relacionamento é do caso de uso extensor (aqui o caso de uso B) para o caso de uso estendido (aqui o caso de uso A).

![[Pasted image 20230512074206.png]]


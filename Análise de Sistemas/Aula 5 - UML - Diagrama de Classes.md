# PILARES DO OO

- **Abstração** -  é a visão concentrada em aspectos essenciais dentro de um contexto, para isso eu devo subtrair da visão detalhes que não são importantes e decompor até chegar nas partes fundamentais.
- **Encapsulamento** -  separação dos aspectos externos de um objeto, acessíveis por outros objetos, dos detalhes internos da implementação daquele objeto
- **Herança** - é o compartilhamento de atributos e operações entre classes com base em um relacionamento hierárquico
- **Polimorfismo**

# DIAGRAMA DE CLASSE
- Descreve as classes e interfaces presentes no sistema, suas características, restrições e os vários tipos de relacionamentos estáticos entre seus objetos


# CLASSES, ATRIBUTOS E MÉTODOS

## CLASSES
- Classe é uma estrutura classificadora que abstrai um conjunto de objetos que compartilham características, restrições e semânticas similares
- A classe define o **comportamento** de seus objetos através de **métodos** e o **estado** por meio de **atributos**.
- classe - planta da casa, objeto - casa em si. O objeto surge da instanciação da classe 
- Boas práticas:
	- as classes devem receber nomes de acordo com o vocabulário do domínio do problema.
	- adotar um padrão para dar nome às classes

## ATRIBUTOS
- representam o conjunto de características ou estados dos objetos de uma determinada classe. 
- Cada atributo permite definir um intervalo de valores em que as instâncias dessa propriedade podem apresentar
- O atributo possui um tipo - qual tipo de informação ele pode assumir 

## MÉTODOS
- representam o conjunto de operações ou comportamento que a classe fornece ao software ou que a classe é responsável por executar.
- pode ou não retornar um valor 
- pode ou não aceitar argumentos
- após encerrar sua execução, retorna o fluxo de controle do programa para quem o chamou
- o método pode ter um tipo, definido pelo tipo do valor que retorna

### VISIBILIDADE
- A [[UNINTER/Programação Orientada a Objetos/Aula 3#VISIBILIDADE|visibilidade]] do atributo  ou método pode ser definida como público (+), protegido (#),  privado (-) ou pacote (~)

| Visibilidade                  | *Public (+)* | *Protected (#)* | *Default* | *Private (-)* |
| ----------------------------- | ------------ | --------------- | --------- | ------------- |
| Classe                        | **SIM**      | **SIM**         | **SIM**   | **SIM**       |
| Pacote                        | **SIM**      | NÃO             | **SIM**   | NÃO           |
| Subclasse, mesmo pacote       | **SIM**      | **SIM**         | **SIM**   | NÃO           |
| Subclasse, pacotes diferentes | **SIM**      | **SIM**         | NÃO       | NÃO           |
| Global                        | **SIM**      | NÃO             | NÃO       | NÃO           |

- Obs.: em Java classes protected também são visíveis dentro do mesmo pacote 

# RELACIONAMENTOS

- Representam a comunicação e o compartilhamento de informações entre as classe

 **CARACTERÍSTICAS**
- *Nome*
- *Sentido de leitura*
- *navegabilidade*
- *multiplicidade* - informação dos limites inferior e superior da quantidade de objetos aos quais outro objeto pode estar associado
- *tipo*
- *papéis*

![[Pasted image 20230513092726.png]]

## TIPOS DE RELACIONAMENTO

### ASSOCIAÇÃO
- Indica que os objetos de uma classe estão vinculados a objetos de outra classe. 
- Uma associação é representada por uma linha sólida entre duas classes
![[Pasted image 20230513093437.png]]

### GENERALIZAÇÃO 
-  indica que a subclasse é uma *especialização* da superclasse ou que a superclasse é uma *generalização* da subclasse
- Qualquer instância da subclasse é também uma instância da superclasse

![[Pasted image 20230513093922.png]]

### DEPENDÊNCIA
- Ocorre se mudança de estado em uma classe (independente) causarem mudanças a outro elemento (dependente)
- identifica uma *ligação fraca* entre objetos de duas classes
- indicado por uma reta tracejada

![[Pasted image 20230513094416.png]]

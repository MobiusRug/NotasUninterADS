# POLIMORFISMO

-   Geralmente descreve a capacidade de objetos de uma superclasse assumirem a forma (métodos e atributos internos) de diferentes subclasses

## POLIMORFISMO UNIVERSAL

-   é o tipo de polimorfismo em que temos um mesmo algoritmo, um mesmo comportamento, que pode ser executado para diversas classes ou dados primitivos.

### SUBTIPAGEM

-   Forma mais conhecida
-   ocorre quando temos uma superclasse que possui determinado método, e suas subclasses reimplementam esse método com outro comportamento
-   Se instanciarmos um objeto do tipo da subclasse em uma variável do tipo da Superclasse, o objeto só terá acesso aos métodos presentes na Superclasse, porém, caso a subclasse redefina um método presente na superclasse, o tipo do objeto que dita qual método será executado, ou seja, será executado o método da subclasse.
-   Em outras palavras, independente do tipo da variável, o método a ser executado é escolhido com base no tipo real do objeto, objetos são polimórficos, o que significa que eles podem ser implementados utilizando diferentes tipos de variáveis (das superclasses).

```java
Superclasse objeto = new Subclasse() //em caso de polimorfismo, os métodos da subclasse serão executados 
```

### PARAMÉTRICO

-   É o tipo de polimorfismo em que uma função e os dados dentro dela podem ser escritos de forma genérica para diferentes tipos de dado.

## POLIMORFISMO AD HOC

-   atua em um conjunto específico de classes para as quais uma mesma chamada de método permite comportamentos diferentes para cada tipo

### COERÇÃO

-   Ocorre quando fazermos conversão, implícita ou explícita, com código descrevendo a transformação entre tipos diferentes de dados

### OVERLOADING

-   Temos funções com o mesmo nome, mas com parâmetros de entrada diferentes, o que permite que executem códigos distintos.

![[Pasted image 20230518203005.png]]

# POLIMORFISMO NA LINGUAGEM JAVA

## REFERÊNCIA E ISNTANCIAÇÃO

-   Quando criamos uma variável de uma classe na linguagem Java, esta se comporta como uma referência.
-   A variável aponta uma posição de memória
-   Para indicar que desejamos criar um novo objeto na memória reservando espaço e efetivamente instanciar o mesmo, utilizamos o comando **new**

## VANTAGENS POLIMORFISMO

-   In addition to each variable's original type, each variable can also be represented by the types of interfaces it implements and classes that it inherits
-   makes programming simpler. Se precisamos apenas dos métodos definidos na Superclasse, podemos passar a Superclasse como parâmetro do método, dessa forma o método pode receber qualquer objeto de subclasses da superclasse definida

# CLASSE ABSTRATA

-   Generally, abstract classes are used in situations where the concept that the class represents is not a clear independent concept
-   **Características**
    -   Não pode ser instanciada
    -   Pode referenciar objetos de subclasses graças ao polimorfismo
    -   Permite criação de métodos desprovidos de implementação, mas que obrigatoriamente devem ser implmentados por suas subclasses

digressão:

-   erros léxicos - comando escrito errado
-   erros de sintaxe - comando escrito corretamente, em local que não faz sentido
-   erros semânticos - são aqueles em que o comando está escrito certo, no local certo, mas executa instruções diferentes das desejadas, em outras palavras, o significado do que está escrito não é o que se imaginava

```java
public abstract class Operation {

    private String name;

    public Operation(String name) {
        this.name = name;
    }

    public String getName() {
        return this.name;
    }

    public abstract void execute(Scanner scanner);
}

public class PlusOperation extends Operation {

    public PlusOperation() {
        super("PlusOperation");
    }

    @Override
    public void execute(Scanner scanner) {
        System.out.print("First number: ");
        int first = Integer.valueOf(scanner.nextLine());
        System.out.print("Second number: ");
        int second = Integer.valueOf(scanner.nextLine());

        System.out.println("The sum of the numbers is " + (first + second));
    }
}
```



# INTERFACE

-   A palavra interface diz respeito ao meio de ligação/comunicação entre dois sistemas
-   Força que as classes diferentes implementem métodos com os mesmos nomes, entradas e saídas, garantindo que a classe Principal possa acessar as diferentes classes que implementam a interface da mesma forma
-   Uma interface pode ser entendida como um protocolo que explica como deve ser a assinatura dos métodos de uma classe
-   Para uma classe implementar uma interface utilizamos a palavra chave `implements`
-   Uma classe pode implementar diversas interfaces
-   só possui a assinatura dos métodos
-   só pode possuir atributos estáticos

```java
public interface Readable {
    String read();
}

public class TextMessage implements Readable {
    private String sender;
    private String content;

    public TextMessage(String sender, String content) {
        this.sender = sender;
        this.content = content;
    }

    public String getSender() {
        return this.sender;
    }

    public String read() {
        return this.content;
    }
}
```

# ENUM

-   utilizado quando sabemos de antemão os possível valores de uma variável
-   em sua forma mais simples lista os valores constantes que declara, separados por vírgula

```java
enum Estacao{
VERAO,
OUTONO,
INVERNO,
PRIMAVERA
}
```

-   É possível fazer um loop por todas estações utilizando o método `values()`
-   Normalmente é declarado no próprio arquivo como uma classe, mas também pode ser declarado dentro de uma classe existente para ser utilizado localmente
-   em Java suas constantes são sempre entendidas como public, static, final
- possui métodos como 
	- `name()`
	- `ordinal()

- Passando valor para as constantes:

```java
public enum Prioridade{
	MIN(1), NORMAL(5), MAX(10);

	private int valor;

	Prioridade(int valor){
		this.valor = valor;
	}

	public int getValor(){
		return this.valor;
	}
}

public class Teste{

	Proridade pMin = Prioridade.Min;
}

```
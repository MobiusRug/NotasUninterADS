# CLASSES E ATRIBUTOS

-  Os **objetos** são os elementos em si que compõem o nosso sistema
-  As **classes** classificam um conjunto de objetos que pertençam a um mesmo conjunto - possuem os mesmos atributos.

De forma geral cada objeto possui três aspectos principais:
- **Atributos:** São as variáveis que descrevem o objeto.
- **Métodos**: São como funções que dizem o que cada objeto faz.
- **Estado**: Seria o valor de cada atributo que representa aquele objeto específico.

## CLASSE EM JAVA 

- Em java todo o código que escrevemos está dentro de alguma classe e as interações entre os dados se dão por meio de métodos e objetos.
- A convenção é criar um arquivo separado para cada classe

![[Pasted image 20230424085016.png]]
- `public static void main(String[] args)`, só pode existir um único método main no projeto
- Numa classe devemos declarar os atributos dos objetos que ela representam

``` Java
package com.empresa;

public class Aluno {
	String nome;
	int matricula;
	String cpf;
}

```
- No POO, um objeto pode ser chamado de *instância de uma classe* e criar uma nova *instância*, o que é chamado de *instanciação.*
- Um objeto é instanciado chamando o método que cria o objeto - o **construtor**, usando a palavra chave `new`

```Java
public static void main (String[] args) {
	Aluno mario = new Alunol();
	mario.cpf="111.111.111-1";
	mario.nome="Super Mario";
	mario.matricula=1001;
}

```

- O comando `new` reserva um espaço de memória para aquele objeto

# MÉTODOS

- Bloco de código que pode ser chamado em outro ponto do programa pelo seu nome
- Semelhante a funções em programação estruturada - diferença básica: sempre está associado a objetos e consegue acessar os dados internos do objeto associado.
- Podem receber parâmetros e opcionalmente um valor de retorno
- Podemos definir um método da seguinte forma dentro da classe aluno:

```Java
public void info(){
	System.out.printin("nome: " + nome);
	System.out.printin("matricula: " + matricula);
	System.out.printin("cpf: " + cpf);
}

```
- Na criação do método deve-se declarar o tipo do retorno, caso o método não tenha retorno utiliza-se a palavra chave `void`

- Podemos chamar o método criado dentro da classe principal através da sintaxe: `objeto.método()`

```Java
mario.info();
```


# PADRÕES DE NOMENCLATURA

- O padrão principal da linguagem é o Camel Case
- **Pacotes**: são descritos inteiramente em letras minúsculas. Ex: com.empresa
- **Classes**: inicia com letra maiúscula e segue o Camel Case. Ex: Aluno
- **Métodos, atributos e variáveis**: iniciam com letra minúscula e seguem o Camel Case. Ex: nomeCompleto
- **Constantes**: inteiramente com letras maiúsculas separadas por underline. Ex: VALOR_PI

# STATIC
- Método `static` : é executado sem estar associado a uma instância - pertence à classe e não ao objeto (instância)
	- ou seja, você pode executar o método sem criar um objeto
- Atributo `static`: O atributo se torna global. É acessada a mesma variável, mesma posição de memória, por todas as instâncias 
	- todos objetos acessam e alteram a mesma variável

# DIAGRAMA DE CLASSE

| Classe    | Aluno        |
| --------- | ------------ |
| Atributos | name: String <br> cpf: String <br> matricula: int |
| Métodos   | void info()  |


![[Pasted image 20230425083952.png]]

# CONSTRUTORES

- Métodos especiais que são chamados automaticamente quando instâncias são criadas através da palavra `new`
- Tem o mesmo nome da classe
- Não é preciso declará-lo, pois não possui nenhum tipo de retorno 
- Através dos construtores podemos inicializar as variáveis de um objeto
- Uma classe pode ter mais de um método construtor - **sobrecarga**
- Quando uma classe é criada um construtor vazio implícito é automaticamente criado. Este construtor deixa de existir a partir do momento que é criado outro.

``` Java
public class Aluno {
	String nome;
	int matricula;
	String cpf;
	
	Aluno(String nome, int matricula, String cpf){
		this.nome = nome;
		this.matricula = matricula;
		this.cpf = cpf;
	}
	Aluno(String nome) {
		this.nome = nome;
	}
	Aluno(){
		System.out.println("Construtor sem parametro”);
	}
}

```

- A palavra chave `this` é utilizada para indicar que está se referindo aos atributos do objeto e não aos parâmetros 
	- No exemplo seria como escrever  `Aluno.nome = nome` (essa sintaxe não é válida, apenas para entender)
	- Para evitar confusão é possível usar nomes diferentes para os atributos e para os parâmetros (ex .: atributo `nome`, parâmetro `nomeAluno`)

## Objeto como variável de objeto

- Objetos podem ter outros objetos como atributos
- É possível inicializá-los no construtor de duas maneiras
	- fornecendo os parâmetros necessários para inicialização desse objeto
	- fornecendo o objeto como parâmetro e, ao instanciar usar "new objeto()"

```java
public class SimpleDate {
    private int day;
    private int month;
    private int year;

    public SimpleDate(int day, int month, int year) {
        this.day = day;
        this.month = month;
        this.year = year;
    }

public class Person {
    private String nome ;
    private SimpleDate birthday;

	public Person(String name, int day, int month, int year) {
	    this.name = name;
	    this.birthday = new SimpleDate(day, month, year);
	}

	public Person(String name, SimpleDate birthday) {
	    this.name = name;
	    this.birthday = birthday
	}
}

public class MainProgram {
    public static void main(String[] args) {
    
	Person muhammad = new Person("Muhammad ibn Musa al-Khwarizmi", new SimpleDate(1, 1, 780)); //objeto como parâmetro
	Person pascal = new Person("Blaise Pascal", 19, 6, 1623); //parâmetros necessários para inicialização do objeto 
	
}
```

- ArrayList como atributo precisa ser inicializado
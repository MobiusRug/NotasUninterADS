# TRATAMENTO DE EXCEÇÕES

- **ERRO**
	- é um problema sério que ocorre em tempo de execução
	- impossível para o compilador detectar e que geralmente não tem tratamento para ele. 
	- No geral, são problemas na plataforma que está rodando o programa Java.

- **EXCEÇÃO**
	- também é um problema, mas que geralmente pode ser manejado pelo programa e tratado de alguma forma.

> [!NOTE]
> Em resumo, *erros* são problemas graves e não recuperáveis, enquanto *exceções* são eventos excepcionais que podem ser tratados e recuperados durante a execução do programa por meio de mecanismos de tratamento de exceção adequados.

-  Erros e exceções geram subclasses de uma superclasse *Throwable*

![[Pasted image 20230519095357.png]]

- Quando ocorre uma exceção/erro em um método, ele gera (throw) um objeto do tipo específico e envia para a máquina virtual Java (JVM)
- O objeto *Exception* contém o nome, uma descrição e o estado do programa no momento que ocorreu o problema
- Tratamento:
	1.  **Lançamento da exceção:** Uma exceção é encontrada durante a execução do programa e um objeto de exceção é lançado.
    
	2.  **Pesquisa por tratadores de exceção:** A JVM procura por um bloco `try-catch` que possa lidar com a exceção lançada, verificando a pilha de chamadas dos métodos em execução.
	    
	3.  **Captura da exceção:** Se um bloco `catch` adequado é encontrado, a execução do programa é desviada para esse bloco e o objeto de exceção é capturado.
	    
	4.  **Tratamento da exceção:** Dentro do bloco `catch`, o código específico para tratar a exceção é executado.
	    
	5.  **Propagação da exceção:** Se não houver um bloco `catch` adequado, a exceção é propagada para o chamador atual e a pesquisa continua na pilha de chamadas até encontrar um bloco `catch` adequado ou, se não houver tratamento adequado, o programa é interrompido e uma mensagem de erro é exibida.


# LIDANDO COM EXCEÇÕES 

```java
try {
    // code which possibly throws an exception
} catch (Exception e ) {
    // code block executed if an exception is thrown
} finally {
	//será sempre executado - até mesmo se tiver return nos blocos anteriores
}
```
- finally é utilizado normalmente para liberar recursos
- é possível também liberar recursos implementando a classe autocloseable - try with resources 

```java
public class TesteConexao{
	public static void main(String[] args){

		try(Conexao conexao = new Conexao()){
			conexao.leDados();
		}catch(IllegalSateException ex){
			System.out.println("Deu erro na conexão")
		}

	}
}

public class Conexao implements AutoCloseable{

	public Conexao(){
		System.out.println("Abrindo conexão");
		//throw new IllegalStateException();
	}

	public void leDados(){
		System.out.println("Recebendo dados");
		threow new IllegamStateException();
	}

	@Override
	public void close(){
		System.out.println("Fechando Conexao")
	}
}

```

```output
Abrindo conexão
Recendo dados
Fechando conexão
Deu erro na conexão
```



# CRIANDO AS PRÓPRIAS EXCEÇÕES

- evitar que o programa continue executando mediante situações anormais e devolver o controle para o método tratador adequado.
- É possível por meio do comando `throw`

```java
public class Grade {
    private int grade;

    public Grade(int grade) {
        if (grade < 0 || grade > 5) {
            throw new IllegalArgumentException("Grade must be between 0 and 5.");
        }

        this.grade = grade;
    }

    public int getGrade() {
        return this.grade;
    }
}
```

## TIPOS DE EXCEÇÕES

- Em Java existem dois tipos de exceções - checked e unchecked
- **checked** 
	- são verificadas em tempo de compilação 
	- precisam ser tratadas com try/catch ou explicitamente anunciar na assinatura do método que pode lançar esse tipo de exceção com a palavra throws
	- caso não sejam tratadas, o compilador gerará um erro
- **unchecked**  - RuntimeException
	- não são checadas em tempo de compilação
	- fica livre ao programador decidir se precaver com o uso de try/catch ou não 
	- RuntimeException

>[!Note]
>In summary, if the exception is specific to the method and its logic, it is generally recommended to use a try-catch block within the method. On the other hand, if you want to handle exceptions in a centralized manner or make different decisions based on the context of the method invocation, catching the exception in the calling main method might be more appropriate. Consider the specific requirements and design principles of your program to make the best decision.

## DESENVOLVENDO SUA PRÓPRIA EXCEPTION

- é possível criar a sua própria exceção subclasse de Exception ou RuntimeException e até mesmo Error. 
- Ao criar uma exceção que estende Exception, ela será do tipo checada e, se ela estender RuntimeException, será do tipo não checada. 

```java
public class MinhaExcecao extends RuntimeException{

	public MinhaExcecao(String msg)
		super(msg);
}
```

## MÉTODOS DAS EXCEÇÕES

- `.getMessage()`
- `printStackTrace()` - rastro da exceção

# IGUALDADE 

```java
public boolean equals(object outro) {
	// Compara consigo mesmo
	if (outro == this) {
		return true;
	}
	//objeto outro é uma instancia de Usuario?
	if (!(outro instanceof Usuario)) {
		return false;
	}
	// type cast para Usuario
	Usuario o = (Usuario) outro;
	
	//Compara os atributos sido iguais
	if( this.id == 0.id &&
		this.nome. equals (o.nome) &&
		this.cpf.equals(o.cpf)) {
			return true;
	}
	return false;
}

```


# TOSTRING

- a classe Object possui o método toString() que, por padrã,o retorna uma String com o endereço na memória daquele objeto.
- podemos sobrescrever o método toString para descrever o objeto como desejamos 

```java
public class Person {
    // ...

    public String toString() {
        return this.name + ", age " + this.age + " years";
    }
}

public class Grade {
    private int grade;

    public Grade(int grade) {
        if (grade < 0 || grade > 5) {
            throw new MinhaExceccao("deu muito errado");
        }

        this.grade = grade;
    }

    public int getGrade() {
        return this.grade;
    }
}
```


# SINGLETON

- Um problema recorrente é a necessidade de termos um objeto que seja instanciado uma única vez e sempre que seja solicitado pelas classes de um projeto seja direcionado ao mesmo objeto.
- Essa classe que é instanciada apenas uma vez é chamada de *Singleton*
- para criar uma classe Singleton, são necessários dois passos:
	1.  Ter um construtor privado.
	2. Criar um método estático que retorna um objeto da classe em questão instanciado. Conceito conhecido como Lazy initialization


```java
class Singleton{
	// variavel estatica que armazenara a nossa unicainstancia
	private static Singleton instancia = null;
	
	// variavel para teste
	public int numero;
	
	//construtor privado
	private Singleton(){
		numero =20;
	}

	// método estatico para criar a instancia
	public static Singleton getInstance(){
		if (instancia == null){
			instancia = new Singleton();
		}
		return instancia;
	}
}

class Principal{
	public static void main(String args[]){
		
		// instantiating Singleton class with variable x
		Singleton x = Singleton.getInstance();
		
		// instantiating Singleton class with variable y
		singleton y = Singleton.getInstance();
		
		// instantiating Singleton class with variable z
		singleton z = Singleton.getInstance();
		
		// changing variable of instance x
		X.numero+=10;
		
		System.out.println("x: " + x.numero);
		System.out.println("y: " + y.numero);
		System.out.println("z: " + z.numero);
		System.out.println("\n");
		// todos imprimem 30 
		
		Z.numero-=5;
	
		System.out.println("x: " + x.numero);
		System.out.println("y: " + y.numero);
		System.out.println("z: " + z.numero);				 		
		System.out.println("\n");
		//Todos imprimem 25
	}

}	



```
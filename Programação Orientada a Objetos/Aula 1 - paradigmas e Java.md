# PARADIGMAS DE PROGRAMAÇÃO

Chamamos de paradigma de programação um dos meios de classificar linguagens de
programação de acordo com sua estruturação, abstração e funcionalidades.

>[!info] Como você escreve/organiza seu código 



## PARADIGMAS IMPERATIVOS

O programador instrui a máquina **COMO** atingir o estado desejado
Ex.:
``` javascript
function double(arr) {
	let results = [];
	for (let i = 0; i < arr.length; i++) {
		results.push(arr[i] * 2);
	)
	return results;
}

```

### PARADIGMA PROCEDURAL

- Estabelece uma série sequencial de passos/tarefas a serem executados
- código é executado de cima para baixo 
- Ex.: C

```JavaScript
function signupHandler(event) {
	event.preventDefault();

	const userNameInput = document.getElementById('username');
	const enteredUsername = userNameInput.value;

	const passwordInput = document.getElementById('password');
	const enteredPasword = passwordInput.value;

	if (enteredUsername.trim().length === 0) {
		alert('Invalid input - username must not be empty!');
		return;
	}
	if (enteredPassword.trim().length <= 5){}
		alert('Invalid input - password must be six characters or longer.');
		return;
	}
	const user = {
		userName: enteredUsername,
		password: enteredPassword
	};

	console. log(user);
	console.log('Hi, I am ' + user.userName);

}

form.addEventListener( ‘submit’, signupHandler);

 


```


###  PARADIGMA ORIENTADO A OBJETOS
- Organiza os dados e lógica do programa em objetos (propriedades + métodos)
- Organiza o código em entidades lógicas (pensa na aplicação em termos do mundo real)
- Ex.: Java

```JS
class Validator {
	static REQUIRED = 'REQUIRED';
	static MIN_LENGTH = 'MIN_LENGTH';
	
	static validate(value, flag, validatorValue) {
		if (flag === this.REQUIRED) {
			return value.trim().length > 0;
		}
		if (flag this.MIN_LENGTH) {
			return value.trim().length > validatorValue;
		}
	}
}
 

class User {
	constructor (uName, uPassword) {
		this.userName = uName;
		this.password = uPassword;
	}
}

greet(){
	console.log('Hi, I am ' + this.userName);
}


class UserInputForm {
	constructor() {
		this. form = document.getElementById('user-input');
		this.userNameInput = document.getElementById( 'username');
		this.passwordInput = document.getElementById( 'password');

		this. form.addEventListener('submit', this.signupHandler.bind(this));
	}
	
	signupHandler (event) {
		event.preventDefault();
		const enteredUserName = this.userNameInput.value;
		const enteredPassword = this.passwordInput.value;
	}
		 if(
			!Validator.validate(enteredUserName, Validator.REQUIRED) ||
			!Validator.validate(enteredPassword, Validator.MIN_LENGTH, 5)
		){
			alert(
				'Invalid input - username or password is wrong (password should be at least six characters');
			return;
		}
		const newUser = new User(enteredUserName, enteredPassword);
		console. log(newUser) ;
		newUser.greet();

	}


}

new UserInputForm();

```


## PARADIGMAS DECLARATIVOS
os paradigmas declarativos que não focam em mudanças de estado sequencial de um programa, mas sim **NO QUE** se deve resolver
Ex.:

```JavaScript
function double(arr) {
	return arr.map( (item) => item * 2);
	}


```

>[!Nota]
>Many (if not all) declarative APIs have some sort of underlying imperative implementation
>https://www.youtube.com/watch?v=E7Fbf7R3x6I


### PARADIGMA FUNCIONAL
- Organiza o código em funções (puras) com tarefas claramente definidas
- Os dados são passados via parâmetros
- Ex: Scala

```JavaScript

const REQUIRED = 'REQUIRED';
const MIN_LENGTH = 'MIN_LENGTH';


function validate(value, flag, validatorValue) {
	if (flag === REQUIRED) {
	return value.trim().length > 0;
	}
	if (flag === MIN_LENGTH) {
		return value.trim().length > validatorValue;
	}
}


function getUserInput(inputElementId) {
	return document.getElementById(inputElementId).value;
}

function createUser(userName, userPassword) {
	if (!validate(userName, REQUIRED) || !validate(userPassword, MIN_LENGTH, 5)){
		throw new Error(
			"Invalid input - username or password is wrong (password should be at least six characters'
		};
	}
	return{
		userName: userName,
		password: userPassword
	};

}

function greetUser(user) {
	console.log('Hi, I am ' + user.userName);
}



function signupHandler (event) {
	event.preventDefault();
	
	const enteredUsername = getUserInput('username');
	const enteredPassword = getUserInput('password');

	try {
		const newUser = createUser(enteredUsername, enteredPassword);
		console.log(newUser);
		greetUser(newUser);
	}catch(err){
		alert(err.message);
	}

}

function connectForm(formId, formSubmitHandler) {
	const form = document.getElementById(formId);
	form.addEventListener('submit', formSubmitHandler);
}

connectForm('user-input', signupHandler);

```


### PARADIGMA LÓGICO
Linguagem de programação baseada na lógica formal. Utiliza fatos e cláusulas.

```prolog
/*** is Socrates mortal? ***/

// if human then mortal
mortal(X) :- human(X).

// define a relation
human(socrates).

// peform a query
?7- mortal(socrates).
LT

```


# HISTÓRICO POO

-  foi pela primeira vez aplicado de forma adaptada na linguagem de programação Simula 67, nos anos de 1960, posteriormente também sendo utilizado de forma exclusiva na linguagem Smalltalk da Xerox.
- Sua grande popularidade influenciou todas as principais linguagens de programação de hoje, C++, C#, PHP, Python e Java
- O pesquisador Alan Kay, que atuou na empresa Xerox, foi quem liderou o projeto que encabeçou as primeiras linguagens de programação baseadas em orientação a objetos, sendo inclusive responsável por cunhar o termo.

> O computador ideal deve funcionar como um organismo vivo, isso é, cada célula se relaciona com outras a fim de alcançar um objetivo, mas cada uma funciona de forma autônoma. As células poderiam também reagrupar-se para resolver um outro problema ou desempenhar outras funções
> 
> \- Alan Kay


# HISTÓRIA DO JAVA


- Surgiu nos anos 1990 na empresa Sun Microsystems
- Green Project/James Gosling - objetivo gerar tecnologias voltadas para conectividade de equipamentos domésticos
	- StarSeven
	- Buscava comunicação entre dispositivos em linguagem independente da plataforma
- Criada Linguagem Oak - interpretada por uma máquina virtual fornecida pela Sun 
- Mudou nome para Java em 1995
- Popularização com internet/applets
- Utilizado para conectar todo tipo de dispositivo móvel
- Utilizado na sonda Opportunity em 2004 
- Adotou Licença de software GPL v3 em 2006
- Sun adquirida pela Oracle em 2010
- Java 20 - 03/2023
- Múltiplas aplicações

# ORGANIZAÇÃO DO JAVA 

- 2 Etapas de funcionamento
	1. código de alto nível é compilador para *bytecode*
	2. bytecode é interpretado pela *Java Virtual Machine*
- Um mesmo bytecode pode ser executado em qualquer sistema que possua uma JVM
- *Hotspot* -  tecnologia que identifica trechos de código com muito processamento e executa uma compilação dos mesmos durante a execução do código - *Just in Time Compilation*
- *Java Runtime Environment* - JVM + bibliotecas padrão do Java
- *Java Development Kit* -JRE + conjunto de utilitários (como o compilador de bytecode)
- *Garbage Collection* - JVM regularmente libera memória alocada não utilizada 


# VERSÕES DO JAVA E IDE ECLIPSE

Uma das [[IDE|IDEs]] mais populares ara Java é o Eclipse.
O Java conta com três versões principais;

-  **Java ME** -  visa à construção de softwares para dispositivos embarcados, sistemas de propósito específico com poucos recursos computacionais. (IoT)
- **Java SE** -  edição padrão do Java com o principal conjunto de bibliotecas, perfeita para desenvolver programas desktop e de console.
- **Java EE** -  edição mais completa que já vem equipada com bibliotecas prontas para soluções empresariais, especialmente voltadas para internet e banco de dados.

## PRIMEIRO CÓDIGO

### PROJETO
O projeto engloba todas as classes e bibliotecas necessárias para a geração de um programa. Seus Principais elementos são:

-  **Bibliotecas:** são bytecodes com funcionalidades específicas implementadas (reaproveitamento de código)
- **Pacotes**: conceito semelhante ao de pasta/diretório para organizar a estrutura dos códigos. Usualmente, o pacote principal de um projeto é nomeado com o inverso do domínio da sua instituição
- **Classe**: os códigos são descritos em arquivos com extensão .java, geralmente um arquivo por classe.

![[Pasted image 20230419094448.png]]


```Java
public class Main {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.println("Hello World!");
	} 
}
```

```Output
Hello World!
```


# VISÃO GERAL SOBRE O CÓDIGO JAVA

## PRINCIPAIS COMANDOS

###  SAÍDA

```Java
System.out.print("msg1"); //Imprime uma mensagem
System.out.println("msg2"); //Imprime uma mensagem e pula linha.
System.out.print("msg3 %d", 10); //Imprime mensagens formatadas, %d será substituído pelo númeroi 10 
```

### ENTRADA
- Importar biblioteca java.util.Scanner logo abaixo da declaração do pacote
- Declarar variável (objeto) do tipo (classe) Scanner
- Ler os dados de alguma fonte passada por parâmetro
- `System.in` aponta a entrada padrão do sistema
- utilizar o objeto para chamar os métodos de leitura
	- `.next()` - para ler strings
	- `.nextInt()` - para ler valor inteiro
	- `.nextFloat()`
	- `.nextDouble()`

```Java
import java.util.Scanner;

public class Aula_1 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner teclado = new Scanner(System.in);
		System.out.println("Digite sua idade:");
		int idade = teclado.nextInt();
	
		}
}
```

### COMANDOS DE DESVIO

```Java
if(idade < 10) {
	System.out.println("Criança");
}
else if(idade < 18) {
	System.out.println("Adolescente");
}
else {
	System.out.println("Adulto");
}
```
The comparisons are executed top down. When execution reaches a conditional statement whose condition is true, its block is executed and the comparison stops.

*Switch case* avalia a expressão e desvia o código para o *case* pertinente ou default

```Java
switch(expressão){
	case constante1:
		//comandos primerio caso
		break;
	case cosntante2:
		//comandos segundo caso
		break;
	default:
		//caso padrão
}
```

### COMANDOS DE REPETIÇÃO

```Java
while(condição){
	//bloco de código
}

do{
	//bloco de código
}while(condição);

for (inicialização; expressão enquanto; iteração){
	//bloco de código 
}
```

`break` para sair do loop
`continue` para voltar ao começo do loop

## TIPOS DE DADOS 

### STRING
- Declarada com `String`
- escritas entre aspas duplas
- possuem diversos métodos internos

```Java
String msg = "mario";
msg = "super" + msg; //concatenação
int tamanho = msg.lenghth();
msg = msg.toUpperCase();
System.out.println(msg);
```

#### COMPARANDO STRINGS

Utiliza-se o método `equals`

```java
String texto = "curso";
String outroTexto = "cavalo";

if (texto.equals(outroTexto)) {
    System.out.println("Os textos são iguals");
} else {
    System.out.println("Os textos não sao iguais!");
}
```

#### DIVIDINDO STRINGS
Método `.split()` - o parâmetro determina onde será feita a divisão 

```java
String text = "first second third fourth";
String[] pieces = text.split(" ");
```

#### FORMATANDO VARIÁVEIS
```JAVA
int i = 461012;
System.out.format("The value of i is: %d%n", i);
```
%d para inteiros. %f para float

### ARRAYS

- Declarados entre chaves e acessados com colchetes indexados do 0

```Java
int[] numbers = new int[3]; //define tamanho
String[] nomes = {"Mario", "Luigi", "Peach", "Yoshi"}; //cria array e já atribui valores
nomes[0] = "Bowser"
```
- Possui diversos métodos como por exemplo `lenght()`

### LISTAS

#### CRIANDO UMA LISTA
```java
// import the list so the program can use it
import java.util.ArrayList;

public class Program {

    public static void main(String[] args) {
        // create a list
        ArrayList<String> list = new ArrayList<>();
    }
}
```

#### TIPO
A declaração dos tipos dos valores da lista deve ser declarado com maiúscula, pois tratam-se de variáveis do tipo referências

>[!Nota]
>**Variáveis Tipo Valor:** 
>Guardam o valor atribuído - *int, double, float, boolean*
>
>**Variáveis Tipo Referência:**
>Contém uma referência ao endereço do valor  - *String, ArrayLists* - são objetos

#### Métodos 

-   Adding to a list is done with the method `add` that receives the value to be added as a parameter.

```java
ArrayList<String> list = new ArrayList<>();
list.add("hello world!");
```

-   The number of elements in a list can be discovered with the non-parameterized method `size`; it returns an integer.

```java
ArrayList<String> list = new ArrayList<>();
int size = list.size();
System.out.println(size);
```

-   You can retrieve a value from a certain index with the method `get` that is given the index at which the value resides as a parameter.

```java
ArrayList<String> list = new ArrayList<>();
list.add("hello world!");
String string = list.get(0);
System.out.println(string);
```

-   Removing elements from a list is done with the help of `remove`. It receives as a parameter either the value that is to be removed, or the index of the value to be removed.

```java
ArrayList<String> list = new ArrayList<>();
// remove the string "hello world!"
list.remove("hello world!");
 // remove the value at index 3
list.remove(3);
```

-   Checking for the existence of a value is done with the method `contains`. It's provided the value being searched for as a parameter, and it returns a boolean value.

```java
ArrayList<String> list = new ArrayList<>();
boolean found = list.contains("hello world!");
```

#### For-Each Loop

```java
for (String teacher: teachers) {
    System.out.println(teacher);
}
```


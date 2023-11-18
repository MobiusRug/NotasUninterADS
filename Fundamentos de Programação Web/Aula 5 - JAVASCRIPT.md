
# VARIÁVEIS, TIPO DE DADOS E OPERADORES

## VARIÁVEIS

- Para declarar variáveis, podemos utilizar as palavras *var* ou *let*, e para constantes, *const*

```JAVASCRIPT
var altura;
altura = 1.7;

let peso;
peso = 70;
```

- o interpretador javascript é case sensitive
- o nome de variáveis não deve começar com números ou utilizar palavras reservadas 
- *let* tem escopo local

## Tipos de dados

### Literais primitivos
- *boolean, number, BigInt, string, symbol e undefined*
- operador *typeof* nos informa o tipo de dado
- *undefined*: é o valor-padrão que todas as variáveis possuem após uma declaração, se nenhum valor for atribuído a elas

```javascript
let ano = 2022;
console.log(typeof ano); // -> number
console.log(typeof 2023); // -> number
let nome = "Alice";
console.log(typeof nome); // -> string
console.log(typeof "João"); // -> string
```

- **interpolação de expressões** -  Com template string, é possível utilizar as substituições sintáticas e tornar o código mais legível

```javascript
let a=6;
let b=10;
console.log (`O resultado da operação é ${a+b} `);// O resultado da operação é 16
```

- oi utilizado o acento crase (\` \`)  para tornar possível visualizar o resultado da operação. O símbolo $ juntamente com { } permite imprimir variáveis, ou resultados de operações diretamente.

```javascript
let pais = "Brasil";
let continente = "América do Sul";
let frase = ` ${pais} se localiza na ${continente}.`;
console.log(frase);// Brasil se localiza na América do Sul.
```

- Todos os dados primitivos possuem objetos correspondentes nos quais podem ser convertidos automaticamente -  **autoboxing**, dessa forma seus métodos podem ser acionados

```javascript
let rio = "Amazonas";
let caracter = rio.charAt(2);
console.log(caracter); // -> a
```

#### Métodos String
- `length`: propriedade que informa o número de caracteres 
- `charAt(index)`: informa a posição “index” da string
- `slice(beginIndex, [opcional] endIndex)`
-  `split(separator, [opcional] limit)` - divide a string em componentes conforme separador, e retorna um array, o número de elementos do array pode ser limitado pelo "limit"

# OPERADORES E INTERAÇÃO

| Grupo       | Operador | Descrição                              |
| ----------- | -------- | -------------------------------------- |
| Atribuição  | =        | Atribuição simples                     |
|             | +=       | Atribuição de adição                   |
|             | -=       | Atribuição de subtração                |
|             | \*=      | Atribuição de multiplicação            |
|             | /=       | Atribuição de divisão                  |
|             | %=       | Atribuição de resto                    |
|             | \*\*=    | Atribuição de exponenciação            |
| Relacional  | ==       | Igual                                  |
|             | ===      | Exatamente igual (conteúdo e tipo)     |
|             | !=       | Diferente                              |
|             | !==      | Exatamente diferente (conteúdo e tipo) |
|             | <        | Menor                                  |
|             | <=       | Menor ou igual                         |
|             | >        | Maior                                  |
|             | >=       | Maior ou igual                         |
| Aritméticos | +        | Adição                                 |
|             | -        | Subtração                              |
|             | *        | Multiplicação                          |
|             | /        | Divisão                                |
|             | %        | Resto da divisão                       |
|             | **       | Exponenciação                          |
|             | ++       | Incremento                             |
|             | --       | Decremento                             |
| Lógicos     | &&       | E (AND)                                |
|             | \|       | OU (OR)                                |
|             | !        | NÃO (NOT)                              |
|             |          |                                        |

## INTERAÇÃO

### alert
 - O método `alert` exibe uma caixa de diálogo com uma mensagem e um botão "OK". É comumente usado para exibir informações importantes ou mensagens de aviso para o usuário.

```javascript
alert("Bem-vindo ao nosso site!");
```

### confirm
- O método `confirm` exibe uma caixa de diálogo com uma mensagem e dois botões: "OK" e "Cancelar". É utilizado para obter a confirmação do usuário em uma ação.

```javascript
var result = confirm("Você deseja realmente excluir este item?");
if (result) {
    // Código para excluir o item
} else {
    // Código para cancelar a exclusão
}
```

### prompt
- O método `prompt` exibe uma caixa de diálogo que permite ao usuário inserir um valor. Ele também pode incluir uma mensagem opcional.

```javascript
var nome = prompt("Por favor, digite o seu nome:");
if (nome !== null && nome !== "") {
    alert("Olá, " + nome + "! Bem-vindo ao nosso site.");
} else {
    alert("Você não inseriu um nome válido.");
}
```

# ESTRUTURAS DE CONTROLE DE FLUXO

### Condicional simples

```javascript
if(condição) {
//bloco de código a ser executado se a condição for verdadeira
}
```


### Condicional composta

```javascript
if (condição) {
//codigo - condição verdadeiro
} else {
//codigo - condicao falso
}
```

### Condicionais aninhadas

```javascript
if (condição_1) {
//codigo
} else if (condição_2) {
//codigo
} else if (condição_3) {
//codigo
} else {
//codigo
}
```

### Condicional de múltipla escolha (switch-case)

``` javascript
switch (//expressão) {
	case resultado 1:
		//código 1
		break;
	case resultado 2:
		//código 2
		break;
	default:
		//código
}
```

# LAÇOS DE REPETIÇÃO

### for

```javascript
for (inicialização; condição; incremento) {
//bloco de código (faça isso)
}
```

### while

```javascript
while(condição) {
//bloco de código
}
```

### do/while

```javascript
do {
//bloco de código
} while(condição);
```
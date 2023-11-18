# Objetos

- coleção de propriedades, onde cada propriedade consiste em um par de chave e valor.
- A chave é uma string que atua como identificador único da propriedade, e o valor pode ser qualquer tipo de dado, incluindo outros objetos.

```javascript
// Criando um objeto que representa uma pessoa
var pessoa = {
  nome: "João",
  idade: 30,
  profissao: "Engenheiro"
};

// Acessando as propriedades do objeto
console.log(pessoa.nome);      // Saída: "João"
console.log(pessoa.idade);     // Saída: 30
console.log(pessoa.profissao); // Saída: "Engenheiro"
```

- é possível adicionar ou modificar propriedades em um objeto após a sua criação:

```javascript
// Adicionando uma nova propriedade
pessoa.endereco = "123 Rua Principal";

// Modificando uma propriedade existente
pessoa.idade = 31;

console.log(pessoa.endereco); // Saída: "123 Rua Principal"
console.log(pessoa.idade);    // Saída: 31
```

- Objetos em JavaScript também podem conter funções, que são chamadas de "métodos"

```javascript
var carro = {
  marca: "Toyota",
  modelo: "Corolla",
  ligar: function() {
    console.log("O carro está ligado.");
  }
};

carro.ligar(); // Saída: "O carro está ligado."

```

## Acessando as propriedades

1. **Operador de ponto (`.`)**:

O operador de ponto é utilizado quando o nome da propriedade é uma identificação válida (ou seja, não contém caracteres especiais ou espaços) e é conhecido no momento da escrita do código.

```javascript
var pessoa = {
  nome: "João",
  idade: 30,
  profissao: "Engenheiro"
};

console.log(pessoa.nome);     // Saída: "João"
console.log(pessoa.idade);    // Saída: 30
console.log(pessoa.profissao); // Saída: "Engenheiro"

```


2. **Operador de colchetes (`[]`)**:

O operador de colchetes é utilizado quando o nome da propriedade contém caracteres especiais, espaços, é armazenado em uma variável ou é calculado dinamicamente em tempo de execução.

```javascript
var pessoa = {
  "nome completo": "Maria Silva",
  idade: 28
};

console.log(pessoa["nome completo"]); // Saída: "Maria Silva"

var propriedade = "idade";
console.log(pessoa[propriedade]);     // Saída: 28

```

- A sintaxe com colchetes também é útil quando você deseja acessar propriedades usando valores dinâmicos ou quando o nome da propriedade é gerado dinamicamente, como em loops:

```javascript
var pessoa = {
  nome: "Carlos",
  idade: 35
};

var propriedadeDesejada = "idade";
console.log(pessoa[propriedadeDesejada]); // Saída: 35

```

## Funções construtoras

- permitem criar múltiplas instâncias de objetos com a mesma estrutura e comportamento, evitando a repetição de código
- são usadas para criar objetos que compartilham características semelhantes, como propriedades e métodos.

1. **Definindo a Função Construtora:**

Uma função construtora é definida como qualquer outra função em JavaScript, mas geralmente começa com uma letra maiúscula para indicar que ela deve ser usada com o operador `new`. Dentro da função construtora, você pode definir as propriedades iniciais do objeto usando a palavra-chave `this`. Você também pode definir métodos dentro da função construtora, que serão compartilhados por todas as instâncias criadas.

```javascript
function Pessoa(nome, idade) {
  this.nome = nome;
  this.idade = idade;
  
  this.apresentar = function() {
    console.log(`Olá, eu sou ${this.nome} e tenho ${this.idade} anos.`);
  };
}

```

2. **Criando Instâncias:**

Para criar novos objetos usando a função construtora, você utiliza o operador `new` seguido pelo nome da função construtora:

```javascript
var pessoa1 = new Pessoa("Alice", 25);
var pessoa2 = new Pessoa("Bob", 30);

pessoa1.apresentar(); // Saída: "Olá, eu sou Alice e tenho 25 anos."
pessoa2.apresentar(); // Saída: "Olá, eu sou Bob e tenho 30 anos."

```

3. **Métodos Compartilhados:**

Uma característica importante das funções construtoras é que os métodos definidos dentro delas são compartilhados por todas as instâncias criadas. Isso significa que você não estará criando uma cópia do método para cada objeto, economizando memória.

```javascript
console.log(pessoa1.apresentar === pessoa2.apresentar); // Saída: true
```

## Iterando por um objeto - for in

- O loop `for...in` é uma forma conveniente de iterar pelas propriedades de um objeto. Ele percorre todas as propriedades enumeráveis do objeto e executa o bloco de código para cada propriedade.

```javascript
var pessoa = {
  nome: "João",
  idade: 30,
  profissao: "Engenheiro"
};

for (var prop in pessoa) {
  console.log(prop + ": " + pessoa[prop]);
}

```

# Arrays
- estrutura de dados que permite armazenar uma coleção ordenada de valores.
- indexados numericamente, começando em 0

1. **Criando um Array:**

Você pode criar um array de várias maneiras. A forma mais comum é usando colchetes `[]` e separando os elementos por vírgulas.

```javascript
var numeros = [1, 2, 3, 4, 5];
var nomes = ["Alice", "Bob", "Carol"];
var misturado = [10, "texto", true];
```

2. **Modificando Elementos:**

```javascript
numeros[2] = 99;
console.log(numeros); // Saída: [1, 2, 99, 4, 5]
```

3. **Propriedade length:**

A propriedade `length` de um array indica o número de elementos que ele contém.

```javascript
console.log(nomes.length); // Saída: 3
```

## Métodos de um array

**push() e pop():**

O método `push()` é usado para adicionar elementos ao final de um array, enquanto o método `pop()` remove o último elemento do array.

```javascript
var numeros = [1, 2, 3];

numeros.push(4);    // Adiciona 4 ao final do array
numeros.pop();      // Remove o último elemento (4)
```

**shift() e unshift():**

O método `shift()` remove o primeiro elemento de um array, e o método `unshift()` adiciona elementos ao início do array.

```javascript
var frutas = ["maçã", "banana", "laranja"];

frutas.shift();     // Remove "maçã"
frutas.unshift("manga"); // Adiciona "manga" no início do array
```

**indexOf():**

O método `indexOf()` retorna o índice da primeira ocorrência de um valor especificado no array. Se o valor não estiver presente, o método retorna -1.

```javascript
var numeros = [10, 20, 30, 40, 50];

var indice = numeros.indexOf(30); // Retorna 2
```

**slice():**

O método `slice()` cria uma cópia superficial (shallow copy) de parte de um array e a retorna como um novo array. Você pode especificar os índices de início e fim para definir a parte do array que deseja copiar.

```javascript
var numeros1 = [1, 2, 3];
var numeros2 = [4, 5, 6];

var numerosCombinados = numeros1.concat(numeros2); // Retorna [1, 2, 3, 4, 5, 6]
```

**forEach():**

O método `forEach()` executa uma função para cada elemento do array, permitindo percorrer todos os elementos de forma conveniente.

```javascript
var frutas = ["maçã", "banana", "laranja"];

frutas.forEach(function(fruta) {
  console.log(fruta); // Itera pelos elementos do array
});
```

## Iterando com o for of

```javascript
for (variavel of iteravel) {
  // Bloco de código a ser executado para cada elemento
}
```

A cada iteração do loop, a variável declarada irá receber o valor do próximo elemento da estrutura iterável, e o bloco de código dentro do loop será executado com esse valor. O loop continuará iterando até que todos os elementos da estrutura iterável tenham sido percorridos.

```javascript
var numeros = [1, 2, 3, 4, 5];

for (var numero of numeros) {
  console.log(numero);
}
```

- Se você precisar acessar os índices, pode usar o método `entries()` antes do loop:

```javascript
var frutas = ["maçã", "banana", "laranja"];

for (var [indice, fruta] of frutas.entries()) {
  console.log(`Índice ${indice}: ${fruta}`);
}
```

# FUNCOES

- bloco de código nomeado que pode ser definido uma vez e executado várias vezes

```JAVASCRIPT
function nome([param[, param[, ... param]]]) {
	instruções
}
```

**Retorno de Valores:**

Uma função pode retornar um valor usando a palavra-chave `return`. Isso permite que a função produza um resultado que pode ser usado posteriormente.

```javascript
function soma(a, b) {
  return a + b;
}

var resultado = soma(3, 5); // Atribui 8 à variável resultado

```

**Escopo de Função:**

As variáveis declaradas dentro de uma função têm escopo local, o que significa que elas só são visíveis e acessíveis dentro da própria função.

```javascript
function exemplo() {
  var mensagem = "Isso é uma mensagem";
  console.log(mensagem); // Acesso válido
}

console.log(mensagem); // Erro, mensagem não definida
```

**Recursividade**

```javascript
function fatorial (n) {
	return n > 1 ? n * fatorial(n - 1) : 1;
}

console.log(fatorial(6)); // -> 720
```

**Funções Anônimas:**

Uma função pode ser definida sem um nome e é chamada de função anônima. Elas são frequentemente usadas como argumentos para outras funções ou atribuídas a variáveis.

```javascript
var saudacao = function(nome) {
  console.log("Olá, " + nome + "!");
};

saudacao("Bob"); // Chama a função anônima
```


**Arrow Functions (Funções Seta):**
permitem escrever funções de forma mais concisa

```javascript
let somar=(n1,n2) =>n1+n2;
console.log(somar(2,3)); //5 (5 será o resultado)
```

## Date()

- construtor de datas e horários
- Datas e horários são extraídos do sistema operacional do usuário
- objeto `Date` pode ser usado para criar instâncias que representam momentos específicos no tempo, permitindo realizar operações relacionadas a datas e horas.

**`new Date()` - Criando uma instância de data:**

Você pode criar uma nova instância do objeto `Date` para representar o momento atual ou um momento específico passando argumentos (opcionalmente) como ano, mês, dia, hora, minuto, segundo e milissegundo.

```javascript
const momentoAtual = new Date(); // Cria uma instância representando o momento atual
const dataEspecifica = new Date(2023, 7, 18, 12, 0, 0); // 18 de agosto de 2023, 12:00:00
```

**`getFullYear()`, `getMonth()`, `getDate()`, `getHours()`, etc.:**

Esses métodos permitem obter os componentes individuais da data, como ano, mês, dia, hora, etc.

``` javascript
const hoje = new Date();
const ano = hoje.getFullYear();
const mes = hoje.getMonth(); // Janeiro é 0, Fevereiro é 1, ...
const dia = hoje.getDate();//dia do mês 1 a 31
const diaSemana = hoje.getDay(); //dia da semana 0-7
const horas = hoje.getHours();//0-23
```

**`getTime()`, `valueOf()`:**

Esses métodos retornam o valor numérico correspondente ao número de milissegundos desde a meia-noite de 1º de janeiro de 1970 (UTC), conhecido como "timestamp".

```javascript
const agora = new Date();
const timestamp = agora.getTime(); // Número de milissegundos desde 1970
```

## setInterval() e setTimeout()

- `setTimeout()` - Método chama uma função após um determinado tempo (em milissegundos). O método é executado apenas uma vez

```javascript
setTimeout(funcao, tempo);
```

- `setInterval()` - Método chama uma função em intervalos determinados em milissegundos.  Para interromper é necessário chamar clearInterval() ou fechar a janela.

```javascript
setInterval(function, milliseconds);
```

# BOM (BROWSER OBJECT MODEL)

- O Browser Object Model (BOM) é um conjunto de objetos que permitem a interação entre JavaScript e o navegador. Ele fornece acesso às características do navegador, como janelas, histórico, cookies e muito mais.

## Objeto Window

- O objeto de nível mais elevado do BOM 
- Representa uma janela aberta do navegador. 

### Closed
- A propriedade closed retorna o valor boleano *true* se a janela estiver fechada e *false* se estiver aberta

```html
<html>
	<head>
		<script>
			var janelaAberta = window.open('','','width=400,height=200');
			// na linha acima criamos uma janela com a propriedade open.
			function testarJanela() {
				if (janelaAberta.closed) { // se a janela estiver fechada
					alert('A janela foi fechada');
				} else {
					alert('A janela está aberta');
				};
			}
		</script>
	</head>
	<body>
		<button type="button" onclick="testarJanela()">Testar janela</button>
		<!--no evento onclick chamamos a função “testarJanela()”-->
	</body>
</html>
```

### Document

- A propriedade document é uma referência ao objeto document que representa a marcação HTML de um documento apresentado na janela do navegador. É possível acessar todos os elementos da marcação via script.

### History
-  O objeto history contém as URLs visitadas pelo usuário (na janela do navegador).
- Sintaxe:
	- `let length = window.history.método;`
	- `let length = history.método;`,

- **`back()` e `forward()`:**

O método `back()` é usado para navegar para a página anterior no histórico, simbolizando o botão "Voltar" do navegador. O método `forward()` é usado para navegar para a próxima página no histórico, simbolizando o botão "Avançar" do navegador.

```javascript
history.back();    // Equivalente a clicar no botão "Voltar"
history.forward(); // Equivalente a clicar no botão "Avançar"
```

- O método `go()` permite navegar para páginas específicas no histórico. Você pode passar um número negativo como argumento para voltar nas páginas visitadas e um número positivo para avançar.

```javascript
history.go(-2); // Voltar duas páginas no histórico
history.go(3);  // Avançar três páginas no histórico
```

### Open()

- O método `open()` abre uma nova janela
-  `window.open(URL, name, specs, replace)`

```html
<html>
	<head>
		<script> // abaixo vamos criar a função abreJanela()
			function abreJanela() {
				novaJanela=window.open('https://google.com','_blank','width=400, height=400'); 
				// passamos os parâmetros, URL do Google, _blank (abrir nova janela),e width (largura) e height (altura).
			}
		</script>
	</head>
	<body>
		<button onclick="abreJanela()">Abrir Janela</button>
		<!-- Chamamos a função abreJanela() no evento onclik do botão -->
	</body>
</html>
```

### Close()
- O método `close()` fecha uma janela.

```html
<html>
	<head>
		<script> // abaixo vamos criar a função abreJanela()
			function abreJanela() {
				novaJanela=window.open('https://google.com','_blank','width=400, height=400'); 
				// passamos os parâmetros, URL do Google, _blank (abrir nova janela),e width (largura) e height (altura).
			}
			function fechaJanela(){ // Criamos a função fecha janela.
				novaJanela.close();
			}
		</script>
	</head>
	<body>
		<button onclick="abreJanela()">Abrir Janela</button>
		<!-- Chamamos a função abreJanela() no evento onclik do botão -->
		<button onclick="fechaJanela()">Fechar Janela</button>
		<!--chamamos a função fechaJanela()-->
	</body>
</html>
```

### Oload()
- O evento `onload()` ocorre quando uma página termina de ser carregada. Exemplo:

```html
<html>
	<head>
		<script>
			window.onload = function() {
					document.forms[0].elements[0].value = 'Anna';
					document.forms[0].elements[1].value = 'Silva';
				}
		</script>
	</head>
	<body>
		<form action="" method="get">
		<input type="text" />
		<input type="text" />
		</form>
	</body>
</html>
```

# DOM - Document Object Model

-  interface independente de plataforma e linguagem que permite aos programas e scripts acessar e atualizar dinamicamente a estrutura, o conteúdo e a estilização de documentos
- representação da estrutura do documento HTML em formato de árvore

## Objeto Document

- quando abrimos um documento HTML em um navegador, é criado um objeto documento que representa a página aberta no navegador 

## getElement*
- O método `getElementById()` acessa o elemento DOM identificado pelo **id**.

```html
<html>
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
		<script>//Se utili
			window.onload = function() {
				var Um = document.getElementById("def");//Aqui selecionamos o id "def"
				var Dois = document.getElementById("tipo");//Aqui selecionamos o id "tipo"
				Um.style.backgroundColor="#0cc";//Aqui atribuímos uma cor de fundo
				Dois.style.border="2px solid #0000ff";//Aqui atribuímos uma borda
			}
		 </script>
	</head>
	<body>
		<h2>Introdução</h2>
		<p>Lorem ipsum </p>
		<h2 id="def">Definição</h2> <!--Aqui colocamos o id="def"-->
		<p>Lorem ipsum?</p>
		<h2 id="tipo">DOM</h2> <!--Aqui colocamos o id="tipo"-->
		<ul>
			<li>DOM para HTML</li>
			<li>DOM para XML</li>
		</ul>
	</body>
</html>
```

-  `getElemenstByClassName()` retorna uma lista com todos os elementos que possuem o nome da classe dada.

```javascript
 let lista = document.getElementsByClassName(“item”)
```

- `getElementsByTagName` retorna uma lista com todos os elementos da tag informada.

```javascript
let lista = document.getElementsByTagName(“p”)
```

## element.style

- A propriedade `style` dos elementos do DOM permite que se definam regras de estilo. Sintaxe: `el.style.propriedade=”valor da propriedade”`
- Em javaScript, as propriedades CSS devem ser escritas em camelCase

| CSS              | Javascript      |
| ---------------- | --------------- |
| background-color | backGroundColor |
| z-index          | zindex          |
| text-indent      | textIndent      |
| padding-left     | paddingLeft     |

## querySelector(seletor)

- O método querySelector() permite acessar o primeiro elemento correspondente ao seletor informado. O seletor pode ser uma tag, um id ou uma classe.

```javascript
let tituloh1=document.querySelector(“h1”).
```

## querySelectorAll(seletor)

- Permite acessar todos os elementos que correspondem ao seletor

```javascript
document.querySelectorAll("p");
```

## TextContent
- Permite acessar o texto digitado entre as tags

```javascript
let textoP = document.querySelector("p").textContent;
console.log(textoP);
```

- Também permite alterar o conteúdo da tag

```javascript
document.querySelector("p").textContent="Vamos ler também";
```

## innerHTML

- Permite adicionar HTML dentro do HTML.

```JAVASCRIPT
let paragrafo = document.querySelector(“p”);
paragrafo.innerHTML="<strong>Olá MUNDO!!!!!!!!!!!!!!!!!!!!!</strong>”;
```

# EVENTOS

- Os eventos podem ocorrer advindos da interação do usuário com um elemento HTML.

| Evento     | Descrição                                          |
|------------|----------------------------------------------------|
| click      | Ocorre quando o usuário pressiona o botão esquerdo do mouse.            |
| dclick     | Ocorre quando o usuário pressiona duas vezes o botão esquerdo do mouse. |
| mousedown  | Ocorre quando o usuário pressiona qualquer um dos botões do mouse.     |
| mouseover  | Ocorre quando o usuário solta qualquer um dos botões do mouse.         |
| mouseout   | Ocorre quando o usuário desloca o ponteiro do mouse de onde estava.    |
| mousemove  | Ocorre quando o usuário move o ponteiro do mouse.                      |
| load       | Ocorre quando há o carregamento da página.                             |
| unload     | Ocorre quando há o fechamento de uma janela.                           |
| scroll     | Ocorre quando o elemento possui barra de rolagem.                      |
| focus      | Ocorre quando o elemento recebe foco.                                  |

## eventListener

- recurso que permite que você monitore e responda a eventos que ocorrem em elementos HTML ou no ambiente do navegador
- A ideia principal por trás do `EventListener` é associar uma função (também chamada de "callback" ou "handler") a um evento específico de um elemento. Quando o evento ocorre, a função associada é executada. Isso permite que você responda a ações do usuário ou a outras mudanças no ambiente do navegador.
- Em JavaScript, o método `addEventListener()` possui três parâmetros:

1. **Tipo de Evento:** Este é o primeiro parâmetro e representa o tipo de evento que você deseja ouvir, como "click", "mouseover", "keydown", etc.
    
2. **Função de Resposta:** O segundo parâmetro é a função que será chamada quando o evento ocorrer. Esta função conterá o código que você deseja executar em resposta ao evento.
    
3. **useCapture (opcional):** O terceiro parâmetro é um valor booleano opcional que indica se o evento deve ser capturado durante a fase de captura ou de propagação. Se for definido como `true`, o evento será capturado na fase de captura (de fora para dentro), e se for definido como `false` (ou omitido), o evento será capturado na fase de propagação (de dentro para fora).

```javascript
// Seleciona o elemento do botão
const botao = document.querySelector("#meuBotao");

// Cria uma função de resposta para o evento de clique
function handleClick() {
  alert("Botão clicado!");
}

// Adiciona o EventListener para o evento de clique
// O terceiro parâmetro useCapture é omitido (ou definido como false)
botao.addEventListener("click", handleClick, false);
```

# localStorage

- O `localStorage` é um recurso oferecido pelo JavaScript que permite que você armazene dados de forma persistente no navegador da web.
- Ele é uma parte da API de Armazenamento da Web, que inclui outras funcionalidades como `sessionStorage` e `IndexedDB`. O `localStorage`
- é usado principalmente para armazenar dados no formato de pares chave-valor e é bastante útil para armazenar informações localmente no navegador, mesmo depois que a página é recarregada ou fechada.

1. **Armazenamento Persistente:** Os dados armazenados no `localStorage` permanecem no navegador mesmo após o navegador ser fechado ou a página ser recarregada. Isso o torna adequado para armazenar configurações, preferências do usuário, histórico, carrinhos de compras e outras informações que precisam ser mantidas entre sessões.
    
2. **Formato Chave-Valor:** O `localStorage` armazena dados no formato de pares chave-valor, onde você atribui um valor a uma chave. A chave é uma string única que identifica o valor. Ambos a chave e o valor são armazenados como strings.
    
3. **Limite de Armazenamento:** Cada domínio e protocolo tem um limite de armazenamento no `localStorage`. Esse limite é geralmente em torno de 5-10 MB, mas pode variar dependendo do navegador. Quando você excede esse limite, novos dados não podem ser armazenados no `localStorage`.
    
4. **Acesso Síncrono:** As operações no `localStorage` são síncronas, o que significa que o código é executado em sequência. Isso pode afetar a velocidade da execução do seu código, especialmente se você estiver armazenando ou recuperando muitos dados.
    
5. **Escopo de Domínio:** O `localStorage` é compartilhado entre todas as páginas do mesmo domínio. Isso significa que se você armazenar dados em uma página, poderá acessá-los em outras páginas do mesmo domínio.

```javascript
// Armazenar um valor no localStorage
localStorage.setItem("username", "joao");

// Recuperar um valor do localStorage
const username = localStorage.getItem("username");
console.log(username); // Saída: "joao"

// Remover um item do localStorage
localStorage.removeItem("username");
```
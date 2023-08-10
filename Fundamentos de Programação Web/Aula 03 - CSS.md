# ÁRVORE DO DOCUMENTO - DOM

- é uma representação em árvore da estrutura e conteúdo de uma página da web, permitindo manipulação dinâmica via JavaScript.

![[Pasted image 20230807091612.png]]

## COMBINADORES CSS

-  são parte do CSS e permitem selecionar elementos HTML com base em sua relação hierárquica com outros elementos.
- Eles especificam como os elementos devem estar relacionados dentro da estrutura do documento para serem estilizados de maneira específica. Existem quatro tipos principais de seletores por grau de parentesco:

1. **Descendente (espaço)** - O seletor descendente seleciona elementos que estão dentro de um elemento específico.

```css
div p {
  color: blue;
}
```

Isso aplicará a cor azul a todos os elementos `<p>` que estão dentro de um elemento `<div>`.

2. **Filho direto (>)** - O seletor de filho direto seleciona elementos que são filhos diretos de um elemento específico.

```css
ul > li {
  list-style-type: square;
}
```

Nesse exemplo, apenas os elementos `<li>` que são filhos diretos de uma lista não ordenada `<ul>` terão marcadores de lista quadrados.

3. **Irmão adjacente (+)** - O seletor de irmão adjacente seleciona o elemento imediatamente após outro elemento dentro do mesmo nível hierárquico.

```css
h2 + p {
  font-weight: bold;
}
```

Isso aplicará negrito a todos os elementos `<p>` que são irmãos adjacentes de um elemento `<h2>`.

4. **Irmãos gerais (~)** - O seletor de irmãos gerais seleciona elementos que estão no mesmo nível hierárquico após um elemento específico, não necessariamente imediatamente após.

```css
p ~ span {
  color: red;
}
```

Nesse exemplo, todos os elementos `<span>` que são irmãos gerais de um elemento `<p>` receberão a cor vermelha.


# PSEUDOCLASSES E PSEUDOELEMENTOS 

## PSEUDOCLASSES
- seletores que permitem aplicar estilos a elementos em estados específicos ou com características especiais que não podem ser alcançadas apenas com seletores de elementos.
- sintaxe - `:pseudoclasse`

1. **:link** -  é usada para estilizar links não visitados. Ela se aplica a elementos âncora `<a>` antes de serem visitados.

```css
a:link {   
color: blue;   
text-decoration: underline;
}
```

2. **:visited** - é usada para estilizar links já visitados. Ela se aplica a elementos âncora `<a>` após terem sido visitados.

```css
a:visited {color: purple; }
```

3. **:hover** - é usada para aplicar estilos quando o cursor do mouse está sobre um elemento.

```css
button:hover {   background-color: lightgray; }
```

4. **:active** -  é usada para estilizar elementos durante o momento em que estão sendo clicados ou pressionados (quando estão ativos).

```css
button:active {   background-color: darkgray; }
```

5. **:focus** -  é usada para estilizar o estado de foco em um elemento, geralmente quando ele é selecionado via teclado ou outro dispositivo de entrada.

```css
input:focus {
  border-color: blue;
  box-shadow: 0 0 5px rgba(0, 0, 255, 0.5);
}
```

6. **:checked** - Essa pseudoclasse é usada para selecionar elementos de entrada, como caixas de seleção (`<input type="checkbox">`) e botões de rádio (`<input type="radio">`), que estão marcados.

```css
input[type="checkbox"]:checked + label {
  font-weight: bold;
}
```

Neste exemplo, quando uma caixa de seleção é marcada, o texto da label associada ficará em negrito.

7. **:enabled** e **:disabled** -são usadas para selecionar elementos de entrada que estão habilitados ou desabilitados, respectivamente.

```css
input:enabled {
  background-color: white;
}

input:disabled {
  background-color: lightgray;
}
```

8. :first-child
9. last-child
10. nth-child(n)

Nesse exemplo, os campos de entrada habilitados terão um fundo branco, enquanto os campos desabilitados terão um fundo cinza claro.
- é uma boa prática definir as pseudoclasses de link na seguinte ordem: `:link`, `:visited`, `:hover`, `:active`.

## PSEUDOELEMENTOS

- são seletores que permitem estilizar partes específicas de um elemento, em vez de todo o elemento em si. 
- Eles são representados por dois "::" seguidos do nome do pseudoelemento.
- Pseudoelementos são usados para adicionar elementos fictícios ao DOM ou para estilizar partes específicas de um elemento que não podem ser alcançadas apenas com CSS tradicional.

1. **::before** -  insere conteúdo antes do conteúdo do elemento selecionado. É frequentemente usado para adicionar ícones ou decorações a elementos.

```css
blockquote::before {
  content: "“";
}
```

Nesse exemplo, um marcador de citação é adicionado antes de cada bloco de citação.

2. **::after** - Similar ao "::before", este pseudoelemento insere conteúdo depois do conteúdo do elemento selecionado.

```css
a::after {
  content: " →";
}
```

Aqui, uma seta é adicionada após cada link.

3. **::first-line** - Este pseudoelemento seleciona a primeira linha de texto dentro de um elemento.

```css
p::first-line {
  font-weight: bold;
}
```

Isso torna a primeira linha de todos os parágrafos em negrito.

4. **::selection** - Este pseudoelemento permite estilizar o texto selecionado pelo usuário.

```css
::selection {
  background-color: yellow;
  color: black;
}
```

Quando o usuário seleciona texto, o fundo fica amarelo e o texto fica preto.

Claro, vou adicionar as explicações e exemplos para os pseudoelementos `::first-letter` e `::marker`:

5. **::first-letter** - Este pseudoelemento seleciona a primeira letra de um bloco de texto dentro de um elemento. É frequentemente usado para estilizar a letra inicial de um parágrafo ou uma seção de texto.

```css
p::first-letter {
  font-size: 2em;
  color: red;
}
```

Nesse exemplo, a primeira letra de cada parágrafo será ampliada e terá uma cor vermelha.

6. **::marker** - Este pseudoelemento é usado para estilizar o marcador de lista de elementos `<li>` em listas ordenadas ou não ordenadas.

```css
li::marker {
  content: "→ ";
  color: blue;
}
```

Nesse caso, todos os marcadores de lista terão uma seta azul (→) antes do texto.

# BARRA DE NAVEGAÇÃO 

## Barra de Navegação Vertical

- Criando o menu

```html
<ul>
<li><a href="index.html">Home</a></li>
<li><a href="noticias.html">Notícias</a></li>
<li><a href="contato.html">Contato</a></li>
</ul>
```

![[Pasted image 20230807100128.png]]





- remove o marcador:list-style- type: none;
- zeram as margens e os enchimento do browser
- Cor de fundo: background- color: f1f1f1;

```css
    <style>
         ul {
            list-style-type: none;
            margin: 0;
            padding: 0;
            width: 200px;
            background-color: #f1f1f1;
        }
    </style>
```

![[Pasted image 20230807100350.png]]

```css
        li a {
            display: block; /*Exibe os links como elementos de bloco e torna toda a área do link clicável*/
            color: #000;
            padding: 8px 16px;
            text-decoration: none;  /*Retirar o sublinhado*/
        }
```

![[Pasted image 20230807100619.png]]


```css
        li a:hover{
            background-color:#555;
            color: white;
        }
```



![[Pasted image 20230807100909.png]]

## Barra de Navegação Horizontal

- Para a barra de navegação horizontal, podemos utilizar a propriedade display ou float.
```css
li{display:inline;}

a {
	color: #000;
	padding: 8px 16px;
	text- decoration: none;
}
```

ou 

```css
        li{
            float: left;
        }

        li a{
            color: black;
            display:block;
            text-align: center;
            padding: 14px 16px;
            text-decoration: none;
        }
```

![[Pasted image 20230807102100.png]]

## Menu vertical com menu suspenso

- Aqui estamos inserindo uma lista dentro de outra para gerar o submenu

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <ul>
        <li><a href="index.html">Home</a> <!--aqui não fechamos o li -->
            <ul>
                <li><a href="#news">Sobre nós</a></li>
                <li><a href="#contato">Nossas Lojas</a></li>
            </ul>
        </li>
        <li><a href="noticias.html">Notícias</a></li>
        <li><a href="contato.html">Contato</a></li>
    </ul>
</body>
</html>
```

![[Pasted image 20230808082118.png]]

- Removendo Bullets e Identação das Listas
```css
        ul{
            margin: 0;
            padding: 0;
            list-style-type: none;
            width: 150px;
        }
```


![[Pasted image 20230808082338.png]]

- Agora vamos posicionar os itens da lista, definir o posicionamento com o valor relativo, porque depois iremos posicionar os submenus na posição absoluta em relação a eles.

```css
        ul li{
            position: relative;
        }
```

- Agora vamos estilizar os submenus. Queremos cada submenu ao lado direito do seu elemento-pai assim que passarmos o mouse sobre ele. Com as propriedades CSS Left e Top, podemos posicionar cada item do submenu ao lado de seu item-pai. Definimos o display: none, para que o submenu não fique visível por padrão, e o display:block para aparecer quando passarmos o mouse

```css
		li ul{
            position: absolute;
            left: 149px;
            top: 0;
            display: none;
        }

        ul li:hover ul {
            display: block;
	        }
```

![[Pasted image 20230808084706.png]]

Aplicando decorações 

```css
        ul li a{
            display: block;
            text-decoration: none;
            color: #E2144A;
            background: #fff;
            padding: 5px;
            border: 1px solid #ccc;
        }

        ul li a:hover{
            text-decoration: underline;
            font-weight: bold;
            background: #ccc;
        }
```

![[Pasted image 20230808085434.png]]

## Botões CSS

- Podemos inserir botões de três maneiras: utilizando o `<button>`, link e `<input type=”button”>`

```html
    <button>Botão Padrão</button>
    <a href="#" class = "button">Link como botão</a>
    <button class="button">Botão</button>
    <input type="button" class = "button" value = "Enviar">
```

# OUTRAS FORMATAÇÕES 


## Dimensionamento do box model

a largura e a altura de um elemento são calculadas assim:

- largura + preenchimento + borda = largura real de um elemento
- altura + preenchimento + borda = altura real de um elemento

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        .div1{
            width: 400px;
            height: 200px;
            border: 1px solid red;
        }

        .div2{
            width: 400px;
            height: 200px;
            padding: 30px;
            border: 1px solid blue;
        }
    </style>
</head>
<body>
    <div class="div1"></div>
    <br>
    <br>
    <div class="div2"></div>
</body>
</html>
```

![[Pasted image 20230808091054.png]]


- A propriedade box-sizing permite incluir os valores da borda e preenchimento no valor total da div. Para que isso ocorra, devemos definir box-
sizing: border-box

```css
        .div1{
            width: 400px;
            height: 200px;
            border: 1px solid red;
            box-sizing: border-box;
        }

        .div2{
            width: 400px;
            height: 200px;
            padding: 30px;
            border: 1px solid blue;
            box-sizing: border-box;
        }
```


![[Pasted image 20230808091248.png]]


- É aconselhável utilizar a propriedade em todos os elementos da página.

```css
* {
box-sizing: border-box;
}
```

## VARIÁVEIS

- Podemos utilizar variáveis com CSS, com a função var(). É possível utilizar variáveis para definir as cores, evitando a repetição de códigos.
- Para declarar uma variável global, utiliza-se o seletor :root. Para declarar uma variável com escopo local, declare-a dentro do seletor que irá utilizá-la.

```CSS

:root{
	--dourado: #DEB44B;
	--branco: #ffffff;
}

body{
	background-color: var(--dourado);
}
```

## FORMATAÇÕES PARA IMAGENS

- Arredondamento dos cantos

```css
img {
	border-radius: 10px;
}
```

- Imagem circular ou oval:

```css
img{
	border-radius:50%;
}
```

- nível de opacidade

```css
img{
	opacity: 0.5;
}
```

- centralizar

```css
img{
	display: block;
	margin: auto;
}
```

- o redimensionamento é feito com os atributos `height` e `width`

# MOVIMENTOS EM CSS

 ## TRANSLATE
- The **translate(X,Y)** method translates (or moves) a page element up, down, left, and/or right on the page by a specified amount

```CSS
div {
  width: 150px;
  height: 150px;
  line-height: 150px;
  border-radius: 20px;
  position: absolute;
  color: #FFFFFF;
  font-family: Arial;
  text-align: center;
}

#div-1 {
  background-color: #213343;
}

#div-2 {
  transform: translate(100px, 75px);
  background-color: #FF5C35;
  opacity: 0.8;
}
```

![[Pasted image 20230808094127.png]]

- Using negative numbers with the **translate()** method will move the element left or up
- You can also use percentages to specify the translation. Percentages move the element a horizontal distance proportional to its width, or a vertical distance proportional to its height.

```CSS
div {
  width: 150px;
  height: 150px;
  line-height: 150px;
  border-radius: 20px;
  position: absolute;
  color: #FFFFFF;
  font-family: Arial;
  text-align: center;
}

#div-1 {
  background-color: #213343;
}

#div-2 {
  transform: translate(100%, 50%);
  background-color: #FF5C35;
  opacity: 0.8;
}
```

![[Pasted image 20230808094245.png]]


In addition to **translate()**, we can also use the **translateX()** and **translateY()** methods. **translateX()** moves an element only horizontally, and takes one argument. the **translateY()** method moves an element vertically


## SCALE

- The **scale()** transform method changes the size of the target element.
- If we provide one argument with **scale()**, we increase or decrease the size of the element by a multiple of its original size.

```CSS
div {
  width: 150px;
  height: 150px;
  line-height: 150px;
  border-radius: 20px;
  position: absolute;
  color: #FFFFFF;
  font-family: Arial;
  text-align: center;
  top: 100px;
  left: 100px;
}

#div-1 {
  background-color: #213343;
}

#div-2 {
  transform: scale(2);
  background-color: #FF5C35;
  opacity: 0.8;
}
```

![[Pasted image 20230808094428.png]]


- If we give two arguments to **scale()** (separated by a comma), the first argument specifies the horizontal scaling and the second specifies the vertical scalinG

```CSS
div {
  width: 150px;
  height: 150px;
  line-height: 150px;
  border-radius: 20px;
  position: absolute;
  color: #FFFFFF;
  font-family: Arial;
  text-align: center;
  top: 50px;
  left: 175px;
}

#div-1 {
  background-color: #213343;
}

#div-2 {
  transform: scale(3, 1.5);
  background-color: #FF5C35;
  opacity: 0.8;
}
```

![[Pasted image 20230808094527.png]]

- We can also use the **scaleX()** and **scaleY()** methods

## Rotate

- rotates a page element. By default, the element will rotate around its center.
- We can specify the rotation in terms of degrees, radians, or turns

```css
#transformed-1 { transform: rotate(45deg); }

#transformed-2 { transform: rotate(1.2rad); }

#transformed-3 { transform: rotate(0.25turn); }

.group {
  display: inline-block;
  width: 200px;
  height: 150px;
}

.original, .transformed {
  width: 150px;
  height: 150px;
  border-radius: 20px;
  color: #FFFFFF;
  font-family: Arial;
  text-align: center;
  background-color: green;
  position: absolute;
}

div {
  line-height: 150px;
}

.original { background-color: #213343; }

.transformed {
  background-color: #FF5C35;
  opacity: 0.8;
}

#container {
  top: 25px;
  left: 25px;
  position: absolute;
}
```

![[Pasted image 20230808094658.png]]

- We can also change the point of rotation with the [transform-origin property](https://blog.hubspot.com/website/css-transform#transform-origin),

## SKEW

- The **skew()** method skews, or slants, an element along its X and/or Y axes
- ts arguments specify the horizontal and vertical angle of the skew

```CSS
div {
  width: 150px;
  height: 150px;
  line-height: 150px;
  border-radius: 20px;
  position: absolute;
  color: #FFFFFF;
  font-family: Arial;
  text-align: center;
  top: 50px;
  left: 100px;
}

#div-1 {
  background-color: #213343;
}

#div-2 {
  transform: skew(50deg, -15deg);
  background-color: #FF5C35;
  opacity: 0.8;
}
```

![[Pasted image 20230808094846.png]]

There's also **skewX()** and **skewY()**

## MATRIX

- Combina todos os métodos de transformação 2D

matrix (scaleX(), skewY(), skewX(), scaleY(), translateX(), translateY())

## TRANSIÇÕES 

- Permite criar transições ao definir uma mudança de valor de uma propriedade CSS, de modo que ela (a mudança de valor) ocorra de forma suave, em um espaço de tempo especificado

- ``transition`` -  no exemplo a transição será aplicada na largura e levará 2 segundos

```css
div {
width: 100px;
height: 100px;
background: blue;
transition: width 2s;
}

div:hover {
width: 300px;
}

```

- `transition delay` - permite especificar um atraso para o efeito da transição

```css
div {
transition-delay: 1s;
}
```

- ``transition-timing-function`` -  A propriedade de função de tempo de transição pode ter os seguintes valores:

- *ease*- início lento, depois rápido, depois termina lentamente (isso é padrão);
- *linear*- mesma velocidade do início ao fim; 
- *ease-in*- início lento;
- *ease-out*- final lento;
- *ease-in-out*- lento do início ao fim;
- *cubic-bezier(n,n,n,n)*- permite definir seus próprios valores em uma função de bezier cúbico.

- é possível associar transição com transformação

```css
div {
width: 100px;
height: 100px;
background: rgb(8, 0, 255);
transition: width 2s, height 2s, transform 2s;
}

div:hover {
width: 300px;
height: 300px;
transform: rotate(360deg);
}
```
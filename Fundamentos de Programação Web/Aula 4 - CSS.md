# ELEMENTOS ESTRUTURAIS (SEMÂNTICOS)

## HEADER

- O elemento `<header>` representa um grupo de ajudas introdutórias ou de navegação.
- Pode conter o cabeçalho da seção (um elemento h1– h6) ou um hgroup
-  Em geral, esses elementos contêm logotipos e caixas de busca.

## SECTION

- m agrupamento temático de conteúdo, normalmente com um título

## ARTICLE

- Item de conteúdo independente
- em princípio, distribuível independentemente ou reutilizável


## NAV
- uma seção com links de navegação.

## ASIDE
- conteúdo tangencialmente relacionado ao conteúdo ao redor do elemento `<aside>` e que pode ser considerado separado desse conteúdo. 

## FOOTER
- rodapé para seu conteúdo de corte ancestral mais próximo ou elemento raiz.

## HGROUP
- usado para agrupar um conjunto de elementos h1– h6 quando o título tem vários níveis

## DIV
- não tem nenhum significado especial
- elemento de último recurso

![[Pasted image 20230809075511.png]]


# GRID

- sistema para criação de layout baseado em uma grade bidimensional em que você pode posicionar elementos HTML
- O layout grid possui linhas, colunas e gap![[Pasted image 20230809080456.png]]
## ELEMENTOS DO GRID

```CSS
.box { background: #FFF; border: 4px solid rgb(16, 1, 1);
border-color: #000; color: #000;}
.container {
display: grid;
grid-template-columns: 100px 50px 80px 200px;
grid-template-rows:80px 100px 100px;
gap:8px;}
```


### GRID CONTAINER
- O elemento que contém os itens do grid é chamado de container do grid. Ele é definido aplicando a propriedade `display: grid;` ao elemento pai.

### Linhas e Colunas
- A grade é composta por linhas horizontais e colunas verticais. Você pode definir o número de linhas e colunas e seus tamanhos usando as propriedades `grid-template-rows` e `grid-template-columns`.

### Espaçamento entre Células
- Você pode controlar o espaçamento entre as células do grid usando propriedades como `grid-column-gap` e `grid-row-gap` ou mais resumidamente `gap` 
- para o `gap` se fornecido dois parâmetros o primeiro será para as linhas e o segundo para as colunas, caso fornecido apenas um parâmetro será utilizado o mesmo espaçamento para ambos.

### Grid Items
- São elementos filho de um grid container.

```html
<div class="container">
<div class="box">1</div>
<div class="box">2</div>
<div class="box">3</div>
<div class="box">4</div>
<div class="box">5</div>
<div class="box">6</div>
<div class="box">7</div>
<div class="box">8</div>
<div class="box">9</div>
</div>
```

![[Pasted image 20230809081419.png]]

- O preenchimento das colunas ocorre no fluxo de linhas
- para alterar a ordem dos grids itens por coluna, pode utilizar a declaração: `grid-auto-flow: column;`

### grid template
-  é a forma abreviada de se declararem as propriedades grid-template-rows e grid-template-columns

```css
.container {
display: grid;
grid-template: 80px 100px 100px / 100px 50px 80px 200px;
}
```

## POSICIONAMENTO DE GRID-ITEM

- A seguintes propriedades permitem posicionar grid-item:
	- `grid-column-start` coluna que inicia a grid vertical;
	- `grid-column-end` coluna que finaliza a grid vertical;
	- `grid-row-start` linha que inicia a grid horizontal; e
	- `grid-row-end` linha que finaliza a grid horizontal.

```css
.container {
	display: grid; 
	grid-template-columns: 100px 50px 80px 200px;
	grid-template-rows: 80px 100px 100px;
	gap: 8px;
}
.box1 {
	grid-column-start: 1;
	grid-column-end: 5;
	grid-row-start: 3;
	grid-row-end: 4;
}
.box2 {
	grid-column-start: 3;
	grid-column-end: 5;
	grid-row-start: 1;
	grid-row-end: 3;
}
```


```html
<div class ="container">
	<div class = "box1">1</div>
	<div class= "box2">2</div>
</div>
```

![[Pasted image 20230809082129.png]]


- Podemos utilizar a notação abreviada

```Css
.box1{
	grid-column: 1/5;
	grid-row: 3/4;
}

.box2{
	grid-column: 3/5;
	grid-row:1/3
}
```

## POSICIONAMENTO UTILIZANDO ÁREA

- Make "item1" start on row 2 column 1, and span 2 rows and 3 columns:

```css
.item1 {  grid-area: 2 / 1 / span 2 / span 3;}
```

## Funções repeat() e calc()

- A função `calc()` permite que se definam valores CSS com uso de expressões matemáticas

```scss
seletor { propriedade: calc(expressao_matematica); }
```

-  A função `repeat()` é usada para criar repetições de colunas ou linhas dentro da definição do grid
- especialmente útil quando você deseja criar um número fixo de colunas ou linhas, todas com o mesmo tamanho.

```scss
repeat(number_of_times, track_size)
```


```css
. container {
display: grid;
grid-template-columns: repeat(8, 7%);
grid-template-rows: repeat(4, 4vh);
grid-gap: 8px calc( (100% - 7%* 8) / 7 );
}
```

## Posicionamento com span 

```css
.container {
display: grid;
grid-template-columns: repeat(6, 100px);
grid-template-rows: repeat(4, 60px);
grid-gap: 5px;
}
.box1 {
grid-column: 2 / span 4;}/*começa na coluna 2 e irá ocupar 4 células*/

.box2 {
grid-row: 3 / span 2;} /*começa na linha 3 e irá ocupar 2 células.*/

.box3 {
grid-column: 3 / span 4; /*começa na coluna 3 e irá ocupar 4 celulas*/
grid-row: 3 / span 2; }/*começa na linha 3 e irá ocupar 2 células.*/*
```

![[Pasted image 20230809091615.png]]


## Posicionamento com regiões nomeadas

- A propriedade para nomear do grid é `grid-template-areas` 
- aceita uma sequência de strings que representam as áreas da grade, onde cada string corresponde a uma linha da grade. Cada elemento dentro de uma string representa uma célula da grade
- Para especificar as áreas que o item irá ocupar utiliza-se a propriedade CSS `grid-area` fornecendo como valor o nome das áreas que irá ocupar

```css
.container {
	display: grid;
	grid-template-rows: 60px 40px 200px 60px;
	grid-template-areas:
		"topo topo topo"
		"menu menu menu"
		"esquerda principal direita"
		"rodape rodape rodape";
	grid-gap: 5px 10px;
}
.topo {grid-area: topo;}
.menu {grid-area: menu;}
.principal {grid-area: principal;}
.esquerda {grid-area: esquerda;}
.direita {grid-area: direita;}
.rodape {grid-area: rodape;}
```

![[Pasted image 20230809092424.png]]


- Para especificar áreas com medidas, basta fazer a especificação de valores em grid-template-rows e grid-template-columns.

## Unidade de Medida fr

- Unidade de medida relativa que significa fração cuja referência é a medida do espaço disponível, tanto na vertical quanto na horizontal.

```css
.container {
	display: grid;
	grid-template-columns: 2fr repeat(6, 1fr ) 2fr;/*Cria 8 colunas, iniciando com 2 fr a esquerda e duas 2 fr a direita. No	centro 6 repetições de 1 fr.*/
	grid-template-rows: repeat(8, 1fr );/*Cria 8 linhas de 1 fr cada*/
	gap: 10px 20px;
	height: 80vh;
}
```

![[Pasted image 20230809092840.png]]

## Função minmax()

-  permite estabeler duas dimensões, tanto para largura quanto para altura.

```css
.container {
	display: grid;
	grid-template-columns: 200px minmax(400px, 800px);/* Define duas colunas, sendo a primeira com largura fixa igual a  200px e a segunda com largura mínima de 400px e máxima de 800px. Ou seja, dentro dessa faixa de valores, o grid é fluido.*/
	grid-template-rows: 50px minmax(200px, auto) 50px;/*
	Define três linhas, sendo a segunda fluida com altura mínima de 200px e máxima igual àquela a acomodar todo o conteúdo nela inserido. As outras duas linhas são de altura fixa igual a 50px.*/
	gap: 10px 20px;
}
```

# FLEXBOX

- Flexible Box Module é um modelo de layout em CSS.
- é usado para criar layouts em uma dimensão (horizontal ou vertical).

## Elementos flexbox

- **container**
- Para ativar o modelo de layout Flexbox em um contêiner, usa-se a propriedade CSS `display` com o valor `flex`.

```css
.container { display: flex; }
```

- **flex-item**
- São os elementos filhos de um container modo flex.

```html
<h2>Display flex</h2>
<div class="container1">
	<div class="box box1">DIV</div>
	<span class="box box2">SPAN</span>
	<em class="box box3">EM</em>
	<div class="box box4">DIV</div>
</div>
<br><br><br><br>
<h2>Display block</h2>
<div class="container2">
	<div class="box box1">DIV</div>
	<span class="box box2">SPAN</span>
	<em class="box box3">EM</em>
	<div class="box box4">DIV</div>
</div>
```

```css
html {box-sizing: border-box;}
.container1 { display: flex; }
.container2 { display: block; }
.box {
	color: white;
	border: 4px solid #333;
	font-size: 24px;
	padding: 10px;
}
.box1 {background: #086bdd;}
.box2 {background: #1c0989;}
.box3 {background: #00028b;}
.box4 {background: #7c58de;}
```

![[Pasted image 20230810082445.png]]


## Propriedades flexbox

- **display**
- O "display: flex" faz com que os "flex items" sejam exibidos em modo flex.

- **flex-direction**
- Define a direção e o sentido do main axis
- Valores:
	- row, column, row-reverse e column- reverse

```css
.flex{
	display:flex;
	flex-direction:row;
}
```

![[Pasted image 20230810082849.png]]

- **justify-content**
- define como será feito o alinhamento dos elementos ao longo do eixo principal.
- valores:
	- flex-start
	- center
	- flex-end
	- space-between 
	- space-around

```css
.container {
display: flex;
justify-content: space-around;
}
```

![[Pasted image 20230810083059.png]]

- **flex-wrap**
- Determina se os elementos devem quebrar para a próxima linha quando não couberem em uma única linha ou coluna.
- valores:
	-  nowrap
	- wrap 
	- wrap-reverse

```css
.container {
	display: flex;
	flex-wrap: wrap; /* o valor padrão é nowrap */
}
```

- **align-items**
- Alinha os elementos ao longo do eixo transversal.
- Essa propriedade é aplicada aos elementos individuais dentro do contêiner flex (os flex items).
- Valores:
	-  flex-start
	- center
	- flex-end
	- stretch

```css
.container {
display: flex;
align-content: flex-start; /* o valor inicial é flex-start */
}
```

![[Pasted image 20230810083535.png]]

- **align-content**
- controlar o alinhamento dos flex items ao longo do eixo transversal quando eles estão dispostos em várias linhas
- Essa propriedade é aplicada ao próprio contêiner flex, quando existem várias linhas de flex items (definidas pelo uso da propriedade `flex-wrap`).
	- **flex-start**: Os flex items são alinhados no início do eixo transversal.
	- **flex-end**: Os flex items são alinhados no final do eixo transversal.
	- **center**: Os flex items são alinhados no centro do eixo transversal.
	- **space-between**: Os flex items são distribuídos uniformemente ao longo do eixo transversal, com espaços iguais entre eles. O primeiro e o último flex item ficam colados nas bordas do contêiner.
	- **space-around**: Os flex items são distribuídos uniformemente ao longo do eixo transversal, com espaços iguais ao redor de cada flex item.
	- **stretch**: Os flex items são esticados para ocupar todo o espaço disponível ao longo do eixo transversal. Isso é o valor padrão

![[Pasted image 20230810084137.png]]


# MEDIA QUERIES

- funcionalidade do CSS que permitem adaptar o estilo de um site ou aplicação web com base nas características do dispositivo em que está sendo visualizado
- As Media Queries funcionam permitindo que você defina regras de estilo condicionais que são aplicadas somente quando certas condições são atendidas, como largura de tela, altura de tela, orientação do dispositivo, densidade de pixels, entre outras
- estrutura básica:

```css
@media condicao {
  /* Estilos a serem aplicados quando a condição é atendida */
}

```

- exemplo simples de como uma Media Query pode ser usada para ajustar o tamanho da fonte em diferentes tamanhos de tela:

```css
/* Estilos padrão */
body {
  font-size: 16px;
}

/* Media Query para telas menores que 600px */
@media (max-width: 600px) {
  body {
    font-size: 14px;
  }
}

```

- o operador `only` é utilizado para esconder folhas de estilo dos navegadores antigos que não suportam *media query*

## Funcionalidades Media Query

- **width**: descreve a largura da área de saída do dispositivo do usuário

```css
@media screen and (min-width: 320px) and (max-width: 700px)
{....}
```

- **height**: descreve a altura da área de saída do dispositivo do usuário

```css
@media screen and (min-height: 600px) and (max-height: 768px)
{....}
```

- **device-width**: descreve a largura física da área de renderização do dispositivo do usuário. 

```css
@media screen and (min-device-width: 400px) and (max-device-width: 700px) 
{....}
```

- **device-height**: descreve a altura física da área de renderização do dispositivo do usuário

```css
@media screen and (min-device-height: 600px) and (max-device-height: 768px) 
{....}
```

- **orientation**: os valores possíveis para orientation são *landscape* e *portrait*.

```css
@media screen and (orientation: landscape) {....}
@media screen and (orientation: portrait) {....}
```

- **aspect-ratio**: considera a razão entre a largura (width) e altura (height) da área de saída do dispositivo do usuário

```css
@media screen and (aspect-ratio: 16/9) {....}
@media screen and (min-aspect-ratio: 5/2) {....}
```

- **device-aspect-ratio**: considera a razão entre a largura (device-width) e altura (device-height) da área de saída do dispositivo do usuário.

```css
@media screen and (device-aspect-ratio: 16/9) {....}
@media screen and (min-device-aspect-ratio: 800/600) {....}
```

- **Color**: descreve o número de bits por componente de cor no dispositivo do usuário.

```css
@media screen and (color: 2) {....} /*dispositivos coloridos de 8 bits*/
@media screen and (color: 0) {....} /*dispositivos monocromáticos*/
```

- **color-index**: descreve o número de entradas da paleta de cores do dispositivo do usuário

```html
<link rel=”stylesheet” media=screen and (color-index) “href=”...”> <!-- todos os dispositivos de paleta de cores-->
```

- **monochrome**: descreve o número de bits por componente monocromático no dispositivo do usuário.

```css
@media screen and (monochrome: 2) {...} /*dispositivos monocromáticos de 2 bits por pixel*/
```

- **resolution**: descreve a resolução, densidade de pixel, no dispositivo do usuário

```css
@media screen and (min-resolution: 300dpi) {...} /*dispositivos com resolução maior que 300 pontos por polegadas*/
```

- **scan**: descreve o processo de escaneamento de imagens em mídias do tipo TV

```css
@media tv and (scan: progressive) {...}
@media tv and (scan: interlace) {...}
```

- **grid**: descreve se a saída do dispositivo é em grid ou bitmap 

```css
@media handheld and (grid) and (max-width: 15em) {...}
```

## Breakpoints

-  são os pontos nos quais o layout se readapta para se ajustar a uma nova largura da janela.

```css
@media only screen and (min-width: 768px) {
 /*Quando a largura mínima da tela do dispositivo for de 768px, ele passa a exibir o layout com três colunas.*/
}

@media only screen and (min-width: 600px) {
	/*O layout passar a ser exibido em duas colunas.*/
}
```

![[Pasted image 20230810092400.png]]

![[Pasted image 20230810092414.png]]

### Mobile First
- O uso de smartphones para navegação é atualmente mais comum do que o acesso em computadores pessoais
-  a recomendação é de desenvolver primeiramente para dispositivos móveis. 

# RESPONSIVIDADE EM IMAGENS 

```css
img {
	display: block;
	margin: 0 auto;
	max-width: 100%;
}
```

1. `display: block;`:
    - Define as imagens como elementos de bloco. Isso faz com que as imagens ocupem a largura total do contêiner pai e garantem que outras propriedades, como margens e alinhamento, funcionem corretamente.
2. `margin: 0 auto;`:
    - Define margens automáticas para centralizar horizontalmente as imagens dentro do contêiner pai.
    - Isso é particularmente útil quando as imagens têm larguras menores do que a largura do contêiner pai. As margens automáticas garantem que as imagens estejam centralizadas na tela.
3. `max-width: 100%;`:
    - Define a largura máxima da imagem como 100% do contêiner pai.
    - Isso impede que imagens maiores do que o contêiner pai se expandam além do espaço disponível, garantindo que a imagem se ajuste automaticamente ao tamanho do contêiner.
- ![[Pasted image 20230810103028.png]]

## IMAGENS FLEXÍVEIS

- Normalmente, necessitamos disponibilizar um conjunto de imagens, para que sejam exibidas de acordo com a largura da viewport (tela).

### SRCSET
- permite que você forneça ao navegador uma lista de URLs de imagem diferentes, cada um com uma resolução ou tamanho específico. O navegador então seleciona a imagem mais adequada com base nas características do dispositivo, como a largura da tela e a densidade de pixels.
- A sintaxe básica do `srcset` é a seguinte:

```html
<img src="imagem-padrão.jpg" srcset="imagem1.jpg 1x, imagem2.jpg 2x, imagem3.jpg 3x" alt="Descrição da imagem">

```

- O atributo `src` contém o URL da imagem padrão que será exibida se nenhum dos URLs no `srcset` for selecionado.
    
- No atributo `srcset`, você especifica uma lista de URLs de imagem, cada um seguido por um valor que indica a relação de densidade de pixels (DPR) da imagem. Por exemplo, `1x`, `2x` e `3x` indicam resoluções de 1, 2 e 3 vezes a densidade de pixels padrão, respectivamente.
    
- O navegador escolherá automaticamente a imagem mais apropriada com base na resolução da tela e na capacidade de exibição do dispositivo. Por exemplo, se o dispositivo tiver uma tela Retina (2x), o navegador escolherá a imagem com `2x` no `srcset`.

- Além da unidade "x" no atributo `srcset`, que se refere à relação de densidade de pixels (DPR), também existem as unidades "w" e "h".

- **Unidade "w" (largura)**: A unidade "w" permite especificar a largura da imagem no `srcset`. Isso é útil quando você quer que o navegador selecione uma imagem com base na largura do contêiner em que a imagem será exibida. Por exemplo:

```html
`<img src="imagem-padrão.jpg" srcset="imagem1.jpg 300w, imagem2.jpg 600w, imagem3.jpg 900w" alt="Descrição da imagem">`
```

  - Nesse exemplo, o navegador escolherá a imagem com base na largura do contêiner onde a imagem está sendo exibida. Se o contêiner tiver uma largura de 450 pixels, o navegador escolherá a imagem `imagem1.jpg` (300 pixels de largura).
    
- **Unidade "h" (altura)**: A unidade "h" permite especificar a altura da imagem no `srcset`. Assim como com a unidade "w", você pode direcionar o navegador para escolher uma imagem com base na altura do contêiner. No entanto, a unidade "h" é menos comum e não é suportada por todos os navegadores.

```html
<img src="imagem-padrão.jpg" srcset="imagem1.jpg 200h, imagem2.jpg 400h, imagem3.jpg 600h" alt="Descrição da imagem">
```

O uso da unidade "h" é menos recomendado devido à falta de suporte em alguns navegadores e à maneira mais complexa como a altura é considerada nas decisões de escolha de imagem.

### PICTURE

- A tag `<picture>` é uma tag HTML introduzida para fornecer suporte avançado para imagens responsivas e otimizadas para diferentes dispositivos e tamanhos de tela
- permite que você envolva um conjunto de elementos `<source>` que especificam diferentes fontes de imagem e condições de visualização.
- O navegador seleciona a primeira fonte de imagem que corresponde às condições do dispositivo e a exibe. Se nenhuma fonte de imagem corresponder, o navegador usará o elemento `<img>` padrão.

```HTML
<picture>
  <source srcset="imagem-1.jpg" media="(max-width: 600px)">
  <source srcset="imagem-2.jpg" media="(max-width: 1200px)">
  <img src="imagem-padrão.jpg" alt="Descrição da imagem">
</picture>

```

- Pode ser usado para criar um conjunto de condições mais complexas para seleção de imagem, como diferentes imagens para diferentes tamanhos de tela.
- Oferece maior controle sobre a seleção da imagem com base em condições específicas.

### ART DIRECTION
- prática de fornecer diferentes versões de imagens ou elementos gráficos, dependendo do dispositivo ou contexto de visualização.
- O objetivo é não apenas ajustar o tamanho da imagem, mas também adaptar o conteúdo visual para melhorar a estética, o foco e a mensagem em diferentes dispositivos ou cenários de exibição.
- Para implementar o "art direction" em design responsivo, são utilizadas técnicas como o uso da tag `<picture>` em HTML com diferentes fontes de imagens, o atributo `srcset` para especificar diferentes resoluções ou tamanhos de imagens, e até mesmo Media Queries para escolher imagens específicas com base nas características do dispositivo.
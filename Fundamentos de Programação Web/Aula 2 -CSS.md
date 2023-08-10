# CASCADING STYLE SHEETS (CSS)

## Definição
- Segundo o W3C: “Folha de estilo em cascata é um mecanismo simples para adicionar estilos (por exemplo: fontes, cores, espaçamentos) aos documentos web”.

## Sintaxe

![[Pasted image 20230801093900.png]]

- O seletor aponta para o elemento HTML que você deseja estilizar
- O bloco de declaração (declaration) contém uma ou mais declarações separadas por ponto e vírgula
- Cada declaração inclui um nome de propriedade (property) CSS e um valor (value), separados por dois-pontos
- Várias declarações CSS são separadas por ponto e vírgula e os blocos de declaração são cercados por chaves.

## SELETORES

Os tipos de seletores são:
- **seletores simples**: definem elementos com base no nome, id e classe;
- **seletores de combinação**: selecionam elementos com base em um relacionamento específico entre eles;
- **seletores de pseudoclasse**: selecionam elementos com base em determinado estado;
- **seletores de pseudoelementos**: selecionam e estilizam parte de um elemento;
- **seletores de atributo**: selecionam elementos com base em um atributo ou valor de atributo.

### Seletores ID

- usa o atributo *id* de um elemento HTML para selecionar um elemento específico
- O id de um elemento é único dentro de uma página
- Para selecionar um elemento com um id específico, escreva um caractere hash (#), seguido do id do elemento.

```css
#paragrafo{
	text-align: justify;
	color: green;
}
```

### Seletores class

- seleciona elementos HTML com um atributo de classe específico.
- Para selecionar elementos com uma classe específica, escreva um caractere ponto (.), seguido do nome da classe.
- Pode-se aplicar mais de uma class em um elemento:

```css
.p.dois{
	text-align: center;
	color: gray;
}
```

### Seletor universal
- Seleciona todos os elementos HTML da página, para aplicar a formatação.

```css
*{color: white;}
```

### Agrupamento de seletores

```css
h1,h2,p{
	text-align: justify;
	color: white;
}
```

## Como aplicar CSS

### CSS Externo

- utiliza uma folha de estilo externa
-  Cada página HTML deve incluir uma referência (href) ao arquivo de folha de estilo externo dentro do elemento `<link>`, dentro da seção `<head>`.

```html
<!DOCTYPE html>
<html lang="pt-br">
	<head>
		<meta charset="UTF-8">
		<link rel="stylesheet" href="estilo.css">
		<title>CSS Externo</title>
	</head>
	<body>
		<h1>Título</h1>
		<p> Aqui tem um parágrafo</p>
	</body>
</html>
```

### CSS interno

- pode ser usada se uma única página HTML tiver um estilo exclusivo.
- O estilo interno é definido dentro do elemento `<style>`, dentro da seção head.

```html
<!DOCTYPE html>
<html lang="pt-br">
	<head>
		<meta charset="UTF-8">
		<title>CSS Interno</title>
		<style>
			*{
				color: white;
			}
			body{
				background-color: black;
			}
		</style>
	</head>
	<body>
		<h1>Título</h1>
		<p> Aqui tem um parágrafo</p>
	</body>
</html>
```


### CSS inline 

- pode ser usado para aplicar um estilo exclusivo para um único elemento, aplicado diretamente na tag
- utiliza o atributo style ao elemento

```html
<!DOCTYPE html>
<html lang="pt-br">
	<head>
		<meta charset="UTF-8">
		<title>CSS Inline</title>
	</head>
	<body>
		<h1 style="color:blue; text-align: center;">Título</h1>
		<p style="color:red;"> Aqui tem um parágrafo</p>
	</body>
</html>
```

## Hierarquia CSS

1. CSS inline (aplicado diretamente na tag);
2. folhas de estilos internas e externas;
3. padrão do browser.

# CSS (COMENTÁRIOS, CORES, FUNDO, BORDAS, MARGEM E PREENCHIMENTO)

## COMENTÁRIOS

- Um comentário CSS é colocado dentro do `<style>` e começa com `/*` e termina com `*/` 

```HTML
<style>
/*assim se marca comentário*/
	p{
		color:red;
	}
</style>
```

## CORES

- Podemos aplicar cores em textos, fundos e bordas.
- As cores podem ser especificadas usando nomes de cores predefinidos ou valores RGB, HEX, HSL, RGBA ou HSLA

### RGB

- Um valor de cor RGB representa fontes de luz red (vermelha), green (verde) e blue (azul).
-  sintaxe: RGB (vermelho, verde, azul).
- Cada parâmetro define a intensidade da cor entre 0 e 255.
- preto, defina todos os parâmetros de cor para 0
- branco, defina todos os parâmetros de cor para 255

### HEX

- é especificada com: \#RRGGBB
- valores hexadecimais entre 00 e FF.

### HSL

- HSL significa **hue** (matiz), **saturation** (saturação) e **lightness** (leveza)
- Matiz é um grau na roda de cores de 0 a 360. 0 é vermelho, 120 é verde e 240 é azul.
- A saturação é um valor percentual. 0% significa um tom de cinza e 100% é a cor completa.
- A leveza também é uma porcentagem. 0% é preto, 50% não é claro nem escuro, 100% é branco

## BACKGROUND

- *background-color*: a cor de plano de fundo 

```CSS
body{
	background-color: black;
}
```
- *background-image*: especifica uma imagem a ser usada como plano de fundo de um elemento. Por padrão, a imagem é repetida para cobrir todo o elemento.

```CSS
body{ background-image: url(“flor.gif”);}
```

## BORDAS

 - define a espessura, o estilo e a cor das bordas do box. 
 - quatro lados: *top, right, bottom e left.*

```css
div{
	border: 1px solid;
	border-top-width:1px;
	border-right-width:1px;
	border-bottom-width:1px;
	border-left-width:1px;
}

/*sintaxe abreviada*/
div{
	border-width: 1px;2px;3px;4px;
}
```

### Propriedades:
- **border-width** - espessura da borda
- **border-color** - cor da borda
- **border-style** -  estilo da borda
- **border-radius** - arredondamento da borda

- É possível definir as propriedades de forma abreviada ao criar a borda:

```css
div{
	border: 3px dotted black;
}
```


![[Pasted image 20230801101333.png]]


## Margin

- criar espaço ao redor dos elementos
```css
p{
	margin-top: 100px;
	margin-bottom: 100px;
	margin-right: 150px;
	margin-left: 80px;
}
```

Se a propriedade tiver quatro valores: margem: 25px 50px 75px 100px;
• a margem superior é de 25px
• a margem direita é 50px
• a margem inferior é de 75px
• margem esquerda é 100px

```css
p{ margin: 25px 50px 75px 100px;}
```

Se a propriedade tiver três valores: margem: 15px 25px 555px;
• a margem superior é de 15px
• as margens direita e esquerda são 25px
• a margem inferior é de 55px

- Se a propriedade tiver dois valores: margem: 20px 25px;
• as margens superior e inferior são 20px
• as margens direita e esquerda são 25px

Se a propriedade tiver um valor: margem: 25px;
• todas as quatro margens são 25px

## Padding

- usado para criar espaço ao redor do conteúdo de um elemento, dentro de qualquer borda definida.
- se formata da mesma maneira que a margin

# CSS (WIDTH, HEIGHT, FORMATAÇÃO DE TEXTO/FONTE. BOX MODEL)

## Width (largura ) e height (altura)

- usadas para definir a altura e a largura de um elemento.
- A propriedade *max-width* é usada para definir a largura máxima de um elemento.
- Podem ter os seguintes valores:
	- auto- este é o padrão. O navegador calcula a altura e a largura
	- length- define a altura/largura em px, cm etc
	- %- define a altura/largura em porcentagem do bloco que contém.

```CSS
div{
	height: 200px;
	width: 50%;
}
```

## Formatação de Texto

### Color
- define a cor do texto.
```css
h1 {
  color: #000000; /* Cor preta */
}

```

### Text Align

- Define o alinhamento do texto dentro do seu contêiner.
- Valores:
    - `left`: Alinha o texto à esquerda.
    - `center`: Alinha o texto ao centro.
    - `right`: Alinha o texto à direita.
    - `justify`: Justifica o texto.

```css
h1 {
  text-align: left;
}

```

### text-decoration-line
- define o tipo de decoração de linha a ser adicionada ao texto.
- Valores:
    - `none`: Nenhuma decoração de texto.
    - `underline`: Adiciona uma linha abaixo do texto.
    - `overline`: Adiciona uma linha acima do texto.
    - `line-through`: Adiciona uma linha no meio do texto.
    - `underline overline`: Adiciona tanto uma linha abaixo quanto acima do texto.

```css
h1 {
  text-decoration-line: overline;
}

h2 {
  text-decoration-line: line-through;
}

h3 {
  text-decoration-line: underline;
}

p.ex {
  text-decoration-line: overline underline;
}

```

### text-decoration-color

define a cor das linhas de decoração de texto.

```css
h1 {
  text-decoration-line: overline;
  text-decoration-color: red;
}

h2 {
  text-decoration-line: line-through;
  text-decoration-color: blue;
}

```

### text-decoration-style

- define o estilo da linha de decoração.
- Valores:
    - `solid`: A linha de decoração é contínua.
    - `dotted`: A linha de decoração é pontilhada.
    - `dashed`: A linha de decoração é tracejada.
    - `double`: A linha de decoração é dupla.
    - `wavy`: A linha de decoração é ondulada.

```css
h2 {
  text-decoration-line: underline;
  text-decoration-style: double;
}
```

## Formatação de fonte

**Propriedade: `font-family`**
- define a família de fonte a ser aplicada ao texto.

```css
h2 {
  font-family: Arial, Helvetica, sans-serif;
}
```

**Propriedade: `font-size`**

- define o tamanho da fonte a ser aplicado ao texto.

```css
h2 {
  font-size: 30px;
}
```

## Box Model

- O box-model é basicamente uma caixa que envolve cada elemento HTML

![[Pasted image 20230801103259.png]]

#  CSS (FLOAT, CLEAR, ELEMENTOS BLOCK E INLINE)

## Float e clear

- A propriedade `float` é utilizada para controlar o posicionamento de um elemento HTML em relação aos elementos ao seu redor. Ela permite que o elemento flutue à esquerda ou à direita do seu contêiner, tirando-o do fluxo normal do documento.
- Valores:
	- `none`: O elemento não flutua e permanece no fluxo normal do documento (valor padrão).
	- `left`: O elemento flutua à esquerda do seu contêiner.
	- `right`: O elemento flutua à direita do seu contêiner.
	- `inherit`: o elemento herda o valor de *float* de seu pai 

```css
img {
  float: left;
}
```

- A propriedade `clear` é utilizada para controlar o comportamento de elementos que seguem elementos flutuantes
- Ela define se um elemento deve ser posicionado abaixo dos elementos flutuantes (`left`, `right`) ou se deve ignorar os elementos flutuantes e posicionar-se ao lado deles (`none`).
- Valores:
	- `none`: O elemento pode ser posicionado ao lado de elementos flutuantes.
	- `left`: O elemento não deve ser posicionado à esquerda de elementos flutuantes.
	- `right`: O elemento não deve ser posicionado à direita de elementos flutuantes.
	- `both`: O elemento não deve ser posicionado à esquerda ou à direita de elementos flutuantes.

```css
div {
  clear: both;
}

```

## Elementos block e inline

-  Os elementos do tipo **block** (bloco) são exibidos um abaixo do outro
-  Os elementos do tipo **inline** são exibidos um à esquerda do outro (na mesma linha).

![[Pasted image 20230802075816.png]]

![[Pasted image 20230802075834.png]]

# CSS (DISPLAY, POSITION, Z-INDEX)

## DISPLAY

- especifica como um elemento será exibido na tela
- pode ser definido como: *block, inline ou none*.

```HTML
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
		<style>
			li {
				display: inline;
			}
		</style>
	</head>
	<body>
		<p>Menu Horizontal:</p>
		<ul>
			<li><a href="#">HTML</a></li>
			<li><a href="#">CSS</a></li>
			<li><a href="#">JavaScript</a></li>
		</ul>
	</body>
</html>
```

![[Pasted image 20230802081259.png]]

## POSITION

- propriedade usada para controlar o posicionamento de um elemento na página web
- permite que você defina como um elemento deve ser exibido em relação aos elementos ao seu redor



### Static 
- valor padrão para a maioria dos elementos HTML.
- são renderizados no fluxo normal do documento, seguindo a ordem em que aparecem no código HTML.
- Qualquer propriedade de deslocamento (top, right, bottom, left) não terá efeito em elementos com posição estática.

```html
<div style="position: static;">
   Este é um elemento com posição estática.
</div>

```

<div style="position: static;">
   Este é um elemento com posição estática.
</div>


### Relative
- Um elemento com `position: relative`; é posicionado em relação à sua posição original no fluxo do documento.
- Você pode usar as propriedades 'top', 'right', 'bottom' e 'left' para deslocar o elemento em relação à sua posição original.
- Elementos posicionados como relativos ainda ocupam espaço no fluxo normal do documento

```html
<div style="position: relative; top: 20px; left: 30px;">
   Este é um elemento com posição relativa, deslocado 20 pixels para baixo e 30 pixels para a direita em relação à sua posição original.
</div>

```

<div style="position: relative; top: 20px; left: 30px;">
   <p>Este é um elemento com posição relativa, deslocado 20 pixels para baixo e 30 pixels para a direita em relação à sua posição original.</p>
</div>

### Absolute
- o elemento é removido do fluxo normal do documento e posicionado em relação ao ancestral posicionado mais próximo (ou ao elemento `<html>` se nenhum ancestral for posicionado).
- Ancestrais posicionados são elementos que têm uma posição diferente de 'static', como 'relative', 'absolute', ou 'fixed'.
- você pode ajustar o posicionamento usando as propriedades 'top', 'right', 'bottom' e 'left'.
- Elementos absolutos não ocupam espaço no fluxo normal do documento, e outros elementos são posicionados como se o elemento absoluto não estivesse presente.

```html
<div style="position: relative;">
   <div style="position: absolute; top: 50px; left: 100px;">
      Este é um elemento com posição absoluta, posicionado 50 pixels abaixo e 100 pixels à direita do elemento 'relativo' pai.
   </div>
</div>

```

### Fixed

- o elemento é removido do fluxo normal do documento e é posicionado em relação à janela de visualização do navegador.
- O elemento permanecerá fixo em sua posição, mesmo que a página seja rolada.
- Você pode ajustar o posicionamento usando as propriedades 'top', 'right', 'bottom' e 'left'.
- Elementos fixos não ocupam espaço no fluxo normal do documento, e outros elementos são posicionados como se o elemento fixo não estivesse presente.

```html
<div style="position: fixed; top: 20px; right: 10px;">
   Este é um elemento com posição fixa, posicionado 20 pixels abaixo e 10 pixels à direita em relação à janela de visualização do navegador.
</div>

```

## Z-index

- é usada para controlar o empilhamento e a sobreposição de elementos posicionados.
- Ela permite definir a ordem de profundidade dos elementos quando há sobreposição entre eles.
- Quando dois ou mais elementos se sobrepõem na página, o elemento com um valor de 'z-index' maior será exibido acima (na frente) dos elementos com valores de 'z-index' menores.
- Utilizado com elementos com position diferente de static 

```html
<style>
  .red-box {
    width: 100px;
    height: 100px;
    background-color: red;
    position: absolute;
    top: 50px;
    left: 50px;
    z-index: 2;
  }

  .blue-box {
    width: 100px;
    height: 100px;
    background-color: blue;
    position: absolute;
    top: 80px;
    left: 80px;
    z-index: 1;
  }

  .green-box {
    width: 100px;
    height: 100px;
    background-color: green;
    position: absolute;
    top: 110px;
    left: 110px;
    /* sem z-index definido, o valor padrão é 'auto' */
  }
</style>

<div class="red-box"></div>
<div class="blue-box"></div>
<div class="green-box"></div>

```

## Overflow

- usada para controlar o comportamento de um elemento quando seu conteúdo ultrapassa as dimensões do próprio elemento
- **visible** -  é o valor-padrão. O estouro não é contido. O conteúdo é renderizado fora da caixa do elemento;
- **hidden** - o estouro é contido e o restante do conteúdo ficará invisível;
- **scroll** - o estouro é contido e uma barra de rolagem é adicionada para ver o restante do conteúdo
- **auto** - semelhante a scroll, mas adiciona barras de rolagem apenas quando necessárias.

```html
<style>
	div {
		background-color: gray;
		width: 250px;
		height: 100px;
		border: 1px solid black;
		overflow: scroll;
		color: white;
	}
</style>
```

![[Pasted image 20230802085010.png]]


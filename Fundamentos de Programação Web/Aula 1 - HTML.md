 # CONCEITOS INICIAIS

## História 
- A sigla HTML significa HyperText Markup Language
- A essência do HTML é o HyperText (hipertexto) -  links que permitem que façamos uma leitura não linear.
- modelos teóricos, ideias que inspiraram o desenvolvimento do HTML.
	- Vannevar Bush - Memex em 1945
-  em 1960, Theodor (Ted) Nelson criou o termo hipertexto/hipermídia -  projeto Xanadu
- Tim Bernard Lee, em 1990, desenvolveu o HTML
- HTML teve como base o SGML (Standard Generalized Mark-up Language)

## Arquitetura Cliente Servidor

- *Cliente* pode ser qualquer dispositivo conectado à internet utilizando o browser ou navegador.
- *Servidores* são computadores que armazenados os sites, com seu conjunto de páginas ou aplicativos
- Quando o browser de um cliente solicita uma página (HTML), uma cópia dela é baixada do servidor para o dispositivo do cliente.
- O que permite ocorrer essa comunicação é protocolo *HTTP*, que significa Hypertext Transfer Protocol

# AMBIENTE DE DESENVOLVIMENTO 

## Visual Studio Code

- **CTRL+SHIFT+P** -  abrir a Paleta de Comandos
- CTRL+SHIFT+P > HTML: Open Preview to the Side.
- Criar pasta de repositório no PC
- Abrir pasta no VsCode
- Criar novo arquivo
- ! - shortcut para estrutura HTML

# HTML
- O produto de uma marcação HTML é um arquivo de texto que deve ser gravado com a extensão .html

## TAG HTML

- Para escrever em HTML, precisamos utilizar **tags** (etiquetas). Iniciamos com uma tag de abertura `<>` e no fim uma tag de fechamento. `</>`
- p, h1

## Estrutura mínima de uma página HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
</head>
<body>

</body>
</html>
```

- `<!DOCTYPE html>` - indica que trata-se de um documento HTML 5
- `<html lang="en">` - tab "raiz" o atributo utilizado especifica o idioma
- `<head> e </head>` - metadados sobre o documento, como seu título, links para scripts e folhas de estilos.
- `<meta charset="UTF-8">` - 
	- Charset: define a codificação de caracteres usada na página
	- UTF-8 (Unicode Transformation Format 8): é o formato recomendado para ser utilizado. Pode representar qualquer caractere Unicode padrão.
- `<title>Document</title>` - título do documento -e é identificado pelos mecanismos de busca e indexação
- `<body> e </body>` contém o conteúdo das páginas que visualizamos

## MARCAÇÕES BÁSICAS

### Títulos (Headings)

- As tags de títulos são definidas de `<h1> `a `<h6>
- `<h1>` define o título mais relevante.
- `<h6>` define o título menos importante.
- Utilize apenas um `<h1>` por página

### Parágrafos, quebras de linhas e linha horizontal
- A tag `<p>` define um parágrafo. Os navegadores adicionam uma linha após um parágrafo `</p>`
- A tag `<br>` força uma quebra de linha. Não possui tag de fechamento.
- A tag `<hr>` insere uma linha horizontal. Não possui tag de fechamento.
- Eles elementos são do tipo nível de bloco.

### Listas
- `<ol>` - ordered list
- `<ul>` - unordered list
- `<li>` - list item
- `<dl>` - description

```html
<h2>Lista não ordenada</h2>

<ul>
	<li>Café</li>
	<li>Chá</li>
	<li>Leite</li>
</ul>

<h2>Lista ordenada</h2>

<ol>
	<li>Café</li>
	<li>Chá</li>
	<li>Leite</li>
</ol>
```

![[Pasted image 20230719102644.png]]



## LINKS, IMAGENS E TABELAS

### Links

-  utilizamos a tag `<a>`  ("anchor")- elemento do tipo inline 
- O atributo `href`  ("hyperlink reference") é necessário e indica o destino do link

```html
<a href = "url"> página </a>
```

- Atributo `target` - onde irá abrir o link
	- \_self - Predefinição. Abre o documento na mesma janela/guia em que foi clicado
	- \_blank - Abre o documento em uma nova janela ou guia 
	- \_parent - Abre o documento no quadro pai 
	- \_top - Abre o documento em todo o corpo da janela

```html
<a href="https://www.google.com" target="_blank">Visite o Goolge</a>
```

### Imagens

- utilizamos o elemento `<img>` - elemento do tipo inline 
- não necessita de tag de fechamento
- requer dois atributos: `src` (caminho da imagem) e `alt `(texto alternativo, se a imagem por algum motivo não puder ser exibida).

```html
<img src="../Imagens/praia.jpg" alt="praia" title="praia de..." style="width:50%;">
```
- Outros atributos: `width`, `height`

### Tabelas

- `<table>` - define a tabelas
- `<tr>` - table row
- `<td>` - table data -  define célula
- Caption -> título da tabela
- Summary -> descrever o objetivo da tabela 
- `<thead>` - cabeçalho da tabela
- `<tbody>` - corpo da tabela
- `<tfoot>` - rodapé

```html
<h2>Tabelas</h2>
<table width="80%" border="1px">
	<caption>Alunos</caption>
	<tr>
		<th>Aluno</th>
		<th>RU</th>
	</tr>
	<tr>
		<td>Ana Maria</td>
		<td>2131</td>
	</tr>
	<tr>
		<td>João Pedro</td>
		<td>4346</td>
	</tr>
</table>
```

<table width="80%" border="1px">
	<caption>Alunos</caption>
	<tr>
		<th>Aluno</th>
		<th>RU</th>
	</tr>
	<tr>
		<td>Ana Maria</td>
		<td>2131</td>
	</tr>
	<tr>
		<td>João Pedro</td>
		<td>4346</td>
	</tr>
</table>

- **Colspan** -> mesclar colunas
- **Rowspan** -> mesclar linhas

```html
   <table border = "1">
        <tr>
            <td colspan="2"> Linha 1 colunas 1 e 2</td>
            <td rowspan="2">Coluna 3, linhas 1 e 2</td>
        </tr>
        <tr>
            <td>Linha 2 célula 1</td>
            <td>Linha 2 célula 3</td>
        </tr>
        <tr>
            <td>Linha 3 célula 1</td>
            <td>Linha 3 célula 2</td>
            <td>Linha 3 célula 3</td>
        </tr>
    </table>
```

   <table border = "1">
        <tr>
            <td colspan="2"> Linha 1 colunas 1 e 2</td>
            <td rowspan="2">Coluna 3, linhas 1 e 2</td>
        </tr>
        <tr>
            <td>Linha 2 célula 1</td>
            <td>Linha 2 célula 3</td>
        </tr>
        <tr>
            <td>Linha 3 célula 1</td>
            <td>Linha 3 célula 2</td>
            <td>Linha 3 célula 3</td>
        </tr>
    </table>

## FORMULÁRIOS

- Utiliza-se a tag `<form>` para criar um formulário
- Utilizado para receber entradas dos usuários

### INPUT
- `<input>` - utilizado para definir a área de entrada, o atributo `type` define o tipo de dado
- `<input type="text"> `- Exibe um campo de entrada de texto de linha única
- 
 <input type="text">
 
- `<input type="radio">` - Exibe um botão de opção (para selecionar uma das muitas opções)

<input type="radio">

- `<input type="check- box">` -Exibe uma caixa de seleção (para selecionar zero ou mais de muitas opções)

<input type="checkbox" name="language" value="java" id="java-checkbox">
<label for="java-checkbox">Java</label>

<input type="checkbox" name="language" value="python" id="python-checkbox">
<label for="python-checkbox">Python</label>

- `<input type="button">` - Exibe um botão clicável

<input type="button" value = "button">

- `<textarea> </textarea>` - Insere uma área de texto para o usuário digitar textos.

<textarea>
</textarea>

- `<select></select>` Cria uma lista suspensa. 
	- Os  `<option>` definem uma opção que pode ser selecionada

<select name="languages">
  <option value="java">Java</option>
  <option value="python">Python</option>
</select>

- `<label></label>` - Permite adicionar rótulos aos elementos  - atributo `for`

```html
<!DOCTYPE html>
<html lang="pt-Br">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial- scale=1.0">
	<title>Exemplo de formulário</title>
</head>
<body>
	<h1>Exemplo de Formulário Simples</h1>
	<form action="" method="">
		<table>
			<tr>
				<th><label for="nome">Nome:</label></th>
				<td><input type="text" name="nome" id="nome"></td>
			</tr>
			<tr>
				<th><label for="email">E-mail:</label></th>
				<td><input type="email" name="email" id="email"></td>
			</tr>
			<tr>
				<th><label for="msg">Digite sua Mensagem:</label></th>
				<td><textarea name="msg" rows="5" cols="40">Digite sua mensagem</textarea></td>
			</tr>
			<tr>
				<td></td>
				<td> <button>Enviar</button></td>
			</tr>
		</table>
	</form>
</body>
</html>
```

<h1>Exemplo de Formulário Simples</h1>
	<form action="" method="">
		<table>
			<tr>
				<th><label for="nome">Nome:</label></th>
				<td><input type="text" name="nome" id="nome"></td>
			</tr>
			<tr>
				<th><label for="email">E-mail:</label></th>
				<td><input type="email" name="email" id="email"></td>
			</tr>
			<tr>
				<th><label for="msg">Digite sua Mensagem:</label></th>
				<td><textarea name="msg" rows="5" cols="40">Digite sua mensagem</textarea></td>
			</tr>
			<tr>
				<td></td>
				<td> <button>Enviar</button></td>
			</tr>
		</table>
	</form>


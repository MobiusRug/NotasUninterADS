# VISIBILIDADE

Os **especificadores de acesso** definem quais outras classes podem acessar seus atributos e métodos.

São eles:

| Visibilidade                  | *Public (+)* | *Protected (#)* | *Default* | *Private (-)* |
| ----------------------------- | ------------ | --------------- | --------- | --------- |
| Classe                        | **SIM**      | **SIM**         | **SIM**   | **SIM**   |
| Pacote                        | **SIM**      | **SIM**         | **SIM**   | NÃO       |
| Subclasse, mesmo pacote       | **SIM**      | **SIM**         | **SIM**   | NÃO       |
| Subclasse, pacotes diferentes | **SIM**      | **SIM**         | NÃO       | NÃO       |
| Global                        | **SIM**      | NÃO             | NÃO       | NÃO       |


- **Public:** acesso global.
- **Private:** só pode ser acessado internamente na classe.
- **Protected:** acesso por classes do mesmo pacote e subclasses (mesmo que fora do pacote)
- **Default**: acesso por classes do mesmo pacote 

![[Pasted image 20230501111605.png]]

# ENCAPSULAMENTO 

- O Paradigma Orientado a Objetos possui três pilares, **herança, polimorfismo e o encapsulamento**.

- O encapsulamento trata-se de um mecanismo em que as variáveis e o funcionamento interno de uma classe ficam "escondidas" de outras classes, e só podem ser acessadas através dos métodos que a classe proporciona (interface).

- Podemos utilizar os modificadores de acesso para esse fim e deixar visível o estritamente necessário

## VANTAGENS
- A possibilidade de acrescentar funcionalidades à classe desde que respeitando a interface original manterá o sistema funcional sem alterações.
-  Simplificação da utilização dos objetos em um alto nível acelera o desenvolvimento dos códigos.
-  O sistema fica robusto a mudanças internas
-  Ajuda a aumentar a divisão de responsabilidades (ou coesão) e, dessa forma, fica mais fácil e rápido desenvolver sistemas em módulos.

## GETTERS E SETTERS
- Uma boa prática em POO é deixar todas variáveis internas como privadas e oferecer métodos de acesso para as que convém.
- *getters* - retornam o valor do atributo
- *setters* - definem o valor do atributo conforme o parâmetros

```Java
public class Horario {
	private int hora;
	private int minuto;
	
	private int segundo;
	
	//setter
	public void setHora(int h) { 
		if (h> 23 || d<o){
			System.out.println("valor invalido");
		} else{
			hora= h;
		}
	//getter
	public int getHora(){
		return hora;
	}

```

# COLLECTIONS

- API que consiste em um conjunto de classes que implementam diferentes [[estruturas de dados]] 
- Quatro grupos principais de estrutura de dos
	- **LIST** - sequência ordenada de valores 
	 - **SET** - agrupamento de items sem ordem definida
	- **MAP** - mapeia chaves em valores
	- **QUEUE** - implementam um tipo de array em que a posição de cada elemento define a prioridade dele em relação aos demais

## Principais Classes

- **ArrayList** - array dinâmico, ordem definida e métodos de manipulação
- **LinkedList** - 
- **Hashset** - conjunto de elementos organizados por meio de uma função Hash (apenas chaves), não garante a ordem
- **LinkedHashSet** - semelhante ao HashSet, porém garante a ordem
- **HashMap** - armazena pares chave-valor, não garante a ordem
- **TreeMap**
- **LinkedHashMap** - semelhante ao HashMap, armazena a ordem
- **Queue** - estrutura de dados adotada para representar filas de prioridade
- **Stack** - semelhante a fila, mas implementa uma ordem reversa, último elemento adicionado é o primeiro a ser tratado - pilha

## HASHMAP

- Utiliza o conceito de *chave-valor*. A chave é o que indexa ela e o valor o conteúdo dentro daquele índice.
- Requer dois tipos de parâmetros, da chave e do valor - `Hashmap<Tipo1,Tipo2>`
- Adicionar elemento - método `put(chave, valor)`
- Recuperar um elemento - `get(chave)`
- Podemos acessar os valores das chaves utilizando o método `keySet()` com um *for-each loop*
- Acessar o conjunto de valores `values()`
- atribui valor da chave ou um valor default a uma variável - `getOrDefault(chave, default)` 

## EXEMPLO DE HASHSET

```Java
HashSet<String> nomes = new HashSet<String>();
nomes.add ("Mario");
nomes.add("Luigi");
nomes.add("Yoshi");
nomes.add("Mario");//Mario ja existe portanto ndo sera adicionado
nomes.add ("Peach");
nomes.remove( "Luigi");//remove luigi

System.out.println(nomes);//Imprime todos os nomes

int total = nomes.size();//descobre total de itens

if(nomes.contains("Luigi")) {//Confere se existe
	System.out.println("Ele esta presente”);

}else {
	System.out.println("Ndo esta presente”);

}

```

## EXEMPLO DE PRIORITYQUEUE

- Armazenam dados se preocupando de forma muito restrita com a ordem
- É indicado adotar esse tipo de estrutura quando temos dois tipos de entidades distintas, um tipo produzindo algum tipo de dado e outro consumindo os dados. (ex.: fila impressora)

```Java
// Criando a fila

PriorityQueue<Integer> fila = new PriorityQueue<Integer>();

// adicionando elementos para fila usando add()
fila.add(10);

fila.add(20);
fila.add(15);
// Imprimindo o elemento do topo da fila

System.out.println(fila.peek());

//Imprimindo e ao mesmo tempo removendo o primeiro elemento

System.out.println(fila.poll());

// Imprimindo o elemento do topo novamente

System.out.println(fila.peek());


```

## Métodos Estáticos Collections

- **Sort(List<> lista)**: coloca em ordem crescente os itens da lista passada por parâmetro.
- **Shuffle (List<> lista, Random rnd)**: embaralha de forma aleatória os elementos da lista passada por parâmetro
- **Max (Collection<> coll, Comparator<> comp)**: retorna o maior elemento, aceita tanto lista, quanto hash. Como segundo parâmetro, você pode indicar como deseja realizar a comparação com um objeto da classe Comparator, caso passe null como segundo parâmetro, a ordem natural será adotada.
-  **Min (Collection<> coll, Comparator<> comp):** análogo ao max, porém, retorna o menor elemento.
- **Reverse (List<> lista)**: coloca todos os itens em ordem reversa.

```Java
// cria uma lista de string

ArraylList<String> lista = new ArrayList<String>();
lista.add("Mario");
lista.add("Luigi");
lista.add("voshi");
lista.add("Toad");
lista.add("Peach”);

//Imprime a lista na ordem original

System.out.println(lista);

//Coloca lista em uma ordem aleatéria
Collections.shuffle(lista);
System.out.println(lista);

//Coloca lista em uma ordem alfabética
Collections.sort(lista);
System.out.println(lista);

//Inverte a ordem anterior da lista
Collections.reverse(lista);
System.out.println(lista);

//Maior elemento alfabético

System.out.println("Maior: "+ Collections.max(lista));

//Menor elemento alfabético

System.out.println("Menor: "+Collections.min(lista));


```

# ITERATOR 

 - O iterator é uma espécie de ponteiro para o elemento da Collection
	 - Inicialmente aponta para primeiro item, e para o próximo, assim por diante, até passar por todos objetos 
- O  método `hasNext()` verifica se existe um próximo elemento e retorna verdadeiro ou falso 
- O método `next()` atualiza o iterador par ao próximo item da coleção 

```Java
ArraylList<Integer> lista = new ArrayList();
HashsSet<Integer> conjunto = new HashSet<Integer>();
HashMap<String,Integer> mapa = new HashMap<String, Integer>();

int soma;


soma=0;//Iterator

//Iterator it = mapa.entryset().iterator();
//Iterator it = conjunto.iterator();
Iterator it = lista.iterator();
while(it.hasNext()) {
	soma += (int)it.next();
}

```

- Como os ponteiros iteradores podem apontar para qualquer tipo primitivo ou objeto, é necessário indicar ao compilador como aquele item deve ser interpretado, no caso (int) -  *[[type-casting]]* 
	- obs: since Java 5, autoboxing and unboxing features were added to the language, which allows automatic conversion between primitive types and their corresponding wrapper classes.

## LISTITERATOR
- Age sobre listas, permite métodos que necessitam de uma ordem sequencial de dados
- O  método `hasPrevious()` verifica se existe um elemento anterior e retorna verdadeiro ou falso 
- `previous()` -  retorna o iterator em si da posição anterior
- `remove()` - remove um elemento

# CLASSE LOCALDATE

- Biblioteca `java.util.LocalDate `
- Cada data é um objeto LocalDate
- `.now()` recupera a data no momento da execução do código
- `DateTimeFormatter` estabelece formatações para datas e horários
	• dd = dia do mês em dois dígitos;
	• MM = mês em dois dígitos;
	• yyyy = ano em quatro dígitos;
	• HH = horas, até 23, em dois dígitos;
	• mm = minutos em dois dígitos;
	• ss = segundos em dois dígitos;
	• hh = horas, até 12, em dois dígitos;
	• d = dia do mês em um ou dois dígitos;
	• M = mês do ano em um ou dois dígitos;
	• yy = ano em dois dígitos;
	• H = horas, até 23, em um ou dois dígitos;
	• m = minutos em um ou dois dígitos;
	• s = segundos em um ou dois dígitos;
	• h = horas, até 12, em um ou dois dígitos.

``` Java
public static void main(String[] args) {

//Captura a data de hoje
LocalDate dataHoje = LocalDate.now();

System.out.println("original: " + dataHoje);
DateTimeFormatter formatador = DateTimeFormatter.ofPattern("dd/MM/yyyy");
String dataForm= hoje.format(formatador);

System.out.println("Formatado : " + dataForm);
}

```
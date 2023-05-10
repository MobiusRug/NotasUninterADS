# HERANÇA

- É possível que uma classe (filha) herde comportamentos (métodos) e características (atributos) de outra classe (mãe), e nessa relação a classe filha pode ter suas características e comportamentos únicos também
- Toda classe Java herda a classe Objeto
- Para definir herança utilizamos a palavra chave `extends`
- Podemos invocar o construtor da classe mãe na filha utilizando `super()` - precisa ser usado na primeira linha do construtor 

```java
public class Mae{
	private String atribute1;
	private String atribute2;

	public Mae(String atribute1, String atribute2){
		this.atribute1 = atribute1;
		this.atribute2 = atribute2;
	}
}


public class Filha extends Mae {
	private int atribute3;
	
	public Filha(String atribute1; String atribute2; int atribute3){
		super(atribute1, atribute2);
		this.attribute3 = atribute3;
	}
}
```

- O comando `super` faz uma referência explícita à superclasse, à classe herdada, semelhante à palavra `this `que faz referência explícita à classe corrente.
-  quando não colocamos explicitamente a chamada de um construtor da classe mãe o construtor vazio da classe mãe é chamado de forma implícita na primeira linha do construtor da classe filha
- A tipagem também é herdada - as classes filhas são consideradas do tipo da classe mãe também
- comando `instanceof` - identificar se uma determinada instância pertence a determinada classe, ele retorna true ou false caso seja ou não uma instância - `filha instaceof Mae`
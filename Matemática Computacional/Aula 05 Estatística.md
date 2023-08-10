# ESTATÍSTICA DESCRITIVA

## MÉDIA
- Número que representa a tendência central de um conjunto de dados 
$$
\bar{x} = \frac{1}{n}\sum_{i=1}^{n} x_i
$$
## MODA
-  está associada ao dado que aparece o maior número de vezes em determinado conjunto. 
-  Se não houver dados que se repetem, não há moda, e o conjunto é chamado de *amodal*

## MEDIANA 
- representa o valor central de um conjunto de dados ordenados.
- Caso tenhamos um número par de elementos, se dá pela média dos dois elementos centrais

## PYTHON
- A biblioteca *pandas* fornece as funções *mean*, *mode* e *median*
- Exemplo
```python
import pandas as pd
x={'Pesos':[48.8, 48.9, 49.0, 49.1, 49.2, 49.3, 49.5, 49.7, 49.7, 49.7, 49.8, 50.0, 50.1, 50.1, 50.2, 50.2, 50.4, 50.6, 50.8, 50.9]}

p=pd.DataFrame(x)
media=p['Pesos'].mean()
moda=p['Pesos'].mode()
mediana=p['Pesos'].median()
print(f'Média: {media}')
print(f'Moda: {moda}')
print(f'Mediana: {mediana}')

```

```output
Média: 49.8
Moda: 0    49.7
Name: Pesos, dtype: float64
Mediana: 49.75
```

## VARIÂNCIA

- A fórmula da variância é uma medida estatística que representa a dispersão ou variabilidade dos dados em relação à média
- Se estivermos trabalhando com uma população completa, tempos:

$$
\sigma² = \frac{\sum(x_i - \mu )²}{N}
$$

- Para uma amostra temos
- $$
\sigma² = \frac{\sum(x_i - \bar{x} )²}{n-1}
$$
- quando calculamos a média amostral $\large \bar{x}$, estamos utilizando a média da amostra como uma estimativa da média populacional $\large \mu$. No entanto, a média amostral tende a subestimar a variabilidade real dos dados em relação à média populacional. A utilização de n-1 é conhecida como *correção de Bessel* que compensa essa subestimação

## DESVIO PADRÃO

- O desvio padrão indica a amplitude de uma faixa com centro na média que concentra a maior parte dos dados, geralmente 65% a 80% dos dados
- É calculado pela raiz quadrada da variância 

### PYTHON
- A biblioteca Pandas fornece a função std() para cálculo do desvio padrão

```python
import pandas as pd
x={'Pesos':[48.8, 48.9, 49.0, 49.1, 49.2, 49.3, 49.5, 49.7,
49.7, 49.7, 49.8, 50.0, 50.1, 50.1, 50.2, 50.2, 50.4, 50.6,
50.8, 50.9]}
p=pd.DataFrame(x)
desviopadrao=p['Pesos'].std()
print(f'Desvio padrão: {desviopadrao}')
```

```output
Desvio padrão: 0.6249210476447995
```


# PROBABILIDADE

- A probabilidade é uma medida numérica que representa a chance de um evento ocorrer ,
- A probabilidade P de ocorrência de um fato A, chamada de P(A), corresponde à divisão do número de elementos n do evento A pelo número N de elementos do espaço amostral

$$
P(A) = \frac{n}{N}
$$
- **Distribuição de probabilidade** - função matemática que descreve a probabilidade de ocorrência de diferentes resultados em um conjunto de eventos ou experimentos
- Uma das distribuições mais comum é distribuição normal - Gaussiana

![[Pasted image 20230606093502.png| 700]]

- **z-score** - representa o número de desvios padrão que um valor está acima ou abaixo da média.

$$
z = \frac{x - \bar{x}}{\sigma}
$$

![[Pasted image 20230606095833.png|750]]


### PYTHON

- Podemos utilizar o Python para resolver problemas relacionados a uma distribuição normal por meio da função norm. Utilizaremos a opção cdf que está associada a uma distribuição normal cumulativa. Neste caso, quando z = 1, por exemplo, o resultado apresentado pelo Python considera a porção abaixo da média que corresponde a 50% mais a porção associada a z = 1 que é igual a 34,13%, totalizando 84,13%.
- para valores de X acima da média , podemos fazer:

```PYTHON
import scipy.stats
media=
desvio_padrao=
X=
p=scipy.stats.norm(media,desvio_padrao).cdf(X)-0.5
print(p)
```

- E para valores de X abaixo da média
```PYTHON
import scipy.stats
media=
desvio_padrao=
X=
p=0.5-scipy.stats.norm(media,desvio_padrao).cdf(X)
print(p)
```

# ESTATÍSTICA INDUTIVA 

- **População** - associada ao conjunto formado por todos os dados relacionados a um fenômeno.
- **Amostra** - subconjunto da população
	- **Aleatória simples** -conjunto de elementos selecionados de forma completamente aleatória de uma população, com cada elemento da população tendo a mesma chance de ser escolhido, sem qualquer tipo de viés ou padrão predefinido.
	- **Estratificada** - é um conjunto de elementos selecionados de uma população dividida em grupos homogêneos (*estratos*), onde cada grupo é representado de forma proporcional na amostra, garantindo que as características de interesse de cada estrato sejam adequadamente refletidas.
	- **Por agrupamento** é um método de seleção de amostras onde a população é dividida em grupos (ou clusters) e, em seguida, alguns grupos são selecionados aleatoriamente para compor a amostra (todo o grupo), em vez de selecionar indivíduos isolados.
	- **Sistemática** - método de seleção de amostras em que os elementos da população são escolhidos de forma sistemática, com base em um *intervalo fixo*, garantindo uma representação equitativa dos elementos ao longo da população.

- **Fórmula de Slovin** para escolha do tamanho de uma amostra de uma população N com margem de erro $e$ aceitável:

$$
n = \frac{N}{1 + Ne²}
$$
# CONFIANÇA

## DESVIO PADRÃO DA MÉDIA

$$
\sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}}
$$

## INTERVALO DE CONFIANÇA
- Define o intervalo que a média real deve ser encontrada associada com uma probabilidade (10+- 2  com 95% indica que há 95% de confiança de que a média real da população está entre -8 e 12)

$$
\bar{x} - c \leq \mu \leq \bar{x} + c
$$

onde:
$$
c = z\sigma_{\bar{x}}
$$
utilizando o z específico para o grau de confiança desejado (ex.: para 95% temos z = 1.96)
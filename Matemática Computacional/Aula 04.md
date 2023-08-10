# CONJUNTOS

## NATURAIS
$$
\mathbb{N} = \{0, 1, 2, 3, \ldots \}
$$

## INTEIROS
$$
\mathbb{Z} = \{\ldots, -3, -2, -1, 0, 1, 2, 3, \ldots \}
$$


## RACIONAIS
$$
\mathbb{Q} = {\frac{a}{b}, a \in \mathbb{Z}, b \in \mathbb{Z}, b \neq 0}
$$

## IRRACIONAIS
- são aqueles que não podem ser expressos como uma fração de dois inteiros

## REAIS

$$
\mathbb{R} = \mathbb{Q} \cup \mathbb{I}
$$


- A cada número real, temos um ponto associado a uma reta, conhecida como reta dos reais, e a cada ponto da reta temos um número real associado.
- O conjunto dos reais é contínuo -  é formado por infinitos números consecutivos


# VETORES E MATRIZES

## VETORES
- Em geometria é uma entidade matemática que representa uma quantidade com magnitude, direção e sentido.
	- Pode ser representado graficamente por meio de uma seta 
- No contexto da ciência da computação, um vetor é uma estrutura de dados que armazena uma sequência ordenada de elementos 
- No contexto da matemática é um elemento do espaço vetorial, definido por várias propriedades que deve obedecer como adição de vetores e multiplicação por um escalar

### PYTHON
- Python não possui um suporte nativo para vetores, sendo necessário utilizar a biblioteca numpy que possui uma função para transformar uma lista em um array

```python
import numpy as np
v=np.array([[2, 4, 5, 9]])
print(v)
```

```output
[[2 4 5 9]]
```

- É possível realizar as operações de soma de vetores e multiplicação por escalar dessa maneira
- Podemos realizar o *produto escalar* utilizando a função `inner()` 

```python
import numpy as np
notas=np.array([[90, 85, 70, 100]])
pesos=np.array([[0.2, 0.2, 0.3, 0.3]])
media=np.inner(notas, pesos)
print(media)
```

- É possível representar matrizes utilizando arrays aninhados 

```python
import numpy as np
A=np.array([[3, 2, -1],[5, 0, 20]])
print(A)
```

```output
[[ 3 2 -1]
 [ 5 0 20]]
```

- Utilizando numpy é possível somar matrizes e multiplicar por escalar normalmente
- Para multiplicação é possível utilizar a função `matmul()`

```python
import numpy as np
A=np.array([[3, 1, 3],[6, 5, 5]])
B=np.array([[100, 50],[50, 100],[50, 50]])
C=np.matmul(A, B)
print(C)
```

```output
[[ 500 400]
[1100 1050]]
```


# FUNÇÕES 

- uma função é uma relação entre um conjunto de entrada (*domínio*) e um conjunto de saída (*contradomínio*) que associa a cada elemento do domínio um único elemento do contradomínio
-  cada elemento do domínio, o conjunto dos possíveis valores da variável independente x precisa estar relacionado a um único elemento do contradomínio, conjunto das variáveis dependentes.
- Todos os elementos do contradomínio que estão relacionados aos elementos do domínio formam um conjunto chamado de *conjunto imagem*
![[Pasted image 20230605092311.png]]


### FUNÇÃO LINEAR

$$ 
y = ax +b
$$

### FUNÇÃO QUADRÁTICA

$$
y = ax^{2} +bx +c
$$

O valor de x associado ao vértice da parábola é dado por:

$$
x_v = \frac{-b}{2a}
$$

O valor de y referente ao vértice é dado por:

$$
y_v = \frac{-\Delta}{4a}
$$



### PYTHON
- Podemos mapear graficamente as funções utilizando a biblioteca `matplotlib.pyplot`
- `linspace()` -  gera um determinado número de valores para x igualmente espaçados em um determinado intervalo.
- `x = np.linspace(min,max,quantidade de valores)`

```python
import matplotlib.pyplot as plt
import numpy as np
x=np.linspace(0, 10, 100)
y=28*x
plt.plot(x,y)
plt.show()
```

![[Pasted image 20230605092919.png| 700]]


# POLINÔMIOS

$$
p(x) = a_nx^n + a_{n-1}x^{n-1} + \ldots + a_2x^2 + a_1x + a_0
$$

- **Interpolação polinomial** - A partir de um conjunto de pontos,obter o polinômio que passa por estes pontos
- Em python podemos utilizar a função `lagrange()` da biblioteca `scipy`

```python
from scipy.interpolate import *
x=[]
y=[]
p=lagrange(x, y)
print(p)
```

# ARITMÉTICA MODULAR 
- é um sistema de aritmética para inteiros, onde os números "retrocedem" quando atingem um certo valor, o **módulo**
- Dado um inteiro $n>1$ , chamado módulo, dois inteiros são considerados *congruentes* (ou côngruos) módulo $n$ n, se $n$  for um divisor de sua diferença (ou seja, se houver um inteiro $k$ tal que $\large a − b = k n$ ).
$$
a \equiv b \pmod{n}
$$

Ex: $\large 15 \equiv 3 \pmod{12}$, 3 é o resto da divisão de 15 por 12

# NORMA IEEE 754

- A norma IEEE 754 é um padrão para representação de números de ponto flutuante.
- Define um formato binário para representar a mantissa, expoente e sinal.
- Permite a representação de números com precisão simples (32 bits) e precisão dupla (64 bits).
- Especifica métodos de arredondamento e tratamento de exceções.
- Garante portabilidade e consistência dos resultados em diferentes plataformas.

# REPRESENTAÇÃO DE NÚMEROS REAIS 

- Em representações computacionais há uma quantidade fixa de bits e  consequentemente, um conjunto finito de números que podem ser representados por meio de computadores, o que leva a imprecisões nas representações de números irracionais

## NOTAÇÃO CIENTÍFICA
- Notação científica:
$$
 x = \pm (M)_b \times b^n 
$$
-  **Notação científica normalizada** -  o número representado terá apenas um dígito antes do separador de casas decimais
- É possível usar o comando `print` com o parâmetro `% . Xe`, onde "X" indica a quantidade de dígitos a serem exibidos após o separador de casas decimais e "e" indica a notação científica normalizada.

```python
a = 3242

print('%.10e' % a )
```

```output
3.2420000000e+03
```
- Utilizando f-string:
```python
print(f'{0.0000054:.4e}')
```

```output
5.4000e-06
```

## REPRESENTAÇÃO NÚMEROS REAIS NORMA IEEE 754


| Sinal | Expoente | Mantissa                |
| ----- | -------- | ----------------------- |
| 1     | 11111111 | 11111111111111111111111 |

- **Representação Simples** - 32 bits
- primeiro bit está associado ao sinal do número (0 quando positivo ou 1 quando negativo). Os oito bits seguintes se referem ao expoente que desta forma pode variar de -126 a 127 e os 23 bits restantes correspondem à mantissa
- Permite 7 casas decimais

- **Representação Dupla** - 64 bits
- são utilizados 64 bits com 11 bits para o expoente e 52 bits para a mantissa
- permite 16 casas decimais

- **Representação Estendida** - 80 bits
- 15 bits para o expoente e 64 bits para a mantissa
- Permite 20 casas decimais 

![[Pasted image 20230603163453.png]]

- Descobrindo maior e menor float possível com Python:
```python
import sys

sys.float_info.min
sys.float_info.max
```

------

### EXEMPLO
To clarify, here is the correct representation of 0.15625 in binary using the IEEE 754 standard:

0.15625 * 2 = 0.3125 (integer part: 0) 0.3125 * 2 = 0.625 (integer part: 0) 0.625 * 2 = 1.25 (integer part: 1) 0.25 * 2 = 0.5 (integer part: 0) 0.5 * 2 = 1.0 (integer part: 1)

So, the binary representation of 0.15625 is 0.00101.

In the 32-bit representation, considering the sign bit (0 for positive), biased exponent (3 + 127 = 130 in binary: 10000010), and the mantissa (01), the complete 32-bit representation would be:

0 10000010 00100000000000000000000

------------


- A precisão da máquina, denotada por *p*, é dada pelo número de dígitos significativos (mantissa + sinal)que são usados para a representação de um número.
- **épsilon da máquina**, representado por $\Large ε_{mach}$ . Por definição, 1 + $\Large ε_{mach}$ é o menor número representável maior do que 1
- Quando um determinado número é muito pequeno, geralmente é aproximado por zero. Essa ocorrência é chamada de *underflow.*
- Quando há um número muito grande (*overflow*), o processamento é interrompido
- números extremamente pequenos estão próximos entre si e números extremamente grandes estão distantes entre si -  o espaçamento não é uniforme

# ARITMÉTICA DO PONTO FLUTUANTE 

- **SOMA E SUBTRAÇÃO**
	- Expoentes iguais - basta realizar a operação
	- Expoentes diferentes - ajustamos o de menor valor de modo a obtermos um número equivalente cujo expoente é igual ao de maior valor. Após a realização da soma, efetuamos a normalização quando necessário
- **MULTIPLICAÇÃO**
	- multiplicamos as mantissas e somamos os expoentes
	- normalizar o resultado
- **DIVISÃO**
	- dividir as mantissas e subtrair os expoentes
	- normalizar o resultado

# REPRESENTAÇÃO DE ERROS

## ERRO ABSOLUTO
- módulo da diferença entre o valor exato e o valor aproximado:

$$
E_A = |x - \bar{x}|
$$

## ERRO RELATIVO
- Divisão do erro absoluto pelo módulo do valor exato

$$
E_A = \frac{|x - \bar{x}|}{|x|}, x \neq 0
$$

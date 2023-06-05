# SISTEMAS NUMÉRICOS 

- Dada a base numérica b temos

$$
(a_na_{n-1} \ldots a_1a_0.c_1c_2c_3 \ldots)_b = \sum_{k=0}^{n}a_kb^k + \sum_{k=1}^{\infty}c_kb^{-k}
$$
## BINÁRIO
- Dois algarismos - 0,1
- **Conversão decimal-binário:** Decomposição por potências de 2
- Atalho de conversão:
	- Para transformarmos um número decimal em binário, precisamos efetuar todas as sucessivas divisões por 2 do número decimal a ser convertido e considerarmos, de trás para a frente, os respectivos restos de cada divisão realizada.

![[Pasted image 20230531182700.png]]


- **Conversão octal - binário** - se dá a partir da tradução de cada algarismo em octal para um conjunto de três bits (2 3 = 8 possibilidades), começando sempre pela direita.

| Octal   | 2   | 5   | 1   | 7   | 3   |
| ------- | --- | --- | --- | --- | --- |
| Binário | 010 | 101 | 001 | 111 | 011 |
- 25173 (Octal) é 010101001111011 (Binário)


- Vale o inverso - um número binário pode ser separado de três em três bits para ser convertido em octal, sempre começando pela direita (parte inteira)

- **Conversão para hexadecimal** - se dá de modo semelhante,  com um conjunto de 4 bits (24 = 16 possibilidades), começar pela direita (parte inteira).

| Hexadecimal | A    | F    | C    | 0    | 2    |
| ----------- | ---- | ---- | ---- | ---- | ---- |
| Binário     | 1010 | 1111 | 1100 | 0000 | 0010 |

## OCTAL

- Utiliza 8 algarismos diferentes para representar os números - 0 a 7
- Para fazer a conversão **decimal-octal** é mais fácil fazer uma conversão intermediária para binário 
- Ex.: 3289 = 2048 + 1024 + 128 + 64 + 16 +8 + 1 = 110011011001

| Binário | 110 | 011 | 011 | 001 |
| ------- | --- | --- | --- | --- |
| Octal   | 6   | 3   | 3   | 1   | 

## HEXADECIMAL 

- Utiliza 16 algarismos 0 a 9, A a F
- Para fazer a conversão **decimal-hexadecimal** é mais fácil fazer uma conversão intermediária para binário 
- São precedidos de 0x (ex 0xFA)
- Ex.: 861 = 512 + 256 + 64 + 16 + 8 + 4 + 1, ou seja, em binário é igual a 1101011101;

| Binário     | 0011 | 0101 | 1101 |
| ----------- | ---- | ---- | ---- |
| Hexadecimal | 3    | 5    | D     |
- O número decimal 861 é igual a 35D em hexadecimal.

# CONVERSÃO DE BASE EM PYTHON 

- Para a conversão de um número decimal inteiro em um binário, temos a função `bin()`

```PYTHON
bin(25)
```

```output
'ob11001'
```

- Para obtermos apenas os termos correspondentes à forma binária, podemos considerar a string sem os dois primeiros termos

```python
bin(25)[2:]
```

```output
'11001'
```

- Para hexadecimais temos `hex()`

```python
hex(11868)
```

```output
'Ox2e5c'
```

```python
hex(11868)[2:]
```

```output
'2e5c'
```


# ARITMÉTICA BINÁRIA

- A soma de dois números binários segue o mesmo princípio da soma de números decimais, mas é importante lembrar que na soma de números binários 1+1=10.
- Nos passos intermediários no caso da necessidade de somar 1+1  escrevemos o último dígito como sendo 0 e o 1 é adicionado à próxima soma

![[Pasted image 20230531192437.png]]

- Se estamos trabalhando com 4 bits e o resultado é um número com 5 bits, a informação será perdida. 

## NÚMERO NEGATIVOS 

- Ideia inicial - utilizar o primeiro bit para indicar o sinal, 1 negativo, 0 positivo 
- Apenas com isso as operações aritméticas não fornecem resultados corretos
- **Complemento de 1** -a forma de representação de números binários negativos em que o primeiro bit indica o sinal, sendo 0 para positivo e 1 para negativo, e os demais bits são invertidos em relação à representação do número positivo correspondente.
	- problema - duas representações para o 0 (ex 0000 e 11111)
- **Complemento de 2** - os bits são invertidos em relação à representação do número positivo correspondente e, em seguida, adiciona-se 1 ao resultado obtido pela inversão.
- Ex -4 em 8 bits
	- 4 = 00000100
	- invertendo bits - 11111011
	- somando 1 - 11111100 (representação de -4 utilizando complemento de 2)
	- 5-4 = 00000101 + 11111100 = 00000001
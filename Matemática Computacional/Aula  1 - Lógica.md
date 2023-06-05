# PROPOSIÇÕES

- **proposições** - um conjunto de palavras ou símbolos que retratam um pensamento de sentido completo e que pode ser classificado como *verdadeiro* ou *falso*.

> [!PRINCÍPIOS DA LÓGICA]
> I.  **Princípio da não contradição:** uma proposição não pode ser classificada como verdadeira e falsa simultaneamente.
   II. **Princípio do terceiro excluído**: uma proposição é verdadeira ou falsa, e não existe a possibilidade de um terceiro caso.

- **Valor lógico de uma preposição** 
	- verdade (V ou 1)
	- falsidade (F ou 0)

- **Proposição simples** - p é dita simples se p não contém nenhuma outra proposição como parte integrante de si mesma
	-  são representadas por letras minúsculas *p, q, r*..., denominadas *letras proposicionais*.
- **Proposição composta** - formada pela combinação, por meio de conectivos, de uma ou mais proposições simples
	- representadas por letras maiúsculas *P,Q,R* 


# OPERADORES LÓGICOS

## NEGAÇÃO (~)

- Conectivo *não*
- A negação de uma proposição *p* é a proposição *~p*, dita “não p” - inverte o valor lógico 

| p   | ~p  |
| --- | --- |
| V   | F   |
| F   | V    |

![[Pasted image 20230531144550.png | 500]]

![[Pasted image 20230531144630.png | 500]]

## CONJUNÇÃO (∧)

- Conectivo *e*
-  A conjunção de duas proposições p e q, representada por *p∧q* ou por p.q 
- é verdadeira sempre que p e q são verdadeiras. Nos demais casos, a conjunção é falsa.

| p   | q   | p∧q |
| --- | --- | --- |
| V   | V   | V   |
| V   | F   | F   |
| F   | V   | F   |
| F   | F   | F   |

![[Pasted image 20230531145611.png | 500]]

![[Pasted image 20230531145633.png|500]]

## Disjunção (∨)

- Conectivo *ou* 
- A disjunção de duas proposições p e q é verdadeira quando pelo menos uma das proposições é verdadeira. 

| p   | q   | p∨q |
| --- | --- | --- |
| V   | V   | V   |
| V   | F   | V   |
| F   | V   | V   |
| F   | F   | F   |

![[Pasted image 20230531145906.png|500]]

![[Pasted image 20230531145932.png|500]]

## DISJUNÇÃO EXCLUSIVA XOR ( ⊕)

- Conectivo *ou...ou*
-  é verdadeira apenas quando p e q possuem valores lógicos diferentes:

| p   | q   | p⊕q |
| --- | --- | --- |
| V   | V   | F   |
| V   | F   | V   |
| F   | V   | V   |
| F   | F   | F   |

![[Pasted image 20230531150344.png|500]]

![[Pasted image 20230531150400.png|500]]


## CONDICIONAL (→)

- Conectivo  *“se..., então...”*
- O valor lógico da condicional é a falsidade quando p é uma proposição verdadeira e q uma proposição falsa. Nos demais casos, a condicional é verdadeira

| p   | q   | p→q |
| --- | --- | --- |
| V   | V   | V   |
| V   | F   | F   |
| F   | V   | V   |
| F   | F   | V   |

## Bicondicional (↔)

- Conectivo *“...se e somente se...”*
- A bicondicional é verdadeira quando as duas proposições possuem o mesmo valor lógico e é falsa quando as duas proposições possuem valores lógicos diferentes.

| p   | q   | p→q |
| --- | --- | --- |
| V   | V   | V   |
| V   | F   | F   |
| F   | V   | F   |
| F   | F   | V   |

# PROPRIEDADES

### DUPLA NEGAÇÃO


$$
\Large \neg(\neg p)⇔ p
$$
### LEIS IDEMPOTENTES

$$
\Large p\lor p⇔ p 
$$
$$
\Large p \land p⇔ p
$$

### COMUTATIVIDADE

$$
\Large p \lor q⇔ q \lor p
$$$$
\Large p \land q⇔ q \land p
$$
### ASSOCIATIVIDADE

$$
\Large (p \lor q) \lor r⇔ p \lor  (q \lor r)
$$

$$
\Large (p \land q) \land r⇔ p \land (q \land r)
$$

### DISTRIBUTIVIDADE

$$
\Large p \land (q \lor r)⇔ (p \land q) \lor (p \lor r)
$$
$$
\Large p \lor (q \land r)⇔ (p \lor q)  \land  (p \lor r)
$$

### LEIS DE MORGAN

$$
\Large \neg(p \lor q)⇔ \neg(p) \land \neg(q)
$$
$$
\Large \neg(p \land q)⇔ \neg(p) \lor \neg(q)
$$

### CONTRAPOSITIVA

$$
\Large p \rightarrow q⇔ \neg q \rightarrow \neg p
$$

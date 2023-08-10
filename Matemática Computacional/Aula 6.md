# CRIPTOGRAFIA

- Processo de transformar um texto plano (*plain text*) em um texto cifrado (*cipher text*) por meio de um algoritmo criptográfico (*cifra*)
- Normalmente é utilizada uma *chave* numérica que quando aplicada ao texto plano gera uma modificação reversível

# CHAVES SIMÉTRICAS 

- A mesma chave é utilizada para a cifragem e para a decifragem do texto.
- ***Cifra de Substituição*** - fazem a substituição de um símbolo da mensagem por outro símbolo (ex. cifra de césar, palavra-chave).
	- Quanto a quantidade de alfabetos utilizados as cifras de substituição podem ser *monoalfabéticas* ou *polialfabéticas*
- ***Cifra de Transposição*** - A chave é uma relação entre as letras do texto plano e do texto criptografado (alterar ordem conforme chave).
- Cifras atuais utilizam operações bit a bit
	- ex.: XOR, utiliza o ou exclusivo na comparação dos bits do texto plano com os bits da chave e, assim, gera o texto cifrado
	- deslocamento para a direito ou para a esquerda os bits de um símbolo ou bloco

## CIFRA DE CESAR

```PYTHON
from string import ascii_uppercase
a=list(ascii_uppercase) # armazena A a Z ['A', 'B', 'C' ... 'Z']
m=input('Digite a mensagem: ')
m=m.upper()
mc=""
for l in m:
i=ord(l)-65 #ord(retorna o código unicode de l), subtrai 65 para ficar no intervalo 0 a 25 (A = 65)
if l in a:
mc+=a[(i+3)%26]#desloca cada letra 3 casas módulo 26, ou seja, ao chegar em Z volta para A
else:
l
print(f'Mensagem criptografada: {mc}')
```

# CHAVES ASSIMÉTRICAS

- há duas chaves diferentes entre si: uma pública, que é utilizada para cifrar a mensagem, e uma privada para decifrar a mensagem.
- elas são independentes e assim não é possível obter a chave privada conhecendo a pública


## CRIPTOGRAFIA RSA 

- Letras são substituídas por 2 dígitos 

Passo 1: Selecione dois números primos distintos, p e q. Esses números devem ser primos grandes e aleatórios.

Passo 2: Calcule o módulo, n, multiplicando p e q: n = p * q.

Passo 3: Calcule a função totiente de Euler, φ(n), que é o número de inteiros positivos menores que n e coprimos (primos entre si) com n. Para dois primos distintos, φ(n) = (p - 1) * (q - 1).
- a e b são coprimos se MDC(a,b) = 1

Passo 4: Escolha um número inteiro e tal que 1 < e < φ(n), e e seja coprimo com φ(n). Esse valor será o expoente público.

Passo 5: Calcule o inverso multiplicativo modular de e módulo φ(n). Isso significa encontrar um número d tal que (d * e) mod φ(n) = 1. O valor de d será o expoente privado.

Passo 6: A chave pública é (e, n). Ela consiste no expoente público e no módulo.

Passo 7: A chave privada é (d, n). Ela consiste no expoente privado e no módulo.

- Criptografia:
	- Texto claro: D (convertido em número) < n
	- Texto cifrado: $C = M^e \bmod n$   

- Descriptografia
	- $D \equiv C^d \bmod n$ 

### ALGORITMO DE EUCLIDES PARA ENCONTRAR O MDC

- MDC(a,b)=MDC(b,r) ( = MDC(r, r2))
- se d divide a e b, é fácil entender que b também divide a-b, e também a%b (lembre-se que a divisão é uma sucessão de subtrações)
- Sendo $a, b \in \mathbb{N}$ , se fizermos repetidamente as divisões:
$$
\begin{aligned}
a &= bq_1 + r_1 \\
b &= r_1q_2 + r_2 \\
r_1 &= r_2q_3 + r_3 \\
&\vdots \\
r_{n-3} &= r_{n-2}q_{n-1} + r_{n-1}\\
r_{n-2} &= r_{n-1}q_n + 0
\end{aligned}
$$

Então $r_{n-1} = MDC(a,b)$


- Notice that the sequence $\{r_1,r_2, r_3, \ldots\} \in \mathbb{N}$ is decreasing, thus it truncates, say at $r_{n-1}$
- $r_{n-1}$ divide $r_{n-2}$ consequentemente $\large \frac{r_{n-3}}{r_{n-1}}$ é um inteiro, logo $r_{n-1}$ também divide $r_{n-3}$, o que eventualmente implicará em $r_{n-1}$ ser divisor de $a$ e $b$
- Suponha que $d$ seja divisor de $a$ e $b$ , logo $d$ é também divisor de $r_{1}$ (pois $a = bq_1 + r_{1}$), porém isso implica que $d$ também é divisor de $r_2$, e assim sucessivamente, e, portanto $d$ é divisor de $r_{n-1}$, logo, $d \leq r_{n-1}$   

### PYTHON
- O Python possui uma biblioteca destinada à criptografia RSA (instalação - `pip install rsa`)
-
```python
import rsa

chavepublica, chaveprivada = rsa.newkeys(512) #rsa.newkeys() gera as chaves

m = input("Digite a mensagem")
mc = rsa.encrypt(m.encode(), chavepublica)
print("Mensagem original:", m)
print("Mensagem criptografada:", mc)
md=rsa.decrypt(mc,chaveprivada).decode()
print("Mensagem descriptografada:", md)
```


# ASSINATURA DIGITAL

- Uma assinatura digital está baseada na criptografia de chaves públicas e vem na forma de código juntamente com os dados
- Por meio de uma chave privada (chave de assinatura), a assinatura é criada pelo remetente e o receptor, por meio de uma chave pública (chave de verificação), tem acesso aos dados descriptografados.
- Primeiro a mensagem a ser enviada passa por um algoritmo de hash, o hash gerado é criptografado com a chave privada do remetente gerando a assinatura digital 
- O receptor também faz o hash do texto recebido, descriptografa a assinatura e compara os dois hashs
- A assinatura digital garante a **autenticidade, a integridade e o não-repúdio**

### PYTHON
- É possível criar assinaturas digitais com a biblioteca pycrypto (`pip install pycrypto`)

```python
from Crypto.Hash import SHA256
from Crypto.PublicKey import RSA
from Crypto import Random
semente=Random.new().read
chaves=RSA.generate(1024,semente)
publica=chaves.publickey()
texto1='Estudo Java'
texto2='Estudo Python'
hash1=SHA256.new(texto1.encode('utf-8')).digest()
assinatura=chaves.sign(hash1, '')
print('Hash 1: '+repr(hash1))
print('Assinatura Digital: '+repr(assinatura))
hash2=SHA256.new(texto1.encode('utf-8')).digest()
hash3=SHA256.new(texto2.encode('utf-8')).digest()
print('Hash 2: '+repr(hash3))
print('Hash 3: '+repr(hash3))
if(publica.verify(hash2, assinatura)):
print('Texto verdadeiro: '+texto1)
elif(publica.verify(hash3, assinatura)):
print('Texto verdadeiro: '+texto2)
```

```output
Hash 1:
b'\xf6}\\\xc1\xbe\x97\xeaI~\x8f;<]*\xb3\xb6\x88\xd4\xfc\x14
k\xd3HsYw\x89\xefS|\xabf'
Assinatura Digital:
(8257296776492579228647629812320222951127847367467422619024
57746389981230818292163999611108930939203769076093250037322
13439451592364099549943681383022730792528267606064988571074
07110197646037606921838913759944219828969399247816349745976
70241372324291895894858233416316453079989836330025610294792
64375526555218,)
Hash 2:
b"\x9b
\xbc`\x924\xc4\x0c'\\\x9d\x93,\xc6\xcd\xa3\xa8{\xea(\x03\x8
b\x06}\xa6\xb9\x00p\x9c\x88o\x93"
Hash 3:
b"\x9b
\xbc`\x924\xc4\x0c'\\\x9d\x93,\xc6\xcd\xa3\xa8{\xea(\x03\x8
b\x06}\xa6\xb9\x00p\x9c\x88o\x93"
Texto verdadeiro: Estudo Java
```

# CERTIFICADOS DIGITAIS

- prova de identidade que pode ser emitido não apenas para pessoas, mas também para softwares, computadores ou outros elementos digitais que precisam dessa certificação.
- são baseados no padrão X.509 da International Telecommunication Union (ITU) 
- A Autoridade Certificadora, chamada de CA (Certification Authority), **gera e armazena uma chave pública**, além de outras informações, referente ao cliente que precisa de um certificado
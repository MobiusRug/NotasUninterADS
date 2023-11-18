# Módulos, diretórios e pacotes

## Módulo em Python
- Arquivo com definições e declarações de classes, funções, variáveis
- Cada arquivo Python com extensão ".py" pode ser tratado como um módulo
- Os módulos fornecem uma forma conveniente de organizar o código

## Diretórios e Pacotes
- Diretórios em Python: são pastas que podem conter um ou mais módulos ou até mesmo outros diretórios
- Pacote em Python: são diretórios que contêm um arquivo especial chamado "init.py". O conteúdo desse arquivo pode ser deixado em branco, mas sua presença indica que o diretório é um pacote Python válido 

# Class ABC (Abstract Base Class) 
- Fornecida pelo módulo ABC, permite definir classes abstratas, que
	- Não podem ser instanciadas diretamente
	- Servem como um esqueleto ou modelo para outras classes que a estendem
	- Definem métodos abstratos que devem ser implementados pelas subclasses

# Herança Múltipla
- Herança múltipla é permitida em python
- Permite que uma classe filho receba atributos e métodos de duas outras classes
- Deve-se tomar cuidado para evitar conflito
- A ordem que é passada a herança importa

```python
from abc import ABC, abstractmethod

class Animal(ABC): 
	def __init__(self, age, height, weight, position):
	self.age = age
	self.height = height
	self.weight = weight
	self.position = position
	
	@abstractmethod
	def move_x(self):
		pass
	
	@abstractmethod
	def move_y(self):
		pass
	
	@abstractmethod
	def move_z(self):
		pass

```

```python
from abc import ABC

from code.Animal import Animal

class Mammal(Animal, ABC):
	def __init__(self, age, height, weight, position):
		super().__init__(age, height, weight, position)
		self.fur = None

	def fur_type(self, ):
		pass

```

```python
from code.Mammal import Mammal


class Dog (Mammal) :
	def __init__(self, age, height, weight, position):
	super().__init__ (age, height, weight, position)
	self.breed = None
	
	def move_x(self): # precisa implementar métodos abstratos
		pass
	
	def move_y (self):
		pass
	
	def move_z(self):
		pass

```

# Introdução a padrões de design de software

- São padrões de projeto
- São soluções reutilizáveis para problemas recorrentes no desenvolvimento de software
- Representam abordagens testadas e comprovadas para projetar e estruturar o código de forma eficiente
- Há vários tipos de *design patterns*, e cada um foca num aspecto do desenvolvimento de software

## Padrões estruturais
- Lidam com a organização de classes e objetos
- Fornecem maneiras de compor estruturas maiores a partir de partes menores
	- ex: Adapter, Proxy

## Padrões comportamentais
- Lidam com a interação entre objetos e a definição de responsabilidades
- Gerenciam comunicação e comportamento entre diferentes objetos
- ex.: Mediator, Observer

## Padrões de criação
- Lidam com a criação de objetos 
- Oferecem mecanismos flexíveis para a instanciação de classe
- ex.: Builder, Factory

# Design Pattern: Método Fábrica

- Cria objetos sem export detalhes ao cliente
- O cliente solicita um objeto á factory, e ela se encarrega de retornar a instância desejada

```python
from code.Dog import Dog

class AnimalFactory:

	@staticmethod
	def new_animal(animal_type, age, weight, height):
		match animal_type:
			case 'dog':
				return Dog(age=age, position=0, weight=weight. height=height)
			case 'cat':
				return Cat(age=age, position=20, weight=weight. height=height)

```

```python
from code.AnimalFactory import AnimalFactory

new_dog = AnimalFactory.new_animal(aninal_type='dog', height=20, weight=10, age=1)
new_cat = AnimalFactory.new_animal(aninal_type='cat', height=20, weight=10, age=1)

print(new_dog.position)
print(new_cat.position)

```

# Design Pattern: Builder
- Usado para criar objetos complexos passo a passo
- Separa a construção do objeto de sua representação
- Permite que o mesmo processo de construção crie diferentes representações 

Sem builder:
```python
class Casa:
	def __init__(self, num_quartos=None, num_banheiros=None, tem_garagem=False, tem_jardim=False):
		self.num_quartos = num_quartos
		self.num_banheiros = num_banheiros
		self.tem_garagem = tem_garagem
		self.tem_jardim = tem_jardim
	
	def __str__(self): # Semelhante ao toString no java 
		caracteristicas = []
		if self.num_quartos:
			caracteristicas.append(f'Nunero de guartos: {self.num_quartos}")
		if self.num_banheiros:
			caracteristicas.append(f"Nomero de banheiros: {self.num_banheiros}")
		if self.tem_garagem:
			caracteristicas.append("Possui garagen")
		if self.tem_jardim:
			caracteristicas.append("Possui jardin")
	
		return ', '.join(caracteristicas)
		
# Construindo uma casa com garagem e jardim
casa = Casa(num_qguartos=3, num_banheiros=2, tem_garagem=True, tem_jardim=True)
	
print("Caracteristicas da casa:", casa)
	
# Construindo outra casa sem garagem e com 4 quartos
outra_casa = Casa(nun_quartos=4, num_banheiros=3)

```

```output
Características da casa: Número de quartos: 3, Número de banheiros: 2, Possui garagem, Possui jardim
Características da outra casa: Número de quartos: 4, Número de banheiros: 3
```

Com builder
```python
# Tema 5 parte 2 - Com builder
# Classe Casa representa o produto final que queremos construir

class Casa:
	def __init__ (self):
		self.num_quartos = None
		self.num_banheiros = None
		self.tem_garagem = False
		self.tem_jardim = False

	def __str__(self): # Semelhante ao toString no java 
		caracteristicas = []
		if self.num_quartos:
			caracteristicas.append(f'Nunero de guartos: {self.num_quartos}")
		if self.num_banheiros:
			caracteristicas.append(f"Nomero de banheiros: {self.num_banheiros}")
		if self.tem_garagem:
			caracteristicas.append("Possui garagen")
		if self.tem_jardim:
			caracteristicas.append("Possui jardin")
		return ', '.join(caracteristic

# Classe Builder para construir a Casa passo a passo
class CasaBuilder:
	def __init__(self):
		self.casa = Casa()
	
	def set_num_quartos(self, num_quartos):
		self.casa.num_quartos = num_quartos
		return self
	
	def set_num_banheiros(self, num_banheiros):
		self.casa.num_banheiros = num_banheiros
		return self

	def adicionar_garagem(self):
		self.casa.tem_garagem = True
		return self

	def adicionar_jardim(self):
		self.casa.tem_jardim = True
		return self
	
	def obter_casa(self):
		return self.casa


# Construindo uma casa com garagem e jardim
builder_casa = CasaBuilder()
casa = builder_casa.set_num_guartos(3).set_num_banheiros(2).adicionar_garagem().adicionar_jardim().obter_casa()
print("Caracteristicas da casa:", casa)

# Construindo outra casa sem garagem e com 4 quartos
outra_casa = CasaBuilder().set_num_quartos(4).set_num_banheiros(3).obter_casa()
print("Caracteristicas da outra casa:", outra_casa)
 



```
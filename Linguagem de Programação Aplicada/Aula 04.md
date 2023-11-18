# EVENTOS

## Eventos de teclado
- Para fazer interrupções de teclado em Python, utiliza-se a biblioteca keyboard
- Esta requer permissões de acesso ao teclado, o que pode variar dependendo do SO

```python
import keyboard  
  
def on_key_event(event):  
    if event.event_type == keyboard.KEY_DOWN:  
        print(f'Tecla pressionada: {event.name}')  
        if event.name == 'a':  
            print('a em especial')  
              
keyboard.on_press(on_key_event)  
  
try:  
    while True:  
        pass # resto do código  
except KeyboardInterrupt:  
    print("Programa interrompido pelo usuário.")
```


## Eventos de tempo
- Para criar eventos de timer em Python sem bloquear a execução do programa, uma alternativa é usar a biblioteca *shed*
- Fornece recursos para agendar e executar funções em momentos específicos ou após determinados intervalos de tempo

```python
 
import sched
import time

def exibir_mensagem(mensagen):
	print (mensagem)

def agendar_evento(scheduler, intervalo, mensagem):
	# Agendando o proximo evento
	scheduler.enter(intervalo, 1, agendar_evento, (scheduler, intervalo, mensagem))

	# Exibindo a mensagem
	exibir_mensagem(mensagem)


# Cria uma instancia do objeto scheduler
new_scheduler = sched.scheduler(time.time, time.sleep)

# Agendando o primeiro evento
agendar_evento(new_scheduler, 1, "Esta é a mensagem agendada a cada 1 segundo!")

print("Esperando para exibir as mensagens agendadas...")

# Executando o scheduler em loop (Ctrl + F2 para interromper manualmente)
new_scheduler.run()

```

# Decorators

- São utilizados para modificar ou estender a funcionalidade de funções ou classes sem precisar alterar seu código interno 
- Os decorators são implementados usando a sintaxe do `@`
- Existem dois tipos principais de decorators em Python
	- de função
	- de classe

- **Decorators de função**
	- São aplicados em funções individuais e permitem adicionar funcionalidades extras antes, depois ou ao redor da função decorada
- **Decorators de classe**
	- Os decorators de classe são aplicados a classes inteiras e permitem modificar ou estender o comportamento da classe 

```python
# Definindo o decorator
def meu_decorator(funcao):
	def wrapper():
		print("A função sera executada agora.")
		funcao()
		print("A funcao foi executada")

	return wrapper

# Aplicando o decorator usando o simbolo @
@meu_decorator
def minha_funcao():
	print("Esta é a função original.")

minha_funcao( )

```


```python
import time

# Definindo o decorator para medir o tempo de execução

def medir_tempo(funcao):
	def wrapper (*args, **kwargs):
		inicio = time.time()
		resultado = funcao(*args, **kwargs)
		fim = time.time()
		print(f"A fungdo ‘{funcao.__name__}' demorou {fim - inicio:.6f} segundos para ser executada.")
		return resultado
	return wrapper

 

@medir_tempo
def exemplo_funcao(tempo_espera):
	time.sleep(tempo_espera)
	print("A função foi executada.")

# Chamando a fungdo decorada
exemplo_funcao(2)



```


```python
# Definindo o decorator de classe
class Carro:
	def __init__(self, classe_decorada):
		self.classe_decorada = classe_decorada

	def __call__(self, *args, **kwargs)
		# Instancia a classe original
		instancia_classe = self.classe_decorada(*args, **kwargs)
		# Adiciona o atributo extra
		instancia_classe.num_rodas = 4
		return instancia_classe


@Carro
class Automovel
	def __init__(self, modelo):
		self.modelo = modelo

 
# Criando uma instancia da classe decorada
new_auto: Automovel = Automovel('Gol')

# Chamando o método da classe e exibindo o atributo extra
print(new.auto_modelo)



```

# List Comprehension

- Permite criar uma nova lista a partir de uma expressão ou iteração em uma única linha
- Uma condição:
```python
lista_pares_quadrado = []
for num in range(10):
	if num % 2 ==  0:
		lista_pares_quadrados.append(num*num)

# usando list comprehension:
lista_pares_quadrado = [num*num for num in range (10) if num % 2 == 0]
```

- Duas condições:
```python
lista_pares_quadrado = []
for num in range(10):
	if num % 2 ==  0:
		lista_pares_quadrados.append(num*num)
	else
		lista_pares_quadrados.append('ímpar')

# usando list comprehension:
lista_pares_quadrado = [num*num if num % 2 == 0 else 'impar' for num in range (10)]
```

# Padrão de design comportamental Mediador (Mediator)

- Útil quando você tem vários componentes que precisam se comunicar entre si de forma desacoplada
- Gerencia as interações entre os componentes, promovendo a baixa dependências

```python
class TorreDeControle:
	def _ init__(self):
		self.avioes = []

	
	def adicionar_aviao(self, aviao):
		self.avioes.append(aviao)
		aviao.registrar_torre(self)
	
	def enviar_mensagem(self, aviao, mensagem):
		print(f"Torre de controle para {aviao.nome}: {mensagem}")
		for outro_aviao in self.avioes:
			if outro_aviao != aviao:
				outro_aviao.receber_mensagem(aviao, mensagem)


class Aviao:
	def _ init__(self, nome):
		self.nome = nome
		self.torre = None

	def registrar_torre(self, torre):
		self.torre = torre
	
	def enviar_mensagem(self, mensagem):
		self.torre.enviar_mensagem(self, mensagem)

	def receber_mensagem(self, aviao, mensagem):
		print(f'{self.nome} recebeu uma mensagem de {aviao.nome}: {mensagem}')

# Criando a torre de controle
torre_de_controle = TorreDeControle()

 
# Criando os avides
aviaol = Aviao("Aviao 1") 
aviao2 = Aviao("Aviao 2")
aviao3 = Aviao("Aviao 3")

# Adicionando os avides a torre de controle
torre_de_controle.adicionar_aviao(aviaol)
torre_de_controle.adicionar_aviao(aviao2)
torre_de_controle.adicionar_aviao(aviao3)

# Enviando mensagens entre os avides
aviaol.enviar_mensagem("Vamos decolar!")
aviao2.enviar_mensagem("Confirmado, prontos para decolar.")
aviao3.enviar_mensagem("Aguardando autorizagdo para decolar.")


```

![[Pasted image 20231113105211.png]]

# Padrão de Design Criacional Observador

- Permite que objetos observadores sejam notificados e atualizados quando ocorrem mudanças no objeto observado
- Isso permite um acoplamento flexível e desacoplado, facilitando a comunicação e a reatividade em um sistema 

```python
class Mensageiro:
	def __init__ (self):
	self.observadores = []
	
	def adicionar_observador(self, observador):
		self.observadores.append(observador)
	
	def remover_observador(self, observador):
		self.observadores.remove (observador)

	def notificar_observadores(self, remetente, mensagem):
		for observador in self.observadores:
			observador.receber_notificacao(remetente, mensagem)


class Usuario:
	def __init__(self, nome):
		self.nome = nome

	def receber_notificacao(self, remetente, mensagem):
		print(f"[{self.nome}] Nova mensagem de {remetente}: {mensagem}")

class Grupo:
	def _ init__(self, nome):
		self.nome = nome 
		self.membros = []
		
	def adicionar_membro(self, membro):
		self.membros.append(membro)

	def receber_notificacao(self, remetente, mensagem):
		print(f"Grupo {self.nome}: Nova mensagem de {remetente}: {mensagem}")

 


mensageiro = Mensageiro()

# Criando usuários
usuariol = Usuario("Alice")
usuario2 = Usuario("Bob")
usuariod = Usuario("Charlie")

 # Criando grupos
grupol = Grupo("Familia")
grupo2 = Grupo(" Trabalho")

# Adicionando observadores ao mensageiro
mensageiro.adicionar_observador (usuariol)
mensageiro.adicionar_observador (usuario2)
mensageiro.adicionar_observador (usuario3)

# Adicionando membros ao grupo
grupol.adicionar_membro(usuariol)
grupol.adicionar_nembro(usuario2)

grupo2.adicionar_membro(usuario2)
grupo2.adicionar_membro(usvario3)

# Enviando mensagens
mensageiro.notificar_observadores("Admin", "Bem-vindos ao nosso aplicativo de mensagens!")
grupol.receber_notificacao("Admin", "Nova reuni&o marcada para amanhd.")
usuario3.receber_notificacao("Alice", "0i, tudo bem?")

```
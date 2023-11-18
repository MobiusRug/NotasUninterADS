# PYGAME

- Primeiro de tudo - `pygame.init()`: sem a invocação desse método não podemos fazer nada
- Janela do Programa (Superfície)

```python
import pygame  
# Inicializar o módulo Pygame  
  
W_WIDTH = 576  
W_HEIGHT = 324  
  
pygame.init()  
  
print('setup start')  
# Criação de janela do pygame  
window = pygame.display.set_mode(size=(W_WIDTH, W_HEIGHT))  
  
# Carregar imagem e gerar uma superfície  
bg_surf = pygame.image.load('./asset/bg.png').convert_alpha()  
player1_surf = pygame.image.load('./asset/player1.png').convert_alpha()  
  
# Obter o Retangulo da superfície  
bg_rect = bg_surf.get_rect(left=0, top=0)  
player1_rect = player1_surf.get_rect(left=0, top=0)  
  
# Desenhar na janela  
window.blit(source=bg_surf, dest=(0,0))  
window.blit(source=player1_surf, dest=(100,100))  
  
# Atualizar a janela  
pygame.display.flip()  
print('setup end')  
  
  
print('loop start')  
while True:  
    for event in pygame.event.get():  
        if event.type == pygame.QUIT:  
            print('loop end')  
            pygame.quit()  
            quit()  
  
    pressed_key = pygame.key.get_pressed()  
    if pressed_key[pygame.K_w]:
```

alterações 

```python
import pygame  
  
# Inicializar o módulo Pygame  
  
W_WIDTH = 576  
W_HEIGHT = 324  
  
pygame.init()  
  
print('setup start')  
# Criação de janela do pygame  
window = pygame.display.set_mode(size=(W_WIDTH, W_HEIGHT))  
  
# Carregar imagem e gerar uma superfície  
bg_surf = pygame.image.load('./asset/bg.png').convert_alpha()  
player1_surf = pygame.image.load('./asset/player1.png').convert_alpha()  
  
# Obter o Retangulo da superfície  
bg_rect = bg_surf.get_rect(left=0, top=0)  
player1_rect = player1_surf.get_rect(left=100, top=100)  
  
# Desenhar na janela  
window.blit(source=bg_surf, dest=bg_rect)  
window.blit(source=player1_surf, dest=player1_rect)  
  
# Atualizar a janela  
pygame.display.flip()  
print('setup end')  
  
# Colocar um relógio no nosso jogo  
clock = pygame.time.Clock()  
  
# Carregar música e deixar ela tocando  
pygame.mixer_music.load('./asset/fase1.mp3')  
pygame.mixer_music.play(-1)  
pygame.mixer_music.set_volume(0.3)  
  
print('loop start')  
while True:  
    clock.tick(140)  # esse lop está acontecendo 30 vezes por segundo  
    #print(f'{clock.get_fps():.0f}')    window.blit(source=bg_surf, dest=bg_rect)  
    window.blit(source=player1_surf, dest=player1_rect)  
    pygame.display.flip()  
    for event in pygame.event.get():  
        if event.type == pygame.QUIT:  
            print('loop end')  
            pygame.quit()  
            quit()  
  
    pressed_key = pygame.key.get_pressed()  
    if pressed_key[pygame.K_w]:  
        player1_rect.centery -= 1  
    if pressed_key[pygame.K_s]:  
        player1_rect.centery += 1  
    if pressed_key[pygame.K_d]:  
        player1_rect.centerx += 1  
    if pressed_key[pygame.K_a]:  
        player1_rect.centerx -= 1
```


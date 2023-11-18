# CONCEITOS

- **Usabilidade**: Medida na qual um produto pode ser usado por usuários específicos para alcançar objetivos específicos com eficácia, eficiência e satisfação em um contexto específico de uso.
- **Eficácia**: Acurácia e completude com as quais usuários alcançam objetivos específicos. 
- **Eficiência**: Recursos gastos em relação à acurácia e abrangência com as quais usuários atingem objetivos.
- **Satisfação**: Ausência do desconforto e presença de atitudes positivas para com o uso de um produto.
- **Contexto de uso**: Usuários, tarefas, equipamento (hardware, software e materiais), e o ambiente físico e social no qual um produto é usado.

- **UX (User eXperience)** refere-se à experiência do usuário ao interagir com um produto ou serviço, abrangendo toda a interação.
- A **UI (Interface de Usuário)** desempenha um papel crucial na experiência do usuário, envolvendo interação física e conceitual.

# USABILIDADE

- Peter Morville sugere considerar sete aspectos para tornar um produto um sucesso:
  - **Utilidade**: O aplicativo resolve uma necessidade?
  - **Usabilidade**: O aplicativo é fácil de usar?
  - **Encontrabilidade**: O aplicativo é facilmente encontrado e oferece suporte?
  - **Acessibilidade**: Pessoas com deficiências podem usá-lo?
  - **Credibilidade**: O aplicativo é confiável e não trava?
  - **Valor**: O aplicativo agrega valor?
  - **Desejabilidade**: As pessoas querem e recomendam o aplicativo?
- Além da usabilidade, a *estética e as reações emocionais* podem afetar a interação.
- Estudos mostraram que a estética influencia na facilidade de uso e na satisfação do usuário.
- A hedonomia estuda o prazer na interação homem-tecnologia, considerando a hierarquia das necessidades de Maslow.
- A hierarquia das necessidades do consumidor inclui prazer, usabilidade e funcionalidade como elementos-chave para um produto/sistema bem-sucedido.

Priamide de Maslow:

![[Pasted image 20230911090504.png]]

Piramide de Hanckock

![[Pasted image 20230911094611.png]]


Piramide de Jordan:

![[Pasted image 20230911090519.png]]


# CONTEXTO ATUAL

- Estamos na era da informação, com acesso facilitado por dispositivos conectados.
- No século XIX e XX, as telecomunicações (rádio, TV, telégrafos, telefones fixos) permitiram a disseminação de informações.
- O acesso à internet acelerou o processo, tornando a publicação online mais barata e eficiente.
- Atualmente, vivemos na era da computação ubíqua e móvel, com dispositivos como a Alexa e smartwatches.
- Dispositivos como desktops e laptops são usados para tarefas longas e gerenciamento de informações.
- Tablets são adequados para leitura, enquanto smartphones são eficazes para tarefas rápidas e espontâneas.
- A análise de tarefas deve considerar a natureza dos dispositivos utilizados pelos usuários.

# DESIGN RESPONSIVO

- Trata-se do navegador consultar a mídia e de se adaptar ao tamanho, reagindo ao dispositivo
- Responsive Design foi utilizado por Ethan Marcotte, em seu livro Responsive Web Design

# DESIGN ADAPTATIVO

- Design adaptativo usa vários tamanhos de layout fixos e media queries em CSS3 para verificar características da mídia e aplicar estilos específicos.
- Empresas podem escolher desenvolver sites otimizados para dispositivos móveis, com diferentes layouts para smartphones e desktops.
- No design adaptativo, o layout se adapta melhor à experiência em smartphones, com botões maiores.
- É possível desenvolver seis designs para tamanhos de tela comuns e criar um site específico para smartphones.
- Páginas são desenvolvidas em camadas usando HTML, CSS e JavaScript para definir a estrutura, aparência e funcionalidade.
- A tag media no HTML ajuda a direcionar o conteúdo com base na mídia.
- Desenvolver exclusivamente para smartphones pode exigir manutenção adicional para manter o conteúdo homogêneo.

## Jacob's law
Os usuários passam a maior parte do tempo em outros sites. Isso significa que os usuários preferem que o seu site funcione da mesma maneira que todos os outros sites que eles já conhecem.

## Fits's law

- O tempo para adquirir um alvo é uma função da distância até o alvo e do tamanho do alvo.
- Os alvos de toque devem ser suficientemente grandes para que os usuários possam selecioná-los com precisão.
- Os alvos de toque devem ter espaçamento adequado entre eles. 
- Os alvos de toque devem ser posicionados em áreas da interface que permitam que sejam facilmente acessados.

## Hick's law 
- O tempo necessário para tomar uma decisão aumenta com o número e complexidade das opções.
- Minimize as opções quando o tempo de resposta é crítico para aumentar o tempo de decisão.
- Divida tarefas complexas em etapas menores para reduzir a carga cognitiva.
- Evite sobrecarregar os usuários destacando opções recomendadas.
- Utilize um processo de introdução progressiva para diminuir a carga cognitiva de novos usuários.
- Tenha cuidado para não simplificar excessivamente ao ponto de tornar abstrato.

## Miller's law
- A pessoa comum só consegue manter em sua memória de trabalho 7 (mais ou menos 2) itens.
- Não utilize o "número mágico sete" para justificar limitações de design desnecessárias.
- Organize o conteúdo em partes menores para ajudar os usuários a processar, entender e memorizar facilmente. (chunking)
- Lembre-se de que a capacidade da memória de curto prazo pode variar de pessoa para pessoa, com base em seu conhecimento prévio e contexto situacional

## Postel's law
- Seja generoso no que você aceita e conservador no que você envia.
- Tenha empatia, flexibilidade e tolerância em relação a qualquer ação que o usuário possa tomar ou qualquer entrada que ele possa fornecer.
- Antecipe praticamente qualquer coisa em termos de entrada, acesso e capacidade, ao mesmo tempo em que oferece uma interface confiável e acessível.
- Quanto mais pudermos antecipar e planejar no design, mais resiliente será o design.
- Aceite entradas variáveis dos usuários, traduzindo essas entradas para atender aos seus requisitos, definindo limites para entrada e fornecendo feedback claro ao usuário.

## Peak-End Rule
- As pessoas avaliam uma experiência principalmente com base em como se sentiram no pico e no final dela, em vez da soma total ou média de todos os momentos da experiência.
- Preste atenção especial aos pontos mais intensos e aos momentos finais (o "final") da jornada do usuário.
- Identifique os momentos em que o seu produto é mais útil, valioso ou divertido e projete-o para encantar o usuário final.
- Lembre-se de que as pessoas lembram das experiências negativas de forma mais vívida do que as positivas.
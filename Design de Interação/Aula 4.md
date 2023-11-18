# EVOLUÇÃO DESIGN RESPONSIVO
**Início da web com Tim Berners-Lee:**

- Tim Berners-Lee, inventor da web e diretor do W3C.
- Navegador chamado de World Wide Web.
- Inicialmente, suportava apenas HTML e compartilhava documentos científicos.

**Desenvolvimento do navegador Mosaic (1992):**

- Centro Nacional de Aplicações para Supercomputadores da Universidade de Illinois.
- Introdução do primeiro elemento <img> para apresentação de imagens.

**Criação do elemento \<table> (1997):**

- Permite layouts complexos, substituindo layouts em uma única coluna.
- Tabelas não são ideais para layouts devido a problemas de manutenção, acessibilidade e SEO.

**Criação do CSS1 (1996, lançado no Brasil em 2003):**

- HTML como camada de estruturação.
- CSS como camada de estilos e apresentação.

**Início do Responsive Web Design (RWD) em 2010:**

- Ethan Marcotte introduz o RWD com base na citação de John Allsopp.
- Migração de layouts fixos para layouts diagramados com DIVs.
- Adoção de layouts fluidos e flexíveis para lidar com diferentes resoluções de dispositivos.

**Elementos do RWD:**

- Grid fluído.
- Imagens e mídias flexíveis.
- Media queries para adaptar o design a diferentes dispositivos e resoluções.

# MOBILE FIRST

**Mobile First (2009):**

- Proposto por Luke Wroblewski.
- Iniciar projetos com foco no layout para dispositivos móveis.
- Razões: crescimento da tecnologia mobile, necessidade de comunicação eficaz em dispositivos móveis, aumento das funcionalidades nativas em dispositivos móveis.

**Web Design Adaptativo (AWD):**

- Criado por Aaron Gustafson.
- Criação de interfaces que se adaptam às capacidades do usuário, seja na forma, seja nas funções.
- Diferente do Responsive Web Design (RWD), que se adapta às diferentes resoluções de tela.

**Diferenças entre Desktop e Mobile:**

- Tamanho de tela.
- Teclado.
- Controles (mouse vs. dedo).
- Conexão (3G/4G vs. banda larga).
- Energia disponível.
- Rede (consistente vs. inconsistente).
- Espaço de armazenamento.
- Poder de processamento.
- Ambiente de uso.

**Recomendação do Mobile First:**

- Melhora a experiência do usuário em dispositivos móveis.
- Pode beneficiar as versões para desktop ao considerar a experiência móvel desde o início.

# DIAGRAMAÇÃO
- Papel
- Wireframes
- Alta fidelidade
# O AMBIENTE MÓVEL

- Princípios do design móvel:
	- Previsível
	- Consistente
	- Responsivo

**Regiões do Layout:**

- Base das experiências interativas.
- Compostas por containers.
- Uma tela de desktop possui três containers principais:
    1. Barra de aplicativos.
    2. Navegação.
    3. Área de conteúdo.

**Grade de Layout Responsiva:**

- Composta por colunas, calhas e margens.
- Medidas das colunas em porcentagens para facilitar a responsividade.
- O número de colunas exibidas depende do ponto de interrupção (breakpoint) da tela.
- Calhas separam os conteúdos.
- Medidas recomendadas:
    - Calhas de 16 dp para celulares (360 dp de breakpoint).
    - Calhas de 24 dp para tablets (600 dp de breakpoint).
    - Margens de 16 dp para smartphones.
- Personalização da grade com calhas de 8 dp para maior proximidade dos elementos ou calhas de 32 dp para mais espaçamento.
- Medidas em dp (densidade de pixels) para considerar a densidade da tela.

$dp = (largura px \times 160)/densidade$

- Uso de dp para elementos de UI no desenvolvimento para Android.






# Arquitetura de Informação

Prática de decidir como organizar as partes de alguma coisa de modo a torná-la compreensível.”
Segundo Steve Krug, autor de “Não Me Faça Pensar” existem 4 perguntas que o usuário precisa conseguir responder rapidamente assim que entra em um site ou em uma tela:
- O que é isto?
- O que eles têm por aqui?
- O que posso fazer aqui?
- Por que devo estar aqui e não em outro site/tela?

## Pilares da Arquitetura de Informação

- **NAVEGAÇÃO**
	- É necessário pensar como o usuário irá navegar pelo site ou por um sistema.
- **BUSCA**
	- É complementar a navegação. Como proporcionar buscas no sistema que efetivamente mostrem o dados necessário.
- **Organização**
	- Como organizar a informação de forma que tenha sentido
- **Rotulação**
	- É a forma como a informação é titulada para cada estrutura. Relaciona-se aos ícones, títulos, opções, blocos de informações.

Tudo isso pode ser documentado em blueprints e Wireframes


# Wireframes

- É uma representação rápida que pode ser rabiscada ou desenhada em uma aplicação
- Nascem durante e depois da etapa da Arquitetura de Informação.
- É um layout simples oferece uma visualização a respeito do conteúdo, posicionamento e a forma básica de como uma página ou tela será apresentada.
- Não são utilizadas cores, fontes e elementos de design final. -preto, branco e cinza
- Não utilizar conteúdo sem sentido, como Loren ipsum
- O objetivo do wireframe é oferecer uma forma estruturada de validar uma ideia .
- PILARES
	- **conteúdo** - o que será exibido?
	- **estrutura** - “Como os elementos desta página serão reunidos?”
	- **hierarquia** - “O que você quer transmitir primeiro para o usuário?
	- **funcionalidade** - “Como esses elementos funcionarão juntos?
	- **comportamento** -Como esses elementos interagem com o usuário?

# Service Blueprints

Tem o objetivo de fornecer uma análise de como a experiência do usuário final é afetada pelos processos internos das empresas.
Mapeamento detalhado que mostra as relações entre elementos, processos, pessoas que fazem parte da jornada do cliente/usuário, dentro de um serviço.
As falhas na experiência do serviço podem ser definidas em 5
razões :

1. Os gerentes incorretamente definem o que os consumidores/clientes esperavam;
2. Os gerentes definem os padrões de serviço errados;
3. Os funcionários não entregam no padrão de qualidade esperados;
4. Consumidores / Clientes têm expectativas equivocadas, possivelmente por erro ou falta de comunicação da Organização;
5. A experiência atual não atende às expectativas e jornada
do cliente.

## VANTAGENS 

1.  **Exposição das Ineficiências dos processos**
2. **Oportunidades de otimização**
3. **Melhoria na visão geral do serviço**

## ELEMENTOS ESSENCIAIS

- **Ações do cliente/ usuário**
- **Ações de Frontstage**
	- ocorrem diretamente com o usuário final (humano-humano/humano-máquina)
- Atividade dos Bastidores
	- fora do campo de visão do usuário final
- **Processos**
	-  interações que dão suporte para os colaboradores conseguirem entregar o serviço ao usuário final.


###  Linhas de Separação
No Service Blueprint, cada elemento principal está dividido em clusters — grupos — separados por linhas

1. LINHA DA INTERAÇÃO
	- representa as interações entre o cliente e a organização;
2. LINHA DA VISIBILIDADE
	- Separa Frontstage e Backstage
3.  LINHA DA INTERAÇÃO INTERNA
	- separa os funcionários que tem contato com o cliente daqueles que não tem interação ou dão suporte ao cliente.

### Evidências
Última camada do Service Blueprint
Elas são referentes aos objetos que são utilizados nos processos e que dão suporte para que o serviço aconteça.

![[Pasted image 20230417113448.png]]

# Modelo Atômico

Permite que você crie estruturas, padrões de componentes que poderão ser reaproveitados no projeto ou em projetos futuros.

## CATEGORIAS

1. ÁTOMOS : item indivisível - componente básico (botão, uma caixa de texto)
2. MOLÉCULA: são componentes funcionais formados pela união de átomos 
3. ORGANISMO: duas células ou mais interagindo entre si, de forma coordenada, de uma forma de oferecer uma funcionalidade para o usuário
4.  TEMPLATE: estrutura, esqueleto de uma página
5. PÁGINA: É quando o template é preenchido com conteúdo
6. MÉTODO: Após a definição de todos os elementos é a hora de testar, revisar e validar e gerar nova iteração até obter o resultado final desejado.

# DESIGN SPRINT

- Processo desenvolvido pelo pessoal do Google Ventures.
- É um método com duração de uma semana onde a equipe se dedica a um problema e ao fina fazem um protótipo e testam com o usuário.
- ETAPAS:
	1. ENTENDIMENTO
	2. REMIX
	3. DECISÃO
	4. PROTÓTIPO
	5. TESTE DE USABILIDADE
- REQUISITOS
	- Desafio significativo
	- Time multidisciplinar
	- Definir um "decisor"
	- Disponibilizar materiais para a equipe
	- Cronômetro

## 1º dia - Entendimento
- Compreender o problema
- Compreender o Objetivo a longo prazo
- Desenvolver o Mapa com a jornada do usuário.
- "Ask the experts"
- Revisão do Mapa
- "How we could" - propostas - post its
- votação das protpostas
- Definir o foco pelo ponto de vista do usuário e definir as pessoas que irão participar do teste de usabilidade.

## 2° Dia - Remix
- Buscar referências de mercado que resolvam o problema.
- Ideação - Brainstorming, Crazy 8's etc.

## 3° Dia - Decisão
- Votação dos sketches
- Ao final desta etapa teremos os pontos das ideias mais votados ou até sktech inteiro mais votado.
- gerar o sketch da solução
- as ideias são transformadas em uma “historia” para a solução do desafio
- Decisor irá verificar os votos e decidir qual caminho será seguido
- Desenvolver storyboard -> Serão desenvolvidos os fluxos para os testes e desenhar telas por telas da solução verificando se a ideia não tem furos.

## 4° Dia - Protótipo
- criação de um protótipo de alta fidelidade.
- O cliente pode participar neste dia ajudando no protótipo.
-  recrutamento do pessoal adequado para o teste de usabilidade.
- desenvolver o questionário para testar as hipóteses.

## 5° Dia - Teste de usabilidade
- Teste de usabilidade
1. Entrevista
2. protótipo
- Não se deve fazer alterações no meio do teste.  Se for necessário faça a correção e refaça o teste com todos novamente.

## Design Sprint – Resultados
-  permite testar uma ideia direto com os usuários e valida-las ou não
- Com o uso de protótipos é possível fazer a atualização das ideias e gerar novas versões para teste de forma fácil e mais barata que o desenvolvimento de um produto
- Este processo é iterativo. Pode-se repetir várias vezes até que todos os ajustes necessários tenham sido feitos.
# PROCESSOS DE NEGÓCIO

- Processos de negócios podem ser entendidos como um conjunto sequenciado de tarefas que são executadas utilizando-se de insumos de entrada, processando essas entradas e gerando uma saída, que é um produto ou serviço, que **gera valor ao cliente.** 
- Refletem como a empresa funciona

![[Pasted image 20230421081407.png]]

- Analista de negócios/requisitos - faz a ponte entre a área de negócios e a área de TI.

## CLASSIFICANDO OS PROCESSOS DE NEGÓCIO

### Processos primários
- Atividades essenciais para o cumprimento da missão da empresa
- agrega valor diretamente ao cliente

### Processos de suporte
- Oferecem apoio e suporte aos processos primários (ou a outros processos de suporte e gerenciamento)
- Ex.: RH, manutenção do software

### Processos gerenciais
- mede, monitora, controla atividades e administra o presente e o futuro do negócio  
- necessários para assegurar que a organização opere de acordo com seus objetivos e metas de desempenho

## DOCUMENTANDO OS PROCESSOS DE NEGÓCIO

-  Uma modelagem clara, documentada e conhecida por todos dos processos é muito importante para que exista uma alta eficiência na empresa, **padronizando o resultado dos processos**, de forma que qualquer profissional consiga seguir o passo a passo e gerar um resultado com a mesma qualidade esperada.

# AS IS/TO BE

- O primeiro passo no mapeamento e na gestão de processos é  **identificar processos.** 
- Características de um processo:
	• Processo é uma junção de atividades e recursos;
	• Processo é voltado à realização de um objetivo global;
	• Processo é orientado para o cliente final;
	• Processo é reforçado de maneira recorrente, para virar hábito;
	• Processo deve ter desempenho, organização e responsabilidades;
	• Processo é uma organização estruturada de tarefas;
	• Processo tem entrada e processamento, para gerar um resultado como saída.
- Resumo: Entradas -> Processamento -> Saída organizado, com objetivo claro, recorrente, com papeis definidos

## AS IS
- Após identificação do processo, mapeia todos os seus passos -> representação num fluxo
- Permite identificar problemas e oportunidades de melhorias
- **atores** - todos envolvidos na execução do processo *AS IS*
- Não é raro encontrar resistência a sua execução - necessário sensibilidade
- Fazer a documentação junto a gestores - comunicar melhorias possíveis e identificar falhas
- Definir o padrão de notação e a ferramenta - padrão mais comum é o BPMN

## TO BE 
- Utilizado para propor um novo processo de negócio ou melhorias no processo já existente. 
- Fluxo - redesenho ou modelagem
- Fundamental a participação dos atores, gestores e pessoas com experiência que possam enriquecer o processo
	• O que é feito que não apresenta valor para o processo?
	• O que não é feito, mas apresenta valor para o processo?
	• O que é feito de uma forma que não traz o resultado esperado?
	• O que é feito além do que é esperado?
	• O que pode ser eliminado?
	• O que pode ser substituído?
	• O que pode ser adicionado?
	• O que pode ser melhorado?
	• O que pode ser unificado?
	• O que pode ser paralelizado para ser executado mais rapidamente?
- É importante que todas as sugestões sejam devidamente documentadas, que responsabilidades sejam definidas e que seja organizado um cronograma para implementação do novo processo, deixando claros os ganhos esperados para cada melhoria proposta

# BPMN

- o BPM é uma disciplina de gestão que combina processos de negócio, pessoas, tecnologia e organização para criar uma visão única e integrada de negócios.
- O BPM propõe a utilização da notação BPMN para modelagem

## VISÃO MACRO DO BPMN 

- O fluxo mostra exatamente como o processo ocorre, com todos os passos seguidos e as consequências a partir de decisões que precisam ser tomadas, além de mostrar quem executa cada uma das tarefas modeladas.

![[Pasted image 20230421092053.png]]

## ELEMENTOS DO BPMN

### PISCINAS
- São representadas por uma caixa retangular e agem como um container para os objetos do fluxo de um participante no processo
- Cada piscina contém um único processo
- Para separar processos diferentes, é boa prática criar piscinas diferentes

![[Pasted image 20230421093851.png]]

### RAIAS
- Uma raia é uma subdivisão dentro de uma piscina usada para organizar as atividades.
- Raias são usadas para distribuir os elementos do processo especificando quais papéis internos são responsáveis por executar as atividades 
 - Normalmente usa-se raia para papéis internos (gerente, analista), sistemas (aplicativos) e departamentos (vendas, cobrança)


![[Pasted image 20230422074336.png]]

### OBJETOS DE FLUXO

- **EVENTOS** - *Círculo* é uma mensagem, indicador, notificação ou algo similar que significa que uma ocorrência que aconteceu e foi registrado, agregam  informações adicionais sobre o processo (estímulo do ambiente externo)

- **ATIVIDADES** -  *Retângulo*: representam um trabalho realizado em uma etapa do processo de negócio. É um passo do processo. As atividades são sequenciais e uma atividade chama a próxima atividade.

- **GATEWAY** (porta ou acesso) – *Losango*: é o elemento que utiliza questionamento lógico para decisões de fluxos diferentes no processo, ou seja, é o elemento utilizado para separar ou juntar os diferentes caminhos de um processo.
![[Pasted image 20230422162436.png]]

### OBJETOS DE CONEXÃO

- **Fluxo de sequência** – *seta:* deve partir de um único elemento e apontar para um outro elemento único
--->
- Caminho feliz - 


### ATIVIDADES OU TAREFAS
São divididas em:
- Comum
- do tipo serviço
- de recebimento
- de envio
- de usuário
- script
- manual

![[Pasted image 20230422164831.png]]

### EVENTOS

- gatilho -> resultado
- Podem ser de **Início, intermediários ou de Fim**

![[Pasted image 20230422165249.png]]


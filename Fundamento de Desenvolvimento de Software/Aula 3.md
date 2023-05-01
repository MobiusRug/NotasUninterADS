# Fluxo de trabalho para criação de um software

1. Baixar código de um repositório
	1. aquisição do código
	2. atualização da versão no repositório
2. Codificar
3. Validação do código
4. Integração
5. Testar

## TRABALHO EM EQUIPE E BOAS PRÁTICAS EM REUNIÕES

- São pessoas que fazem um software
- Daily Scrum:
	- Priorizar tarefas
	- comunicação com a equipe
	- foco no cliente
- O trabalho em equipe e a colaboração impactam no sucesso de uma aplicação

### REUNIÃO
- boa estratégia para saber em que cada um do time está trabalhando e quais tarefas são prioridades.
- O excesso de reuniões pode atrapalhar a produtividade
- Mudanças importantes:
	- escolha criteriosa de temas;
	- envio prévio da pauta
	- definição de quem faz o quê
	- limitação do tempo total de reunião
	-  limitação de participantes
- Zoom fatigue - associado ao uso prolongado e repetido de ferramentas de vídeo conferência

# FERRAMENTAS COLABORATIVAS DE TRABALHO EM EQUIPE

- softwares ou plataformas que permitem o compartilhamento de arquivos e a efetiva comunicação entre os integrantes de um mesmo projeto
- ex.: Trello, Jira, Slack, Teams, Discord, Zoom

# VERSIONAMENTO E REUSO

## REUSO
- Reúso diz respeito a qualquer parte de um sistema implementado anteriormente, podendo ser uma especificação, módulo, arquitetura e padrões, dentre outras
- VANTAGENS:
	- aumento da produtividade
	- redução do tempo de entrega do produto
	- aumento da qualidade
- PROBLEMAS
	- Síndrome do NIh
	- medo de falhas
	- custo da reutilização 
	- questões legais
	- compreender a parte reutilizada
	- mudança na mentalidade da equipe 

## SISTEMA DE CONTROLE DE VERSÃO
dá suporte ao desenvolvimento de software por meio do registro de histórico, permitindo que mais de um programador realize as modificações concorrentemente, e proporcionando ainda a manutenção de diferentes versões de um projeto

# REPOSITÓRIOS DE CÓDIGOS
- Guardam todos os artefatos (componentes, códigos) em repositórios
- 2 perspectivias
	- Repositórios de gerência de configuração (Git, Bitkeeper, Subversion, Mercurial)
	- Repositórios de reutilização (Bootstrap, Spring, Angular )

## REPOSITÓRIOS DE GERÊNCIA DE CONFIGURAÇÃO
- Sistemas de Controle de versão (VCS/SCM)
- Tipos:
	- **CENTRALIZADO** : único servidor central e várias estações de trabalho
	- **DESCENTRALIZADO**: possuem diversos repositórios autônomos e independentes para cada desenvolvedor 

## REPOSITÓRIO DE IDEIAS 
- espaço em que que os desenvolvedores e futuros desenvolvedores podem trocar informações e dicas sobre ferramentas, códigos e linguagens
- Ex.: Oracle developer, Cisco, AWS Academy, Mozzila Developers Network etc.

# TESTES DE SOFTWARE

Tem como objetivo revelas os erros de um software

## VERIFICAÇÃO
conjunto de tarefas que garantem que o software implemente corretamente uma função específica

## VALIDAÇÃO
conjunto de tarefas que asseguram que o software foi criado e pode ser rastreado segundo os requisitos do cliente

## TERMOS:

- **error (mistake)/ erro (engano)**: Uma ação humana que produz um resultado incorreto.
- **fault/ defeito (bug)**: Manifestação de um erro em software. Popularmente conhecidos como bugs.
- **failure/ falha**: capacidade de um sistema ou componente de software de executar suas funções exigidas dentro dos requisitos de desempenho especificados. Uma failure ocorre quando uma fault é encontrada.

Os custos de modificar um software aumentam conforme o projeto avança.
Os testes de software garantem ainda que a **qualidade** do produto seja alcançada

## ESTRATÉGIA DE TESTE POR PRESSMAN

### Teste de Unidade
se concentra em cada unidade de software implementada no código-fonte

### Teste de Integração
verifica se as unidades se comunicam, se integram corretamente sem falhas

### Teste de Validação
Mostra se o software atende aos requisitos

### Teste de sistema
verificam se todos os requisitos estão de acordo com o
especificado e se foram realmente atendidos

## Implantação
- Deploy -  implantação de um software, é necessário, além dele, as suas dependências, bem como interpretadores, compiladores, pacotes e extensões. Existem ainda a configuração do ambiente, licenças de outros softwares e senhas de banco de dados
-  O contêiner surge para resolver um grande problema de desenvolvimento: um programa rodar bem no ambiente de desenvolvimento e não funcionar em outro ambiente


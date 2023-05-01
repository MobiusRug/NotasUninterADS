# Redes de computadores
Rede de computadores é um conjunto de computadores interligados

## MEIOS DE TRANSMISSÃO

### FÍSICOS
- Cabos - fibra ótica, par trançado, coaxial
- Wireless
- Ondas de rádio

## EXTENSÃO DA REDE
### LAN
- Local Area Network - pequena área geográfica conecta computadores, impressoras dentro de um prédio

### MAN
Metropolitan Area Networks -  ampla área geográfica conecta LANs

### WAN
Wide Area Networks - ligação remota prestadores de serviço

## TOPOLOGIA

### BARRAMENTO
• Ligados no mesmo barramento físico
• Falha no cabo paralisa toda a rede

### ANEL
• Dispositivos conectados formando um anel
• Falha no cabo em apenas um ponto – pode-se mudar o
sentido de propagação para continuar operacional

### ESTRELA
• Ligados através cabos saindo de um equipamento central
• Falha no cabo, apenas o computador a ele conectado ficará
fora da rede

## PROTOCOLOS DE REDE
- Conjunto de normas
- permitem comunicação entre máquinas 
- Definem acordos para a transmissão de dados
![[Pasted image 20230417141202.png]]

## TIPOS DE REDE

#### PONTO A PONTO - PEER TO PEER
todos os computadores podem ter a função de cliente ou de servidor

#### BASEADO EM SERVIDOR 
Rede que possui computadores dedicados a tarefas específicas - SERVIDOR
CLIENTE - utiliza algum recurso disponível na rede

# INTERNET
Pode ser definida como uma rede de redes
Benefício das redes: surgimento da Internet 
Principal característica técnica: descentralização

## HISTÓRICO

- Criada em 1969, com o nome de ARPANET, pelo Departamento de Defesa dos Estados Unidos
- Objetivo: permitir que pesquisadores pudessem se comunicar
- NO BRASIL:
	- 1987 - FAPESP/LNCC
	- 1990 - RNP/Educação
	- 1995 - Comercial

## SERVIÇOS

A Internet pode ser vista como uma infraestrutura que provê serviços a aplicações
Serviços: são aplicações cliente/servidor que realizam alguma tarefa para o usuário

# WORLD WIDE WEB

A World Wide Web (WWW) é um sistema de servidores internet
Protocolo principal: HTTP (HyperText Transfer Protocol)
Confundida com a própria internet

## PÁGINAS WEB

- Informação apresentada em páginas hospedadas em servidores www
- Documento escrito em HTML (hypertext markup language)
- Hyperlinks ou hypertextos: permitem que o usuário acesse outro documento

## SITE OU WEBSITE
- Conjunto de páginas relacionadas
- Hospedado em servidor web
- Possui endereço único
- Associado a um nome de domínio

# COMPUTAÇÃO EM NUVEM

- **Nuvem:** computador localizado em algum lugar acessado via Internet e usado de alguma maneira
- Recursos de armazenamento e de processamento compartilhados (no lugar de compra e manutenção de servidores)
- Considerar e utilizar infraestrutura como software

## MODELOS DE COMPUTAÇÃO EM NUVEM

### IaaS
• Usuário gerencia o servidor e o sistema operacional
• Oferece capacidade de hardware ao usuário por meio de software
• Exemplo: EC2 da AWS
• Windows azure

### PaaS
• Outra pessoa gerencia o hardware e o sistema operacional
• Ambiente de desenvolvimento remoto para que o usuário possa desenvolver uma aplicação.
• Exemplo: Elastic Beanstalk e RDS

### SaaS
• Usuário não precisar se preocupar com a sua instalação, manutenção ou atualização
• Usuário só precisa se preocupar com o software e como deseja usá-lo
• Ex: Facebook e Dropbox, office 365

## MODELO DE IMPLANTAÇÃO
- All in cloud
- Híbrido
- privada

BENEFÍCIOS - agilidade, elasticidade, economia de custo, implantação global em minutos

# HISTÓRIA DA INTERNET
- 1969 - ARPANET
	- Rede militar que conectava 4 computadores no oeste americano
	- função: segurança de dados em posto de Guerra Fria
	- Protocolo NCP (Network Control Protocol)
		- FTS
		- DNS
		- SMTP
- Protocolo TCP/IP - 1973
	- Bob Khan e Vint Cent - primeiros a publicarem o termo internet
	- TCP -quebra as mensagens em pacotes
	- IP - endereçamento de máquinas
	- Tecoologias permitiram o aumento da rede
	- Substitui o NCP por completo em 1983
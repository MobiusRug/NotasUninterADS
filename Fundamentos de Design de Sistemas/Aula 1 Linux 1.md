# LINUX

## HISTÓRICO
- 1969 - Ken Thompson e Dennis Ritchie desenvolvem o sistema operacional UNIX
- 1983 - Richard Stallman inicia o projeto GNU
	- É criada a GPL - The GNU general public license - uma licença de software livre
- 1991 - Linus Torvalds cria oi kernel Linux

## KERNEL 

Um kernel é o núcleo de um sistema operacional. As principais funcionalidades do kernel incluem:
-  Gerenciamento de memória
- Gerenciamento de processos
- Gerenciamento de arquivos
- Gerenciamento de dispositivos

![[Pasted image 20230417080354.png]]

## FILOSOFIA LINUX
- A filosofia do software livre é baseada no princípio de que este deve ser livre para ser usado, estudado, modificado e distribuído
- Outra parte importante da filosofia do Linux e do software livre é a colaboração e a comunidade.

## APLICAÇÕES DE LINUX

- O Linux é um sistema operacional versátil e utilizado em uma variedade de aplicações,
- muitas empresas e organizações utilizam o Linux como sistema operacional
de servidor para aplicações como web hosting, e-mail, arquivos e banco de dados
- Grandes empresas usam o Linux como sistema operacional para sistemas de nuvem, como o Amazon Web Services e o Google Cloud.
- Outra aplicação comum do Linux é em dispositivos móveis - ex.: Android
- Além disso, o Linux é usado em Smart TVs,
dispositivos de streaming, como o Chromecast e mesmo a Raspberry Pi
 Linux também é usado em aplicações industriais.

## FUNDAÇÕES LIGADAS AO LINUX

- **Linux Foundation** - organização sem fins lucrativos que foi fundada em 2000, Tem como objetivo promover e proteger o Linux como um projeto de software livre e colaborativo.
-  **Free Software Foundation (FSF)** 
	- Fundada por Richard Stallman em 1985 
	- objetivo  de promover a utilização de software livre e garantir a liberdade dos usuários. 
	- criou a licença GPL

# LICENÇAS DE SOFTWARES

Licenças de software são contratos legais que regulamentam a utilização, distribuição e modificação de software.

## SOFTWARE LIVRE
Código-fonte está disponível para ser modificado e distribuído livremente pelos usuários.  

## OPEN SOURCE
Possui definição similar a software livre, as principais diferenças são históricas e filosóficas. Software livre possui um foco na questão  ética da necessidade de softwares serem livres para respeitar as liberdades dos usuários, enquanto open source foca mais nos aspectos práticos e técnicos das vantagens que traz para o desenvolvimento. 

## COPYLEFT
Categoria especial de licenças de software livre que garantem que as modificações e distribuições derivadas do software se mantenham iguais.
Exemplo GPL v2.

## FREEWARE
Software gratuito, que é distribuído sem custo algum e pode ser usado, copiado e distribuído livremente pelos usuários - diferente de free software, não precisa ter o código fonte aberto.

## SHAREWARE
Distribuído gratuitamente para teste e avaliação, mas que geralmente requer uma licença de uso paga para ser usado permanentemente.

## SOFTWARE PROPRIETÁRIO
Controlado e licenciado por uma empresa ou indivíduo, que tem o direito exclusivo de
distribuir, modificar e usar o software.

## SOFTWARE AS A SERVICE (SAAS)
Modelo de entrega de software cujas aplicações são acessadas por meio da internet e geralmente são oferecidas por meio de assinatura.

#  DISTRIBUIÇÕES LINUX
Sistemas operacionais que utilizam o kernel Linux
![[Pasted image 20230417082702.png]]

![[Pasted image 20230417083103.png]]

## DEBIAN

- Criada em 1993 por Ian Mudock
- Gerenciador de pacotes - APT
- Principal interface gráfica é o GNOME
- Deu origem a diversas outras distribuições

## UBUNTU

- Baseado no Debian
- Criado pela empresa sul africana chamada Canonical
- O comando `sudo` surgiu com ubuntu
- Compatível com WSL

## MINT

- Baseado no Ubuntu
- Fornece experiência ao usuário similar ao Windows
- Principal Ambiente de desktop - Cinnamon
- Variedade de aplicativos populares pré-instalados

## Red Hat

- Utilizado principalmente por organizações empresariais
- Gerenciador de pacotes RPM
- Disponibilizada sob uma licença comercial

# TERMINOLOGIA LINUX

## PROCESSO DE BOOT

- **Carregamento do firmware - BIOS/UEFI**
	- Verifica dispositivos de armazenamento
	- inicia o bootloader (em geral o GRUB)
- **Inicialização do S.O.**
	- carrega módulos de dispositivos
	- configura hardware
	- inicia serciços de sistema
	- inicia interface gráfica

![[Pasted image 20230417083754.png]]

## SISTEMA DE ARQUIVOS

- Estruturas de dados que organizam e gerenciam arquivos em um dispositivo de armazenamento.
- Mais comuns no Linux - EXT4, XFS, Btrfs
- **EXT4** - Sistema de arquivos padrão, suporta arquivos de até 16TB
- **XFS** - Suporte de arquivos de até 9EB - usado em sistemas de arquivos de alta capacidade, como servidores
- **Btrfs** -  sistema de arquivos de nova geração, projetado para oferecer recursos avançados como snapshots, replicação e balanceamento de carga

##  X WINDOW SYSTEM

- **X/X11** - sistema de gerenciamento de janelas para sistemas Unix-like
- Os aplicativos se comunicam com o servidor X através de uma API  chamada Xlib
- camada inferior de toda a interface gráfica
![[Pasted image 20230417084323.png]]

## LINHA DE COMANDO 

Meio de interagir com o sistema operacional por meio de comandos digitados
em uma interface de texto.
Podem ser automatizados através de scripts para realizar tarefas repetitivas
ou complexas.

## SHELL
- Interpretador de comandos
- Mais comuns - Bash (padrão na maioria das distribuiçoes Linux), Zsh, Tcsh

# SERVIÇOS NO LINUX E CERTIFICAÇÕES

## SERVIÇOS POPULARES
- **LibreOffice** - aplicativos de escritório de código aberto
- **Mozilla Firefox** - navegador web de código aberto
- Outros - GIMP, VLC, OBS Studio

## JOGOS NO LINUX

Softwares de emulação: Wine e Proton

## CERTIFICAÇÕES LINUX
- A Linux Professional Institute (LPI) é uma organização sem fins lucrativos que oferece certificações para profissionais de sistemas Linux. 
- 4 níveis de certificação: **Linux Essentials, LPIC-1, LPIC-2 e LPIC-3.**

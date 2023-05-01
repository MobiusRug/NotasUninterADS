# ESTRUTURA DE DIRETÓRIOS DO LINUX

No Linux, a estrutura de diretórios é hierárquica e baseada em raízes. A raiz é representada pelo símbolo "/" e todos os outros diretórios são organizados em relação a ela.

## /bin

-  Armazena arquivos binários executáveis - programas que podem ser executados diretamente pelo sistema

## /boot
- Contém os arquivos necessários para o S.O. inicializar
- Contém uma imagem do kernel, o initrd, o GRUB

## /dev
- Cada arquivo é represenatdo por um arquivo especial
	- dev/sda para o primeiro disco rígido , dev/sdb para o segundo, /dev/sdc para removíveis
	- partições de um disco rígido são identificadas com um número adicional, como "/dev/sda1"

## /etc
- Mantém as configurações gerais do sistema para todos os usuários

## /home
- Usado para armazenar os arquivos pessoais e de configuração de cada usuário do sistema.
- Cada usuário tem o seu próprio diretório dentro do "/home"

## /root
diretório raiz para o usuário administrador (root); armazena arquivos e configurações exclusivas para o usuário root.

## /lib
Mantém as bibliotecas usadas por softwares

## /media
Local de montagem de discos removíveis automáticos

## /mnt
Local de montagem de discos manuais pelo usuário

## /opt
diretório usado para armazenar aplicativos adicionais que não fazem parte do sistema operacional padrão 

## /proc
- Mantém arquivos sobre o sistema e seus processos
- Permite interagir e observar as estruturas internas do kernel em formato de arquivos

## /run
diretório usado para armazenar informações de tempo de execução para o sistema e os aplicativos

## /sbin
semelhante ao bin, mas são binários que só podem ser acessados pelo root

## /temp
Diretório de arquivos temporários de cada sessão

## /usr
- Já foi a pasta de usuários
- Hoje, mantém arquivos de programas para usuários

## /var
armazena arquivos que variam, como logs de sistema, arquivos de e-mail e outros arquivos de dados dinâmicos


# COMANDO DE MANIPULAÇÃO DE DIRETÓRIOS

# ls
- Lista o conteúdo de um diretório
- `ls [opções] [arquivo]`
- Principais parâmetros
	- -l : exibe as permissões de arquivo e a data de modificação
	- -a : mostra todos arquivos, inclusive ocultos
	- - h: exibe o tamanho dos arquivos de forma mais legível

## cd
- change directory
- `cd [caminho\diretório]`
- Principais parâmetros
	- . - representa o diretório atual
	- .. - representa o diretório pai
	- ~- vai para home

## mkdir
- cria diretório
- `mkdir [nomeDir]`
- opções:
	- -p - cria os diretórios-pai de um caminho, caso eles não existam ainda
	- -m - permite definir as permissões 

## rmdir
- remove diretórios vazios
- `rmdir [opções] [nome diretorio]`
- opções:
	- -p permite remover diretórios aninhados
	- -v exibe mensagens na tela sobre as ações realizadas pelo comando 

## rm 
- remove arquivos e diretórios
- `rm [opções] diretório`
- opções:
	- -r - remove diretórios e conteúdo recursivamente 

## pwd
- imprimir o caminho completo da pasta atual

# COMANDOS DE GERENCIAMENTO DE PACOTES
 
- **Gerenciadores de Pacotes**: 
	- Permite que os usuários instalem, atualizem, removam e gerenciem facilmente os programas e bibliotecas instalados no sistema.
	- garantem que as dependências sejam resolvidas corretamente
	- permite que os usuários atualizem todo o sistema, ou apenas pacotes específicos, de maneira fácil e segura
- No Ubuntu:
	- pacotes são arquivos *.deb*
	- gerenciador *apt* 

## APT
`apt [opções] [comando] [pacote1] [pacote2]`

Principais parâmetros:
- update: atualiza a lista de pacotes disponíveis;
- upgrade: atualiza os pacotes já instalados para sua versão mais recente;
- install: instala um pacote;
- remove: remove um pacote;
- list: descobre se o pacote está instalado ou não, e qual a sua versão; e
- search: procura por um pacote no repositório.

## DPKG
- Gerenciador de pacotes para sistemas operacionais baseados em Debian
-  É útil para instalar pacotes fora do repositório padrão do sistema
- Não instala dependências

`dpkg [opções] nome_do_pacote`

Parâmetros:
-i (instalar): instala um pacote específico;
-r (remover): remove um pacote específico;
-l (listar): lista todos os pacotes instalados; e
-S (buscar): busca por um pacote específico.

# COMANDOS DE PROCESSOS

- Um processo é uma instância em execução de um programa ou aplicação.
- Cada processo tem a sua própria identificação única (PID)
- **Estados**: foreground, background, suspensos
- Os processos em foreground costumam segurar o controle do terminal até encerrarem
- Podemos mandar o processo para background para não deter o controle do terminal 

## ps
- Retorna uma lista de processos em execução 

Parâmetros:
-a: mostra todos os processos, incluindo aqueles de outros usuários;
-e: mostra todos os processos, como o parâmetro -a;
-f: exibe a árvore de processos; e
-u: exibe informações sobre os processos de um determinado usuário.
-x: exibe processos que não possuem um terminal associado

## top
Mostra uma lista interativa de processos que estão sendo executados no
sistema, incluindo informações como CPU, memória, nome do processo e tempo de execução.

Opções:
-d: especifica a frequência de atualização da lista de processos;
-p: especifica quais processos deseja-se visualizar;
-u: especifica um usuário específico para exibir processos; e
-h: mostra ajuda com informações sobre os parâmetros do comando.

## jobs
Mostra processos que estão parados ou rodando em segundo plano.

## fg e bf
Colocam processos em foreground e background respectivamente

## kill
Encerra ou interrompe processos
`kill [opções] [sinal] [PID]`

-l: lista os sinais que podem ser enviados para os processos;
-s: envia o sinal SIG para o processo; e
-9: envia o sinal de interrupção SIGKILL, que é usado para forçar o encerramento de um processo.

# COMANDOS DE ACESSO E PERMISSÕES

- **DONO**:
	- É quem criou o arquivo ou diretório
	- identificado pelo user ID 
- GRUPO:
	- coleção de usuários com acesso a um ou mais máquinas ou diretórios
	- identificado pelo group ID
- Permissões de Acesso:
	- Existem para proteger o sistema e arquivos de acessos indevidos

## TIPOS DE PERMISSÕES DE ACESSO
- **-r**:
	- permissão de leitura para arquivos
	- para diretórios, permite listar seu conteúdo (ls)
- **-w**:
	- permissão de escrita para arquivos
	- para diretórios, permite a gravação/exclusão de arquivos ou outros diretórios dentro dele 
- **-x**:
	- permite executar um arquivo
	- para diretórios permite que seja acessado através do comando `cd`.

Essas permissões são sempre atribuídas a 3 entidades diferentes: **dono, grupo, outros**
Ex.:

`--rwxr-xr--
1° caractere: define o tipo do arquivo (um "d" é um diretório; um "l“, um link a um arquivo no sistema; um "-" é um arquivo comum).
(2-4)° caractere: permissões do dono do arquivo `rwx`
(5-7)° caractere: permissões do grupo do arquivo `r-x`
(8-10)° caractere: permissões de outros usuários ao arquivo. `r--`

## ROOT (SUPERUSUÁRIO)

O root é o usuário administrador no sistema Linux. Ele tem permissões totais sobre o sistema

## COMANDO CHMOD
Modifica as permissões de um arquivo ou diretório

`chmod [opções][permissões][diretório/arquivo/`

![[Pasted image 20230417093612.png]]

Ex.:
`chmod u+rw,g+rw,o+r arquivo.txt`
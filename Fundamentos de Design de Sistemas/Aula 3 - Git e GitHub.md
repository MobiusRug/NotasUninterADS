# GIT

## INTRODUÇÃO

Uma das ferramentas mais populares para controle de versionamento

### Benefícios:

- **Rastreabilidade**: linha cronológica completa de todas as alterações feitas em seu código
- **Colaboração:** permite que várias pessoas trabalhem no mesmo código e mesclem as suas contribuições sem causar conflitos
- **Backup**: Mantém uma cópia de todas as versões 
- **Integração contínua:** compatível com muitas ferramentas de integração contínua
- **Comunidade**: open source e tem uma comunidade ativa e vibrante

### REPOSITÓRIO GIT
É o local em que ficam os arquivos do projeto, que serão controlados por versionamento.


## CONFIGURANDO O GIT 

### git config 
Usado para configurar opções do GIT

- `$ git config --global user.name "Seu Nome"`
- `$ git config --global user.email "seu.email@exemplo.com"`
- `$ git config –list`

### git init
- Inicializa um novoi repositório Git em um diretório existente
- Cria uma pasta oculta .git
- Arquivo HEAD - mantém histórico das alterações realizadas no projeto 


## TERMINOLOGIA GIT 

### BRANCHES (RAMIFICAÇÕES)

- Podemos ramificar nosso projeto para trabalharmos em funcionalidades separadas simultaneamente
- O branch padrão é chamado de **master**, é criado quando você cria o repositório
- Podemos mesclar branches para juntar partes desenvolvidas (**merge**)


###  FLUXO DE TRABALHO

- ***Add*:** Adiciona mudanças ao Index (prepara alterações que você fez no código para serem incluídas no próximo *commit*)

```
git add <arquivo>
git add *
git add file.txt
git add folder/
```

`*` usado para referenciar todos os arquivos do diretório
 

- ***Commit***: Passas as mudanças do Index para o Head (Registra as alterações adicionadas em um repositório Git local)

```
git commit -m "mensagem"
```
-m é utilizado para informar uma mensagem sobre o commit realizado


- ***Push*:** Envia as mudanças a um repositório remoto 

```
git push origin master
git push origin funcionalidade_x
```


###  OUTROS COMANDOS GIT

#### GIT LOG
- Apresenta o histórico de commits

```
git log
git log <file>
git log --since=<YYYY-MM--DD> --UNTIL=<YYYY-MM-DD>
```

visualizar todos commits em uma linha `git log --oneline`
visualizar as alterações feitas pelos commit `git log -p`    q para sair
`git log --help`


mais opções visite https://devhints.io/git-log

#### GIT STATUS
Mostra os arquivos alterados e também os novos ainda não monitorados

```
git status 
git status <branch>
```

#### GIT RESET
- Rertorna a um estado anterior de commit

```
git reset --tipo <ID_commit>
git reset --soft HEAD^
git reset <nome do arquivo>
```

- Tipos de reset
	- **soft**:  retorna imediatamente ao estado antes do commit
	- **Mixed**: retorna ao estado antes do commit e antes do add
	- **Hard**: apaga tudo para antes do commit 

#### GIT DIFF

- Mostra os detalhes das alterações nos arquivos

```
git diff (diferença do que foi editado antes do add)
git diff <hash-do-commit><nome-do-arquivo>
git diff <hash-commit1><hash_commit2>
git diff <origin><master> # diferença entre commit atual e ultimo push
```

#### GIT REVERT
- Desfaz um commit
`git revert <hash do commit>`


### TRABALHANDO COM BRANCHES

#### GIT BRANCH
- Exibe/cria branches

```
git branch
git branch <nome da branch>
```

### GIT CHECKOUT
- Altera a branch atual de trabalho

```
git checkout <nomeBranch>
git checkout -b <nome> - cria uma nova branch e muda para ela 
git checkout <hashCommit><nomedoArquivo> - recupera versão antiga
git checkout --<nome do arquivo> - desfazer alterações de um arquivo
```

#### GIT PULL
- Busca as modificações do repositório remoto para o local
```
git pull origin master
git pull origin funcionalidade-X
```

#### GIT CLONE
- Clona o repositório de um terceiro para trabalhar

```
git clone <nomeRepositorio>
```

#### GIT REMOTE ADD
- Adicionar um repositório remoto
`git remote add origin <endereço>`

#### GIT PUSH
envia mudanças para repositório remoto 
`git push -u origin master`





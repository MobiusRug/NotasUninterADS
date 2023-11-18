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

### Estados do GIT
- Untracked
- Unmodified
- Modified
- Staged


## CONFIGURANDO O GIT 

### git config 
Usado para configurar opções do GIT

- `$ git config --global user.name "Seu Nome"`
- `$ git config --global user.email "seu.email@exemplo.com"`
- `$ git config –list`

### git init
- Inicializa um novo repositório Git em um diretório existente
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

visualizar todos commits em uma linha `git log --oneline`, outros opções `--decorate`
visualizar as alterações feitas pelos commit `git log -p`    q para sair
`git log --help`


mais opções visite https://devhints.io/git-log

#### GIT STATUS
Mostra os arquivos alterados e também os novos ainda não monitorados

```
git status 
git status <branch>
```

#### GIT RESTORE
- Desfaz quaisquer unstaged changes 
- Modified -> último commit
- Para desfazer staged `git restore --staged`
#### GIT RESET
- Rertorna a um estado anterior de commit, ou seja desfaz as staged changes depois do git add 
- Staged -> Modified

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
- o padrão é mostrar as diferenças no estado modified mas não staged
- caso queira ver as diferenças no estado staged, antes do commit, utilizar `git diff --staged`

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

#### GIT CHECKOUT
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

#### GIT FETCH
- utilizado para baixar conteúdos do repositorio remoto, sem aplicar as mudanças no working directory
`git fetch`
- é possível verificar as modificações com `git diff origin/master`

#### GIT MERGE
- utilizado para combinar alterações de um ramo em outro.

1. **Selecionar o Ramo de Destino:** Começa-se por verificar o ramo no qual se deseja mesclar as alterações. Geralmente, este é o ramo no qual se deseja atualizar com as alterações de outro ramo.
    
    bashCopy code
    
    `git checkout ramo_de_destino`
    
2. **Executar o Comando de Mesclagem:** Após ter verificado o ramo de destino, utiliza-se o comando `git merge` para especificar o ramo de origem que se deseja mesclar no ramo de destino.
    
    bashCopy code
    
    `git merge ramo_de_origem`
    
    O `ramo_de_origem` contém as alterações que se deseja incorporar no `ramo_de_destino`.
    
3. **Resolver Conflitos:** Se houver conflitos entre os dois ramos (ou seja, alterações nas mesmas partes do código), o Git identificará esses conflitos. É necessário resolver manualmente esses conflitos, editando os arquivos afetados. Após resolver os conflitos, deve-se adicionar e confirmar as alterações.
    
4. **Confirmar a Mesclagem:** Após resolver quaisquer conflitos e efetuar as alterações necessárias, pode-se confirmar a mesclagem.
    
    bashCopy code
    
    `git commit -m "Mesclar o ramo 'ramo_de_origem' no 'ramo_de_destino'"`
    
5. **Enviar as Alterações:** Se estiver trabalhando em um repositório compartilhado, geralmente será necessário enviar as alterações mescladas para o repositório remoto para que fiquem disponíveis para os outros.
    
    bashCopy code
    
    `git push origin ramo_de_destino`
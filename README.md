# Git

`GIT` - track changes

`GITHUB` - cloud platform to store repositories online and collaborate with others. Microsoft.

`GITLAB` - same thing but is Open Source.

Quando clona um repo do github, será nomeado como ORIGIN por padrão.

`Branch` - versão paralela do código original

`git add .` - envia os arquivos para staging area

# MANDAR CÓDIGO P/ REPOSITÓRIO NOVO
```
1. criar repositório novo
2. git init
3. git add .
4. git commit -m "menssagem"
5. git remote add origin LinkDoRep.git
6. git push -u origin main
```
# BRANCH
```
git branch nomeDaBranchNova:
cria uma nova branch com base na branch atualmente selecionada (HEAD).

git branch branch1 branch2:
branch1, nome da nova branch a criar
branch2, da onde virá o código base
*Altera pra nova branch direto.
*Variação do comando acima para especificar a branch de referência ao criar uma nova branch.

git branch -m antigoNome novoNome: altera o nome da branch
```

`git switch (nome da branch ou hash)` - muda para a branch onde as alterações serão feitas.

`git checkout (nome da branch ou hash)` - igual switch

`git checkout -b nomeDaBranch` - cria e move as alterações para a branch criada direto.
***
`git pull` - atualiza as alterações do gituhub para o pc, na branch selecionada
***
`git push -u origin nomeDaBranchCriada` - cria a branch no github

`git push --set-upstream origin nomeDaBranchCriada` - maneira longa
***
`git fetch --prune` - verifica se alguma branch foi deletada no github, ou seja, remotamente

`git branch -d nomeDaBranch` - deleta a branch localmente, porque o git nao faz isso automaticamente
***
`git status` - mostra branch atual, commits e untracked files. (files não adicionados com git add .)
***
`git log --oneline` - mostra hash e mensagem  
`git log` - mostra histórico de commits. (hash, autor, data e msg do commit)  
`git log --all` - mostra histórico de commits de todas as branches.

```
git branch myNewBranch
git switch myNewBranch

git add .
git commit -m "mensagem aqui"
git push -u origin myNewBranch

git add .
git commit -m "mensagem 2 aqui"
git push

git fetch --prune
git branch -d nomeDaBranch
```

# ⬇️ CONCEITOS ⬇️ 

`stagin area`: arquivos adicionadas via "git add." e prontos para serem comitados. Ou seja, estão estaged, estão no repositório local
unstaged: arquivos não comitados, não estão na pasta oculta do git ainda, ou seja, estão no working tree / working directory (a pasta normal do pc) 

# ⬇️ GIT AVANÇADO ⬇️ 

### ✅ git reset
> Deleta todos commits APÓS O COMMIT SELECIONADO (pode manter as alterações ou não).  
```
git reset —hard hashDoCommit: descomita localmente, as alterações são 100% deletadas do working directory/pc e da staging area.  
git push —force: atualiza o GitHub

git reset —mixed hashDoCommit: descomita localmente, as alterações voltam para o working directory/pc (desfaz o  git add .).  
git push —force: atualiza o GitHub

git reset —soft hashDoCommit: descomita localmente, as alterações voltam para a staging area.  
git push —force: atualiza o GitHub

⚠️git reset hashDoCommit (git reset —mixed hashDoCommit por padrão)  
⚠️git push —force (deleta/atualiza os commit no Github à força baseado nos commit locais, some do mapa). Não deleta as alterações locais/pc.
```

### ✅ git revert
> Cria um novo commit que desfaz as mudanças de um commit anterior, preservando o histórico. Se tiver 3 commits e quiser desfazer o segundo, o histórico do git log fica assim:  
Commit 1  
Commit 2  
Commit 3  
Revert commit 2 (o commit 3 não vai pro github ao dar git add .)

```
git add .  
git commit -m “mensagem aqui”  
git revert (hash do commit que quer voltar)

*apagar as linhas para resolver o conflito

git add .  
git revert --continue
```

### ✅ git stash
> Salva o progresso atual não comitado em um memory card. Às vezes o estado do código atual não está pronto pra ser comitado. Dai usa git stash pra salvar, trabalhar em outra coisa urgente e voltar depois.

```
git stash -m “msg” (-m “msg” é opcional)

*vai fazer outra coisa

git stash list  
git stash apply (volta as alterações, continua no stash)  
git stash apply stash@{4} (volta apenas alteração específica do index 4, continua no stash)

git stash clear: limpa a lista toda (deleta tudo)  
git stash drop stash@{5}: deleta só a mudança de index 5 da lista.

git stash pop: manda a mudança do topo da lista de volta pra branch e remove do stash  
git stash pop —index 1: somente a mudança de index 1 volta

git stash branch NomeDaBranch 3: cria uma nova branch e coloca a mudança de index 3 na branch
```

### ✅ git restore
> Remove tudo que não estiver na staging area, ou seja tudo antes do "git add .". Útil para quando fez cagada e quer voltar ao estado original do repositório.
```
git restore .
git clean -fd
git fetch origin
git reset --hard origin/$(git branch --show-current)
```

# ⬇️ APRENDER UM DIA ⬇️ 

git diff  
git merge  
git rebase

ncu checa TODAS as dependencias  
ncu -u atualiza TODAS as dependencias pra ultima versao

### git rebase
> Troca o nome do commit (⚠️fica tudo registrado!! Ver com git reflog).

```
git commit --amend -m "nova mensagem" (troca nome do commit mais recente)
git push --force

git rebase -i HEAD~2 (troca nome do commit desejado, nesse caso mostra os 2 últimos)
```

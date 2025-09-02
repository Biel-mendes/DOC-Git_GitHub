# Git e GitHub

---

## Comandos Mais Comuns

Aqui vou colocar, para futuras consultas, os principais comandos do git.

Ao criar um repositório no github e um projeto localmente, o primeiro comando que deve ser executado no terminal dentro do diretório do projeto é:

```bash
git init
```

isso irá criar um diretório “.git” em seu projeto assim permitindo com que consiga sincronizar com o repositorio online e possa fazer mudanças posteriores.

Quando executar o primeiro comando você deve “dizer ao git” quais arquivos do seus diretório deseja adicionar ao repositório. Para isso, use o seguinte comando:

```bash
git add .  # Adiciona todos os arquivos presentes no diretório ao repositório
git add nomeDoArquivo  # Adiciona apenas um arquivo específico
```

No final desta etapa todos os arquivos que adicionou usando o comando acima estarão disponíveis para o `commit`. 

O `commit` é um comando que registra, localmente, as alterações adicionadas ao `git add`.

```bash
git commit -m " discrição da alteração "
#ao fazer um commit, é obrigatório deixar 
#uma mensagem sobre a alteração feita
```

Assim todos os arquivos serão salvos localmente e estarão prontos para serem enviados ao repositório remoto via `git push`.

Caso seja seu primeiro `commit` informe ao git o link do repositório, desta forma seu arquivos serão salvos no seu repositório.

```bash
git remote add origin <URL_DO_REPOSITÓRIO>
```

O `push` é o comando responsável por enviar as alterações feitas ao repositório remoto.

```bash
git push origin main
```

Assim, todas as alterações estarão disponíveis no seu repositório online e poderão ser acessadas de qualquer computador com permissão.

Quando existe mais de um colaborador no projeto o `git pull` é um comando muito importante para sempre trabalhar em suas versão mais atualizada, pois ele que traz as alterações remotas para o diretório local.

```bash
git pull
```

---

## Configurações de Conta

```bash
git config --global user.name "Seu Nome de Usuario"
git config --global user.email "Seu Email do GitHub"
```

---

## Comandos Para Versionamento

A parte do versionamento é uma das partes mais importantes de um projeto, pois permite que os colaboradores trabalhem em conjunto em diferentes versões do código, sem que a raiz principal seja modificada.

### Branches

São como cópias do projeto que podem ser trabalhadas em paralelo sem modificar a raiz do código.

Criando uma `Branch`:

```bash
git branch nome-da-branch 
git checkout -b nome-da-branch #criar uma branch e mudar para ela logo em seguida
```

Trocando para a `Branch` criada:

```bash
git checkout nome-da-branch
git switch nome-da-branch
```

Listar todas as `Branches` criadas:

```bash
git branch
git branch -a #listar todas as branch incluindo as remotas
```

Deletar uma `Branch`:

```bash
git branch -d nome-da-branch
git branch -D nome-da-branch #força a exclusão da branch 
```

Mudar o nome de uma `Branch`:

```bash
git branch -m novo-nome #caso esteja na branch atual
git branch -m nome-antigo novo-nome #caso esteja em alguma outra branch
```

Mostrar as diferenças entres `branches`:

```bash
git diff nome-da-branch
```

`Push` de uma `Branch` para o repositório remoto:

```bash
git push origin nome-da-branch
```

Outro comando muito útil para manter uma `branch` atualizada é o:

```bash

git rebase main

```
esse comando traz todos os `commits` da branch main para sua nova `branch`, garantindo assim que sua branche ao realizar o `menge` não seja uma versão desatualizada.

---

### Merge

É um comando que junta `branches`, muito util para atualização do projeto, trazendo atualizações e mudanças feitas em paralelo

Ao mudar para a `Branch` que principal, realize o seguinte comando para realizar um `Merge`: 

```bash
git checkout main #muda para a raiz do projeto
git merge nome-da-branch
```

---

### Comandos úteis do Git

```bash
git status #isso mostra arquivos modifocado e adicionados 
						#ou que ainda não foram rastreados
						
git log	#isso mostra o historico de todos os commits feitos

git clone https://github.com/usuario/repositorio.git 
#clona um repositorio em uma pasta no seu computador

git show <id do commit> # mostra todas as informações do commit selecionado

git diff # esse comando permite você vizualizar todas suas alterações ainda não comitadas e permite comparar commits 
git diff <id do commit> # compara a sua alteração com o último commit
git diff <id do commit>..<outro id de commit> #ele faz a comparação entre dois commits
			
```

Um outro comando muito útil para o git é o `git stash`, ele permite guardar suas alterações incompletas(não podem ser commitadas) para poder resgatá-las mais tarde. 

```bash
#guarda todas suas alterações e mantém o código sem elas, você pode fazer varias stash
git stash
# todos os stash são guardados em um índice, com apply você escolhe qual você stash você quer aplicar
git stash apply numero-do-stash
git stash pop # aplica a modificação no topo do índice
git stash drop # apaga a modificação no topo do índice
```

---

### Como Reverter um Commit?

```bash
git log #mostra todos os commits e seus id
git revert "coloque aqui o id do seu commit"
git push origin main
```

### E Como Deletar um Commit?

```bash
git log #é preciso pegar o id do commit 
				#anterior ao que deseja deletar
git reset --hard "coloque o id do anterior commit aqui"
```

### Como Alterar um Commit?

```bash
git commit --amend -m "nova menssagem"
#ou
git add <file não adicionado>
git commit --amend
```

### Como Reverter uma Modificação

```bash
# você apaga todas as modificações feitas, você também adicionar no lugar do ponto o arquivo.file que deseja resetar
git restore .
```

---

### [README.md](http://README.md)

Pode ser formatado com tags html ou markdown.

diga: usar o notion para gerar um arquivo em markdawn e passar para o [README.md](http://README.md) no git. 

---

### .gitignore.

É uma ferramenta muito útil para ignorar arquivos que deseja esconder ou que não são relevantes.

diga: usar o site [gitignore.i](http://gitignore.io)o, ele gera um arquivo gitignore com todos os arquivos que podem ser ignorado em um  projeto de determinada linguagem.

---
### Parâmetros do `log` 

No comando `git log` podemos adicionar diversos parâmetros para otimizar nossas buscas pelos commits 

```bash
git log -p #exibe com detalhes todas as informações do commit incluindo trechos de códigos modificados

git log --oneline #exibe um resumo do commit, somente com as informações mais relavantes

```

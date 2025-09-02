# Git e GitHub

---

## Comandos Mais Comuns

Este guia reúne os principais comandos do Git para consulta rápida e prática.

### Inicializando um Projeto Git

Após criar um repositório no GitHub e um projeto localmente, o primeiro comando a ser executado no terminal, dentro do diretório do projeto, é:

```bash
git init
```
Cria o diretório `.git`, tornando seu projeto rastreável pelo Git e pronto para sincronização com o repositório remoto.

### Adicionando Arquivos

Escolha os arquivos que deseja rastrear pelo Git:

```bash
git add .                # Adiciona todos os arquivos
git add nomeDoArquivo    # Adiciona apenas um arquivo específico
```
Após esta etapa, os arquivos estão prontos para serem commitados.

### Realizando Commits

O commit registra as alterações localmente. É obrigatório informar uma mensagem descrevendo o que foi alterado:

```bash
git commit -m "descrição da alteração"
```

### Vinculando ao Repositório Remoto

Se for seu primeiro commit, conecte seu projeto ao repositório online:

```bash
git remote add origin <URL_DO_REPOSITÓRIO>
```

### Enviando Alterações para o Remoto

O comando abaixo envia todas as alterações para o repositório remoto:

```bash
git push origin main
```

### Sincronizando com o Remoto

Para garantir que está trabalhando na versão mais atualizada (especialmente em projetos colaborativos):

```bash
git pull
```

---

## Configurações de Conta

Configure seu nome de usuário e e-mail para que sejam associados aos commits:

```bash
git config --global user.name "Seu Nome de Usuário"
git config --global user.email "Seu Email do GitHub"
```

---

## Comandos Para Versionamento

O versionamento permite que colaboradores trabalhem simultaneamente em diferentes versões do código. Os principais conceitos envolvem branches (ramificações) e tags.

### Branches

Permitem criar cópias paralelas do projeto para desenvolver funcionalidades ou correções sem afetar o código principal.

- **Criar uma branch:**
  ```bash
  git branch nome-da-branch
  git checkout -b nome-da-branch  # Cria e já muda para ela
  ```
- **Trocar de branch:**
  ```bash
  git checkout nome-da-branch
  git switch nome-da-branch
  ```
- **Listar branches:**
  ```bash
  git branch         # Locais
  git branch -a      # Inclui remotas
  ```
- **Deletar branch:**
  ```bash
  git branch -d nome-da-branch     # Deleção segura
  git branch -D nome-da-branch     # Força a exclusão
  ```
- **Renomear branch:**
  ```bash
  git branch -m novo-nome
  git branch -m nome-antigo novo-nome
  ```
- **Mostrar diferenças entre branches:**
  ```bash
  git diff nome-da-branch
  ```
- **Enviar branch para o remoto:**
  ```bash
  git push origin nome-da-branch
  ```
- **Atualizar branch com commits da main:**
  ```bash
  git rebase main
  ```
  Traz os commits da `main` para sua branch, evitando desatualizações antes do merge.

---

### Git Tag – Controle de Versão

Tags são usadas para marcar pontos específicos na linha do tempo do projeto, geralmente indicando versões estáveis ou releases.

- **Criar uma tag simples:**
  ```bash
  git tag v1.0.0
  ```
- **Tag com anotação (recomendado para releases):**
  ```bash
  git tag -a v1.0.0 -m "Release versão 1.0.0"
  ```
- **Listar todas as tags:**
  ```bash
  git tag
  ```
- **Enviar tags para o repositório remoto:**
  ```bash
  git push origin v1.0.0
  git push origin --tags        # Envia todas as tags
  ```
- **Ver detalhes de uma tag:**
  ```bash
  git show v1.0.0
  ```
- **Deletar tag local/remota:**
  ```bash
  git tag -d v1.0.0
  git push origin --delete v1.0.0
  ```

---

### Merge

Junta branches, trazendo alterações desenvolvidas em paralelo para a principal.

```bash
git checkout main          # Vai para branch principal
git merge nome-da-branch  # Une branch especificada na main
```

---

### Git Cherry-pick

O comando `git cherry-pick` permite aplicar um commit específico de outra branch na branch atual. É muito útil para trazer correções ou funcionalidades pontuais sem precisar fazer um merge completo da branch de origem.

**Como usar:**
```bash
git cherry-pick <id-do-commit>
```

**Exemplo de uso:**  
Suponha que você está na branch `main` e deseja trazer apenas um commit específico da branch `feature-x`, basta executar:

```bash
git cherry-pick a1b2c3d4
```
Onde `a1b2c3d4` é o ID do commit desejado.  
O Git irá aplicar esse commit na sua branch atual, preservando o histórico do commit original.

**Observações:**
- Você pode cherry-pick múltiplos commits de uma vez:  
  ```bash
  git cherry-pick id1 id2 id3
  ```
- Caso ocorra conflito, o Git irá solicitar que você resolva antes de concluir o cherry-pick.
- Ideal para aplicar hotfixes ou correções específicas em produção sem trazer todo o histórico de outra branch.

---

### Comandos Úteis do Git

```bash
git status                 # Mostra arquivos modificados, adicionados ou não rastreados
git log                    # Histórico de commits
git clone <URL>            # Clona um repositório remoto
git show <id do commit>    # Detalhes de um commit específico
git diff                   # Visualiza alterações não commitadas; compara commits
git diff <id do commit>    # Compara alterações com o último commit
git diff <id1>..<id2>      # Compara dois commits diferentes
```

---

### Git Stash

Permite guardar alterações não finalizadas, para recuperá-las depois.

```bash
git stash                  # Salva todas alterações não commitadas
git stash apply <num>      # Aplica stash específico
git stash pop              # Aplica e remove o topo do stash
git stash drop             # Remove o topo do stash
git stash list             # Lista todos stashes
```

---

### Como Reverter, Deletar e Alterar Commits

- **Reverter um commit:**
  ```bash
  git log
  git revert <id do commit>
  git push origin main
  ```
- **Deletar um commit (retroceder para commit anterior):**
  ```bash
  git log
  git reset --hard <id do commit anterior>
  ```
- **Alterar mensagem ou incluir arquivos em um commit:**
  ```bash
  git commit --amend -m "nova mensagem"
  git add <arquivo>
  git commit --amend
  ```

---

### Reverter Modificações

```bash
git restore .                      # Apaga todas modificações feitas
git restore <arquivo>              # Restaura arquivo específico
```

---

### README.md

Este arquivo pode ser formatado com tags HTML ou Markdown. Dica: use ferramentas como o Notion para gerar o conteúdo e exportar em Markdown para facilitar o processo.

---

### .gitignore

Ferramenta para ignorar arquivos desnecessários ou confidenciais. Dica: o site [gitignore.io](https://gitignore.io) gera arquivos `.gitignore` customizados para diferentes linguagens e frameworks.

---

### Parâmetros Avançados do `git log`

- **Exibir detalhes completos dos commits:**
  ```bash
  git log -p
  ```
- **Resumo dos commits:**
  ```bash
  git log --oneline
  ```

---

### Viajando no Tempo

O comando `restore` permite transitar entre commits anteriores, reverter estados e desfazer adições ao staging.

```bash
git restore --staged nome-do-arquivo     # Remove arquivo do staging
git restore --source=<id-do-commit> .    # Restaura projeto/arquivo de commit específico
```

---

## Referências

- [Documentação Oficial Git](https://git-scm.com/doc)
- [Documentação GitHub](https://docs.github.com/)
- [gitignore.io](https://gitignore.io)

# Fluxo de Trabalho

O fluxo de trabalho padrão que deve ser utilizado em todos os projetos é o [Forking Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow).


#### 1. Faça o _fork_

1. Entre no Projeto desejado
1. Clique no botão "Fork" (no canto superior).

#### 2. Clone o seu _fork_

Faça o Clone do projeto em questão de preferencia usando SSH.
- [SSH/GIT ](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)


#### 3. Crie uma ramificação  e faça as modificações

```bash
git checkout -b xpto
```
#### 4. Matenha sua ramificação main sempre sincronizado

```bash
git rebase upstream/master
```
#### 7. Envie as modificações para seu _fork_
```bash
git commit -a -m "fix bug xpto"
git push origin xpto
```

#### 8. Abra o Pull Request

[Pull Requesrt](https://github.com/dotnet-guides/blob/master/documentation/dev-ops/pullrequest.md)

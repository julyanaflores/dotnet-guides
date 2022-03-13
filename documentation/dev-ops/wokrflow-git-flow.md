## git flow


#### Conceito


- É uma ideia abstrata do fluxo de trabalho git, a qual nos possibilita a definição de quando as diferentes ramificações devem interagir. O propósito de implementar essa ideia através de uma ferramenta é, facilitar e dar transparência ao processo, trabalhando como uma extensão a qual não influencia diretamente o repositório.

![diagrama](https://wac-cdn.atlassian.com/dam/jcr:61ccc620-5249-4338-be66-94d563f2843c/05%20(2).svg?cdnVersion=1256
)

Em contrapartida ao modelo beseado em fork, o git-flow trabalha usando duas ramificações para o armazenamento de histórico do projeto:
- **Ramificações**
- **main**:
  contém todo o histório de atuações de todas as outras ramificações, refletindo o ambiente de produção.

- **release**:
  a partir de um agrupamento de features considerada entregável, que tenha valor, então será gerado uma nova release.

- **develop**:
  tem o papél de integrar todos os outros recursos e contextos do processo, como: bugs ou features.

- **feature**: Funcionalidades do sistema que entrega um benefício ou resolve um problema real do cliente.

    - **hotfix**:
      responsável pelo processo de correção de bugs gerados ao nosso incremento do produto, ou algo já estabelecido



#### Ferramenta
- [Instalação](https://git-scm.com/)
    - Para quem já tem o git instalado na máquina, não seria necessário configurações adicionais.

#### Fluxo

- Para construir toda essa ideia, considerando que o o git-flow já estejá instalado na máquina, devemos fazer a distribuição entre as ramificações prícipais, **main** e **develop**. Uma boa maneira de fazer isso é criando uma branch **develop** local e executando um **push** para o repositório  remoto utilizando, no nosso caso, o **Github**:

  ```git
  git branch develop
  git push -u origin develop
  ```
- O primeiro comando irá cria a nossa branch de desenvolvimento. Para checar se tudo ocorreu bem, execute:
  ```git branch -a```, e então podemos executar o segundo comando, o qual irá criar uma nova branch no nosso repositório remoto.

#### DevOps

- Para que todos os envolvido no processo possam estar trabalhando com as novas ramificações, será necessário efetuar o clone do repositório central e configurar o git-flow. Para que isso aconteça, basta que os mesmos execute o seguinte comando:
  ```
  git flow init
  ```
- A partir disso será necessário configura todos os recursos nas suas ramificações de forma adequada, permitindo que posteriomente possam ser utilizadas da melhor maneira.
  ```
  Branches name for production releases: [main] = default
  Branches name for "next release" development: [develop] = default

  How to name your suppporting branch prefixes ?

  Feature branches? [feature/] = feature-xpto
  Release branches? [release/] = release-xpto
  hotfix  branches? [hotfix/]  = hotfix-xpto
  Support branches? [support/] = support-xpto

  Version tag prefix? [] = default
  ```
- Feito isso, se executarmos o comandos que lista as nossas ramificações, ```git branch -a```, teremos o retorno apenas da branch **main** e **develop**. Isso acontece porque todos os outros recursos devem ser derivados do contexto da branch **develop**, e aparir do momento da sua conclusão poderá voltar a sua origem.

#### Exemplo

##### Features

- Todas as branches de recurso são baseadas na versão mais atual da **develop**, e para trabalhar em uma atividade relacionado ao nosso board teremos que dar um start na ramificação desse recurso e para isso basta executar o seguinte comando:
   ```
   git flow feature start documentando-git-flow
   ```
- Como definimos um padrão para as nossas features, o resultado, se executarmos o comando: ```git branch -a```, será:
   ```
   master
   develop
   feature-xpto/documentando-git-flow.
  ```
- Ao finalizar a ativade e executar todos os commits necessários, teremos que passar pela aprovação do time e para que isso ocorra devemos executar o seguinte comando:
  ```
  git add . ou git add <file>
  git commit -m "documentando git flow"
  git flow feature publish documentando-git-flow
 
  ```
- Isso vai permitir que seja possível abrir um **pull request** e por conseguinte a análise e aprovação do time. A partir do momento em que as alterações da **feature**
-  foram para a branch **develop** no **Github**, será necessário finalizar a **feature** local. Uma coisa importante é, ao executar esse passo todas as alterações da sua feature **local** serão megeadas para a **main** local, isso tira a necessidade de atualizar esta ramificação.

- Para finalizar a feature local, execute:

  ```
  git flow feature finish documentando-git-flow
  ```

##### Releases

- Para um incremento de uma nova release, ou seja, a liberação de um novo pacote de valor para o cliente, é necessário que a branch de **develop** tenha adquirido recurso o bastante para a sua liberação, isso dependendo da regra que o time implementar. Para criação de uma nova release basta executar o seguinte comando:
   ```
   git flow release start v1.0.0
   ```

- A partir desse momento, se não for um caso urgente como: correção de bugs, geração de documentação e outras tarefas relacionadas ao lançamento, nenhum outro recurso pode ser adicionado.

- Devemos publicar o release para o repositório remoto, assim todos vão saber que temos um release candidate, a qual consequentemente já está em um ambiente de pré-produção:
   ```
   git flow release publish v1.0.0
   ```

- Quando a release, ou lançamento, estiver pronto para agregrar valor ao cliente, será necessário efetuar o merger com as demais ramificações, no caso a **main**, marcando-a com o número da versão. Além disso, devemos fazer o merge com a branch **develop**, a qual pode ter progredido no decorrer do lançamento, **release**.

- Para finalizar a release, será necessário executar o seguinte comando:
   ```
   git flow release finish v1.0.0
   ```

##### Hotfix

- É uma ramificação de manutenção, que nos permite corrigir rápidamente bugs em produção, ou em releases/lançamentos, sem impedir que as outras atividades sejam interrompidas. Essa branch é a única baseada na branch **main**. Um vez que a correção seja feita, deve-se efetuar o **merge** com a branch **main**, marcada com a versão atualizada, e **develop**.

- "Ter uma linha de desenvolvimento dedicada para correções de bugs permite que sua equipe aborde problemas sem ter que interromper o resto do fluxo de trabalho ou esperar o próximo ciclo de lançamento", [Atlassian](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow#:~:text=O%20conjunto%20de%20ferramentas%20git,tem%20um%20processo%20de%20instala%C3%A7%C3%A3o.&text=O%20Git%2Dflow%20%C3%A9%20um,ser%20criar%20ramifica%C3%A7%C3%B5es%20para%20voc%C3%AA.).

- Para criar uma branch de manutenção, **hotfix**, será necessário executar o seguinte comando:
   ```
   git flow hotfix start melhorando-documento-git-flow
   ```
- Devemos publicar o **hotfix** para o repositório remoto, assim todos vão saber que temos um bug em produção que precisa ser corrigido.
   ```
   git flow hotfix publish melhorando-documento-git-flow
   ```
- Assim como na finalização da ramificação de **release**, a ramificação de **hotfix** é mesclada tanto na branch **main** quanto na de **develop**.

- Para finalizar uma branch **hotfix**, execute o seguinte comando:
   ```
   git flow hotfix finish  melhorando-documento-git-flow
   ```
##### Referências

[Atlassian - Fluxo de trabalho de Git flow](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow#:~:text=O%20conjunto%20de%20ferramentas%20git,tem%20um%20processo%20de%20instala%C3%A7%C3%A3o.&text=O%20Git%2Dflow%20%C3%A9%20um,ser%20criar%20ramifica%C3%A7%C3%B5es%20para%20voc%C3%AA.)

[Medium - Trabalhando com git e git-flow no dia a dia(básico)](https://medium.com/diegowribeiro/trabalhando-com-git-e-git-flow-no-dia-a-dia-b%C3%A1sico-96a3ae02f8e3)
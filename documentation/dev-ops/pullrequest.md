# Pull Request

Após realizar as implementações e enviar as alterações para o seu _fork_, é necessário abrir um Pull Request para seguir o fluxo de aprovação e posteriormente o _merge_.

## Antes de criar

1. Garanta que existe uma _issue_ no que será associada a este PR.
1. Certifique-se que utilizou as boas práticas.
1. Garanta que as [mensagens de commit](https://chris.beams.io/posts/git-commit/) estão claras.
1. Divida grandes alterações em uma série de pequenos _patchs_, isso facilitará o entendimento/análise das alterações.

## Criar
1. Clique no botão _Pull Request_ e selecione o _branch_ que contém sua alteração.
1. Escreva o título do seu PR, o texto deve ser breve.
1. Adicione uma descrição de acordo com o "pullrequest-template"
1. Selecione, pelo menos, dois revisores para o seu PR.
1. Verifique mais detalhes de como criar um pull request [aqui](https://help.github.com/articles/about-pull-requests/).

## Revisar

1. Durante a revisão, o PR deve estar com a label `in-review`. Lembre-se de adicionar e remover.
1. Entenda o motivo das alterações, seja através da descrição do PR ou _issue_.
1. Avalie os impactos das alterações, faça uma execução mental do código e, quando necessário, clone o _branch_.
1. Evite revisar o código com o autor, se for necessário pedir explicação sobre o código, acenda o sinal de alerta.
1. Identifique soluções não-adequadas, sinalize o melhor caminho e inclua nos guias quando necessário.
1. Verifique os testes automatizados, eles também são código.

## Ajustes

1. Durante a execução dos ajustes, o PR deve estar com o label `work-in-progress`. Lembre-se de adicionar e remover.
1. Todos os ajustes devem ser realizados de acordo com os comentários dos revisores. Não adicionar, em hipótese alguma, novas implementações.
1. Avaliar os comentários e, quando necessário, questionar os revisores.
1. Faça um `commit` para cada comentário realizado pelo revisores.
1. Adicionar um comentário em resposta aos revisores apenas se não foi realizado (exatamente) o que foi solicitado.
1. Notifique os revisores (através de um comentário com citação) quando finalizar os ajustes.

## Mergear

1. Aguarde a validação de, pelo menos, dois revisores.
1. Matenha o PR aberto por 24h, quando possível.
1. Verifique se o PR não esta com o label `do-not-merge`.
1. Altere os status das _issues_ associadas ao PR.

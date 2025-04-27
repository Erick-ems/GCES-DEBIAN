# Guia de Contribuição de Pacotes

Antes de contribuir, por favor, leia cuidadosamente este guia para garantir que seguimos um processo organizado, eficiente e em conformidade com as práticas da comunidade Debian.

## 1. Selecione um Pacote

Escolha um pacote para trabalhar. Você pode encontrar pacotes que precisam de ajuda de várias maneiras:

- **Pacotes órfãos**: [Pacotes órfãos no Debian](https://www.debian.org/devel/wnpp/orphaned.pt.html)
- **Pedidos de pacotes novos**: [Pacotes solicitados no Debian](https://www.debian.org/devel/wnpp/requested)
- **Listas de pacotes que precisam de ajuda**: [Lista do Eriberto](https://people.debian.org/~eriberto/udd/help_a_package.html) e [Lista do Talau](https://people.debian.org/~talau/udd/)
- **Usando `how-can-i-help`**: [How can I help](https://wiki.debian.org/how-can-i-help)

## 2. Crie uma Issue no Salsa

Após escolher o pacote, crie uma issue no nosso repositório de documentação no Salsa:

[https://salsa.debian.org/debian-brasil-team/docs/-/issues/new](https://salsa.debian.org/debian-brasil-team/docs/-/issues/new)

Preencha os campos da seguinte forma:

- **Título**: `Package <nome_do_pacote>`
- **Tipo**: `Issue`
- **Descrição**: Inclua informações como:
  - Link para a página do pacote no Tracker
  - Link para o repositório no Salsa, se existir
  - Link para a Merge Request no repositório Salsa do pacote, se houver
  - Link para bugs relacionados ao trabalho que será feito
  - Link para a página do pacote em [lintian.debian.org](https://lintian.debian.org/sources/<nome_do_pacote>)

## 3. Trabalhe no Pacote

Faça um fork do repositório do pacote no Salsa e inicie o trabalho. Utilize ferramentas como `git-buildpackage` para gerenciar o empacotamento. Se o pacote não possuir um repositório no Salsa, entre em contato com um revisor para providenciar a criação do mesmo.

Durante o trabalho, mantenha a issue atualizada e mova a label para `Doing`.

## 4. Submeta uma Merge Request

Quando o trabalho estiver finalizado e pronto para revisão, submeta uma Merge Request (MR) para o repositório oficial do pacote. Adicione o link da MR na issue e mude a label da issue para `Review`.

## 5. Revisão do Pacote

Com a issue na label `Review`, envie uma notificação no canal do Debian Brasil para encontrar um sponsor, usando o link para a issue. Ao encontrar um sponsor, ele deve se adicionar como `Assignee`.

A revisão será feita na própria MR, com comentários inline quando possível. Pode haver uma ou mais iterações de revisão até que o sponsor esteja satisfeito com as modificações.

## 6. Upload do Pacote

O sponsor irá construir o pacote e fazer o upload para o repositório oficial do Debian. Assim que o email de confirmação do upload for recebido, a issue deverá ser fechada pelo sponsor ou contribuidor.


# Visão geral sobre o Tracker

O [Debian Tracker](https://tracker.debian.org) é uma ferramenta essencial para quem deseja acompanhar e contribuir com pacotes no ecossistema Debian. Ele centraliza informações como bugs, versões, status de construção, repositórios Git, lintian, changelogs e muito mais.

Este guia foi feito especialmente para iniciantes que desejam entender o fluxo de contribuição com empacotamento Debian, utilizando o Tracker em conjunto com ferramentas como o Salsa, IRC, Matrix, quadro de issues e Git.


##  Como Usar o Debian Tracker

1. Acesse: [https://tracker.debian.org](https://tracker.debian.org)
2. Procure um pacote pelo nome (ex: `flask`, `python3-requests`, `ffmpeg`)
3. A página do pacote exibe:
   - Versões nas releases (Stable, Testing, Unstable)
   - Bugs abertos (por gravidade)
   - Status de construção por arquitetura
   - Problemas apontados pelo lintian
   - Link para repositório no Salsa
   - Changelog e uploads recentes
   - Mantenedores e colaborações


##  Como Escolher um Pacote Para Contribuir

Você pode ter ideia do nível de dificuldade de um pacote observando os **sinais visíveis no Tracker**. Aqui está um guia dividido em três níveis:

### Pacotes Fáceis

**Tarefas típicas:**
- Atualizar para nova versão upstream
- Ajustar `Standards-Version` no `debian/control`
- Melhorar descrições (`Description`) ou manpages
- Adicionar `Rules-Requires-Root: no`

**Sinais no Tracker:**
- Nenhum ou poucos bugs abertos
- Sem `lintian errors` (pode ter warnings simples)
- Campo de `Maintainer` ativo
- Último upload recente
- Não aparece em `Autoremoval from testing`
- Build em todas as arquiteturas OK (`Build status: success`)
- Upstream com releases frequentes (ver link de `Homepage`)


###  Pacotes de Dificuldade Média

**Tarefas típicas:**
- Corrigir avisos do `lintian` (como `hardening`, `missing-depends`, etc.)
- Atualizar dependências desatualizadas
- Corrigir bugs normais ou wishlist
- Adicionar testes (`debian/tests/control`)
- Ajustar compatibilidade com `Python 3.x`, `systemd`, etc.

**Sinais no Tracker:**
- Bugs normais ou `wishlist` abertos
- `Lintian` com warnings ou minor errors
- Repositório Git atualizado, mas com poucos commits recentes
- Último upload com mais de 6 meses
- Build com falha em uma ou duas arquiteturas não principais
- Aparece em `Autoremoval from testing` (mas ainda com prazo)
- Depende de pacotes que foram removidos ou estão em transição (`out-of-date`)

###  Pacotes Difíceis

**Tarefas típicas:**
- Corrigir bugs críticos (RC: Release Critical)
- Resolver `FTBFS` (Fails To Build From Source)
- Trabalhar com pacotes em transição de bibliotecas ou grandes mudanças de linguagem
- Refatorar pacotes com estrutura obsoleta
- Migrar empacotamento de `CDBS` para `dh` (ou modernizar `debian/rules`)
- Corrigir pacotes órfãos (ver `WNPP`)

**Sinais no Tracker:**
- Muitos bugs `serious` ou `grave` (veja lista no topo da página)
- Status de build: `failed`, `not-for-us`, `missing`, `out-of-date`
- Aparece como **candidato a remoção do Testing**
- `Lintian` com `serious errors` (ex: arquivos binários sem fontes, violação de políticas)
- Último upload há vários anos
- Mantenedor ausente, pacote órfão (ver `WNPP`, com status como `O`, `RFA`, `ITA`)
- Repositório Git desatualizado ou inexistente
- Problemas de transição complexos envolvendo bibliotecas

##  **Observação**

Este é um **guia introdutório**, feito **por e para iniciantes**. Ele não cobre todos os detalhes do ecossistema Debian nem substitui a documentação oficial.

Pode conter erros, estar desatualizado ou faltar pontos importantes — e tudo bem! A ideia é servir como um **ponto de partida acessível** para quem está começando a entender como usar o Debian Tracker e contribuir com pacotes.

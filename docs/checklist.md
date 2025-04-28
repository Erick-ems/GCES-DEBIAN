# Checklist

## 📦 Gerência e Controle de Versão

- [x] Repositório público no GitHub/GitLab (com histórico limpo e organizado)  
  - Localizado no salsa: [https://salsa.debian.org/debian-brasil-team](https://salsa.debian.org/debian-brasil-team)
- [ ] Uso de `git-flow` ou similar para estratégia de branches
- [ ] Versionamento semântico (SemVer) aplicado
- [ ] Tags e releases publicados com **Release Notes** claras
- [ ] GitHub Actions / GitLab CI configurado com:
  - [ ] Build automatizado
  - [ ] Testes automatizados (unitários/integrados)
  - [x] Linter (ex: ESLint, Flake8, etc.)
    - Encontrado em: [Contribuindo para o Projeto — Debian Salsa](https://salsa.debian.org/Oleari/python-humanize/-/blob/master/.github/CONTRIBUTING.md)
  - [x] Validação de segurança e dependências (ex: Dependabot, Snyk)
    - Encontrado em: [Políticas de Segurança — Debian Salsa](https://salsa.debian.org/Oleari/python-humanize/-/blob/master/.github/SECURITY.md)
  - [ ] Arquivos de configuração de ambiente: `Dockerfile`, `docker-compose.yml`, `.env.example`
---

## 📚 Documentação

Em vez de manter arquivos `.md` diretamente no repositório para a documentação, a comunidade optou por centralizar e apresentar as informações de forma mais completa e organizada em um site.

- [ ] `README.md` completo com:
  - [x] Visão geral do projeto (com prints de como funciona o projeto)  
    - Encontrado em: [Debian Brasil - Quem Somos](https://debianbrasil.org.br/pt-br/quem-somos)
  - [x] Tecnologias utilizadas  
    - Ferramentas: [Debian Brasil - Sbuild](https://debianbrasil.org.br/pt-br/howto/sbuild)
  - [x] Como rodar localmente (instalação + execução)  
    - [Configurando seu ambiente](https://debianbrasil.org.br/empacotamento/configurando-seu-ambiente)
  - [x] Como contribuir (passo a passo)  
    - [Como colaborar](https://debianbrasil.org.br/pt-br/como-colaborar)
  - [x] Como usar a aplicação (guia de usuário)  
    - [Manual do usuário Debian](https://www.debian.org/doc/user-manuals.pt.html)
  - [x] Licença  
    - [Licenças Debian](https://www.debian.org/legal/licenses/)
- [x] `CONTRIBUTING.md` com diretrizes de contribuição  
  - [Como colaborar](https://debianbrasil.org.br/pt-br/como-colaborar)
- [x] `CODE_OF_CONDUCT.md` com boas práticas de convivência  
  - [Código de Conduta Debian](https://www.debian.org/code_of_conduct.pt.html)
- [ ] `CHANGELOG.md` com histórico de alterações
- [ ] GitPage com:
  - [ ] Landing page - visão de produto (ex: [Discourse](https://www.discourse.org/))
  - [ ] Arquitetura da solução
  - [ ] Roadmap e backlog público
  - [ ] Dicionário de dados (se aplicável)
  - [x] Documentação técnica de como contribuir  
    - [Como colaborar](https://debianbrasil.org.br/pt-br/como-colaborar)

---

## 📢 Comunicação e Comunidade

- [x] Sistema de governança (ex: mantenedores, comitês, votação)  
  - [Constituição Debian](https://www.debian.org/devel/constitution)
- [x] Templates para issues e pull requests  
  - [Templates de Issues](https://salsa.debian.org/debian-brasil-team/docs/-/tree/main/gitlab/issue_templates?ref_type=heads)
- [x] Etiquetas (labels) para organizar issues  
  - [Issues no Salsa](https://salsa.debian.org/debian-brasil-team/docs/-/issues/?sort=created_date&state=opened&first_page_size=100)
- [ ] Agendas públicas de reuniões (caso ocorram)  
  - Eventos são divulgados: [Eventos Debian Brasil](https://debianbrasil.org.br/eventos)

---

## ⚖️ Licenciamento e Aspectos Legais

- [x] `LICENSE` com licença de software livre (ex: MIT, GPL, Apache 2.0)  
  - [Licença Debian](https://www.debian.org/license)
- [ ] Verificação de licenças das dependências utilizadas
- [x] Termos de uso e política de privacidade (para projetos web/app)  
  - [Política de Privacidade Debian](https://www.debian.org/legal/privacy.pt.html)

---

## 🧪 Qualidade e Testabilidade

- [ ] Cobertura de testes mínima estabelecida e monitorada
- [ ] Testes end-to-end automatizados (se aplicável)
- [ ] Ferramentas de análise estática de código
- [ ] Monitoramento de qualidade com badges (ex: Codecov, SonarCloud)

---

## 📈 Sustentabilidade e Crescimento

- [ ] Roadmap público com funcionalidades desejadas
- [ ] Planejamento de onboarding de novos contribuidores (documentação de onboarding)

---

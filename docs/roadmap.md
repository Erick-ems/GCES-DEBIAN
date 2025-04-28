# Roadmap / Cronograma

# Roadmap de Empacotamento Debian

## 📍 Visão Geral

Este roadmap descreve as etapas essenciais para o empacotamento de softwares no formato Debian (.deb), desde o planejamento até a publicação e manutenção dos pacotes.

## Etapas do Roadmap

### 1. Planejamento Inicial
- Definir quais softwares serão empacotados.
- Levantar dependências e compatibilidades.
- Escolher a versão alvo do Debian (stable, testing, unstable).

### 2. Preparação do Ambiente
- Montar ambiente de build:
- Instalar ferramentas necessárias:
  - `dpkg-dev`, `lintian`, `devscripts`, entre outros.

### 3. Empacotar o Software
- Criar o diretório `debian/` dentro do código-fonte.
- Escrever arquivos essenciais:
  - `control`, `rules`, `changelog`, `copyright`.
- Gerar o primeiro pacote `.deb` funcional.

### 4. Testes de Empacotamento
- Instalar o `.deb` em ambiente isolado.
- Executar ferramentas de verificação:
  - `lintian`, `piuparts`, entre outras.

### 5. Ajustes e Melhorias
- Corrigir erros e warnings apontados nas validações.
- Atualizar as dependências e metadados no `control`.
- Melhorar scripts de instalação e remoção

### 6. Assinatura e Publicação
- Assinar pacotes (se necessário).
- Publicar pacotes:
  - Preparar submissão para repositório oficial Debian.

### 7. Manutenção
- Atualizar pacotes com novas versões.
- Corrigir bugs e vulnerabilidades de segurança.
- Realizar rebuilds periódicos conforme novas dependências.

---

## 📅 Cronograma

| Semana | Atividade | Responsáveis | Observação |
|:------:|:----------|:-------------|:-----------|
| 1 | Definição de softwares e análise de dependências | Todo o grupo | Completar lista até o final da semana |
| 2 | Preparação do ambiente de build | Todo o grupo | Testar pbuilder e sbuild |
| 3 | Empacotar Software| Todo o grupo | Gerar .deb inicial |
| 4 | Empacotar Software| Todo o grupo| Gerar .deb inicial |
| 5 | Empacotar Software| Todo o grupo | Gerar .deb inicial |
| 6 | Empacotar Software| Todo o grupo| Gerar .deb inicial |
| 7 | Empacotar Software| Todo o grupo | Gerar .deb inicial |
| 8 | Testes gerais e correções | Todo o grupo | Rodar lintian, piuparts, corrigir problemas |
| 9 | Assinar pacotes e configurar repositório interno | Todo o grupo | Teste de distribuição |
| 10 | Documentar processo e preparar manutenção | Todo o grupo | Atualizar instruções internas |

---

## 📂 Ferramentas Recomendadas

- `dh_make`: Criar esqueleto inicial de empacotamento.
- `debuild`: Gerar o pacote `.deb`.
- `pbuilder` / `sbuild`: Build limpo em ambiente isolado.
- `lintian`: Validar a qualidade do pacote.
- `piuparts`: Testar instalação e remoção do pacote.
- `reprepro` / `aptly`: Gerenciar repositórios APT internos.

---

## 🔄 Checklist para Cada Pacote

- [ ] Diretório `debian/` criado.
- [ ] Arquivos obrigatórios escritos (`control`, `rules`, etc).
- [ ] Build bem-sucedido em ambiente isolado.
- [ ] Instalação e remoção testadas.
- [ ] Validação com `lintian` realizada.
- [ ] Pacote assinado (se aplicável).
- [ ] Documentação interna atualizada.

---

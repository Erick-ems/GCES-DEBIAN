
# 🧰 Tutorial de Empacotamento e Atualização Upstream no Debian

Este guia é voltado para iniciantes que desejam contribuir com o empacotamento de software no Debian, especialmente via o Salsa e com o apoio da comunidade Debian Brasil.

---

## ✅ Pré-requisitos

Antes de começar, é altamente recomendado estar utilizando uma distribuição baseada no Debian, como:

- **Debian** (de preferência a versão estável ou testing)
- **Devuan**, **Kali**, **MX Linux** (com algumas ressalvas)
- **Ubuntu** (é possível, mas não ideal para empacotar para o Debian oficial)

Isso garantirá que as ferramentas estejam compatíveis com os procedimentos oficiais do projeto Debian.

---

## 🧾 1. O que é o Salsa?

**Salsa** é a plataforma oficial de hospedagem de código do Projeto Debian, baseada no GitLab. Lá ficam os repositórios de pacotes, automações de CI/CD, issues, merge requests etc.

Se você deseja colaborar com o empacotamento de software no Debian, precisa ter uma conta no Salsa.

---

## 👤 2. Criando uma conta no Salsa

1. Acesse: https://salsa.debian.org  
2. Clique em **"Register"**  
3. Preencha com:  
   - **Username**: seu nome de usuário (único)  
   - **Email**: use um e-mail válido (de preferência com nome completo)  
   - **Full name**: seu nome completo  
   - **Password**: crie uma senha forte  
4. Clique em **Sign up**  
5. Confirme o e-mail clicando no link enviado para você

---

## 🔐 3. O que é uma chave SSH?

A chave SSH é uma forma segura de autenticação entre seu computador e servidores remotos, como o Salsa.

Ela é composta de dois arquivos:
- `id_rsa` ou `id_ed25519`: chave privada, fica no seu PC (NUNCA compartilhe)
- `id_rsa.pub` ou `id_ed25519.pub`: chave pública, é a que você envia para o Salsa

---

## 🔎 4. Verificando se você já tem uma chave SSH

Abra um terminal e digite:

```bash
ls ~/.ssh
```

Se aparecerem arquivos como `id_rsa.pub` ou `id_ed25519.pub`, você já tem uma chave e pode seguir para a próxima etapa.

---

## 🔧 5. Criando uma chave SSH (caso não tenha)

No terminal:

```bash
ssh-keygen -t ed25519 -C "seu-email@exemplo.com"
```

Se sua máquina for antiga e não suportar `ed25519`, use:

```bash
ssh-keygen -t rsa -b 4096 -C "seu-email@exemplo.com"
```

Quando pedir o local para salvar, apenas pressione **Enter** para aceitar o padrão (`~/.ssh/id_ed25519`).

Você pode definir uma senha (passphrase) para a chave ou deixar em branco.

---

## 📤 6. Adicionando sua chave SSH ao Salsa

1. Copie o conteúdo da sua chave pública:

```bash
cat ~/.ssh/id_ed25519.pub
```

2. Copie TODO o conteúdo (começa com `ssh-ed25519` ou `ssh-rsa`)

3. Acesse: https://salsa.debian.org/-/profile/keys  
4. Clique em **"Add SSH Key"**  
5. Cole o conteúdo no campo **Key**  
6. Dê um título descritivo (ex: “Notebook Casa”)  
7. Clique em **"Add key"**

---

## 🐞 7. Interagindo com Issues no Salsa

As *issues* são tarefas, bugs ou sugestões nos repositórios do Salsa.

- Acesse: https://salsa.debian.org/debian-brasil-team/docs/-/issues
- Você pode:
  - Pegar uma issue aberta
  - Criar uma nova issue (ex: “Quero atualizar o pacote X para a versão nova”)

### 🏷️ Labels

São etiquetas que ajudam a classificar as issues, como `beginner`, `bug`, `enhancement`. Peça permissão à comunidade para aplicá-las.

---

## 📡 8. Usando o Debian Package Tracker

- Acesse: https://tracker.debian.org
- Pesquise o pacote desejado (ex: cppman)
- Veja:
  - Versões disponíveis
  - Bugs abertos
  - Histórico
  - QA status

---

## 🧪 9. Validando com Lintian

Após o build do pacote, execute:

```bash
lintian nome-do-pacote.changes
```

Isso checa se o pacote está conforme as políticas Debian.

---

## 🤝 10. Comunidade Debian Brasil

Acesse: https://debianbrasil.org

Canais ativos:
- Matrix: [#debian-brasil:matrix.org](https://matrix.to/#/#debian-brasil:matrix.org)
- Telegram: https://t.me/debianbrasil

Participe das reuniões, tire dúvidas e contribua com revisões.

---

# 🚀 Tutorial de Atualização Upstream

## 1. Atualize seu chroot

```bash
sudo sh /usr/share/doc/sbuild/examples/sbuild-debian-developer-setup-update-all
```

## 2. Fork e Clone

```bash
gbp clone git@salsa.debian.org:seu-usuario/nome-do-pacote.git
cd nome-do-pacote
git remote add debian git@salsa.debian.org:debian/nome-do-pacote.git
git remote -v
```

## 3. Build inicial

```bash
# Branch master:
gbp buildpackage

# Branch debian/sid:
gbp buildpackage --git-debian-branch=debian/sid
```

## 4. Importando nova versão

```bash
gbp import-orig --uscan --pristine-tar
```

## 5. Gerar changelog

```bash
gbp dch --commit --team
```

## 6. Revisar diff

```bash
git diff
```

## 7. Editar changelog

```bash
nvim debian/changelog
```

## 8. Commits finais

```bash
git add debian/changelog
git commit --amend
git push --all && git push --tags
```

## 9. Criar Merge Request

No Salsa, clique em **Create Merge Request**.

---

🎉 **Parabéns! Você completou sua primeira contribuição de empacotamento e atualização upstream para o Debian!**
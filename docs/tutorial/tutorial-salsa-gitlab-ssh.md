# Tutorial Completo: Configuração de Conta com SSH, GitLab e Salsa 

## O que é o SSH?

**SSH** significa **Secure Shell**. É um protocolo de rede usado para se conectar com segurança a outro computador pela internet ou por uma rede local.

## O que é o GitLab?

**GitLab** é uma plataforma web para DevOps que permite:

- Hospedar projetos Git
- Fazer controle de versão de código
- Trabalhar em colaboração com outras pessoas
- Automatizar testes, builds e deploys (CI/CD)
- Gerenciar tarefas, issues, merge requests e wikis

É uma alternativa a serviços como GitHub, mas pode ser instalado em servidores próprios.


##  O que é o Salsa?

**Salsa** é a **instância oficial do GitLab usada pelo Projeto Debian**.

- Endereço: [https://salsa.debian.org](https://salsa.debian.org)
- Usado por membros para empacotar, revisar, manter pacotes, entre outros

> Salsa é **o GitLab do Debian**.


## Requisitos para usar o Salsa

Antes de configurar sua conta e usar o Salsa, você precisa:

1. Ter uma conta no Salsa
2. Ter uma chave SSH no seu sistema
3. Ter o Git configurado
4. Ser membro de uma equipe (se for fazer uploads ou merge requests)

### 1. Como criar uma conta no Salsa

1. Acesse: [https://salsa.debian.org/users/sign_up](https://salsa.debian.org/users/sign_up)
2. Preencha seu nome, email e nome de usuário
3. Confirme o email
4. Peça acesso à equipe que deseja contribuir, pode ser no [canal de comunicação geral](https://app.element.io/#/room/#debian-devel-br:matrix.debian.social/$vcvfKM3OVpxJqv7nbDx2RJPNy7gr4sEHox9NUUXHw0Y) avisando que é da disciplica de GCES e gostaria de contribuir, ou entre em contato com o seu monitor.


## 2. Gerando e adicionando uma chave SSH


### a. Instalar dependências (se necessário)

```bash
sudo apt update
sudo apt install git openssh-client
```

### b. Verifique se já tem uma chave SSH

Abra o terminal e digite:

```bash
ls ~/.ssh/id_rsa.pub
```

Se aparecer o arquivo, você já tem uma chave.

### b. Gerar uma nova chave (se necessário, caso não tenha uma chave)

```bash
ssh-keygen -t rsa -b 4096 -C "seu-email@exemplo.com"
```

- Pressione ENTER para aceitar o caminho padrão (`~/.ssh/id_rsa`)
- Crie uma senha se quiser (ou deixe vazio)

> ⚠️ Importante: Nunca compartilhe o arquivo `id_rsa`. Ele é sua chave privada. Compartilhe somente o conteúdo de `id_rsa.pub`.

### c. Exibir a chave pública:

```bash
cat ~/.ssh/id_rsa.pub
```

Copie a saída.

### d. Adicionar chave SSH no Salsa

1. Vá para: [https://salsa.debian.org/-/profile/keys](https://salsa.debian.org/-/profile/keys)
2. Clique em **"Add SSH Key"**
3. Cole a chave no campo
4. Dê um nome (ex: "Meu notebook Ubuntu")
5. Clique em **"Add key"**


## 3. Configurar o Git localmente

### a. Configure seu nome e email:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@exemplo.com"
```

### b. Teste a conexão com o Salsa:

```bash
ssh -T git@salsa.debian.org
```

**Saída esperada:**

```
Welcome to Salsa, [seu-usuário]
```

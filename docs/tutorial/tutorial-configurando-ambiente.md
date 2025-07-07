# Configurando seu Ambiente de Desenvolvimento Debian

Este tutorial ensina como configurar **um ambiente completo para empacotar e construir pacotes Debian**, ideal para iniciantes.


##  Pré-requisitos

- Ter um sistema **Debian GNU/Linux** já instalado.
- Ter acesso de **superusuário (root)** ou poder usar `sudo`.


## Instalando os Pacotes Necessários

Abra o terminal e execute:

```bash
sudo apt update
sudo apt install debootstrap sbuild schroot blhc devscripts dh-make git-buildpackage git sbuild-debian-developer-setup
```

> Esses pacotes incluem ferramentas como `sbuild`, `git`, `gbp`, `dh-make`, etc., usados em todo o ciclo de empacotamento.


## Configurando Variáveis de Ambiente

### 1. Bash

Abra o terminal e edite o arquivo `.bashrc`:

```bash
nano ~/.bashrc
```

Adicione ao final do arquivo:

```bash
export DEBFULLNAME="Seu Nome"
export DEBEMAIL="seuemail@mail.com"
```

> Substitua `"Seu Nome"` e `"seuemail@mail.com"` pelos seus dados reais.

Depois salve com `Ctrl + O`, `Enter` e saia com `Ctrl + X`.

Para aplicar as mudanças:

```bash
source ~/.bashrc
```

### 2. Git

Crie ou edite o arquivo `~/.gitconfig` com:

```bash
nano ~/.gitconfig
```

E insira:

```ini
[user]
    name = Seu Nome
    email = seuemail@mail.com
```

> Use os **mesmos dados do `.bashrc`**, pois eles devem ser consistentes.


## Configurando o Sbuild

`sbuild` é a ferramenta usada para construir pacotes de forma isolada em um chroot.

### 1. Criando o ambiente chroot

Execute:

```bash
sudo sbuild-debian-developer-setup
```

### 2. Adicionando seu usuário ao grupo `sbuild`

```bash
sudo sbuild-adduser $USER
```

> Reinicie o sistema ou execute:

```bash
newgrp sbuild
```

### 3. Copiando e configurando `.sbuildrc`

```bash
cp /usr/share/doc/sbuild/examples/example.sbuildrc ~/.sbuildrc
```

Abra o arquivo:

```bash
nano ~/.sbuildrc
```

Adicione (ou edite) as seguintes linhas:

```perl
# Faz o build de pacotes arch-independent.
$build_arch_all = 1;

# Por padrão realiza o build para unstable
$distribution = 'unstable';

# Produz um source package (.dsc) além do pacote binário.
$build_source = 1;

# Uploads para o Debian precisam ser, na grande maioria das vezes, source-only.
$source_only_changes = 1;

# Não executa o "clean" target fora do chroot.
$clean_source = 0;

# Sempre executa o lintian no final dos builds.
$run_lintian = 1;
$lintian_opts = ['--info', '--display-info'];
```

Salve com `Ctrl + O`, `Enter` e saia com `Ctrl + X`.


## Configurando o Git-Buildpackage (gbp)

Crie ou edite o arquivo `~/.gbp.conf` com:

```bash
nano ~/.gbp.conf
```

E insira:

```ini
[DEFAULT]
builder = sbuild
pristine-tar = True
```

---

## Testando o Ambiente

Você pode testar se tudo está funcionando usando o pacote `hello`:

```bash
sudo apt source hello
cd hello-*
sbuild --dist=unstable
```

Se o build funcionar, você verá uma saída com "Status: successful" no final.


## Extra: Usando o Vim (opcional para edições)

Se preferir usar o `vim` para editar arquivos, execute:

```bash
vim ~/.bashrc
```

Navegue com as setas até o fim e pressione `i` para entrar em **modo de inserção**.

Depois de editar:

- Pressione `Esc` para sair do modo de inserção
- Digite `:wq` (significa **write and quit**) e pressione `Enter` para salvar e sair


# 📦 Tutorial: Corrigindo e Aplicando Patches em um Pacote Debian com `quilt` e `debuild`

Este guia mostra como aplicar e corrigir patches em um pacote Debian usando `quilt`, garantir conformidade com o DEP-3, e buildar corretamente com `debuild`.

---

## 🔧 Requisitos

Instale os pacotes necessários:

```bash
sudo apt update
sudo apt install devscripts build-essential quilt debhelper
```

---

## 🧬 Clone o repositório do pacote

Clone o seu *fork* do repositório no Salsa:

```bash
git clone git@salsa.debian.org:SEU_USUARIO/wxedid.git
cd wxedid
```

---

## ⚙️ Configurar o ambiente `quilt`

Configure as variáveis de ambiente para o `quilt`:

```bash
export QUILT_PATCHES=debian/patches
export QUILT_REFRESH_ARGS="--no-timestamps --no-index -p ab"
```

Essas variáveis:
- Dizem ao `quilt` onde estão os patches.
- Evitam timestamps e índices nos diffs.

---

## 🩹 Aplicar e editar patches

### Aplicar todos os patches

```bash
quilt push -a
```

### Editar um patch existente

Abra o patch com seu editor:

```bash
nano debian/patches/spelling.patch
```

> Ou edite os arquivos do código fonte e depois atualize com `quilt refresh`.

---

## ✏️ Atualizar um patch com `quilt refresh`

Se você editou o código-fonte diretamente (e não o patch):

1. Certifique-se de que o patch está aplicado:
   ```bash
   quilt push spelling.patch
   ```

2. Atualize:
   ```bash
   quilt refresh
   ```

---

## 🧾 Adicionar cabeçalho DEP-3

Todo patch deve ter um cabeçalho [DEP-3](https://dep-team.pages.debian.net/deps/dep3/).

### Exemplo de cabeçalho válido:

```diff
Description: Corrige erros de ortografia em mensagens e comentários
Author: Maria <maria@exemplo.com>
Bug-Debian: https://bugs.debian.org/123456
Forwarded: no
Last-Update: 2025-06-01
```

Abra o patch para editar:

```bash
nano debian/patches/spelling.patch
```

E adicione o cabeçalho acima no topo.

---

## 📜 Verifique a ordem dos patches

Abra o arquivo `debian/patches/series` e veja se o seu patch está listado:

```bash
cat debian/patches/series
```

Se necessário, adicione o nome do patch no final do arquivo (sem caminho, só o nome do `.patch`).

---

## 🧹 Limpando e buildando

### Desaplique todos os patches:

```bash
quilt pop -a
```

### Limpe a build anterior:

```bash
debuild clean
```

### Aplique os patches novamente:

```bash
quilt push -a
```

### Faça o build do pacote:

```bash
debuild -us -uc
```

---

## 🧰 Corrigindo erro de tarball `.orig`

Se o build falhar com erro de `.orig.tar.gz` ausente:

1. Baixe o tarball original da upstream (ex: do GitHub, site do autor etc).
2. Renomeie com o nome correto:

```bash
mv ~/Downloads/wxedid-0.0.32.tar.gz ../wxedid_0.0.32.orig.tar.gz
```

3. Tente buildar novamente:

```bash
debuild -us -uc
```

---

## 📤 Enviando alterações para seu fork

Adicione e *commite* os patches e o arquivo `series`:

```bash
git add debian/patches/*
git commit -m "Fix spelling errors and add DEP-3 metadata to patch"
git push
```

---

## ✅ Checklist Final

- [x] Todos os patches estão em `debian/patches/`
- [x] Cada patch possui cabeçalho DEP-3
- [x] O arquivo `series` lista os patches
- [x] `debuild -us -uc` roda sem erro
- [x] O `.orig.tar.gz` está na pasta raiz
# 📦 Tutorial: Corrigindo e Aplicando Patches em um Pacote Debian com `quilt` e `debuild`

Este guia mostra como aplicar e corrigir patches em um pacote Debian usando `quilt`, garantir conformidade com o DEP-3, e buildar corretamente com `debuild`.

---

## 🔧 Requisitos

Instale os pacotes necessários:

```bash
sudo apt update
sudo apt install devscripts build-essential quilt debhelper
```

---

## 🧬 Clone o repositório do pacote

Clone o seu *fork* do repositório no Salsa:

```bash
git clone git@salsa.debian.org:SEU_USUARIO/wxedid.git
cd wxedid
```

---

## ⚙️ Configurar o ambiente `quilt`

Configure as variáveis de ambiente para o `quilt`:

```bash
export QUILT_PATCHES=debian/patches
export QUILT_REFRESH_ARGS="--no-timestamps --no-index -p ab"
```

Essas variáveis:
- Dizem ao `quilt` onde estão os patches.
- Evitam timestamps e índices nos diffs.

---

## 🩹 Aplicar e editar patches

### Aplicar todos os patches

```bash
quilt push -a
```

### Editar um patch existente

Abra o patch com seu editor:

```bash
nano debian/patches/spelling.patch
```

> Ou edite os arquivos do código fonte e depois atualize com `quilt refresh`.

---

## ✏️ Atualizar um patch com `quilt refresh`

Se você editou o código-fonte diretamente (e não o patch):

1. Certifique-se de que o patch está aplicado:
   ```bash
   quilt push spelling.patch
   ```

2. Atualize:
   ```bash
   quilt refresh
   ```

---

## 🧾 Adicionar cabeçalho DEP-3

Todo patch deve ter um cabeçalho [DEP-3](https://dep-team.pages.debian.net/deps/dep3/).

### Exemplo de cabeçalho válido:

```diff
Description: Corrige erros de ortografia em mensagens e comentários
Author: Maria <maria@exemplo.com>
Bug-Debian: https://bugs.debian.org/123456
Forwarded: no
Last-Update: 2025-06-01
```

Abra o patch para editar:

```bash
nano debian/patches/spelling.patch
```

E adicione o cabeçalho acima no topo.

---

## 📜 Verifique a ordem dos patches

Abra o arquivo `debian/patches/series` e veja se o seu patch está listado:

```bash
cat debian/patches/series
```

Se necessário, adicione o nome do patch no final do arquivo (sem caminho, só o nome do `.patch`).

---

## 🧹 Limpando e buildando

### Desaplique todos os patches:

```bash
quilt pop -a
```

### Limpe a build anterior:

```bash
debuild clean
```

### Aplique os patches novamente:

```bash
quilt push -a
```

### Faça o build do pacote:

```bash
debuild -us -uc
```

---

## 🧰 Corrigindo erro de tarball `.orig`

Se o build falhar com erro de `.orig.tar.gz` ausente:

1. Baixe o tarball original da upstream (ex: do GitHub, site do autor etc).
2. Renomeie com o nome correto:

```bash
mv ~/Downloads/wxedid-0.0.32.tar.gz ../wxedid_0.0.32.orig.tar.gz
```

3. Tente buildar novamente:

```bash
debuild -us -uc
```

---

## 📤 Enviando alterações para seu fork

Adicione e *commite* os patches e o arquivo `series`:

```bash
git add debian/patches/*
git commit -m "Fix spelling errors and add DEP-3 metadata to patch"
git push
```

---

## ✅ Checklist Final

- [x] Todos os patches estão em `debian/patches/`
- [x] Cada patch possui cabeçalho DEP-3
- [x] O arquivo `series` lista os patches
- [x] `debuild -us -uc` roda sem erro
- [x] O `.orig.tar.gz` está na pasta raizam
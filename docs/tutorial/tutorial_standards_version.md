
# ✅ Tutorial: Como Atualizar a Standards-Version de um Pacote Debian

Atualizar a **Standards-Version** de um pacote Debian é uma tarefa essencial para garantir que o pacote esteja conforme as últimas diretrizes e boas práticas do projeto Debian.

Este tutorial é para iniciantes e explicará **passo a passo** como fazer essa atualização de maneira segura e correta.

## 📝 O que é a Standards-Version?

A **Standards-Version** indica a versão da **Debian Policy** com a qual o pacote está em conformidade. 

Periodicamente, a Debian Policy é atualizada com novos requisitos ou recomendações. Quando isso acontece, é importante verificar se o pacote continua compatível e, se sim, atualizar a declaração de Standards-Version.

**⚠️ Importante:** Atualizar a Standards-Version **não significa** mudar o funcionamento do pacote, mas sim garantir que ele está conforme as novas políticas.

## 📚 Passo 1: Leia a checklist oficial

Antes de tudo, consulte a **checklist oficial** de mudanças na política Debian:

🔗 https://www.debian.org/doc/debian-policy/upgrading-checklist.html

- Veja as mudanças entre a versão atualmente declarada no pacote e a mais recente.
- Avalie se alguma mudança **impacta diretamente** o pacote.
- Se não houver impacto, você pode apenas atualizar a declaração.
- Se houver, ajustes no pacote podem ser necessários.


## 🔍 Passo 2: Verifique a Standards-Version atual

Abra o arquivo **`debian/control`**:

```bash
nano debian/control
```

Procure por uma linha como esta:

```plain
Standards-Version: 4.6.2
```

- Esta é a versão atual declarada.

## 📘 Passo 3: Consulte o checklist de mudanças 

- Compare o que mudou entre a sua versão e a versão **mais recente** da Debian Policy: https://www.debian.org/doc/debian-policy/


## 🖊️ Passo 4: Atualize a versão


### Exemplo: Mudanças da Policy entre 4.6.2 → 4.7.2

#### ✅ 4.7.0 (abril/2024)
- **Scripts de mantenedor (`postinst`, `prerm`)**:
  - Não devem usar `dpkg-divert` para arquivos de configuração do systemd.
  - Não devem usar `update-alternatives` para arquivos de configuração do systemd.
- Pacotes `contrib` ou `non-free` com `Autobuild: yes`:
  - Não podem acessar a rede durante `debian/rules`.
- Pacotes que **iniciam serviços**:
  - Devem fornecer arquivos `*.service` para systemd.

#### ✅ 4.7.1 (fev/2025)
- **Não instale** arquivos em `/bin`, `/lib`, `/sbin` → use `/usr/bin`, `/usr/lib`, `/usr/sbin`.
- **Dois pacotes diferentes não podem instalar** binários com **nomes iguais** mesmo em diretórios diferentes do `PATH`.
- Seu pacote não pode depender de:
  - `/usr/share/locale` (para funcionar em `C`/`C.UTF-8`)
  - `/usr/share/man`
  - `/usr/share/info`

#### ✅ 4.7.2 (fev/2025)
- Apenas relaxamento sobre uso de `/usr/games`. Nenhuma exigência nova.

### Teste se o pacote precisa de mudanças

O que revisar:
- [`postinst`, `prerm`, `postrm`] → usam `dpkg-divert` ou `update-alternatives` para systemd?
- Instala algo fora de `/usr/...`? Verifique `debian/install`, `Makefile`, `d/rules`.
- Verifique arquivos obrigatórios no sistema para man/info/locale.
- O binário principal só funciona com manpage/locale? ⚠️ Corrigir.
- Usa `init.d` mas não tem `.service`? ⚠️ Adicionar.
Se não houver impacto relevante, edite a linha:


## ✅ Passo 5: Ferramentas úteis

```bash
lintian
debuild -us -uc
sbuild
```

Essas ferramentas ajudam a detectar erros comuns automaticamente. Corrija qualquer erro ou advertência crítica. Se aparecer algo relacionado à nova política, ajuste.


## 🛠️ Passo 5: Atualize o changelog

### a. Edite `debian/control`

```diff
- Standards-Version: 4.6.2
+ Standards-Version: 4.7.2
```

### b. Atualize o `debian/changelog` com `dch -i`

Se não precisou alterar nada:

```txt
  * Bump Standards-Version to 4.7.2. No changes needed.
```

Se precisou: documentar as mudanças. Exemplo:

```txt
  * Bump Standards-Version to 4.7.2.
    - Migrated systemd config handling (no dpkg-divert)
    - Avoided installing files outside /usr/*
```

⚠️ Lembre-se de mudar o número da versão Debian, normalmente incrementando o número de revisão.

## ✅ Passo 6: Rebuild e verifique

```bash
debuild -us -uc
lintian ../nomedopacote_*.changes
```

Se estiver tudo certo, o pacote já está pronto para subir com a nova Policy.

## 🧑‍💻 Dicas Finais

- Sempre leia a Debian Policy com atenção.
- Nunca atualize a Standards-Version **sem verificar as mudanças**.
- Use o `lintian` para manter a qualidade do pacote.
- Participe das discussões no Salsa se tiver dúvidas!

## 📝 Nota final

Este tutorial foi feito por iniciantes com base na [Debian Policy Upgrading Checklist](https://www.debian.org/doc/debian-policy/upgrading-checklist.html) e cobre especificamente o exemplo entre a transição da versão **4.6.2 para 4.7.2**.  
Se tiver dúvidas, consulte a documentação oficial ou peça ajuda nos canais oficiais.
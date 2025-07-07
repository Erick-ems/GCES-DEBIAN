
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
- Compare com a versão **mais recente** da Debian Policy: https://www.debian.org/doc/debian-policy/


## 🖊️ Passo 3: Atualize a versão

Se não houver impacto relevante, edite a linha:

```plain
Standards-Version: 4.7.0
```

Substitua pela **última versão disponível**.

💡 **Dica:** Sempre leia o **upgrading-checklist** antes de atualizar!


## ✅ Passo 4: Verifique o pacote

Rode as ferramentas para verificar se o pacote está de acordo:

```bash
lintian
```

- Corrija qualquer erro ou advertência crítica.
- Se aparecer algo relacionado à nova política, ajuste.


## 🛠️ Passo 5: Atualize o changelog

Edite o arquivo **`debian/changelog`** com o `dch` (Debian ChangeLog Helper):

```bash
dch -i
```

Adicione uma mensagem como:

```plain
* Declare compliance with Debian Policy 4.7.0.
```

Exemplo de entrada:

```plain
python-immutabledict (2.2.4-2) UNRELEASED; urgency=medium

  * Declare compliance with Debian Policy 4.7.0.

 -- Seu Nome <seuemail@debian.org>  Sat, 01 Jun 2025 10:00:00 -0300
```

⚠️ Lembre-se de mudar o número da versão Debian, normalmente incrementando o número de revisão.

## ✅ Exemplo prático

**Antes**:

```plain
Standards-Version: 4.6.2
```

**Depois**:

```plain
Standards-Version: 4.7.0
```

**Changelog**:

```plain
* Declare compliance with Debian Policy 4.7.0.
```

## 🧑‍💻 Dicas Finais

- Sempre leia a Debian Policy com atenção.
- Nunca atualize a Standards-Version **sem verificar as mudanças**.
- Use o `lintian` para manter a qualidade do pacote.
- Participe das discussões no Salsa se tiver dúvidas!


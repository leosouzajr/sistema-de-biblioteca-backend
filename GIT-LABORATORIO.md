# Git nos Computadores do Laboratório

<!-- LEIA ANTES DE COMEÇAR A AULA -->

O repositório do professor está configurado como **template**. Isso significa que você cria sua própria cópia limpa apenas com a `main`, sem as branches de aulas anteriores. Conforme o curso avança, você puxa as branches do professor quando precisar.

---

## Pré-requisito

Ter uma conta no [GitHub](https://github.com) criada antes da aula.

---

## 1. Criar sua cópia a partir do template

1. Acesse o repositório do professor no GitHub
2. Clique em **"Use this template"** → **"Create a new repository"**
3. Dê um nome ao repositório (`sistema-de-biblioteca-backend`)
4. Deixe como **Public** ou **Private** conforme preferir
5. Clique em **"Create repository"**

> Diferente do fork, o template copia apenas a branch `main` — as branches de aulas completas do professor não aparecem na sua cópia.

---

## 2. Clonar o seu repositório

> No VSCode entre na pasta na qual voce quer criar o seu projeto local e execute no terminal os comandos seguintes:

```bash
git clone https://github.com/seu-usuario/sistema-de-biblioteca-backend.git
cd sistema-de-biblioteca-backend
```

> Substitua `seu-usuario` pelo seu usuário do GitHub.

---

## 3. Configurar o repositório do professor como upstream

```bash
git remote add upstream https://github.com/usuario-professor/sistema-de-biblioteca-backend.git
```
OBS: lembre de substituir pelo link correto do repositorio do professor
Para confirmar que os dois remotos estão configurados:

```bash
git remote -v
```

Você deve ver:

```
origin    https://github.com/seu-usuario/sistema-de-biblioteca-backend.git (fetch)
origin    https://github.com/seu-usuario/sistema-de-biblioteca-backend.git (push)
upstream  https://github.com/usuario-professor/sistema-de-biblioteca-backend.git (fetch)
upstream  https://github.com/usuario-professor/sistema-de-biblioteca-backend.git (push)
```

---

## 4. Configurar nome e e-mail (obrigatório no laboratório)

Nos computadores compartilhados, configure sempre de forma **local**:

```bash
git config --local user.name "Seu Nome"
git config --local user.email "seu@email.com"
```

---

## 5. Fluxo de trabalho durante a aula

```bash
# Salvar seu progresso no seu GitHub
git add .
git commit -m "aula 01 - meu progresso"
git push origin main
```

---

## 6. Puxar uma branch do professor (aula que faltou ou revisão)

```bash
# Buscar as branches mais recentes do professor
git fetch upstream

# Criar uma branch local a partir da branch do professor
git checkout -b aula-02-completa upstream/aula-02-completa
```

Para voltar ao seu trabalho:

```bash
git checkout main
```

---

## 7. Usar a branch do professor no seu trabalho

Após puxar a branch do professor (passo 6), você tem duas opções:

### Opção A — Combinar o código do professor com o seu trabalho

Use quando quiser manter o que você já fez e adicionar o que o professor desenvolveu:

```bash
git checkout main
git merge aula-02-completa
```

Se houver conflitos, o Git vai indicar os arquivos. Abra cada um, resolva o conflito e depois:

```bash
git add .
git commit
```

> Antes de fazer o merge, salve seu trabalho com `git push origin main` para garantir que nada seja perdido.

---

### Opção B — Substituir seu trabalho pelo da aula completa

Use quando seu código estiver incompleto ou com problemas e você quiser partir do código do professor:

```bash
# 1. Salvar seu trabalho atual no GitHub (mesmo incompleto)
git add .
git commit -m "trabalho incompleto - antes de resetar"
git push origin main

# 2. Substituir o main pelo código do professor
git checkout main
git reset --hard aula-02-completa
```

> O `push` antes do reset é obrigatório. Sem ele, seu trabalho anterior é apagado permanentemente sem possibilidade de recuperação.

---

## 8. Ao terminar no laboratório — limpar credenciais

```bash
git config --local --unset user.name
git config --local --unset user.email
```

---

## Resumo rápido

```bash
# Configurar (início da aula no laboratório)
git config --local user.name "Seu Nome"
git config --local user.email "seu@email.com"

# Salvar progresso no seu GitHub
git add .
git commit -m "descrição"
git push origin main

# Puxar branch de uma aula do professor
git fetch upstream
git checkout -b aula-02-completa upstream/aula-02-completa

# Voltar ao seu trabalho
git checkout main

# Combinar código do professor com o seu (mantém seu trabalho)
git checkout main
git merge aula-02-completa

# Substituir seu trabalho pelo do professor (salve antes!)
git add . && git commit -m "backup" && git push origin main
git reset --hard aula-02-completa

# Limpar (ao sair do laboratório)
git config --local --unset user.name
git config --local --unset user.email
```

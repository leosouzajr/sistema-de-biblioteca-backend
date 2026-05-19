# Passo a Passo — Criação do Projeto Base

<!-- DOCUMENTO PARA FIM DE CONSULTA CASO QUEIRA CRIAR UM PROJETO DE BACKEND
    COM NEXT.JS DO ZERO FUTURAMENTE COM BASE NO ATUAL
 -->

Registro dos comandos executados para criar o projeto do zero até a configuração inicial do Prisma.

---

## Pré-requisitos

Antes de começar, a máquina precisa ter instalado:

| Ferramenta  | Versão mínima | Verificar        |
| ----------- | ------------- | ---------------- |
| **Node.js** | 20.19+        | `node --version` |
| **pnpm**    | qualquer      | `pnpm --version` |
| **Git**     | qualquer      | `git --version`  |

### Node.js

Site oficial: https://nodejs.org

Recomenda-se instalar via **nvm** (gerenciador de versões), o que facilita trocar de versão futuramente:

- **macOS / Linux:**

  ```bash
  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
  # Feche e reabra o terminal, depois:
  nvm install 22
  nvm use 22
  ```

- **Windows:** Instale o [nvm-windows](https://github.com/coreybutler/nvm-windows/releases) e depois:

  ```bash
  nvm install 22
  nvm use 22
  ```

- **Instalador direto** (sem nvm): Baixe o instalador LTS em https://nodejs.org e siga o assistente.

### pnpm

Site oficial: https://pnpm.io/installation

Com Node.js já instalado:

```bash
npm install -g pnpm
```

Ou via script oficial:

- **macOS / Linux:**

  ```bash
  curl -fsSL https://get.pnpm.io/install.sh | sh -
  ```

- **Windows (PowerShell):**

  ```powershell
  Invoke-WebRequest https://get.pnpm.io/install.ps1 -UseBasicParsing | Invoke-Expression
  ```

### Git

Site oficial: https://git-scm.com/downloads

- **macOS:** já vem instalado. Para atualizar, use o instalador do site ou:

  ```bash
  brew install git
  ```

- **Windows:** Baixe o instalador em https://git-scm.com/downloads/win e siga o assistente. Marque a opção **Git Bash** durante a instalação.

- **Linux (Debian/Ubuntu):**

  ```bash
  sudo apt update && sudo apt install git
  ```

---

## 1. Criar o repositório Git

```bash
git init sistema-de-biblioteca-backend
cd sistema-de-biblioteca-backend
```

---

## 2. Criar o projeto Next.js

Dentro da pasta do repositório, criamos o projeto Next.js numa subpasta chamada `back`:

```bash
pnpm dlx create-next-app@latest back
```

Opções selecionadas no assistente:

- TypeScript: **Yes**
- ESLint: **Yes**
- Tailwind CSS: **No**
- `src/` directory: **Yes**
- App Router: **Yes**
- Turbopack: **Yes**
- Import alias: **No** (padrão `@/*`)

---

## 3. Acessar a pasta do projeto e instalar dependências

```bash
cd back
pnpm install
```

---

## 4. Instalar o Prisma

```bash
pnpm add prisma @prisma/client
```

---

## 5. Inicializar o Prisma

```bash
pnpx prisma init
```

Esse comando cria:

- `prisma/schema.prisma` — arquivo de definição do banco de dados
- `prisma.config.ts` — configuração do Prisma CLI
- `.env` — arquivo com a variável `DATABASE_URL`

---

## 6. Configurar o .gitignore

O `.gitignore` gerado pelo `create-next-app` já cobre os principais casos. Adicionamos também a proteção para arquivos de banco SQLite local:

```
/prisma/*.db
/prisma/*.db-journal
```

---

## Estado atual do schema.prisma

```prisma
generator client {
  provider = "prisma-client"
  output   = "../src/generated/prisma"
}

datasource db {
  provider = "postgresql"
}
```

---

## Estrutura de pastas resultante

```
sistema-de-biblioteca-backend/
├── back/
│   ├── prisma/
│   │   └── schema.prisma
│   ├── prisma.config.ts
│   ├── src/
│   │   └── app/
│   ├── .env
│   ├── .gitignore
│   ├── next.config.ts
│   ├── package.json
│   └── tsconfig.json
├── SETUP.md
└── comandos.md
```

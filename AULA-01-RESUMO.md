# Aula 01 — Configuração do Banco de Dados com Prisma

## O será  feito

Nesta aula configuramos a camada de persistência do sistema de biblioteca, conectando a aplicação Next.js a um banco PostgreSQL via Prisma ORM.

---

## Arquivos criados e modificados


### `back/prisma/schema.prisma` 
Define os dois primeiros modelos de dados do sistema:

- **`Livro`** — tabela do acervo com campos: `id`, `titulo`, `autor`, `isbn` (único), `categoria`, `disponivel` (boolean, padrão `true`), `createdAt`, `updatedAt`
- **`Usuario`** — tabela de usuários com campos: `id`, `nome`, `email` (único), `telefone` (opcional), `createdAt`

### `back/src/app/lib/prisma.ts` 
Instância singleton do `PrismaClient` para uso em toda a aplicação. Resolve o problema de múltiplas conexões causadas pelo hot reload do Next.js em desenvolvimento, armazenando a instância em `globalThis`.

### `back/prisma/migrations/20260520143653_initial/migration.sql` (gerado)
Migration SQL inicial gerada automaticamente pelo Prisma ao rodar `prisma migrate dev`. Cria as tabelas `Livro` e `Usuario` com suas respectivas colunas, constraints e índices únicos.

---

## Conceitos abordados

| Conceito | Descrição |
|---|---|
| **ORM** | Mapeamento objeto-relacional — escreve-se TypeScript, o Prisma traduz para SQL |
| **Schema Prisma** | Fonte de verdade dos modelos de dados; gera tipos TS e migrations SQL |
| **Migration** | Arquivo SQL versionado que registra cada alteração no banco |
| **Singleton** | Padrão para garantir uma única instância do `PrismaClient` na aplicação |
| **Variáveis de ambiente** | `DATABASE_URL` em `.env` mantém credenciais fora do código-fonte |
| **cuid()** | Gerador de IDs únicos sem auto-incremento de banco — portável e seguro |

---

## Comandos utilizados na aula

```bash
# Gerar o Prisma Client a partir do schema (necessário após qualquer alteração no schema)
pnpx prisma generate

# Gerar e aplicar a primeira migration (cria as tabelas no banco)
pnpx prisma migrate dev --name initial

# Abrir interface visual para inspecionar os dados
pnpx prisma studio
```

---

## Variável de ambiente necessária

Crie o arquivo `back/.env` , pode usar o .env.exemplo: 

```env
DATABASE_URL="postgresql://usuario:senha@localhost:5432/nome_do_banco"
```
esse database_url se pega no seu projeto do neon

> O arquivo `.env` **não deve** ser commitado no Git (já está no `.gitignore`).

---

## Estrutura de pastas após a aula

```
back/
├── prisma/
│   ├── schema.prisma          # Modelos de dados (Livro, Usuario)
│   ├── prisma.config.ts       # Configuração do Prisma (conexão, paths)
│   └── migrations/
│       └── 20260520143653_initial/
│           └── migration.sql  # SQL gerado para criar as tabelas
└── src/
    └── app/
        └── lib/
            └── prisma.ts      # Singleton do PrismaClient
```

---

## Próximos passos

Na próxima aula utilizaremos o `prisma` exportado de `lib/prisma.ts` para criar as **rotas de API** (Route Handlers do Next.js) que farão as operações CRUD nas tabelas `Livro` e `Usuario`.

# 📝 Comandos Úteis - pnpm

## Desenvolvimento
```bash
pnpm dev                 # Iniciar servidor de desenvolvimento
pnpm build              # Build para produção
pnpm start              # Rodar build de produção
```

## Prisma
```bash
pnpx prisma studio      # Interface visual do banco
pnpx prisma migrate dev # Criar/aplicar migration
pnpx prisma generate    # Gerar Prisma Client
```

## Git + Branches
```bash
git checkout aula-03-completa  # Ver código completo da aula 3
pnpm install                   # ⚠️ Sempre após trocar branch!
git checkout main              # Voltar para seu código
```

## Troubleshooting
```bash
# Limpar tudo e reinstalar:
rm -rf node_modules pnpm-lock.yaml
pnpm install

# Verificar versões:
node --version    # Deve ser 18+
pnpm --version    # Deve estar instalado
```
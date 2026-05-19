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
git fetch upstream                                           # Buscar branches do professor
git checkout -b aula-03-completa upstream/aula-03-completa  # Puxar aula completa
pnpm install                                                 # ⚠️ Sempre após trocar branch!
git checkout main                                            # Voltar para seu código
```

> Para combinar ou substituir seu código pelo da aula completa, consulte **GIT-LABORATORIO.md**.

## Troubleshooting
```bash
# Limpar tudo e reinstalar:
rm -rf node_modules pnpm-lock.yaml
pnpm install

# Verificar versões:
node --version    # Deve ser 20.19+
pnpm --version    # Deve estar instalado
```
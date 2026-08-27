# nest-prisma-app

Backend em NestJS + Prisma + TypeScript.

## Requisitos
- Node.js 20+ (recomendado 22)
- Docker (opcional, para o Postgres) ou um Postgres já rodando

## Passo a passo

```bash
# 1. Instalar dependências
npm install

# 2. Copiar variáveis de ambiente
cp .env.example .env

# 3. Subir o banco (opcional, se usar Docker)
docker compose up -d

# 4. Gerar o Prisma Client
npm run prisma:generate

# 5. Criar as tabelas / primeira migration
npm run prisma:migrate -- --name init

# 6. (opcional) Popular o banco
npm run db:seed

# 7. Rodar em modo dev
npm run start:dev
```

App sobe em http://localhost:3000

## Comandos úteis
- `npm run prisma:studio` — abre a UI do Prisma Studio
- `npm run prisma:migrate` — cria/aplica migrations em dev
- `npm run build && npm run start:prod` — build de produção

## Estrutura
```
prisma/
  schema.prisma      # modelos do banco
  seed.ts            # seed opcional
src/
  main.ts            # bootstrap
  app.module.ts      # módulo raiz
  prisma/
    prisma.module.ts # módulo global do Prisma
    prisma.service.ts# service com connect/disconnect
```
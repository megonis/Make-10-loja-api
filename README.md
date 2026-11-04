# Make 10 — Backend

Estrutura inicial baseada na seção 3 do PDF `documentacao_tecnica_ecommerce_local.pdf`.
Este repositório corresponde ao `ecommerce-backend` da documentação.

```text
src/
├── modules/
│   ├── products/        # Produtos
│   ├── categories/      # Categorias
│   ├── inventory/       # Estoque
│   ├── orders/          # Pedidos
│   └── auth/            # Autenticação e autorização
├── common/             # Recursos compartilhados
├── config/             # Configurações da aplicação
└── main.ts             # Futuro ponto de entrada NestJS

prisma/
├── schema.prisma       # Futura modelagem do banco
└── migrations/         # Migrações versionadas
```

## Estado atual

Apenas a estrutura foi criada. `src/main.ts` e `prisma/schema.prisma` são
marcadores documentados, sem implementação. Os arquivos `.gitkeep` preservam
as pastas vazias no Git e podem ser removidos quando elas receberem código.
Ainda não há API executável, dependências instaladas ou banco configurado.

## Próximos passos

1. Inicializar NestJS com TypeScript nesta raiz, preservando a estrutura.
2. Configurar Prisma e PostgreSQL no NeonDB para desenvolvimento.
3. Definir os modelos de produtos, categorias, usuários, estoque e pedidos.
4. Implementar os módulos, a validação de dados, a autenticação e o Swagger/OpenAPI.
5. Configurar o armazenamento de imagens no Cloudflare R2.

O frontend fica em `../../app/Make-10-loja-app` e consumirá esta API REST.
O acesso ao banco será exclusivo do backend.

## Ambientes e versionamento previstos

- `main`: produção; `develop`: desenvolvimento.
- `feature/*` e `fix/*`: branches temporárias a partir de `develop`.
- DEV: banco `ecommerce_dev`; PROD: banco `ecommerce_prod`, com `DATABASE_URL` própria.
- Usar bancos isolados, preferencialmente em projetos Neon separados.
- Após configurar o Prisma, usar `prisma migrate dev` em DEV e `prisma migrate deploy` nos deploys.
- Não usar `prisma db push` diretamente em produção.
- Manter credenciais fora do Git e usar buckets ou prefixos de imagens separados por ambiente.

Deploys, bancos, serviços externos e branches ainda não foram configurados.
Pagamentos, checkout completo e frete automatizado ficam para etapas futuras,
conforme o PDF.

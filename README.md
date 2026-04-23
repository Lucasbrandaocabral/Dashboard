# Dashboard de Uniformes

Sistema web completo para gestão de uma empresa de uniformes — controle de pedidos, produtos, clientes, gastos e análise financeira em tempo real.

---

## Funcionalidades

- **Dashboard financeiro** — receita bruta, custo de produção, lucro líquido e margem de lucro do mês
- **Pedidos** — criação e acompanhamento de pedidos com status: pendente, em produção, aguardando pagamento, concluído e atrasado
- **Produtos** — cadastro de uniformes com preço de custo e preço de venda
- **Clientes** — registro e gerenciamento de clientes
- **Gastos** — lançamento de despesas por categoria com visão mensal
- **Backup** — exportação dos dados do sistema
- **Tema claro/escuro** — alternância de tema integrada

---

## Tecnologias

### Frontend
| Tecnologia | Uso |
|---|---|
| [React 19](https://react.dev) | Interface do usuário |
| [TypeScript](https://www.typescriptlang.org) | Tipagem estática |
| [Tailwind CSS 4](https://tailwindcss.com) | Estilização |
| [Vite 7](https://vite.dev) | Build e servidor de desenvolvimento |
| [Radix UI](https://www.radix-ui.com) | Componentes de UI acessíveis |
| [Recharts](https://recharts.org) | Gráficos e visualizações |
| [TanStack Query](https://tanstack.com/query) | Cache e sincronização de dados |
| [React Hook Form](https://react-hook-form.com) + [Zod](https://zod.dev) | Formulários e validação |
| [Wouter](https://github.com/molefrog/wouter) | Roteamento |
| [Framer Motion](https://www.framer.com/motion) | Animações |

### Backend
| Tecnologia | Uso |
|---|---|
| [Node.js](https://nodejs.org) + [Express](https://expressjs.com) | Servidor HTTP |
| [tRPC 11](https://trpc.io) | API type-safe entre client e server |
| [Drizzle ORM](https://orm.drizzle.team) | Acesso ao banco de dados |
| [SQLite](https://www.sqlite.org) | Banco de dados local |
| [Jose](https://github.com/panva/jose) | Autenticação JWT |
| [AWS S3](https://aws.amazon.com/s3) | Armazenamento de arquivos |

---

## Estrutura do projeto

```
dashboard/
├── client/
│   └── src/
│       ├── pages/          # Páginas: Home, Pedidos, Produtos, Clientes, Gastos, Configurações
│       ├── components/     # Componentes reutilizáveis (layout, modais, gráficos)
│       ├── components/ui/  # Biblioteca de componentes base (Shadcn/Radix)
│       ├── hooks/          # React hooks customizados
│       ├── contexts/       # ThemeContext (tema claro/escuro)
│       └── lib/            # Cliente tRPC, utilitários, formatadores
├── server/
│   ├── routers/            # Rotas tRPC: pedidos, produtos, clientes, gastos, dashboard, backup
│   ├── _core/              # Setup Express, contexto tRPC, integração Vite
│   ├── db.ts               # Inicialização do banco de dados
│   └── storage.ts          # Integração com S3
├── drizzle/
│   └── schema.ts           # Schema do banco: clientes, produtos, pedidos, itens_pedido, gastos
├── shared/                 # Tipos compartilhados entre client e server
└── dist/                   # Build de produção
```

---

## Banco de dados

O sistema usa **SQLite** (arquivo `database.db` na raiz do projeto). As tabelas principais são:

| Tabela | Descrição |
|---|---|
| `clientes` | Dados dos clientes (nome, contato, endereço) |
| `produtos` | Catálogo de produtos com preço de custo e venda |
| `pedidos` | Pedidos com status, data de entrega e valor total |
| `itens_pedido` | Itens de cada pedido vinculados a produtos |
| `gastos` | Despesas por categoria e data |

---

## Solução de problemas

**"Node.js não encontrado"**
→ Instale o Node.js em https://nodejs.org e reinicie o computador.

**"dist/index.js não encontrado"**
→ Rode `npm run build` para gerar o build de produção.

**O navegador não abriu automaticamente**
→ Acesse manualmente: `http://localhost:3000`

**Porta 3000 já está em uso**
→ O sistema tenta as portas 3001, 3002... automaticamente. Verifique no console qual porta foi usada.

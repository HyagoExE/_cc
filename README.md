# Projeto 01

Aplicação web full-stack construída com **Next.js (App Router)**, seguindo a abordagem *Server Component First*. O projeto está em fase inicial: a estrutura de pastas e as convenções já estão definidas, e a página atual ainda é o template padrão do `create-next-app`.

## Tecnologias

**Instaladas hoje**

- [Next.js 16](https://nextjs.org) (App Router) + [React 19](https://react.dev)
- [TypeScript](https://www.typescriptlang.org)
- [Tailwind CSS 4](https://tailwindcss.com)
- ESLint (`eslint-config-next`)

**Previstas na arquitetura (ainda não instaladas)**

- [shadcn/ui](https://ui.shadcn.com) + Radix UI para componentes
- React Hook Form + [Zod](https://zod.dev) para formulários e validação
- [Supabase](https://supabase.com) para autenticação e banco de dados
- Jest + React Testing Library para testes

## Pré-requisitos

- Node.js 20 ou superior
- npm

## Como rodar

```bash
# 1. Instalar dependências
npm install

# 2. Configurar variáveis de ambiente
cp .env.example .env.local

# 3. Subir o servidor de desenvolvimento
npm run dev
```

Acesse [http://localhost:3000](http://localhost:3000).

## Scripts

| Comando              | Descrição                                   |
| -------------------- | ------------------------------------------- |
| `npm run dev`        | Servidor de desenvolvimento (porta 3000)    |
| `npm run build`      | Build de produção                           |
| `npm run start`      | Executa o build de produção                 |
| `npm run lint`       | Análise estática com ESLint                 |
| `npm run type-check` | Gera tipos do Next e checa com `tsc`        |

## Estrutura do projeto

```
app/            Rotas (App Router), layout e estilos globais
actions/        Server Actions globais
components/     Componentes de feature
  ui/           Primitivos reutilizáveis (shadcn/ui)
lib/            Helpers, clients e configurações
types/          Tipos globais e schemas Zod compartilhados
public/         Arquivos estáticos
```

Dentro de cada rota, o padrão é:

```
app/nome-da-pagina/
├── page.tsx          # Server Component (busca dados, valida acesso)
├── _components/      # Componentes específicos da página
├── _actions/         # Server Actions da página
└── _data-access/     # Camada de acesso a dados
```

## Convenções

- Server Components por padrão; `"use client"` apenas quando houver estado, efeitos, eventos ou APIs do browser.
- Mutações somente via Server Actions, nunca acessando o banco direto de Client Components.
- Validação de entrada com Zod no servidor.
- Estilização apenas com Tailwind (sem CSS inline).
- Arquivos em `kebab-case`, componentes em `PascalCase`.
- Sem `any` explícito: usar `unknown` com type guard.
- Segredos apenas no servidor; `NEXT_PUBLIC_*` somente para valores seguros.
- Branches: `feat/`, `fix/`, `chore/` + descrição em kebab-case. Commits em inglês, no imperativo.

Mais detalhes em [`CLAUDE.md`](./CLAUDE.md) e [`.claude/rules/rules-global.md`](./.claude/rules/rules-global.md).

## Deploy

Pensado para [Vercel](https://vercel.com) ou VPS. Veja a [documentação de deploy do Next.js](https://nextjs.org/docs/app/building-your-application/deploying).

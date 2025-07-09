# NLW Agents

Projeto desenvolvido durante o evento **NLW (Next Level Week)** da [Rocketseat](https://rocketseat.com.br).

## 🚀 Tecnologias

- **Node.js** - Runtime JavaScript
- **TypeScript** - Tipagem estática
- **Fastify** - Framework web rápido e eficiente
- **Drizzle ORM** - ORM type-safe para TypeScript
- **PostgreSQL** - Banco de dados relacional
- **pgvector** - Extensão PostgreSQL para vetores
- **Docker** - Containerização
- **Zod** - Validação de esquemas
- **Biome** - Linter e formatador

## 🏗️ Arquitetura

O projeto segue uma arquitetura em camadas com separação clara de responsabilidades:

### **Camada de Aplicação**
- **Server** (`src/server.ts`) - Configuração e inicialização do servidor Fastify
- **Environment** (`src/env.ts`) - Validação e tipagem de variáveis de ambiente com Zod

### **Camada de Apresentação**
- **Routes** (`src/http/routes/`) - Definição dos endpoints da API
- **Middlewares** - Validação de dados e tratamento de erros

### **Camada de Dados**
- **Schema** (`src/db/schema/`) - Definição das tabelas com Drizzle ORM
- **Migrations** (`src/db/migrations/`) - Controle de versão do banco de dados
- **Connection** (`src/db/connection.ts`) - Configuração da conexão com PostgreSQL

### **Padrões Implementados**
- **Repository Pattern** - Abstração de acesso a dados
- **Dependency Injection** - Injeção de dependências via Fastify
- **Type Safety** - Validação de tipos em tempo de compilação e runtime
- **Environment Configuration** - Configuração centralizada com validação

## 📁 Estrutura do Projeto

```
src/
├── db/
│   ├── migrations/     # Migrações do banco
│   ├── schema/         # Esquemas das tabelas
│   └── connection.ts   # Conexão com o banco
├── http/
│   └── routes/         # Rotas da API
├── env.ts              # Configuração de ambiente
└── server.ts           # Servidor principal
```

## 🔧 Setup e Configuração

### 1. Clonar o repositório
```bash
git clone <repository-url>
cd nlw-agents
```

### 2. Instalar dependências
```bash
npm install
```

### 3. Configurar ambiente
Copie o arquivo `.env.example` para `.env`:
```bash
cp .env.example .env
```

### 4. Iniciar o banco de dados
```bash
docker-compose up -d
```

### 5. Executar migrações
```bash
npx drizzle-kit migrate
```

### 6. Popular o banco (opcional)
```bash
npm run db:seed
```

### 7. Iniciar o servidor
```bash
# Desenvolvimento
npm run dev

# Produção
npm start
```

## 🐳 Docker

O projeto utiliza Docker para o banco PostgreSQL com a extensão pgvector:

```yaml
services:
  nlw-agents-pg:
    image: pgvector/pgvector:pg17
    ports:
      - "5432:5432"
```

## 🛠️ Comandos Úteis

```bash
# Desenvolvimento com watch mode
npm run dev

# Executar seed do banco
npm run db:seed

# Formatação de código
npx biome format --write .

# Lint
npx biome lint .

# Gerar migrações
npx drizzle-kit generate

# Aplicar migrações
npx drizzle-kit migrate
```

## 🔍 Desenvolvimento

Use o arquivo `client.http` para testar os endpoints da API com a extensão REST Client do VS Code.

---

Desenvolvido com ❤️ durante o NLW da Rocketseat
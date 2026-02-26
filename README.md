# Autoflex API

API REST para controle de estoque e sugestão de produção industrial.

## Pré-requisitos

- Node.js 18+
- Yarn
- Docker e Docker Compose

## Como rodar localmente

### 1. Subir o banco de dados

```bash
yarn docker:up
```

### 2. Configurar variáveis de ambiente

```bash
cp .env.example .env
```

Edite o `.env` se necessário.

### 3. Instalar dependências

```bash
yarn
```

### 4. Rodar a aplicação

```bash
yarn start:dev
```

A API estará disponível em `http://localhost:3000/api`.

### Parar o banco de dados

```bash
yarn docker:down
```

## Estrutura do projeto

```
src/
  modules/
    products/          # Módulo de produtos acabados
    raw-materials/     # Módulo de matérias-primas
    compositions/      # Módulo de composições (receitas)
    production/        # Módulo de produção e sugestões
  shared/
    database/          # Configurações de banco de dados
    filters/           # Exception filters globais
    interceptors/      # Interceptors globais
  main.ts              # Bootstrap da aplicação
  app.module.ts        # Módulo raiz
```

## Scripts disponíveis

| Script | Descrição |
|---|---|
| `yarn start:dev` | Inicia em modo desenvolvimento (watch) |
| `yarn start:debug` | Inicia em modo debug |
| `yarn build` | Compila o projeto |
| `yarn start:prod` | Inicia a build de produção |
| `yarn test` | Executa testes unitários |
| `yarn test:cov` | Executa testes com cobertura |
| `yarn docker:up` | Sobe o PostgreSQL via Docker |
| `yarn docker:down` | Para o PostgreSQL via Docker |

## Padrões da API

### Resposta de sucesso

```json
{
  "data": {},
  "timestamp": "2026-01-01T00:00:00.000Z"
}
```

### Resposta de erro

```json
{
  "statusCode": 400,
  "message": "Validation error",
  "timestamp": "2026-01-01T00:00:00.000Z",
  "path": "/api/resource"
}
```

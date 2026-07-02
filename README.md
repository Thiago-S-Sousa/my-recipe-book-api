# BookStore API

Backend da aplicação **MyRecipeBook**, desenvolvido em **.NET 9**, responsável pelo gerenciamento do catálogo de receitas da plataforma.

O projeto segue os princípios de **Domain-Driven Design (DDD)**, **SOLID** e uma arquitetura em camadas inspirada na **Clean Architecture**, priorizando baixo acoplamento, alta coesão e facilidade de manutenção.

## Tecnologias

- .NET 9
- ASP.NET Core Web API
- Entity Framework Core
- PostgreSQL
- FluentValidation
- JWT Authentication
- Swagger/OpenAPI
- Docker
- GitHub Actions

---

## Estrutura do Projeto

```text
src/
├── Backend
│   ├── MyRecipeBook.Api
│   ├── MyRecipeBook.Application
│   ├── MyRecipeBook.Domain
│   └── MyRecipeBook.Infrastructure
│
└── Shared
    ├── MyRecipeBook.Communication
    └── MyRecipeBook.Exception

tests/
├── MyRecipeBook.Api.Tests
├── MyRecipeBook.Application.Tests
├── MyRecipeBook.Domain.Tests
└── MyRecipeBook.Infrastructure.Tests
```

### Camadas

| Camada | Responsabilidade |
|---------|------------------|
| MyRecipeBook.Api | Controllers, Middlewares, autenticação, configuração da aplicação e documentação da API |
| MyRecipeBook.Application | Casos de uso, validações, orquestração das regras de negócio e serviços de aplicação |
| MyRecipeBook.Domain | Entidades, contratos, Value Objects e regras de negócio |
| MyRecipeBook.Infrastructure | Persistência, repositórios, serviços externos e implementações técnicas |
| MyRecipeBook.Communication | Contratos da API (Requests, Responses, DTOs e ViewModels) |
| MyRecipeBook.Exception | Exceções customizadas e tratamento padronizado de erros |

---

## Arquitetura

O projeto está organizado seguindo a separação de responsabilidades proposta pelo DDD.

```text
HTTP Request
      │
      ▼
Controller
      │
      ▼
Application (Use Cases)
      │
      ▼
Domain
      │
      ▼
Infrastructure
      │
      ▼
PostgreSQL
      │
      ▼
HTTP Response
```

---

## Estratégia de Branches

O projeto utiliza uma estratégia baseada em **Git Flow simplificado**.

```text
main
│
├─ Produção
│
develop
│
├─ Integração e homologação
│
feature/*
│
├─ Novas funcionalidades
│
hotfix/*
│
└─ Correções urgentes
```

### Fluxo de Desenvolvimento

```text
feature/*
        ↓
Pull Request
        ↓
develop
        ↓
Validações automatizadas
        ↓
Merge

develop
        ↓
Pull Request
        ↓
main
        ↓
Validações automatizadas
        ↓
Merge Manual
```

---

## Convenção de Branches

### Nova funcionalidade

```bash
feature/nome-da-funcionalidade
```

Exemplos:

```bash
feature/create-order
feature/authentication
feature/book-catalog
```

### Correção de erro

```bash
hotfix/correcao-descricao
```

Exemplos:

```bash
hotfix/order-validation
hotfix/login-token
```

---

## Pull Requests

Todo desenvolvimento deve ser realizado através de Pull Requests.

### Requisitos para aprovação

- Build executado com sucesso.
- Testes executados com sucesso.
- No mínimo **1 aprovação**.
- Aprovação dos Code Owners.
- O autor do Pull Request não pode aprovar o próprio PR.
- Todas as conversas devem estar resolvidas antes do merge.

---

## GitHub Actions

As validações automáticas são executadas em Pull Requests destinados às branches:

```text
develop
main
```

### Validações executadas

- Restore dos pacotes.
- Build da solução.
- Execução dos testes unitários.
- Execução dos testes de integração.
- Verificação da cobertura mínima de testes (quando configurada).
- Validação das regras de proteção da branch.

---

## Executando Localmente

### Pré-requisitos

- .NET SDK 9
- PostgreSQL
- Docker (opcional)
- Git

### Clonar o projeto

```bash
git clone https://github.com/Thiago-S-Sousa/my-recipe-book-api.git
```

### Restaurar dependências

```bash
dotnet restore
```

### Compilar

```bash
dotnet build
```

### Executar testes

```bash
dotnet test
```

### Aplicar as migrations

```bash
dotnet ef database update --project src/Backend/MyRecipeBook.Infrastructure --startup-project src/Backend/MyRecipeBook.Api
```

### Executar aplicação

```bash
dotnet run --project src/Backend/MyRecipeBook.Api
```

### Swagger

Após iniciar a aplicação:

```text
https://localhost:{porta}/swagger
```

---

## Versionamento da API

A API seguirá versionamento por URL.

Exemplo:

```text
/api/v1/users
```

Novas versões deverão preservar a compatibilidade sempre que possível.

---

## Boas Práticas

- Não realizar commits diretamente em `main`.
- Não realizar commits diretamente em `develop`.
- Sempre utilizar Pull Requests.
- Respeitar a arquitetura DDD definida para o projeto.
- Não adicionar regras de negócio na camada `Api`.
- Manter o domínio independente de frameworks.
- Utilizar FluentValidation para validações de entrada.
- Adicionar testes para novas funcionalidades.
- Atualizar a documentação sempre que necessário.

---

## Convenção de Commits

O projeto adota **Conventional Commits**.

### Funcionalidade

```text
feat: add order creation use case
```

### Correção

```text
fix: validate customer email
```

### Refatoração

```text
refactor: simplify order repository
```

### Testes

```text
test: add order validation tests
```

### Documentação

```text
docs: update project documentation
```

### Integração Contínua

```text
ci: update github actions workflow
```

### Manutenção

```text
chore: update dependencies
```

---

<!--

## Roadmap

### MVP

- Catálogo de livros
- Cadastro de pedidos
- Pagamento via Pix
- Autenticação administrativa
- Gerenciamento de pedidos

### Futuras versões

- Múltiplos livros
- Controle de estoque
- Dashboard administrativo
- Integração com gateway Pix
- Cálculo de frete
- Área do cliente
- Relatórios gerenciais

---

-->

## Licença

Este projeto está disponível publicamente para fins de visualização e aprendizado.

Salvo disposição em contrário em um arquivo de licença (LICENSE) neste repositório, todos os direitos são reservados pelo proprietário do repositório. O código-fonte, a documentação e outros ativos do projeto não podem ser copiados, modificados, redistribuídos ou utilizados para fins comerciais sem permissão prévia por escrito.
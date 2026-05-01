# Arquitetura

## Estrutura de diretórios

```
finanpy/
├── manage.py
├── pyproject.toml
├── uv.lock
│
├── kernel/                     # Configurações Django (projeto)
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
│
├── core/                       # Landing page pública
├── users/                      # CustomUser — autenticação por e-mail
├── accounts/                   # Contas bancárias
├── categories/                 # Categorias de transações
├── transactions/               # Receitas e despesas
├── goals/                      # Metas financeiras
├── dashboard/                  # Dashboard principal
│
└── templates/                  # Templates globais compartilhados
    ├── base.html
    └── partials/
        ├── navbar.html
        ├── sidebar.html
        └── messages.html
```

Cada app segue a estrutura padrão Django acrescida de `forms.py`, `urls.py` e o diretório `templates/<app>/`.

Apps que utilizam signals mantêm a lógica em `signals.py` dentro da própria app.

## Apps

| App | Responsabilidade |
|---|---|
| `kernel` | Configurações globais do projeto Django |
| `core` | Landing page pública |
| `users` | Modelo `CustomUser`, cadastro, login e logout |
| `accounts` | CRUD de contas bancárias |
| `categories` | Categorias padrão e personalizadas |
| `transactions` | Registro e listagem de receitas e despesas |
| `goals` | Metas financeiras e aportes |
| `dashboard` | Visão consolidada das finanças |

## Modelo de dados

```mermaid
erDiagram
    CUSTOM_USER {
        int id PK
        string email UK
        string first_name
        string last_name
        string password
        datetime date_joined
        bool is_active
        bool is_staff
    }

    ACCOUNT {
        int id PK
        int user_id FK
        string name
        string type
        decimal initial_balance
        datetime created_at
        datetime updated_at
    }

    CATEGORY {
        int id PK
        int user_id FK "nullable — null = padrão do sistema"
        string name
        string type "income | expense"
        bool is_default
        datetime created_at
        datetime updated_at
    }

    TRANSACTION {
        int id PK
        int user_id FK
        int account_id FK
        int category_id FK
        string type "income | expense"
        decimal amount
        string description
        date date
        datetime created_at
        datetime updated_at
    }

    GOAL {
        int id PK
        int user_id FK
        string name
        decimal target_amount
        decimal current_amount
        date deadline
        datetime created_at
        datetime updated_at
    }

    GOAL_CONTRIBUTION {
        int id PK
        int goal_id FK
        decimal amount
        string note
        date date
        datetime created_at
        datetime updated_at
    }

    CUSTOM_USER ||--o{ ACCOUNT : "possui"
    CUSTOM_USER ||--o{ CATEGORY : "cria"
    CUSTOM_USER ||--o{ TRANSACTION : "registra"
    CUSTOM_USER ||--o{ GOAL : "define"
    ACCOUNT ||--o{ TRANSACTION : "recebe"
    CATEGORY ||--o{ TRANSACTION : "classifica"
    GOAL ||--o{ GOAL_CONTRIBUTION : "recebe"
```

## Fluxo de navegação

```mermaid
flowchart TD
    A([Acessa o sistema]) --> B{Está autenticado?}
    B -- Não --> C[Landing Page]
    C --> D[Cadastro]
    C --> E[Login]
    D --> F{Dados válidos?}
    F -- Não --> D
    F -- Sim --> G[Dashboard]
    E --> H{Credenciais válidas?}
    H -- Não --> E
    H -- Sim --> G
    B -- Sim --> G

    G --> I[Transações]
    G --> J[Contas Bancárias]
    G --> K[Metas]
    G --> L[Categorias]
```

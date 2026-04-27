# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Comandos

```bash
# Instalar dependências (preferir uv)
uv sync
# ou: pip install -e .

# Aplicar migrations
python manage.py migrate

# Iniciar servidor de desenvolvimento
python manage.py runserver

# Criar superusuário
python manage.py createsuperuser

# Criar nova app
python manage.py startapp <nome>

# Abrir shell interativo
python manage.py shell_plus   # requer django-extensions
```

## Arquitetura

### Apps existentes

| App | Responsabilidade |
|-----|-----------------|
| `kernel/` | Configuração central do Django (settings, URLs raiz, wsgi/asgi) |
| `accounts/` | Cadastro, login e logout (login via **e-mail**, não username) |
| `categories/` | Categorias padrão do sistema + categorias personalizadas do usuário |
| `transactions/` | Registro de receitas e despesas |
| `profiles/` | Dados de perfil do usuário autenticado |
| `users/` | Extensão do modelo de usuário Django |

### Apps a criar (conforme PRD)

- `core/` — Landing page pública
- `dashboard/` — Visão consolidada financeira do mês
- `goals/` — Metas financeiras e aportes

### Autenticação

Login é feito por e-mail. Requer backend customizado em `accounts/backends.py` registrado em `settings.py`:

```python
AUTHENTICATION_BACKENDS = ['accounts.backends.EmailBackend']
LOGIN_URL = '/login/'
LOGIN_REDIRECT_URL = '/dashboard/'
LOGOUT_REDIRECT_URL = '/'
```

### Isolamento de dados

Todas as queries de objetos do usuário devem filtrar pelo usuário autenticado via `get_queryset`. Nunca expor dados de outros usuários.

## Padrões obrigatórios

### Código
- PEP 8; aspas simples
- Código em inglês, interface em português brasileiro
- Class-Based Views (CBVs) sempre que possível
- Views privadas sempre com `LoginRequiredMixin`
- Signals separados em `signals.py` dentro do app correspondente

### Models
Todo model deve incluir `created_at` e `updated_at`:

```python
created_at = models.DateTimeField(auto_now_add=True)
updated_at = models.DateTimeField(auto_now=True)
```

### Templates
Templates globais (`base.html`, `partials/`) ficam em `templates/` na raiz do projeto. Templates de cada app ficam em `app/templates/app/`. Essa estrutura já está configurada em `kernel/settings.py` via `DIRS: [BASE_DIR, 'templates']`.

Herança a partir de `base.html`. Sidebar e navbar incluídas via `{% include %}`:

```html
{% extends 'base.html' %}
{% block content %}...{% endblock %}
```

### Frontend
TailwindCSS via CDN (sem compilação no MVP). Fundo escuro obrigatório:

```html
<body class="bg-gray-950 text-white min-h-screen">
```

Paleta principal: `gray-950/900/800` (fundo), `emerald-400` (receitas), `red-400` (despesas), `violet-400/600` (destaques/botões).

## Restrições do MVP

- Sem Docker
- Sem testes automatizados
- Banco de dados: SQLite apenas
- Nada além do que está especificado no PRD deve ser adicionado

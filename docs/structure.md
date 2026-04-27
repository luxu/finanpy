# Estrutura do Projeto

## Visão Geral

```
finanpy/
├── kernel/          # Configuração principal do projeto Django
├── accounts/        # Autenticação de usuários
├── categories/      # Gerenciamento de categorias
├── transactions/    # Registro de transações
├── profiles/        # Perfil de usuário
├── users/           # Modelo de usuário estendido
├── manage.py
├── pyproject.toml
└── db.sqlite3
```

## Apps

### `kernel/`
Configuração central do Django. Contém `settings.py`, `urls.py`, `wsgi.py` e `asgi.py`.

- `settings.py` — Configurações do projeto (banco de dados, apps instalados, idioma, timezone)
- `urls.py` — Roteamento raiz (atualmente inclui apenas `/admin/`)

### `accounts/`
Responsável pelo fluxo de autenticação: cadastro, login e logout.  
Login é feito por e-mail, não por username.

### `categories/`
Gerencia as categorias vinculadas às transações.  
O sistema terá categorias padrão pré-cadastradas e categorias criadas pelo usuário.

### `transactions/`
Registro de receitas e despesas. Cada transação pertence a uma categoria e a um usuário.

### `profiles/`
Dados de perfil associados ao usuário autenticado.

### `users/`
Extensão do modelo de usuário padrão do Django.

## Configurações Relevantes (`kernel/settings.py`)

```python
LANGUAGE_CODE = 'pt-br'
TIME_ZONE = 'America/Sao_Paulo'
USE_I18N = True
USE_TZ = True

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

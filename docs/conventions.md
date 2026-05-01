# Convenções

## Código

- Seguir **PEP8** em todo o código Python
- Usar **aspas simples** para strings
- Todo o código (variáveis, funções, classes, comentários) deve ser escrito em **inglês**
- A interface do usuário (labels, mensagens, textos de template) deve estar em **português brasileiro**

## Models

- Todo model deve conter os campos `created_at` e `updated_at`:

```python
created_at = models.DateTimeField(auto_now_add=True)
updated_at = models.DateTimeField(auto_now=True)
```

- O modelo de usuário customizado é `CustomUser`, herdando de `AbstractUser`, com `email` como `USERNAME_FIELD` (sem campo `username`)
- `AUTH_USER_MODEL` deve ser configurado como `'users.CustomUser'` em `settings.py`

## Views

- Preferir **Class-Based Views** sempre que possível
- Views de páginas autenticadas devem usar `LoginRequiredMixin`
- Queries de formulários (ex: listas de contas e categorias) devem ser filtradas pelo usuário autenticado

## Signals

- Signals devem ficar no arquivo `signals.py` dentro da app correspondente

## Gerenciamento de pacotes

- Usar exclusivamente o `uv` para gerenciar pacotes e o ambiente virtual
- Proibido usar `pip` diretamente ou manter `requirements.txt`
- Dependências ficam em `pyproject.toml` + `uv.lock`

## Banco de dados

- SQLite é o banco padrão do projeto

## Escopo

- Não adicionar funcionalidades, abstrações ou dependências além do que o projeto exige
- Manter o código simples e direto

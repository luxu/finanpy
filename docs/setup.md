# Setup

## Pré-requisitos

- Python 3.12+
- [`uv`](https://docs.astral.sh/uv/) instalado

## Instalação

```bash
# Clonar o repositório
git clone <url-do-repositorio>
cd finanpy

# Instalar dependências e criar o ambiente virtual
uv sync
```

## Configuração do ambiente

Crie um arquivo `.env` na raiz do projeto com as variáveis abaixo:

```env
SECRET_KEY=sua-chave-secreta-aqui
DEBUG=True
```

O projeto usa `python-decouple` para leitura das variáveis de ambiente.

## Rodando o projeto

```bash
# Aplicar migrations
uv run manage.py migrate

# Iniciar servidor de desenvolvimento
uv run manage.py runserver
```

Acesse em: `http://127.0.0.1:8000`

## Comandos úteis

| Ação | Comando |
|---|---|
| Adicionar dependência | `uv add <pacote>` |
| Adicionar dependência de dev | `uv add --dev <pacote>` |
| Sincronizar ambiente | `uv sync` |
| Criar migrations | `uv run manage.py makemigrations` |
| Aplicar migrations | `uv run manage.py migrate` |
| Criar superusuário | `uv run manage.py createsuperuser` |
| Carregar fixtures | `uv run manage.py loaddata <fixture>` |
| Criar nova app | `uv run manage.py startapp <nome>` |

> **Atenção:** O uso direto de `pip` ou de `requirements.txt` é proibido neste projeto. Use sempre `uv`.

## Dependências

Definidas em `pyproject.toml`:

- `django>=6.0.4`
- `django-extensions>=4.1`
- `ipython>=9.13.0`
- `python-decouple>=3.8`

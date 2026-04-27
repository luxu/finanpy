# Setup

## Pré-requisitos

- Python 3.12+
- `uv` ou `pip`

## Instalação

```bash
# Clone e entre na pasta
cd finanpy

# Crie e ative o ambiente virtual
python -m venv .venv

# Windows
.venv\Scripts\activate

# Linux/macOS
source .venv/bin/activate

# Instale as dependências
pip install -e .
```

## Executando

```bash
# Aplica migrations
python manage.py migrate

# Cria superusuário para o admin
python manage.py createsuperuser

# Inicia o servidor
python manage.py runserver
```

Acesse em `http://localhost:8000`.  
Painel admin em `http://localhost:8000/admin/`.

## Dependências

Definidas em `pyproject.toml`:

| Pacote | Uso |
|--------|-----|
| `django>=6.0.4` | Framework web |
| `django-extensions>=4.1` | Utilitários de admin/shell |
| `ipython>=9.12.0` | Shell interativo aprimorado |
| `python-decouple>=3.8` | Configuração via variáveis de ambiente |

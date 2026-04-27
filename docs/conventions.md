# Convenções de Código

## Geral

- **Linguagem do código:** Inglês (variáveis, funções, classes, comentários)
- **Linguagem da interface:** Português Brasileiro
- **Estilo:** PEP 8
- **Aspas:** Simples (`'string'`, não `"string"`)

## Django

### Views
Usar **Class-Based Views (CBVs)** sempre que possível.  
Views que requerem autenticação devem usar `LoginRequiredMixin`.

```python
from django.contrib.auth.mixins import LoginRequiredMixin
from django.views.generic import ListView

class TransactionListView(LoginRequiredMixin, ListView):
    model = Transaction
    template_name = 'transactions/list.html'
```

### Models
Todos os models devem incluir os campos `created_at` e `updated_at`.

```python
from django.db import models

class Transaction(models.Model):
    # campos do model
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
```

### Signals
Signals devem ser separados em arquivo `signals.py` dentro do app correspondente.

### Templates
Usar herança de templates com `base.html` como template raiz.

```html
{% extends 'base.html' %}

{% block content %}
  ...
{% endblock %}
```

## Estrutura de cada App

```
app_name/
├── models.py
├── views.py
├── urls.py
├── forms.py
├── admin.py
├── apps.py
├── signals.py      # se necessário
├── tests.py
└── migrations/
```

## O que não fazer

- Não usar Docker ou ferramentas de containerização no MVP
- Não implementar testes automatizados no MVP
- Não adicionar complexidade desnecessária — sem over-engineering

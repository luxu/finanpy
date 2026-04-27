# Agentes de Desenvolvimento — Finanpy

Agentes especializados na stack do projeto para uso com Claude Code.

> **Para ativar:** copie os arquivos `.md` desta pasta para `.claude/agents/` na raiz do projeto.
> O Claude Code carrega automaticamente os agentes sub-agent a partir desse diretório.

---

## Índice

| Agente | Arquivo | Especialidade |
|--------|---------|---------------|
| [Backend Django](#backend-django) | [backend.md](backend.md) | Models, views CBVs, forms, URLs, autenticação, signals, migrations |
| [Frontend DTL + TailwindCSS](#frontend-dtl--tailwindcss) | [frontend.md](frontend.md) | Templates Django, componentes do design system dark mode |
| [QA / Tester](#qa--tester) | [qa.md](qa.md) | Testes funcionais e visuais via Playwright no browser |

---

## Backend Django

**Arquivo:** `backend.md`

**Quando usar:**
- Criar ou alterar models, migrations, forms, views (CBVs) e URLs
- Implementar ou ajustar autenticação por e-mail (`EmailBackend`)
- Configurar `kernel/settings.py`, `kernel/urls.py` ou backends customizados
- Criar signals em `signals.py`, registrar models no `admin.py`
- Criar fixtures de categorias padrão ou outros dados iniciais
- Implementar lógica de negócio (cálculo de saldo, progresso de metas)
- Qualquer código Python/Django no servidor

**Não usar para:** markup HTML, classes TailwindCSS, testes de UI no browser

**Usa MCP:** context7 para consultar documentação oficial do Django

---

## Frontend DTL + TailwindCSS

**Arquivo:** `frontend.md`

**Quando usar:**
- Criar ou editar templates HTML com Django Template Language
- Implementar componentes do design system (cards, inputs, botões, badges)
- Criar ou editar `base.html` e partials (`navbar.html`, `sidebar.html`, `messages.html`)
- Aplicar o tema dark com a paleta de cores do projeto
- Garantir responsividade mobile (375px), tablet (768px) e desktop (1280px)
- Criar páginas: landing, login, cadastro, dashboard, listagens, formulários

**Não usar para:** lógica Python, models, views, migrações, queries ao banco

**Usa MCP:** context7 para consultar documentação do TailwindCSS e DTL

---

## QA / Tester

**Arquivo:** `qa.md`

**Quando usar:**
- Verificar se um fluxo funciona de ponta a ponta no browser
- Confirmar se o design visual está correto e consistente com o design system
- Testar responsividade em diferentes viewports (375px, 768px, 1280px)
- Validar comportamento de formulários: erros de validação, redirecionamentos
- Checar isolamento de dados entre usuários (segurança)
- Capturar screenshots de evidência após implementações

**Requer:** servidor rodando em `http://localhost:8000` (`task runserver`)

**Usa MCP:** Playwright para controlar o browser e interagir com o sistema

---

## Stack do Projeto

| Camada | Tecnologia |
|--------|-----------|
| Backend | Python 3.12+, Django 5.x |
| Frontend | Django Template Language + TailwindCSS via CDN |
| Banco de dados | SQLite |
| Autenticação | Django Auth com login por e-mail |
| Gerenciador de pacotes | `uv` |
| Task runner | `taskipy` (`task <nome>`) |
| Linter | `ruff` (`task lint`) |

## Fluxo de Uso Recomendado

```
Tarefa de backend (model/view/form/URL)
  → Agente: backend

Tarefa de frontend (template/componente/layout)
  → Agente: frontend

Verificação após implementação
  → Agente: qa (com servidor rodando)
```

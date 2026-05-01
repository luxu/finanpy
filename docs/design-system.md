# Design System

O frontend usa **TailwindCSS via CDN** dentro do Django Template Language. O tema é **dark mode** com gradientes em violet/indigo.

## Paleta de cores

| Token Tailwind | Uso |
|---|---|
| `bg-gray-950` | Fundo principal (body) |
| `bg-gray-900` | Fundo de cards e containers |
| `bg-gray-800` | Inputs, bordas, separadores |
| `bg-gray-700` | Hover de itens de lista |
| `from-violet-600 to-indigo-600` | Gradiente primário (botões, destaques) |
| `text-white` | Texto principal |
| `text-gray-400` | Texto secundário e placeholders |
| `text-gray-200` | Corpo de texto |
| `text-emerald-400` | Receitas / valores positivos |
| `text-red-400` | Despesas / valores negativos |
| `text-violet-400` | Metas / destaques |
| `border-gray-800` | Bordas de cards |
| `border-gray-700` | Bordas de inputs |

## Tipografia

| Elemento | Classe Tailwind |
|---|---|
| Título de página | `text-2xl font-bold text-white` |
| Subtítulo / label | `text-sm font-medium text-gray-400` |
| Corpo de texto | `text-base text-gray-200` |
| Valor monetário grande | `text-3xl font-bold text-white` |
| Valor positivo (receita) | `text-emerald-400 font-semibold` |
| Valor negativo (despesa) | `text-red-400 font-semibold` |
| Fonte do sistema | `font-sans` — Inter via Google Fonts CDN |

## Botões

```html
<!-- Primário — ação principal -->
<button class="bg-gradient-to-r from-violet-600 to-indigo-600 hover:from-violet-700
  hover:to-indigo-700 text-white font-semibold py-2 px-4 rounded-lg
  transition-all duration-200 cursor-pointer">
  Salvar
</button>

<!-- Secundário — cancelar / ação neutra -->
<button class="bg-gray-800 hover:bg-gray-700 text-gray-200 font-semibold py-2 px-4
  rounded-lg border border-gray-700 transition-all duration-200 cursor-pointer">
  Cancelar
</button>

<!-- Perigo — exclusão -->
<button class="bg-red-600 hover:bg-red-700 text-white font-semibold py-2 px-4
  rounded-lg transition-all duration-200 cursor-pointer">
  Excluir
</button>

<!-- Ghost — ação secundária sutil -->
<button class="text-violet-400 hover:text-violet-300 font-medium transition-colors
  duration-200 cursor-pointer">
  Ver todos
</button>
```

## Inputs e formulários

```html
<label class="block text-sm font-medium text-gray-400 mb-1">Nome</label>

<input type="text"
  class="w-full bg-gray-800 border border-gray-700 text-white rounded-lg px-4 py-2
    focus:outline-none focus:ring-2 focus:ring-violet-500 placeholder-gray-500
    transition-all duration-200">

<select class="w-full bg-gray-800 border border-gray-700 text-white rounded-lg px-4 py-2
  focus:outline-none focus:ring-2 focus:ring-violet-500 transition-all duration-200">
  <option>Selecione...</option>
</select>

<textarea class="w-full bg-gray-800 border border-gray-700 text-white rounded-lg px-4 py-2
  focus:outline-none focus:ring-2 focus:ring-violet-500 placeholder-gray-500
  transition-all duration-200"></textarea>

<input type="date"
  class="w-full bg-gray-800 border border-gray-700 text-white rounded-lg px-4 py-2
    focus:outline-none focus:ring-2 focus:ring-violet-500 transition-all duration-200
    [color-scheme:dark]">

<!-- Erro de campo -->
<span class="text-red-400 text-sm mt-1 block">Campo obrigatório.</span>
```

## Cards

```html
<!-- Card padrão -->
<div class="bg-gray-900 border border-gray-800 rounded-xl p-6 shadow-lg">
  <!-- conteúdo -->
</div>

<!-- Card de KPI (dashboard) -->
<div class="bg-gray-900 border border-gray-800 rounded-xl p-6 shadow-lg flex flex-col gap-2">
  <span class="text-sm font-medium text-gray-400">Saldo do Mês</span>
  <span class="text-3xl font-bold text-white">R$ 1.250,00</span>
</div>
```

## Layout

```html
<!-- Container principal de página -->
<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
  <!-- conteúdo -->
</div>

<!-- Grid de 3 colunas (dashboard) -->
<div class="grid grid-cols-1 md:grid-cols-3 gap-6">
  <!-- cards -->
</div>

<!-- Layout base com sidebar -->
<div class="flex min-h-screen bg-gray-950">
  <aside class="w-64 bg-gray-900 border-r border-gray-800 flex-shrink-0">
    <!-- navegação -->
  </aside>
  <main class="flex-1 overflow-auto">
    <!-- páginas -->
  </main>
</div>
```

## Navbar e Sidebar

```html
<!-- Navbar superior -->
<nav class="bg-gray-900 border-b border-gray-800 px-6 py-4 flex items-center justify-between">
  <span class="text-xl font-bold bg-gradient-to-r from-violet-400 to-indigo-400
    bg-clip-text text-transparent">
    Finanpy
  </span>
  <div class="flex items-center gap-4">
    <span class="text-gray-400 text-sm">Olá, {{ user.first_name }}</span>
    <a href="{% url 'users:logout' %}"
      class="text-gray-400 hover:text-white text-sm transition-colors duration-200">
      Sair
    </a>
  </div>
</nav>

<!-- Item de sidebar (normal) -->
<a href="#" class="flex items-center gap-3 px-4 py-3 text-gray-400 hover:text-white
  hover:bg-gray-800 rounded-lg transition-all duration-200">
  Dashboard
</a>

<!-- Item de sidebar (ativo) -->
<a href="#" class="flex items-center gap-3 px-4 py-3 text-white bg-gray-800
  rounded-lg font-medium">
  Dashboard
</a>
```

## Barra de progresso

```html
<div class="w-full bg-gray-800 rounded-full h-2">
  <div class="bg-gradient-to-r from-violet-600 to-indigo-600 h-2 rounded-full
    transition-all duration-500"
    style="width: {{ goal.progress_percent }}%">
  </div>
</div>
<div class="flex justify-between text-xs text-gray-400 mt-1">
  <span>R$ {{ goal.current_amount }}</span>
  <span>{{ goal.progress_percent }}%</span>
  <span>R$ {{ goal.target_amount }}</span>
</div>
```

## Mensagens de feedback

```html
<!-- Sucesso -->
<div class="bg-emerald-900/40 border border-emerald-700 text-emerald-400 px-4 py-3
  rounded-lg text-sm">
  Transação salva com sucesso.
</div>

<!-- Erro -->
<div class="bg-red-900/40 border border-red-700 text-red-400 px-4 py-3
  rounded-lg text-sm">
  Ocorreu um erro. Verifique os dados e tente novamente.
</div>
```

## Tabela de dados

```html
<div class="bg-gray-900 border border-gray-800 rounded-xl overflow-hidden">
  <table class="w-full text-sm">
    <thead>
      <tr class="border-b border-gray-800">
        <th class="px-6 py-4 text-left text-xs font-medium text-gray-400 uppercase tracking-wider">
          Descrição
        </th>
      </tr>
    </thead>
    <tbody class="divide-y divide-gray-800">
      <tr class="hover:bg-gray-800/50 transition-colors duration-150">
        <td class="px-6 py-4 text-gray-200">Supermercado</td>
      </tr>
    </tbody>
  </table>
</div>
```

# Design System

Interface em dark mode moderno, construída com TailwindCSS via CDN.

## Cores

| Uso | Classe Tailwind | Hex |
|-----|----------------|-----|
| Background principal | `bg-gray-950` | `#030712` |
| Background de cards | `bg-gray-900` | `#111827` |
| Texto principal | `text-white` | — |
| Texto secundário | `text-gray-400` | — |
| Valores positivos (receitas) | `text-emerald-400` | — |
| Valores negativos (despesas) | `text-red-400` | — |
| Metas / destaques | `text-violet-400` | — |
| Botão primário (gradiente) | `from-violet-600 to-indigo-600` | — |

## Tipografia

| Elemento | Classes |
|----------|---------|
| Título de página | `text-2xl font-bold text-white` |
| Label / rótulo | `text-sm font-medium text-gray-400` |
| Corpo | `text-base text-gray-200` |
| Valores monetários grandes | `text-3xl font-bold text-white` |

Fonte: **Inter** (via CDN).

## Componentes

### Card
```html
<div class="bg-gray-900 border border-gray-800 rounded-xl p-6 shadow-lg">
  ...
</div>
```

### Input
```html
<input class="bg-gray-800 border border-gray-700 text-white rounded-lg focus:ring-2 focus:ring-violet-500">
```

### Botão primário
```html
<button class="bg-gradient-to-r from-violet-600 to-indigo-600 text-white rounded-lg px-4 py-2">
  Salvar
</button>
```

### Botão secundário
```html
<button class="bg-gray-700 text-white rounded-lg px-4 py-2">
  Cancelar
</button>
```

### Botão de perigo
```html
<button class="bg-red-600 text-white rounded-lg px-4 py-2">
  Excluir
</button>
```

## Layout

```html
<!-- Container padrão -->
<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

<!-- Grid responsivo de cards -->
<div class="grid grid-cols-1 md:grid-cols-3 gap-6">
```

## Navbar e Sidebar

```
Navbar:  bg-gray-900 border-b border-gray-800
Sidebar: bg-gray-900 border-r border-gray-800
```

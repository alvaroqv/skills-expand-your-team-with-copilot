# Instruções para Copilot — Design System Genérico com Bootstrap 5, HTML, CSS, JavaScript, ApexCharts e Lucide

## 1. Objetivo

Este documento define as instruções para o GitHub Copilot refatorar um projeto de dashboard/backoffice baseado em **HTML, CSS, JavaScript, Bootstrap 5, ApexCharts e Lucide Icons**, transformando o layout em uma estrutura **genérica, reutilizável e orientada a Design System**.

O objetivo principal é evitar que o projeto fique acoplado a um domínio específico, como financeiro, vendas ou operações. A estrutura deve ser reutilizável em diferentes sistemas corporativos, como:

- backoffice administrativo;
- dashboards executivos;
- sistemas internos;
- CRM;
- ERP;
- portais operacionais;
- painéis financeiros;
- painéis comerciais;
- painéis de atendimento;
- sistemas de suporte.

O projeto deve usar **Bootstrap 5 como base estrutural e comportamental**, mas a identidade visual final deve ser definida por uma camada própria de CSS, evitando aparência padrão de Bootstrap.

---

## 2. Stack obrigatória

O Copilot deve manter a seguinte stack:

```text
HTML5
CSS3
JavaScript Vanilla
Bootstrap 5
ApexCharts
Lucide Icons
```

### 2.1. Bootstrap 5

Bootstrap deve ser usado para:

- grid responsivo;
- containers;
- rows e columns;
- utilitários responsivos;
- dropdowns;
- modals;
- offcanvas;
- collapse;
- forms;
- tables;
- acessibilidade básica de componentes;
- comportamento JavaScript quando necessário.

Bootstrap **não deve ser usado como identidade visual final**.

Evitar que o layout final pareça Bootstrap puro.

### 2.2. ApexCharts

ApexCharts deve ser usado para gráficos:

- sparkline charts;
- line charts;
- area charts;
- bar charts;
- donut charts;
- charts de KPI.

Os gráficos devem ser isolados em módulos reutilizáveis.

### 2.3. Lucide Icons

Lucide deve ser usado para ícones.

Os ícones devem seguir um padrão visual único, com classes próprias como:

```text
app-icon
app-icon-box
app-icon-action
app-icon-muted
```

---

## 3. Princípios arquiteturais do layout

### 3.1. Bootstrap como fundação, não como aparência

Use Bootstrap para estrutura e comportamento, mas use CSS próprio para a identidade visual.

Exemplo correto:

```html
<div class="card app-card app-metric-card">
  <div class="card-body">
    ...
  </div>
</div>
```

Exemplo a evitar:

```html
<div class="card">
  <div class="card-body">
    ...
  </div>
</div>
```

O componente pode usar `.card`, mas sempre deve ter uma classe de Design System do projeto, como `.app-card`.

---

### 3.2. Componentes nomeados por função, não por domínio

Os componentes devem ser nomeados pela função estrutural ou finalidade visual.

Não usar nomes de domínio como:

```text
finance-header.html
cashflow-card.html
transactions-card.html
sales-widget.html
customer-widget.html
```

Usar nomes genéricos:

```text
page-header.html
chart-card.html
data-list-card.html
metric-card.html
featured-card.html
navigation-sidebar.html
global-header.html
```

O nome do componente deve responder a uma destas perguntas:

- Qual papel estrutural este componente exerce?
- Qual padrão visual este componente implementa?
- Que tipo de informação este componente exibe?

---

### 3.3. Separação de responsabilidades

O projeto deve separar:

```text
HTML parcial
CSS de Design System
JavaScript de comportamento
JavaScript de gráficos
Dados mockados ou configuração da página
```

Evitar arquivos gigantes com muitas responsabilidades misturadas.

---

### 3.4. Reutilização

O layout deve ser reutilizável em outros projetos sem depender de nomes como:

```text
finance
cashflow
transaction
income
expense
```

Esses termos podem aparecer apenas como **dados de exemplo**, nunca como nome de componente estrutural.

---

## 4. Estrutura de pastas recomendada

```text
project/
├── index.html
│
├── partials/
│   ├── layout/
│   │   ├── app-shell.html
│   │   ├── navigation-sidebar.html
│   │   ├── global-header.html
│   │   └── content-wrapper.html
│   │
│   ├── navigation/
│   │   ├── page-breadcrumb.html
│   │   └── tab-navigation.html
│   │
│   ├── page/
│   │   ├── page-header.html
│   │   └── section-header.html
│   │
│   ├── cards/
│   │   ├── featured-card.html
│   │   ├── metric-card.html
│   │   ├── chart-card.html
│   │   ├── data-list-card.html
│   │   ├── summary-card.html
│   │   ├── status-card.html
│   │   ├── progress-card.html
│   │   └── category-overview-card.html
│   │
│   ├── controls/
│   │   ├── search-input.html
│   │   ├── period-filter.html
│   │   ├── action-button-group.html
│   │   ├── view-toggle.html
│   │   └── pagination-controls.html
│   │
│   └── states/
│       ├── loading-state.html
│       ├── empty-state.html
│       ├── error-state.html
│       ├── permission-state.html
│       └── offline-state.html
│
├── assets/
│   ├── css/
│   │   ├── tokens.css
│   │   ├── base.css
│   │   ├── layout.css
│   │   ├── components.css
│   │   ├── dashboard.css
│   │   └── utilities.css
│   │
│   ├── js/
│   │   ├── core/
│   │   │   ├── component-loader.js
│   │   │   ├── app-init.js
│   │   │   └── dom-utils.js
│   │   │
│   │   ├── ui/
│   │   │   ├── icons.js
│   │   │   ├── sidebar.js
│   │   │   ├── dropdowns.js
│   │   │   └── theme-toggle.js
│   │   │
│   │   ├── charts/
│   │   │   ├── chart-factory.js
│   │   │   ├── sparkline-chart.js
│   │   │   ├── bar-chart.js
│   │   │   ├── area-chart.js
│   │   │   └── donut-chart.js
│   │   │
│   │   ├── data/
│   │   │   └── dashboard.mock.js
│   │   │
│   │   └── pages/
│   │       └── dashboard-page.js
│   │
│   └── img/
│       ├── avatars/
│       ├── logos/
│       └── illustrations/
│
├── .github/
│   ├── copilot-instructions.md
│   └── agents/
│       ├── agent-orchestrator.md
│       ├── design-system-agent.md
│       ├── bootstrap-layout-agent.md
│       ├── html-refactor-agent.md
│       ├── javascript-ui-agent.md
│       ├── chart-agent.md
│       ├── accessibility-agent.md
│       └── qa-review-agent.md
│
├── skills/
│   ├── bootstrap5-design-system.md
│   ├── html-partials-refactor.md
│   ├── css-token-system.md
│   ├── apexcharts-integration.md
│   ├── lucide-icons-standard.md
│   ├── responsive-layout.md
│   ├── accessibility-review.md
│   └── refactor-validation.md
│
├── Instruction.md
├── AGENTS.md
├── SKILLS.md
└── README.md
```

---

## 5. Convenção de nomes dos componentes

### 5.1. Layout estrutural

| Componente | Finalidade |
|---|---|
| `app-shell.html` | Estrutura principal da aplicação |
| `navigation-sidebar.html` | Menu lateral principal |
| `global-header.html` | Header/topbar global da aplicação |
| `content-wrapper.html` | Área que envolve o conteúdo principal |
| `page-container.html` | Container interno da página |

---

### 5.2. Navegação

| Componente | Finalidade |
|---|---|
| `page-breadcrumb.html` | Breadcrumb da página atual |
| `tab-navigation.html` | Navegação por abas |
| `sidebar-menu.html` | Lista de grupos e itens da sidebar |
| `sidebar-menu-group.html` | Agrupamento de itens da sidebar |
| `sidebar-menu-item.html` | Item individual de menu |

---

### 5.3. Cabeçalhos de conteúdo

| Componente | Finalidade |
|---|---|
| `page-header.html` | Cabeçalho principal da página |
| `section-header.html` | Cabeçalho de seção |
| `card-header.html` | Cabeçalho interno de card |

---

### 5.4. Cards reutilizáveis

| Componente | Finalidade |
|---|---|
| `metric-card.html` | Exibe KPI, métrica ou indicador |
| `featured-card.html` | Card de destaque principal |
| `chart-card.html` | Card com gráfico |
| `data-list-card.html` | Card com lista de dados |
| `summary-card.html` | Card de resumo textual ou numérico |
| `status-card.html` | Card de status operacional |
| `progress-card.html` | Card com progresso ou percentual |
| `category-overview-card.html` | Card com categorias e distribuição |

---

### 5.5. Controles

| Componente | Finalidade |
|---|---|
| `search-input.html` | Campo de busca |
| `period-filter.html` | Filtro de período |
| `action-button-group.html` | Grupo de botões de ação |
| `view-toggle.html` | Alternância de visualização |
| `pagination-controls.html` | Paginação |
| `table-filter.html` | Filtros para tabela |

---

### 5.6. Estados de tela

| Componente | Finalidade |
|---|---|
| `loading-state.html` | Estado de carregamento |
| `empty-state.html` | Estado sem dados |
| `error-state.html` | Estado de erro |
| `permission-state.html` | Estado sem permissão |
| `offline-state.html` | Estado sem conexão |

---

## 6. Mapeamento de nomes específicos para nomes genéricos

| Nome específico | Nome genérico recomendado |
|---|---|
| `finance-header.html` | `page-header.html` |
| `cashflow-card.html` | `chart-card.html` |
| `transaction-summary-card.html` | `metric-card.html` |
| `transactions-list-card.html` | `data-list-card.html` |
| `my-card.html` | `featured-card.html` |
| `money-go-card.html` | `category-overview-card.html` |
| `finance-dashboard.js` | `dashboard-page.js` |
| `cashflow-chart.js` | `bar-chart.js` |
| `transaction-chart.js` | `sparkline-chart.js` |

---

## 7. Convenção de CSS

### 7.1. Prefixo obrigatório

Todas as classes customizadas do projeto devem usar prefixo:

```text
app-
```

Exemplos:

```text
app-shell
app-sidebar
app-global-header
app-content
app-page-header
app-page-title
app-page-actions
app-card
app-metric-card
app-chart-card
app-data-list-card
app-btn-primary
app-btn-light
app-icon-box
app-badge-soft-primary
```

### 7.2. Evitar classes soltas sem namespace

Evitar:

```css
.card-custom {}
.button-blue {}
.sidebar-link {}
```

Usar:

```css
.app-card {}
.app-btn-primary {}
.app-sidebar-link {}
```

---

## 8. Arquivo `tokens.css`

O arquivo `tokens.css` deve centralizar todas as decisões visuais do Design System.

```css
:root {
  /* Backgrounds */
  --app-bg: #f5f7fb;
  --app-surface: #ffffff;
  --app-surface-muted: #f8fafc;
  --app-surface-soft: #f1f5f9;

  /* Text */
  --app-text-primary: #111827;
  --app-text-secondary: #64748b;
  --app-text-muted: #94a3b8;
  --app-text-inverse: #ffffff;

  /* Borders */
  --app-border: #e5eaf1;
  --app-border-strong: #cbd5e1;

  /* Brand */
  --app-primary: #2563eb;
  --app-primary-hover: #1d4ed8;
  --app-primary-soft: #eff6ff;

  /* Semantic */
  --app-success: #10b981;
  --app-success-soft: #ecfdf5;
  --app-danger: #ef4444;
  --app-danger-soft: #fef2f2;
  --app-warning: #f59e0b;
  --app-warning-soft: #fffbeb;
  --app-info: #0ea5e9;
  --app-info-soft: #f0f9ff;

  /* Radius */
  --app-radius-xs: 6px;
  --app-radius-sm: 10px;
  --app-radius-md: 14px;
  --app-radius-lg: 18px;
  --app-radius-xl: 24px;
  --app-radius-pill: 999px;

  /* Shadows */
  --app-shadow-xs: 0 1px 2px rgba(15, 23, 42, 0.04);
  --app-shadow-sm: 0 4px 14px rgba(15, 23, 42, 0.06);
  --app-shadow-md: 0 12px 32px rgba(15, 23, 42, 0.08);
  --app-shadow-lg: 0 20px 48px rgba(15, 23, 42, 0.12);

  /* Typography */
  --app-font-family: Inter, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  --app-font-size-xs: 0.75rem;
  --app-font-size-sm: 0.875rem;
  --app-font-size-md: 1rem;
  --app-font-size-lg: 1.125rem;
  --app-font-size-xl: 1.5rem;
  --app-font-size-2xl: 2rem;

  /* Layout */
  --app-sidebar-width: 280px;
  --app-header-height: 72px;
  --app-content-padding: 2rem;

  /* Transitions */
  --app-transition-fast: 150ms ease;
  --app-transition-base: 220ms ease;
}
```

---

## 9. Arquivo `base.css`

```css
html {
  min-height: 100%;
}

body {
  min-height: 100vh;
  margin: 0;
  background: var(--app-bg);
  color: var(--app-text-primary);
  font-family: var(--app-font-family);
  font-size: var(--app-font-size-md);
  -webkit-font-smoothing: antialiased;
  text-rendering: optimizeLegibility;
}

a {
  color: inherit;
}

button,
input,
select,
textarea {
  font-family: inherit;
}

img {
  max-width: 100%;
  display: block;
}
```

---

## 10. Arquivo `layout.css`

```css
.app-shell {
  display: grid;
  grid-template-columns: var(--app-sidebar-width) minmax(0, 1fr);
  min-height: 100vh;
  background: var(--app-bg);
}

.app-sidebar {
  position: sticky;
  top: 0;
  height: 100vh;
  background: var(--app-surface);
  border-right: 1px solid var(--app-border);
  overflow-y: auto;
}

.app-main {
  min-width: 0;
  display: flex;
  flex-direction: column;
}

.app-global-header {
  position: sticky;
  top: 0;
  z-index: 100;
  height: var(--app-header-height);
  background: rgba(245, 247, 251, 0.92);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--app-border);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 var(--app-content-padding);
}

.app-content {
  flex: 1;
  padding: var(--app-content-padding);
}

.app-page-container {
  max-width: 1440px;
  margin: 0 auto;
}

.app-dashboard-grid {
  display: grid;
  grid-template-columns: repeat(12, minmax(0, 1fr));
  gap: 1.5rem;
}

.app-grid-span-3 {
  grid-column: span 3;
}

.app-grid-span-4 {
  grid-column: span 4;
}

.app-grid-span-6 {
  grid-column: span 6;
}

.app-grid-span-8 {
  grid-column: span 8;
}

.app-grid-span-12 {
  grid-column: span 12;
}

@media (max-width: 1199.98px) {
  .app-shell {
    grid-template-columns: 1fr;
  }

  .app-sidebar {
    position: fixed;
    left: 0;
    top: 0;
    z-index: 1050;
    width: var(--app-sidebar-width);
    transform: translateX(-100%);
    transition: transform var(--app-transition-base);
  }

  .app-sidebar.is-open {
    transform: translateX(0);
  }

  .app-grid-span-3,
  .app-grid-span-4,
  .app-grid-span-6,
  .app-grid-span-8 {
    grid-column: span 6;
  }
}

@media (max-width: 767.98px) {
  :root {
    --app-content-padding: 1rem;
  }

  .app-dashboard-grid {
    gap: 1rem;
  }

  .app-grid-span-3,
  .app-grid-span-4,
  .app-grid-span-6,
  .app-grid-span-8,
  .app-grid-span-12 {
    grid-column: span 12;
  }
}
```

---

## 11. Arquivo `components.css`

```css
.app-card {
  border: 1px solid var(--app-border);
  border-radius: var(--app-radius-lg);
  background: var(--app-surface);
  box-shadow: var(--app-shadow-sm);
}

.app-card .card-header {
  background: transparent;
  border-bottom: 1px solid var(--app-border);
  padding: 1.25rem 1.5rem;
}

.app-card .card-body {
  padding: 1.5rem;
}

.app-card-title {
  margin: 0;
  color: var(--app-text-primary);
  font-size: var(--app-font-size-lg);
  font-weight: 700;
}

.app-card-subtitle {
  margin: 0.25rem 0 0;
  color: var(--app-text-secondary);
  font-size: var(--app-font-size-sm);
}

.app-page-header {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 1.5rem;
  margin-bottom: 1.5rem;
}

.app-page-title {
  margin: 0;
  color: var(--app-text-primary);
  font-size: var(--app-font-size-2xl);
  font-weight: 750;
  letter-spacing: -0.03em;
}

.app-page-subtitle {
  margin: 0.35rem 0 0;
  color: var(--app-text-secondary);
}

.app-page-actions {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  flex-wrap: wrap;
}

.app-btn-primary {
  --bs-btn-bg: var(--app-primary);
  --bs-btn-border-color: var(--app-primary);
  --bs-btn-hover-bg: var(--app-primary-hover);
  --bs-btn-hover-border-color: var(--app-primary-hover);
  --bs-btn-color: var(--app-text-inverse);
  --bs-btn-hover-color: var(--app-text-inverse);
  border-radius: var(--app-radius-sm);
  font-weight: 650;
  box-shadow: 0 8px 18px rgba(37, 99, 235, 0.22);
}

.app-btn-light {
  --bs-btn-bg: var(--app-surface);
  --bs-btn-border-color: var(--app-border);
  --bs-btn-hover-bg: var(--app-surface-soft);
  --bs-btn-hover-border-color: var(--app-border-strong);
  color: var(--app-text-primary);
  border-radius: var(--app-radius-sm);
  font-weight: 650;
}

.app-icon-box {
  width: 2.5rem;
  height: 2.5rem;
  border-radius: var(--app-radius-md);
  background: var(--app-primary-soft);
  color: var(--app-primary);
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.app-icon-box svg {
  width: 1.15rem;
  height: 1.15rem;
  stroke-width: 2.1;
}

.app-badge-soft-primary,
.app-badge-soft-success,
.app-badge-soft-danger,
.app-badge-soft-warning,
.app-badge-soft-info {
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
  border-radius: var(--app-radius-pill);
  padding: 0.35rem 0.7rem;
  font-size: var(--app-font-size-xs);
  font-weight: 700;
}

.app-badge-soft-primary {
  background: var(--app-primary-soft);
  color: var(--app-primary);
}

.app-badge-soft-success {
  background: var(--app-success-soft);
  color: var(--app-success);
}

.app-badge-soft-danger {
  background: var(--app-danger-soft);
  color: var(--app-danger);
}

.app-badge-soft-warning {
  background: var(--app-warning-soft);
  color: var(--app-warning);
}

.app-badge-soft-info {
  background: var(--app-info-soft);
  color: var(--app-info);
}

.app-sidebar-link {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem 1rem;
  color: var(--app-text-secondary);
  border-radius: var(--app-radius-sm);
  text-decoration: none;
  font-weight: 600;
  transition: background var(--app-transition-fast), color var(--app-transition-fast);
}

.app-sidebar-link:hover {
  background: var(--app-surface-soft);
  color: var(--app-text-primary);
}

.app-sidebar-link.active {
  background: var(--app-primary-soft);
  color: var(--app-primary);
}

.app-form-control,
.form-control.app-form-control {
  border-radius: var(--app-radius-sm);
  border-color: var(--app-border);
  padding: 0.75rem 1rem;
}

.app-form-control:focus,
.form-control.app-form-control:focus {
  border-color: var(--app-primary);
  box-shadow: 0 0 0 4px rgba(37, 99, 235, 0.12);
}
```

---

## 12. Exemplo de `index.html`

O `index.html` deve ser simples, servindo como ponto de composição da aplicação.

```html
<!doctype html>
<html lang="pt-BR">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Enterprise Dashboard Template</title>

    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
      rel="stylesheet"
    />

    <link rel="stylesheet" href="assets/css/tokens.css" />
    <link rel="stylesheet" href="assets/css/base.css" />
    <link rel="stylesheet" href="assets/css/layout.css" />
    <link rel="stylesheet" href="assets/css/components.css" />
    <link rel="stylesheet" href="assets/css/dashboard.css" />
    <link rel="stylesheet" href="assets/css/utilities.css" />
  </head>

  <body>
    <div class="app-shell">
      <aside id="navigationSidebar" class="app-sidebar"></aside>

      <main class="app-main">
        <header id="globalHeader" class="app-global-header"></header>

        <section class="app-content">
          <div class="app-page-container">
            <div id="pageBreadcrumb"></div>
            <div id="pageHeader"></div>

            <div class="app-dashboard-grid">
              <div class="app-grid-span-3" id="featuredCard"></div>
              <div class="app-grid-span-3" id="metricCardPrimary"></div>
              <div class="app-grid-span-3" id="metricCardSecondary"></div>
              <div class="app-grid-span-3" id="metricCardTertiary"></div>
              <div class="app-grid-span-4" id="dataListCard"></div>
              <div class="app-grid-span-8" id="chartCard"></div>
              <div class="app-grid-span-8" id="categoryOverviewCard"></div>
            </div>
          </div>
        </section>
      </main>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/apexcharts"></script>
    <script src="https://unpkg.com/lucide@latest"></script>

    <script type="module" src="assets/js/pages/dashboard-page.js"></script>
  </body>
</html>
```

---

## 13. Componentes HTML parciais

### 13.1. `partials/page/page-header.html`

```html
<div class="app-page-header">
  <div>
    <h1 class="app-page-title" data-page-title>Dashboard</h1>
    <p class="app-page-subtitle" data-page-subtitle>
      Overview, indicators and operational insights.
    </p>
  </div>

  <div class="app-page-actions">
    <button type="button" class="btn app-btn-light">
      <i data-lucide="download"></i>
      Export
    </button>

    <button type="button" class="btn app-btn-primary">
      <i data-lucide="plus"></i>
      Add New
    </button>
  </div>
</div>
```

---

### 13.2. `partials/navigation/page-breadcrumb.html`

```html
<nav class="app-breadcrumb mb-3" aria-label="breadcrumb">
  <ol class="breadcrumb mb-0">
    <li class="breadcrumb-item"><a href="#">Home</a></li>
    <li class="breadcrumb-item"><a href="#">Dashboard</a></li>
    <li class="breadcrumb-item active" aria-current="page" data-current-page>Overview</li>
  </ol>
</nav>
```

---

### 13.3. `partials/cards/metric-card.html`

```html
<div class="card app-card app-metric-card h-100">
  <div class="card-body">
    <div class="d-flex align-items-start justify-content-between gap-3 mb-3">
      <div>
        <p class="app-card-subtitle mb-1" data-metric-label>Total Metric</p>
        <h3 class="app-card-title fs-3" data-metric-value>$650k</h3>
      </div>

      <span class="app-icon-box">
        <i data-lucide="trending-up"></i>
      </span>
    </div>

    <div class="app-sparkline-chart" data-chart="sparkline"></div>

    <p class="app-card-subtitle mt-3 mb-0" data-metric-caption>
      Compare to previous period
    </p>
  </div>
</div>
```

---

### 13.4. `partials/cards/chart-card.html`

```html
<div class="card app-card app-chart-card h-100">
  <div class="card-body">
    <div class="d-flex align-items-start justify-content-between gap-3 mb-4">
      <div>
        <h2 class="app-card-title">Performance Overview</h2>
        <p class="app-card-subtitle">Monthly comparison by category</p>
      </div>

      <div class="d-flex align-items-center gap-2">
        <span class="app-badge-soft-success">
          <i data-lucide="trending-up"></i>
          5.44%
        </span>

        <button class="btn app-btn-light btn-sm" type="button">
          Monthly
        </button>
      </div>
    </div>

    <div id="mainBarChart" class="app-chart-container"></div>
  </div>
</div>
```

---

### 13.5. `partials/cards/data-list-card.html`

```html
<div class="card app-card app-data-list-card h-100">
  <div class="card-body">
    <div class="d-flex align-items-start justify-content-between gap-3 mb-4">
      <div>
        <h2 class="app-card-title">Recent Items</h2>
        <p class="app-card-subtitle">Latest records from the selected period</p>
      </div>

      <button type="button" class="btn app-btn-light btn-sm" aria-label="Open options">
        <i data-lucide="more-horizontal"></i>
      </button>
    </div>

    <div class="app-data-list" data-list="recent-items">
      <div class="app-data-list-item d-flex align-items-center justify-content-between gap-3 py-3 border-bottom">
        <div class="d-flex align-items-center gap-3">
          <span class="app-icon-box">
            <i data-lucide="building-2"></i>
          </span>
          <div>
            <h3 class="fs-6 fw-bold mb-1">Example Item</h3>
            <p class="app-card-subtitle mb-0">#ITEM-0001</p>
          </div>
        </div>

        <div class="text-end">
          <strong>$210,000</strong>
          <div class="app-badge-soft-danger mt-1">10.6%</div>
        </div>
      </div>
    </div>
  </div>
</div>
```

---

### 13.6. `partials/cards/featured-card.html`

```html
<div class="card app-card app-featured-card h-100">
  <div class="card-body">
    <div class="d-flex align-items-start justify-content-between gap-3 mb-4">
      <div>
        <h2 class="app-card-title">Featured Item</h2>
        <p class="app-card-subtitle">Highlighted information</p>
      </div>

      <button type="button" class="btn app-btn-light btn-sm" aria-label="Open options">
        <i data-lucide="more-horizontal"></i>
      </button>
    </div>

    <div class="app-featured-panel mb-4">
      <div class="d-flex justify-content-between align-items-start mb-5">
        <span class="fw-semibold">Primary Label</span>
        <i data-lucide="credit-card"></i>
      </div>

      <div>
        <p class="mb-1 opacity-75">Owner</p>
        <h3 class="fs-5 mb-3">John Smith</h3>
        <p class="mb-0 letter-spacing-wide">•••• •••• •••• 1234</p>
      </div>
    </div>

    <p class="app-card-subtitle mb-1">Total Balance</p>
    <h3 class="fs-2 fw-bold mb-0">$1,480,000</h3>
  </div>
</div>
```

---

### 13.7. `partials/cards/category-overview-card.html`

```html
<div class="card app-card app-category-overview-card h-100">
  <div class="card-body">
    <div class="d-flex align-items-start justify-content-between gap-3 mb-4">
      <div>
        <h2 class="app-card-title">Category Overview</h2>
        <p class="app-card-subtitle">Distribution by category</p>
      </div>

      <button type="button" class="btn app-btn-primary btn-sm">
        <i data-lucide="plus"></i>
        Add New
      </button>
    </div>

    <div class="row g-3">
      <div class="col-md-4">
        <div class="app-category-box">
          <span class="app-icon-box mb-3">
            <i data-lucide="wallet"></i>
          </span>
          <h3 class="fs-6 fw-bold mb-1">Category A</h3>
          <p class="app-card-subtitle mb-0">$12,400</p>
        </div>
      </div>

      <div class="col-md-4">
        <div class="app-category-box">
          <span class="app-icon-box mb-3">
            <i data-lucide="shopping-bag"></i>
          </span>
          <h3 class="fs-6 fw-bold mb-1">Category B</h3>
          <p class="app-card-subtitle mb-0">$8,200</p>
        </div>
      </div>

      <div class="col-md-4">
        <div class="app-category-box">
          <span class="app-icon-box mb-3">
            <i data-lucide="activity"></i>
          </span>
          <h3 class="fs-6 fw-bold mb-1">Category C</h3>
          <p class="app-card-subtitle mb-0">$5,100</p>
        </div>
      </div>
    </div>
  </div>
</div>
```

---

## 14. JavaScript modular

### 14.1. `assets/js/core/component-loader.js`

```js
export async function loadComponent(selector, path) {
  const target = document.querySelector(selector);

  if (!target) {
    console.warn(`Component target not found: ${selector}`);
    return;
  }

  try {
    const response = await fetch(path);

    if (!response.ok) {
      throw new Error(`Failed to load component: ${path}`);
    }

    target.innerHTML = await response.text();
  } catch (error) {
    console.error(error);
    target.innerHTML = `
      <div class="alert alert-danger" role="alert">
        Unable to load component: ${path}
      </div>
    `;
  }
}

export async function loadComponents(components) {
  await Promise.all(
    components.map((component) => loadComponent(component.selector, component.path))
  );
}
```

---

### 14.2. `assets/js/ui/icons.js`

```js
export function initIcons() {
  if (!window.lucide) {
    console.warn('Lucide Icons is not available.');
    return;
  }

  window.lucide.createIcons({
    attrs: {
      'stroke-width': 2,
    },
  });
}
```

---

### 14.3. `assets/js/charts/chart-factory.js`

```js
export function createChart(selector, options) {
  const element = document.querySelector(selector);

  if (!element) {
    console.warn(`Chart container not found: ${selector}`);
    return null;
  }

  const chart = new ApexCharts(element, options);
  chart.render();
  return chart;
}
```

---

### 14.4. `assets/js/charts/sparkline-chart.js`

```js
import { createChart } from './chart-factory.js';

export function createSparklineChart(selector, seriesData, chartColor = '#2563eb') {
  return createChart(selector, {
    chart: {
      type: 'line',
      height: 70,
      sparkline: {
        enabled: true,
      },
      toolbar: {
        show: false,
      },
    },
    stroke: {
      curve: 'smooth',
      width: 3,
    },
    colors: [chartColor],
    series: [
      {
        name: 'Value',
        data: seriesData,
      },
    ],
    tooltip: {
      enabled: true,
    },
  });
}
```

---

### 14.5. `assets/js/charts/bar-chart.js`

```js
import { createChart } from './chart-factory.js';

export function createBarChart(selector, categories, series) {
  return createChart(selector, {
    chart: {
      type: 'bar',
      height: 320,
      toolbar: {
        show: false,
      },
    },
    plotOptions: {
      bar: {
        borderRadius: 8,
        columnWidth: '42%',
      },
    },
    dataLabels: {
      enabled: false,
    },
    grid: {
      borderColor: '#e5eaf1',
      strokeDashArray: 4,
    },
    xaxis: {
      categories,
      labels: {
        style: {
          colors: '#64748b',
        },
      },
    },
    yaxis: {
      labels: {
        style: {
          colors: '#64748b',
        },
      },
    },
    colors: ['#2563eb', '#10b981'],
    series,
    legend: {
      position: 'top',
      horizontalAlign: 'right',
    },
  });
}
```

---

### 14.6. `assets/js/pages/dashboard-page.js`

```js
import { loadComponents } from '../core/component-loader.js';
import { initIcons } from '../ui/icons.js';
import { createSparklineChart } from '../charts/sparkline-chart.js';
import { createBarChart } from '../charts/bar-chart.js';

const pageComponents = [
  {
    selector: '#navigationSidebar',
    path: 'partials/layout/navigation-sidebar.html',
  },
  {
    selector: '#globalHeader',
    path: 'partials/layout/global-header.html',
  },
  {
    selector: '#pageBreadcrumb',
    path: 'partials/navigation/page-breadcrumb.html',
  },
  {
    selector: '#pageHeader',
    path: 'partials/page/page-header.html',
  },
  {
    selector: '#featuredCard',
    path: 'partials/cards/featured-card.html',
  },
  {
    selector: '#metricCardPrimary',
    path: 'partials/cards/metric-card.html',
  },
  {
    selector: '#metricCardSecondary',
    path: 'partials/cards/metric-card.html',
  },
  {
    selector: '#metricCardTertiary',
    path: 'partials/cards/metric-card.html',
  },
  {
    selector: '#dataListCard',
    path: 'partials/cards/data-list-card.html',
  },
  {
    selector: '#chartCard',
    path: 'partials/cards/chart-card.html',
  },
  {
    selector: '#categoryOverviewCard',
    path: 'partials/cards/category-overview-card.html',
  },
];

async function initDashboardPage() {
  await loadComponents(pageComponents);

  initIcons();

  createSparklineChart('#metricCardPrimary [data-chart="sparkline"]', [12, 18, 14, 22, 19, 26, 30], '#2563eb');
  createSparklineChart('#metricCardSecondary [data-chart="sparkline"]', [8, 12, 11, 17, 15, 21, 25], '#10b981');
  createSparklineChart('#metricCardTertiary [data-chart="sparkline"]', [30, 24, 25, 19, 20, 16, 14], '#ef4444');

  createBarChart(
    '#mainBarChart',
    ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul'],
    [
      {
        name: 'Category A',
        data: [44, 55, 57, 56, 61, 58, 63],
      },
      {
        name: 'Category B',
        data: [35, 41, 36, 46, 45, 48, 52],
      },
    ]
  );
}

initDashboardPage();
```

---

## 15. Observação importante sobre `fetch()` e partials

Como os componentes HTML parciais são carregados com `fetch()`, o projeto deve ser executado por servidor local.

Não abrir o `index.html` diretamente com duplo clique.

Executar:

```bash
python -m http.server 8080
```

Acessar:

```text
http://localhost:8080
```

---

## 16. Instruções para `.github/copilot-instructions.md`

Criar ou atualizar o arquivo `.github/copilot-instructions.md` com o seguinte conteúdo:

```md
# Copilot Instructions — Generic Bootstrap 5 Enterprise Dashboard

## Project Goal

This project is a reusable enterprise dashboard/backoffice template built with HTML, CSS, JavaScript, Bootstrap 5, ApexCharts and Lucide Icons.

The project must not be coupled to a specific business domain such as finance, sales, CRM, operations or support.

All components must be named by structural role or visual purpose.

## Technology Stack

Use only:

- HTML5
- CSS3
- Vanilla JavaScript
- Bootstrap 5
- ApexCharts
- Lucide Icons

Do not introduce React, Vue, Angular, Tailwind, jQuery or additional UI frameworks unless explicitly requested.

## Bootstrap Usage

Use Bootstrap 5 as the structural and behavioral foundation.

Bootstrap should be used for:

- responsive grid;
- containers;
- rows and columns;
- layout utilities;
- dropdowns;
- modals;
- offcanvas;
- collapse;
- forms;
- tables;
- accessibility-friendly components.

Do not rely on default Bootstrap visual identity.

Avoid raw visual Bootstrap classes as the final design language:

- avoid plain `btn-primary` without a project class;
- avoid plain `card` without `app-card`;
- avoid plain `bg-primary`, `text-primary`, `alert-primary` as the main identity.

Every visible reusable component must use project-level design classes.

## CSS Rules

All custom CSS classes must use the `app-` prefix.

Use CSS variables from `assets/css/tokens.css` for:

- colors;
- shadows;
- border radius;
- typography;
- spacing;
- layout dimensions;
- transitions.

Do not hardcode repeated visual values across files.

## Component Naming Rules

Name components by responsibility, not by sample data or business domain.

Avoid:

- finance-header.html
- cashflow-card.html
- transactions-card.html
- sales-widget.html
- customer-list.html

Use:

- page-header.html
- chart-card.html
- data-list-card.html
- metric-card.html
- featured-card.html
- navigation-sidebar.html
- global-header.html

## JavaScript Rules

Use ES modules.

Separate JavaScript by responsibility:

- component loading;
- page initialization;
- icons;
- sidebar behavior;
- theme behavior;
- chart rendering;
- data/mock configuration.

Do not place all scripts in `index.html`.

## ApexCharts Rules

All chart creation must go through reusable chart modules.

Use:

- chart-factory.js
- sparkline-chart.js
- bar-chart.js
- area-chart.js
- donut-chart.js

Do not instantiate ApexCharts directly inside HTML.

## Lucide Rules

Use Lucide Icons through `data-lucide` attributes.

Initialize icons after loading partial HTML components.

Use standard icon wrapper classes:

- app-icon
- app-icon-box
- app-icon-action
- app-icon-muted

## Accessibility Rules

Use semantic HTML whenever possible.

All interactive elements must be keyboard accessible.

Buttons must have accessible labels when they only contain icons.

Use `aria-label` for icon-only buttons.

Use proper heading hierarchy.

## Refactoring Rules

When refactoring:

1. Preserve visual behavior.
2. Rename domain-specific components to generic names.
3. Extract reusable partials.
4. Move repeated styles to CSS tokens and component classes.
5. Move chart logic to chart modules.
6. Keep Bootstrap as foundation.
7. Ensure the final UI looks like a custom enterprise product, not default Bootstrap.
```

---

## 17. Arquivo `AGENTS.md`

Criar o arquivo `AGENTS.md` na raiz do projeto.

```md
# Agents — Bootstrap 5 Generic Design System

This project uses specialized Copilot agents to maintain a reusable enterprise dashboard/backoffice template.

## Agent List

1. Agent Orchestrator
2. Design System Agent
3. Bootstrap Layout Agent
4. HTML Refactor Agent
5. JavaScript UI Agent
6. Chart Agent
7. Accessibility Agent
8. QA Review Agent

## Coordination Rules

- The Agent Orchestrator plans the work and delegates tasks.
- The Design System Agent owns CSS tokens and visual consistency.
- The Bootstrap Layout Agent owns responsive layout and Bootstrap usage.
- The HTML Refactor Agent owns partial extraction and semantic markup.
- The JavaScript UI Agent owns component loading and UI behavior.
- The Chart Agent owns ApexCharts integration.
- The Accessibility Agent reviews keyboard navigation, ARIA and semantic HTML.
- The QA Review Agent validates final consistency, naming and maintainability.

## Shared Constraints

- Do not introduce new frameworks.
- Do not couple component names to business domains.
- Use generic naming based on structure or visual responsibility.
- Use Bootstrap for structure, not final visual identity.
- Use `app-` prefix for all custom CSS classes.
- Use CSS variables from `tokens.css`.
```

---

## 18. Agent: `.github/agents/agent-orchestrator.md`

```md
# Agent Orchestrator

## Role

Coordinate the refactoring of the Bootstrap 5 dashboard into a generic reusable design system.

## Responsibilities

- Analyze the current project structure.
- Identify domain-specific component names.
- Plan the refactoring sequence.
- Delegate work to specialized agents.
- Ensure no agent introduces domain-specific coupling.
- Ensure final output remains HTML, CSS, JavaScript, Bootstrap 5, ApexCharts and Lucide.

## Execution Plan

1. Inspect current files.
2. Identify layout regions.
3. Identify reusable visual patterns.
4. Rename domain-specific files.
5. Extract partial HTML components.
6. Normalize CSS classes with `app-` prefix.
7. Extract CSS tokens.
8. Modularize JavaScript.
9. Validate charts.
10. Run accessibility and QA review.

## Done Criteria

- Layout is reusable.
- Components are generically named.
- CSS tokens are centralized.
- Bootstrap default visual identity is minimized.
- Charts are modular.
- Icons are standardized.
```

---

## 19. Agent: `.github/agents/design-system-agent.md`

```md
# Design System Agent

## Role

Own the visual system of the project.

## Responsibilities

- Maintain `assets/css/tokens.css`.
- Maintain visual consistency across cards, buttons, sidebar, topbar and forms.
- Ensure Bootstrap does not appear visually generic.
- Ensure all custom classes use the `app-` prefix.
- Avoid hardcoded repeated colors, shadows, radii and spacing.

## Rules

- Use CSS variables for design tokens.
- Prefer reusable component classes.
- Do not use Bootstrap classes as the final visual identity.
- Do not create one-off visual classes unless strictly necessary.

## Expected Files

- `assets/css/tokens.css`
- `assets/css/base.css`
- `assets/css/layout.css`
- `assets/css/components.css`
- `assets/css/dashboard.css`
- `assets/css/utilities.css`
```

---

## 20. Agent: `.github/agents/bootstrap-layout-agent.md`

```md
# Bootstrap Layout Agent

## Role

Own responsive layout using Bootstrap 5 and project layout CSS.

## Responsibilities

- Use Bootstrap grid correctly.
- Ensure responsive behavior for desktop, tablet and mobile.
- Maintain sidebar, topbar and content layout.
- Avoid unnecessary custom layout code when Bootstrap utilities are enough.
- Keep Bootstrap as structural foundation.

## Rules

- Use `.container`, `.row`, `.col-*`, `.d-flex`, `.gap-*`, `.align-items-*`, `.justify-content-*` where appropriate.
- Use custom classes for final visual styling.
- Do not overuse Bootstrap visual classes such as `bg-primary` or `text-primary`.

## Done Criteria

- Layout works at common breakpoints.
- Sidebar behaves correctly on smaller screens.
- Cards reflow cleanly.
- No horizontal overflow.
```

---

## 21. Agent: `.github/agents/html-refactor-agent.md`

```md
# HTML Refactor Agent

## Role

Extract and maintain reusable HTML partials.

## Responsibilities

- Split large HTML files into partials.
- Use semantic HTML.
- Rename domain-specific partials to generic structural names.
- Keep components reusable.
- Use data attributes for dynamic content where useful.

## Naming Rules

Avoid:

- finance-header.html
- cashflow-card.html
- transaction-list.html

Use:

- page-header.html
- chart-card.html
- data-list-card.html
- metric-card.html

## Done Criteria

- `index.html` is a composition shell.
- Components live under `partials/`.
- Component names describe structure or visual purpose.
- HTML is accessible and readable.
```

---

## 22. Agent: `.github/agents/javascript-ui-agent.md`

```md
# JavaScript UI Agent

## Role

Own UI behavior and page initialization using Vanilla JavaScript modules.

## Responsibilities

- Maintain component loading.
- Initialize icons after partials are loaded.
- Initialize sidebar behavior.
- Initialize dropdowns and UI interactions.
- Avoid placing large scripts inside HTML.

## Rules

- Use ES modules.
- Keep functions small and named clearly.
- Add error handling for component loading.
- Do not introduce jQuery.
- Do not introduce frontend frameworks.

## Expected Files

- `assets/js/core/component-loader.js`
- `assets/js/core/app-init.js`
- `assets/js/ui/icons.js`
- `assets/js/ui/sidebar.js`
- `assets/js/ui/dropdowns.js`
- `assets/js/ui/theme-toggle.js`
- `assets/js/pages/dashboard-page.js`
```

---

## 23. Agent: `.github/agents/chart-agent.md`

```md
# Chart Agent

## Role

Own ApexCharts integration.

## Responsibilities

- Create reusable chart modules.
- Keep chart configuration isolated.
- Avoid inline chart initialization in HTML.
- Use generic chart names, not domain-specific names.

## Naming Rules

Avoid:

- cashflow-chart.js
- sales-chart.js
- transaction-chart.js

Use:

- bar-chart.js
- sparkline-chart.js
- area-chart.js
- donut-chart.js
- chart-factory.js

## Done Criteria

- Charts render correctly.
- Chart modules are reusable.
- Chart containers are generic.
- Colors use Design System values where practical.
```

---

## 24. Agent: `.github/agents/accessibility-agent.md`

```md
# Accessibility Agent

## Role

Review accessibility, semantics and keyboard usability.

## Responsibilities

- Validate heading hierarchy.
- Ensure icon-only buttons have `aria-label`.
- Ensure navigation uses semantic elements.
- Ensure forms have labels or accessible names.
- Ensure contrast is acceptable.
- Ensure focus states are visible.

## Rules

- Prefer semantic HTML.
- Do not remove keyboard accessibility.
- Do not use clickable divs when buttons or links are appropriate.

## Done Criteria

- Main navigation is accessible.
- Buttons have accessible labels.
- Forms are labeled.
- Color is not the only indicator of status.
```

---

## 25. Agent: `.github/agents/qa-review-agent.md`

```md
# QA Review Agent

## Role

Perform final quality review after refactoring.

## Responsibilities

- Validate naming conventions.
- Validate reusable structure.
- Validate Bootstrap usage.
- Validate CSS prefix rules.
- Validate responsive layout.
- Validate absence of domain-specific coupling.
- Validate that no unnecessary frameworks were added.

## Checklist

- [ ] No domain-specific component names.
- [ ] All custom CSS classes use `app-` prefix.
- [ ] Bootstrap is used structurally.
- [ ] Visual identity is custom, not default Bootstrap.
- [ ] CSS tokens are centralized.
- [ ] JavaScript is modular.
- [ ] Charts are isolated.
- [ ] Icons are standardized.
- [ ] Layout works on desktop, tablet and mobile.
- [ ] `index.html` is not overloaded.
```

---

## 26. Arquivo `SKILLS.md`

```md
# Skills — Bootstrap 5 Generic Dashboard Template

This project uses the following skills:

1. Bootstrap 5 Design System
2. HTML Partials Refactor
3. CSS Token System
4. ApexCharts Integration
5. Lucide Icons Standard
6. Responsive Layout
7. Accessibility Review
8. Refactor Validation

Each skill defines a repeatable capability used by Copilot agents to update and maintain the project.
```

---

## 27. Skill: `skills/bootstrap5-design-system.md`

```md
# Skill — Bootstrap 5 Design System

## Purpose

Use Bootstrap 5 as a structural foundation while applying a custom enterprise visual identity.

## Rules

- Use Bootstrap grid, utilities and components when useful.
- Add project-specific classes for visual identity.
- Do not let the final UI look like default Bootstrap.
- Use CSS variables from `tokens.css`.
- All custom classes must use the `app-` prefix.

## Examples

Correct:

```html
<button class="btn app-btn-primary">Save</button>
<div class="card app-card">...</div>
```

Avoid:

```html
<button class="btn btn-primary">Save</button>
<div class="card">...</div>
```
```

---

## 28. Skill: `skills/html-partials-refactor.md`

```md
# Skill — HTML Partials Refactor

## Purpose

Split large HTML pages into reusable partial components.

## Rules

- Extract layout sections into `partials/layout/`.
- Extract cards into `partials/cards/`.
- Extract controls into `partials/controls/`.
- Extract page-level headers into `partials/page/`.
- Extract screen states into `partials/states/`.

## Naming

Use generic names:

- page-header.html
- metric-card.html
- chart-card.html
- data-list-card.html
- navigation-sidebar.html
- global-header.html

Do not use domain-specific names.
```

---

## 29. Skill: `skills/css-token-system.md`

```md
# Skill — CSS Token System

## Purpose

Centralize visual decisions through CSS variables.

## Token Categories

- backgrounds;
- text colors;
- semantic colors;
- borders;
- shadows;
- radius;
- typography;
- spacing;
- layout dimensions;
- transitions.

## Rules

- Do not duplicate color values repeatedly.
- Do not hardcode repeated shadows and radii.
- Prefer `var(--app-token-name)`.
- Add new tokens only when the value is reusable.
```

---

## 30. Skill: `skills/apexcharts-integration.md`

```md
# Skill — ApexCharts Integration

## Purpose

Standardize chart creation using reusable ApexCharts modules.

## Rules

- Use `chart-factory.js` to instantiate charts.
- Create specific modules by chart type.
- Do not create domain-specific chart modules.
- Keep chart containers generic.
- Initialize charts after partials are loaded.

## Recommended Modules

- chart-factory.js
- sparkline-chart.js
- bar-chart.js
- area-chart.js
- donut-chart.js
```

---

## 31. Skill: `skills/lucide-icons-standard.md`

```md
# Skill — Lucide Icons Standard

## Purpose

Standardize icon usage with Lucide Icons.

## Rules

- Use `<i data-lucide="icon-name"></i>`.
- Initialize icons after partials are loaded.
- Use standard wrappers:
  - app-icon-box
  - app-icon-action
  - app-icon-muted
- Icon-only buttons must have `aria-label`.
```

---

## 32. Skill: `skills/responsive-layout.md`

```md
# Skill — Responsive Layout

## Purpose

Ensure the layout works across desktop, tablet and mobile.

## Rules

- Use Bootstrap breakpoints where possible.
- Use CSS grid for dashboard card composition when appropriate.
- Avoid horizontal overflow.
- Collapse or hide sidebar on smaller screens.
- Ensure cards stack properly on mobile.

## Validation

Check:

- 1440px desktop
- 1200px laptop
- 992px tablet landscape
- 768px tablet portrait
- 375px mobile
```

---

## 33. Skill: `skills/accessibility-review.md`

```md
# Skill — Accessibility Review

## Purpose

Review the interface for basic accessibility and semantic correctness.

## Rules

- Use semantic HTML.
- Use accessible labels.
- Ensure keyboard navigation.
- Ensure icon-only buttons have `aria-label`.
- Maintain visible focus states.
- Avoid using only color to communicate status.
```

---

## 34. Skill: `skills/refactor-validation.md`

```md
# Skill — Refactor Validation

## Purpose

Validate whether the refactor preserved behavior and improved reuse.

## Checklist

- [ ] Existing visual layout was preserved or improved.
- [ ] Component names are generic.
- [ ] No domain-specific file names remain.
- [ ] CSS variables are used consistently.
- [ ] Custom classes use `app-` prefix.
- [ ] JavaScript modules are separated by responsibility.
- [ ] Charts render correctly.
- [ ] Icons render correctly.
- [ ] Layout is responsive.
- [ ] Project runs through local server.
```

---

## 35. Prompt operacional para usar no Copilot Agent

Usar este prompt no Copilot Agent para executar a refatoração:

```md
Refatore este projeto HTML/CSS/JavaScript com Bootstrap 5, ApexCharts e Lucide Icons para uma estrutura genérica e reutilizável de Design System para dashboards e backoffices corporativos.

Objetivos obrigatórios:

1. Manter a stack atual:
   - HTML5
   - CSS3
   - JavaScript Vanilla
   - Bootstrap 5
   - ApexCharts
   - Lucide Icons

2. Usar Bootstrap 5 apenas como base estrutural e comportamental.
   A identidade visual final deve ser customizada com classes próprias do projeto.

3. Remover nomes acoplados ao domínio financeiro ou qualquer domínio específico.
   Substituir nomes como:
   - finance-header.html
   - cashflow-card.html
   - transaction-card.html
   - transaction-list-card.html

   Por nomes genéricos como:
   - page-header.html
   - chart-card.html
   - metric-card.html
   - data-list-card.html
   - featured-card.html

4. Criar ou ajustar a estrutura de pastas:
   - partials/layout
   - partials/navigation
   - partials/page
   - partials/cards
   - partials/controls
   - partials/states
   - assets/css
   - assets/js/core
   - assets/js/ui
   - assets/js/charts
   - assets/js/pages

5. Criar ou atualizar os arquivos CSS:
   - tokens.css
   - base.css
   - layout.css
   - components.css
   - dashboard.css
   - utilities.css

6. Todas as classes customizadas devem usar prefixo `app-`.

7. Evitar aparência padrão de Bootstrap.
   Não usar `.card`, `.btn-primary`, `.bg-primary`, `.text-primary` como identidade visual final sem classes customizadas do projeto.

8. Modularizar JavaScript:
   - component-loader.js
   - app-init.js
   - icons.js
   - sidebar.js
   - theme-toggle.js
   - chart-factory.js
   - sparkline-chart.js
   - bar-chart.js
   - dashboard-page.js

9. Padronizar ApexCharts:
   - nenhum gráfico deve ser inicializado diretamente no HTML;
   - gráficos devem ser criados por módulos reutilizáveis;
   - nomes dos módulos devem ser genéricos por tipo de gráfico.

10. Padronizar Lucide Icons:
    - usar `data-lucide`;
    - inicializar ícones após carregar partials;
    - botões somente com ícone devem ter `aria-label`.

11. Criar ou atualizar:
    - `.github/copilot-instructions.md`
    - `AGENTS.md`
    - `SKILLS.md`
    - arquivos em `.github/agents/`
    - arquivos em `skills/`

12. Ao final, valide:
    - responsividade;
    - nomenclatura genérica;
    - ausência de acoplamento ao domínio;
    - consistência visual;
    - acessibilidade básica;
    - renderização dos gráficos;
    - renderização dos ícones.

Não introduza React, Vue, Angular, Tailwind, jQuery ou bibliotecas adicionais.
```

---

## 36. Checklist final de aceite

Antes de considerar a refatoração concluída, validar:

```md
## Estrutura

- [ ] `index.html` atua como composição principal, não como arquivo gigante.
- [ ] Componentes HTML foram extraídos para `partials/`.
- [ ] Arquivos estão organizados por responsabilidade.
- [ ] Componentes possuem nomes genéricos.

## Naming

- [ ] Não existem arquivos com nomes ligados ao domínio financeiro.
- [ ] Não existem nomes como `cashflow`, `finance`, `transaction` em componentes estruturais.
- [ ] Nomes indicam função estrutural ou finalidade visual.

## CSS

- [ ] `tokens.css` centraliza decisões visuais.
- [ ] Classes customizadas usam prefixo `app-`.
- [ ] Bootstrap não define sozinho a aparência final.
- [ ] Cards, botões, badges, sidebar e topbar têm identidade própria.

## JavaScript

- [ ] JavaScript está modularizado.
- [ ] Component loader possui tratamento de erro.
- [ ] Ícones são inicializados após carregamento dos partials.
- [ ] Gráficos são criados por módulos reutilizáveis.

## Bootstrap

- [ ] Bootstrap é usado para grid e comportamento.
- [ ] Componentes Bootstrap recebem classes próprias do projeto.
- [ ] O layout final não parece Bootstrap padrão.

## ApexCharts

- [ ] Gráficos renderizam corretamente.
- [ ] Não há inicialização inline de gráficos no HTML.
- [ ] Módulos de gráficos são genéricos.

## Lucide

- [ ] Ícones renderizam corretamente.
- [ ] Botões de ícone possuem `aria-label`.
- [ ] Ícones usam classes padronizadas.

## Responsividade

- [ ] Layout funciona em desktop.
- [ ] Layout funciona em tablet.
- [ ] Layout funciona em mobile.
- [ ] Não existe overflow horizontal indevido.

## Acessibilidade

- [ ] Estrutura usa HTML semântico.
- [ ] Navegação principal é identificável.
- [ ] Botões são acessíveis por teclado.
- [ ] Estados visuais não dependem somente de cor.
```

---

## 37. Definition of Done

A refatoração estará concluída quando:

1. O projeto continuar executando localmente.
2. O layout visual estiver preservado ou melhorado.
3. O projeto estiver menos acoplado a um domínio específico.
4. Os componentes estiverem nomeados por função estrutural ou finalidade visual.
5. O Bootstrap for usado como fundação, não como identidade visual final.
6. O Design System estiver centralizado em tokens CSS.
7. O JavaScript estiver modularizado.
8. Os gráficos ApexCharts estiverem isolados em módulos.
9. Os ícones Lucide estiverem padronizados.
10. A estrutura puder ser reaproveitada em outros projetos de dashboard/backoffice.

---

## 38. Resumo da decisão arquitetural

A escolha recomendada para este projeto é:

```text
Bootstrap 5
+ CSS variables próprias
+ Design System com prefixo app-
+ HTML partials reutilizáveis
+ JavaScript Vanilla modular
+ ApexCharts isolado por tipo de gráfico
+ Lucide Icons padronizado
```

Essa abordagem mantém a simplicidade para times com maior experiência em backend, preserva facilidade de manutenção e permite construir uma interface moderna, com aparência profissional e menos dependente da identidade visual padrão do Bootstrap.

# Engenharia de Dados com IA — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build 20 HTML pages (landing + 3 trilha indexes + 16 modules) following INEMA.CLUB format and publish to GitHub Pages at `inematds/engdadosai`.

**Architecture:** Static HTML-only site using Tailwind CDN. No build step. All pages self-contained with inline CSS and JS. Images from `/doc/` referenced via relative paths. Published to GitHub Pages on `main` branch.

**Tech Stack:** HTML5, Tailwind CSS (CDN), Vanilla JS, Inter font (Google Fonts), GitHub Pages

**Content source:** `/home/nmaldaner/projetos/engdadosai/doc/dataeng (1).txt` (main transcript) + `/doc/Texto colado (1).txt` (skills transcript) + 10 infographics in `/doc/*.png`

**MASTER reference:** `/home/nmaldaner/.claude/skills/formato-curso/references/MASTER_COMPLETO.md`

---

## File Map

```
engdadosai/
├── index.html                        # Landing page (all 3 trilhas)
├── curso/
│   ├── trilha1/                      # Emerald — Fundamentos
│   │   ├── index.html
│   │   ├── modulo-1-1.html           # O Que é Engenharia de Dados
│   │   ├── modulo-1-2.html           # O Stack Completo
│   │   ├── modulo-1-3.html           # A Pirâmide de Dados
│   │   └── modulo-1-4.html           # Discreto vs Contínuo
│   ├── trilha2/                      # Blue — Dicas e Procedimentos
│   │   ├── index.html
│   │   ├── modulo-2-1.html           # Auditoria de 4 Eixos
│   │   ├── modulo-2-2.html           # A Regra das 100 Linhas
│   │   ├── modulo-2-3.html           # De Disparado para Unificado
│   │   ├── modulo-2-4.html           # Tabelas-Resumo + DuckDB
│   │   ├── modulo-2-5.html           # Monitoramento e Gestão
│   │   └── modulo-2-6.html           # Painel de Alertas
│   └── trilha3/                      # Purple — Visão Avançada
│       ├── index.html
│       ├── modulo-3-1.html           # Skills Lean-Down
│       ├── modulo-3-2.html           # Devemos Construir um Sistema?
│       ├── modulo-3-3.html           # Data Dictionary
│       ├── modulo-3-4.html           # Text-to-SQL
│       ├── modulo-3-5.html           # Primitivos Corretos
│       └── modulo-3-6.html           # Enterprise vs PME
└── doc/                              # Source images (already exists)
```

---

## Design Rules (from MASTER_COMPLETO.md)

| Rule | Value |
|------|-------|
| Trilha 1 color | `emerald` — `text-emerald-400`, `bg-emerald-500/20`, `border-emerald-500/30` |
| Trilha 2 color | `blue` — `text-blue-400`, `bg-blue-500/20`, `border-blue-500/30` |
| Trilha 3 color | `purple` — `text-purple-400`, `bg-purple-500/20`, `border-purple-500/30` |
| Topic indicators | Number in circle `<span class="w-6 h-6 rounded-full ...">` — never arrow |
| Buttons | `justify-start` — never `justify-center` |
| Module title | `text-2xl font-bold` |
| Min topics/module | 6 |
| Sections/topic | 3: "O que é / Por que aprender / Conceitos-chave" |
| INEMA.CLUB link | `text-sky-400` present on every page |
| Quick nav | Required in every trilha index, between header and "Conteúdo detalhado" |
| Modal | `<iframe src="modulo-X-X.html">` — never duplicate content |
| "Ver Completo" | Required on every module card |
| Light mode CSS | Full block on every page (base + accent + remove gradient + specials + nav) |

---

## Light Mode CSS Blocks (copy exactly)

### Trilha 1 — Emerald
```css
html:not(.dark) .text-emerald-400 { color: #059669; }
html:not(.dark) .bg-emerald-500\/20 { background-color: rgba(5, 150, 105, 0.12); }
html:not(.dark) .bg-emerald-500\/10 { background-color: rgba(5, 150, 105, 0.08); }
html:not(.dark) .border-emerald-500\/30 { border-color: rgba(5, 150, 105, 0.25); }
html:not(.dark) .hover\:bg-emerald-500\/30:hover { background-color: rgba(5, 150, 105, 0.18); }
```

### Trilha 2 — Blue
```css
html:not(.dark) .text-blue-400 { color: #2563eb; }
html:not(.dark) .bg-blue-500\/20 { background-color: rgba(37, 99, 235, 0.12); }
html:not(.dark) .bg-blue-500\/10 { background-color: rgba(37, 99, 235, 0.08); }
html:not(.dark) .border-blue-500\/30 { border-color: rgba(37, 99, 235, 0.25); }
html:not(.dark) .hover\:bg-blue-500\/30:hover { background-color: rgba(37, 99, 235, 0.18); }
```

### Trilha 3 — Purple
```css
html:not(.dark) .text-purple-400 { color: #7c3aed; }
html:not(.dark) .bg-purple-500\/20 { background-color: rgba(124, 58, 237, 0.12); }
html:not(.dark) .bg-purple-500\/10 { background-color: rgba(124, 58, 237, 0.08); }
html:not(.dark) .border-purple-500\/30 { border-color: rgba(124, 58, 237, 0.25); }
html:not(.dark) .hover\:bg-purple-500\/30:hover { background-color: rgba(124, 58, 237, 0.18); }
```

---

## Task 1: Git Setup + GitHub Pages

**Files:**
- Create: `.github/workflows/pages.yml` (optional, main branch publishes directly)

- [ ] Init git repo
```bash
cd /home/nmaldaner/projetos/engdadosai
git init
git remote add origin https://github.com/inematds/engdadosai.git
```

- [ ] Create directory structure
```bash
mkdir -p curso/trilha1 curso/trilha2 curso/trilha3
```

- [ ] Create initial commit with spec
```bash
git add docs/
git commit -m "docs: add spec and design plan"
```

---

## Task 2: Landing Page (index.html)

**Files:**
- Create: `index.html`

- [ ] Create `index.html` — landing page showing all 3 trilhas as cards

Content:
- Hero: "Engenharia de Dados com IA" + tagline "A fundação que todo sistema de IA precisa"
- 3 trilha cards (emerald, blue, purple) linking to each `curso/trilha*/index.html`
- Each card shows: título, descrição, nº de módulos, nível

Full `<head>` (base HTML from MASTER Sec. 8.1):
```html
<!DOCTYPE html>
<html lang="pt-BR" class="dark">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Engenharia de Dados com IA | INEMA.CLUB</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: { extend: { colors: { primary: '#FACC15', dark: { 900: '#111827', 800: '#1f2937', 700: '#374151', 600: '#4b5563' } } } }
    }
  </script>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <style>
    body { font-family: 'Inter', sans-serif; }
    .dark body { background-color: #111827; }
    html:not(.dark) body { background-color: #f8fafc; }
    html:not(.dark) .bg-dark-900 { background-color: #ffffff; }
    html:not(.dark) .bg-dark-800 { background-color: #f9fafb; }
    html:not(.dark) .bg-dark-700 { background-color: #f3f4f6; }
    html:not(.dark) .bg-dark-600 { background-color: #e5e7eb; }
    html:not(.dark) .text-neutral-100 { color: #111827; }
    html:not(.dark) .text-neutral-300 { color: #4b5563; }
    html:not(.dark) .text-neutral-400 { color: #6b7280; }
    html:not(.dark) .border-dark-600 { border-color: #d1d5db; }
    html:not(.dark) [class*="bg-gradient-to"] { background-image: none !important; }
    html:not(.dark) .text-primary { color: #a16207; }
    html:not(.dark) .text-sky-400 { color: #0369a1; }
    html:not(.dark) .text-yellow-400 { color: #a16207; }
    html:not(.dark) .hover\:text-sky-300:hover { color: #0284c7; }
    html:not(.dark) .bg-dark-900\/95 { background-color: rgba(255, 255, 255, 0.95); }
    /* All trilha hover colors for landing */
    html:not(.dark) .hover\:text-emerald-400:hover { color: #059669; }
    html:not(.dark) .hover\:bg-emerald-500\/10:hover { background-color: rgba(5, 150, 105, 0.08); }
    html:not(.dark) .group:hover .group-hover\:text-emerald-400 { color: #059669; }
    html:not(.dark) .hover\:text-blue-400:hover { color: #2563eb; }
    html:not(.dark) .hover\:bg-blue-500\/10:hover { background-color: rgba(37, 99, 235, 0.08); }
    html:not(.dark) .group:hover .group-hover\:text-blue-400 { color: #2563eb; }
    html:not(.dark) .hover\:text-purple-400:hover { color: #7c3aed; }
    html:not(.dark) .hover\:bg-purple-500\/10:hover { background-color: rgba(124, 58, 237, 0.08); }
    html:not(.dark) .group:hover .group-hover\:text-purple-400 { color: #7c3aed; }
  </style>
</head>
```

Nav: logo "🏗️ Eng. Dados com IA" + INEMA.CLUB link + theme toggle

Hero section:
```html
<header class="bg-gradient-to-br from-dark-800 via-dark-900 to-dark-900 py-20 border-b border-dark-600">
  <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
    <h1 class="text-4xl sm:text-5xl font-bold mb-6">🏗️ Engenharia de Dados com IA</h1>
    <p class="text-xl text-neutral-400 max-w-3xl mx-auto mb-4">
      A fundação que todo sistema de IA precisa — mas que 90% das pessoas ignora.
    </p>
    <p class="text-neutral-500">3 trilhas · 16 módulos · da base ao expert</p>
  </div>
</header>
```

3 trilha cards grid (each links to `curso/trilhaX/index.html`):
- T1 Emerald: "Fundamentos" — 4 módulos — Iniciante
- T2 Blue: "Dicas e Procedimentos Técnicos" — 6 módulos — Intermediário
- T3 Purple: "Visão Avançada para Experts" — 6 módulos — Avançado

- [ ] Add theme toggle JS (MASTER Sec. 9.2)
- [ ] Commit: `git add index.html && git commit -m "feat: landing page"`

---

## Task 3: Trilha 1 Index (curso/trilha1/index.html)

**Files:**
- Create: `curso/trilha1/index.html`

Color: emerald. Nav active: T1.

- [ ] Header (MASTER 7.4): "🧱 Fundamentos" badge TRILHA 1, stats: 4 módulos, 24 tópicos, ~2h, Iniciante

- [ ] Quick nav (MASTER 7.4b) — 4 anchor cards:
  - 1.1 🔍 O Que é Engenharia de Dados (~40 min)
  - 1.2 🏗️ O Stack Completo (~35 min)
  - 1.3 🔺 A Pirâmide de Dados (~30 min)
  - 1.4 📊 Discreto vs Contínuo (~30 min)

- [ ] 4 module cards (MASTER 7.3), each with `id="modulo-1-X"`, 6 expandable topics, buttons `justify-start`, "Ver Completo" link

Module 1-1 topics (expandable, 3 sections each):
1. 🔍 A definição real de Engenharia de Dados
2. 🏠 A metáfora do piso — "se o piso balança, a casa balança"
3. 🔬 DE vs Data Science vs Analytics Engineering
4. 🤖 Por que IA é inútil sem dados limpos
5. ⚠️ O que acontece quando você pula a DE
6. 👷 O papel do Engenheiro de Dados em projetos de IA hoje

Module 1-2 topics:
1. 📁 Camada 1: Fontes Brutas — o que são e onde vivem
2. 🔧 Camada 2: Engenharia de Dados — auditoria, limpeza, modelagem
3. 🗄️ Camada 3: Resumos + Warehousing — DuckDB, Supabase, Postgres
4. ⚙️ Camada 4: Skills, Regras e Orquestração — o Agentic OS
5. 🤖 Camada 5: Agentes, Briefs e Decisões — a parte visível
6. 📺 Por que 90% dos YouTubers só falam da camada 5

Module 1-3 topics:
1. 📁 Camada Base: Fontes Brutas (CSV, XLSX, PDF, exportações)
2. 🔍 Camada 2: Auditoria — o que checar antes de tudo
3. 📋 Camada 3: Snippets — amostras representativas
4. 📊 Camada 4: Resumos — tabelas fato e dimensão
5. 🧠 Topo: Briefs, Agentes e Decisões
6. 🔗 Como cada camada alimenta a próxima

Module 1-4 topics:
1. 📈 O que é dado contínuo e quando ele aparece
2. 🏷️ O que é dado discreto e seus exemplos reais
3. 🔬 Por que a distinção muda a auditoria que você faz
4. ➗ Operações válidas em cada tipo (min, max, median vs top-N)
5. ❓ Casos ambíguos: idade, tenure, dias desde último contato
6. 🤖 Como Claude Code trata cada tipo ao analisar dados

- [ ] Modals for each module (iframe, MASTER 9.3)
- [ ] Footer + JS (toggleTopic + theme + modal)
- [ ] Commit: `feat: trilha 1 index`

---

## Task 4: Trilha 1 Módulos (modulo-1-1.html até modulo-1-4.html)

**Files:**
- Create: `curso/trilha1/modulo-1-1.html`
- Create: `curso/trilha1/modulo-1-2.html`
- Create: `curso/trilha1/modulo-1-3.html`
- Create: `curso/trilha1/modulo-1-4.html`

Each module page structure (MASTER 6.2):
- Nav (emerald active, T1)
- Breadcrumb: Início / Trilha 1 — Fundamentos / Módulo 1.X
- Header (MASTER 7.5): badge MÓDULO 1.X, title, description, stats grid
- 6 topic sections (MASTER 7.7): large circle number, h2, intro paragraph, boxes
- Summary section (MASTER 7.14): checklist, next module button
- Footer + JS

**Modulo 1-1 — "O Que é Engenharia de Dados e Por Que Importa"**

Topic 1 (A definição real):
- Intro: "Engenharia de Dados é a disciplina de construir e manter os sistemas que coletam, armazenam, transformam e entregam dados de forma confiável para quem precisa deles."
- Box Conceito Principal: "O engenheiro de dados é o encanador do mundo digital. Ninguém pensa nele quando tudo funciona, mas quando o cano estoura, é o primeiro a ser chamado."
- Box Dica Prática: "Quando alguém fala em 'pipeline de dados', está falando do trabalho do engenheiro de dados — o fluxo que leva o dado bruto até onde ele tem valor."

Topic 2 (A metáfora do piso):
- Intro: "Existe uma imagem que resume tudo: se o piso balança, a casa balança."
- Infographic reference: `../../doc/ChatGPT Image 14 de mai. de 2026, 02_03_47.png`
- Box Conceito: "Seus agentes de IA são o último andar do prédio. Mas se a fundação — os dados — está podre, o prédio inteiro vai cair, não importa o quão sofisticado seja o telhado."
- Box Alerta: "Dado sujo não faz o agente parar. Faz ele responder com confiança — e errar."

Topic 3 (DE vs DS vs AE):
- Grid Fazer vs Evitar com exemplos de cada papel

Topic 4 (Por que IA é inútil sem dados limpos):
- Timeline com exemplos: agente mandado em wild goose chase, tokens gastos sifting through data sujo
- "Um agente é tão bom quanto o dado que você alimenta nele."

Topic 5 (O que acontece quando você pula):
- Box Alerta + casos reais da transcrição (empresa Dubai, Coca-Cola)

Topic 6 (O papel do Engenheiro hoje):
- Box Dados/Pesquisa: "Em 12-18 meses muitas funções admin serão automatizadas. Mas cybersecurity e data engineers continuarão empregados — porque a maioria das empresas não tem dados organizados o suficiente para que isso aconteça."

**Modulo 1-2 — "O Stack Completo"**

Topic 1 (Fontes Brutas):
- Box Conceito: planilhas, CSVs, APIs, bancos legados — o Wild West dos dados
- Infographic: `../../doc/ChatGPT Image 14 de mai. de 2026, 02_04_54.png`

Topic 2 (Camada DE):
- Box Timeline: auditoria → limpeza → normalização → modelagem

Topic 3 (Resumos + Warehousing):
- DuckDB, Supabase, PostgreSQL — quando usar cada um
- "Você não joga 10 milhões de linhas no contexto do Claude Code"

Topic 4 (Skills, Regras e Orquestração):
- O Agentic OS: skills como sugestões, hooks como regras determinísticas

Topic 5 (Agentes e Decisões):
- A camada que todos veem, a menos importante sozinha

Topic 6 (Por que 90% ignoram as outras camadas):
- Box Alerta: "Vibe coding sem DE é construir em areia."

**Modulo 1-3 — "A Pirâmide de Dados"**

Infographic: `../../doc/ChatGPT Image 14 de mai. de 2026, 02_03_55.png`

Topic 1-6: each level of pyramid with detail

**Modulo 1-4 — "Discreto vs Contínuo"**

Infographic: `../../doc/ChatGPT Image 14 de mai. de 2026, 02_04_09.png`

Topics follow the spec — continuous vs discrete with real examples from transcript (receita, tenure, horas, status, país)

- [ ] Build all 4 module pages
- [ ] Verify each has: nav, breadcrumb, header, 6 topics, summary, footer, JS
- [ ] Commit: `feat: trilha 1 modules`

---

## Task 5: Trilha 2 Index (curso/trilha2/index.html)

Color: blue. Nav active: T2. Stats: 6 módulos, 36 tópicos, ~3h30, Intermediário.

- [ ] Quick nav: 6 anchor cards (2-1 to 2-6)
- [ ] 6 module cards with topics (see spec for topic lists)
- [ ] Modals + JS
- [ ] Commit: `feat: trilha 2 index`

Module 2-1 topics (Auditoria 4 Eixos):
1. 📦 Eixo Volume — linhas, colunas, tamanho do arquivo
2. 🗂️ Eixo Schema — nomes, tipos, % de nulos
3. 🔬 Eixo Snippet — a amostra de 100 linhas
4. 📊 Eixo Distribuição — min, mediana, máx, categorias
5. 🏢 Walkthrough real: BrightPath Advisory
6. 💬 O prompt exato para Claude Code auditar

Module 2-2 topics (Regra das 100 Linhas):
1. 🎯 Por que 100 linhas e não 10 ou 1.000
2. 📋 Como amostrar: topo + meio aleatório + bordas estranhas
3. 🔍 O que procurar: duplicatas, NAs, tipos errados
4. 💥 Casos reais de anomalias encontradas em 100 linhas
5. 📈 Quando escalar para 1.000 ou 10.000 linhas
6. 🔒 Protegendo PII na amostra antes de compartilhar

Module 2-3 topics (Pipeline Passo a Passo):
1. 🗂️ O estado inicial: 5 fontes bagunçadas sem padrão
2. 1️⃣ Passo 1 — Auditar cada fonte individualmente
3. 2️⃣ Passo 2 — Normalizar tipos, datas e moedas
4. 3️⃣ Passo 3 — Criar IDs de junção entre tabelas
5. 4️⃣ Passo 4 — Eliminar colunas mortas de migrações antigas
6. 5️⃣ Passo 5 — Entregar o warehouse limpo e documentado

Module 2-4 topics (Tabelas-Resumo + DuckDB):
1. 📊 O que é uma tabela-resumo e por que ela existe
2. 🕐 Grain design — semana, mês, trimestre: como escolher
3. 📐 Dimensões vs Fatos — a estrutura de cada tabela
4. ⚙️ Passo a passo: carregar CSVs no DuckDB
5. 💬 Rodando SQL para responder perguntas de negócio
6. 🤖 Conectando o agente ao DuckDB — arquitetura mínima

Module 2-5 topics (Monitoramento):
1. 🕐 O campo `generated_at` — por que toda tabela-resumo precisa dele
2. 📝 Versionamento de resumos — como rastrear reprocessamentos
3. 🚨 Sinais de dado podre: como detectar antes que o agente detecte
4. 📋 SLA de dados — definindo frequência e qualidade mínima
5. 🤖 Automando reprocessamento com Claude Code
6. 📖 Documentando o pipeline para o próximo engenheiro

Module 2-6 topics (Painel e Alertas):
1. 👁️ O que monitorar: volume, frescor, schema drift, nulos
2. 🖥️ Construindo um painel simples sobre DuckDB ou Supabase
3. 🔔 Alertas por anomalia — threshold e lógica de disparo
4. 🤖 Integrando alertas com agentes (notificação automática)
5. 📊 Dashboard mínimo viável vs dashboard completo
6. 💡 Casos onde o painel salvou um projeto antes que explodisse

---

## Task 6: Trilha 2 Módulos (modulo-2-1.html até modulo-2-6.html)

Color: blue. Breadcrumb: Início / Trilha 2 — Técnica / Módulo 2.X

**Modulo 2-1 — Auditoria 4 Eixos:**
- Infographic: `../../doc/ChatGPT Image 14 de mai. de 2026, 02_04_02.png`
- Topic 5 deep: BrightPath Advisory walkthrough (Stripe JSON blob, HubSpot nulls, Time Tracker 3 sheets different formats, QuickBooks messy)
- Topic 6: exact prompt "read claude md and tell me what the five sources are and what is unusual about each one. Then run an audit pass on raw Stripe payments using the four axis framework. I want volume schema distribution in a 100-row snippet. Do not modify anything in raw."

**Modulo 2-2 — Regra das 100 Linhas:**
- Infographic: `../../doc/ChatGPT Image 14 de mai. de 2026, 02_04_16.png`
- Real anomalies: currency mixing (EUR/USD/JPY), JSON in cells, blank rows from migration, mismatched date formats

**Modulo 2-3 — Pipeline Passo a Passo:**
- Infographic: `../../doc/ChatGPT Image 14 de mai. de 2026, 02_04_29.png`
- Timeline component (MASTER 7.12) for the 5 steps
- Real BrightPath example: Stripe → normalize → HubSpot → normalize → merge

**Modulo 2-4 — Tabelas-Resumo + DuckDB:**
- Code examples for DuckDB SQL
- "Load all four into a single DuckDB database called engagement.duckdb at the root, and then run a query that returns the top five clients by revenue."
- Box Conceito: grain design — se o cliente pergunta por mês, o grain é mensal

**Modulo 2-5 — Monitoramento:**
- No infographic — use boxes and timeline
- Box Dica: "O generated_at é o seu GPS temporal. Sem ele, você não sabe se está olhando para dados de ontem ou de seis meses atrás."

**Modulo 2-6 — Painel e Alertas:**
- Box conceito: dashboard mínimo viável = 4 métricas: volume, frescor, nulos, schema
- Grid Fazer vs Evitar: alertas úteis vs alertas que ninguém lê

- [ ] Build all 6 module pages
- [ ] Commit: `feat: trilha 2 modules`

---

## Task 7: Trilha 3 Index (curso/trilha3/index.html)

Color: purple. Nav active: T3. Stats: 6 módulos, 36 tópicos, ~4h, Avançado.

- [ ] Quick nav: 6 anchor cards (3-1 to 3-6)
- [ ] 6 module cards with topics
- [ ] Modals + JS
- [ ] Commit: `feat: trilha 3 index`

Module 3-1 topics (Skills Lean-Down):
1. 🗃️ O problema do skill sprawl — 15 skills que se sobrepõem
2. 📂 Progressive disclosure — como segmentar um skill por seção
3. 🏷️ Nomes únicos e descrições trigger-heavy
4. 🔧 Consolidando skills sobrepostos em um único bem estruturado
5. 🤖 Testando skills com sub-agentes em paralelo
6. ✂️ O processo de lean-down: de 15 para 5 skills + 3 regras

Module 3-2 topics (Devemos Construir um Sistema?):
1. ❓ A pergunta central: vale responder mais de uma vez?
2. 🔄 A resposta muda conforme o negócio evolui?
3. 👥 Mais de uma pessoa (ou agente) vai usar isso?
4. 💰 O custo de sistemas prematuros: complexidade sem valor
5. 📜 Quando um script único é suficiente
6. 🌳 O decision tree completo — skill vs regra vs tabela vs sistema

Module 3-3 topics (Data Dictionary):
1. 📖 O que é um Data Dictionary e por que grandes empresas exigem
2. 🗂️ Campos essenciais: nome, tipo, formato, descrição, exemplo
3. 🤝 Como pedir o Data Dictionary a um cliente
4. 🤖 Alimentando Claude Code com o dicionário para auditar melhor
5. ✍️ Criando um Data Dictionary do zero com Claude Code
6. 📋 Data Dictionary como contrato entre engenheiro e agente

Module 3-4 topics (Text-to-SQL):
1. 💬 O que é Text-to-SQL e onde ele falha sem dados limpos
2. 🏗️ Arquitetura: agente → SQL → DuckDB → resposta
3. 🚫 Por que você não joga milhões de linhas no contexto
4. ✅ O prompt de auditoria como pré-requisito do Text-to-SQL
5. 💡 Exemplos reais: "top 5 clientes por receita" com Claude Code
6. ⚠️ Limites do Text-to-SQL e quando escalar para outra arquitetura

Module 3-5 topics (Primitivos Corretos):
1. ❌ O conceito de "wrong primitive" — ferramenta errada para o trabalho certo
2. ⚖️ Quando usar Skill vs Regra vs Hook vs Script Python
3. 🔄 Reverse meta prompting — melhorando um skill depois de uma sessão ruim
4. 🧪 O teste "run it cold" — como saber se o skill vai disparar certo
5. ⚡ Skill como sugestão vs Hook como regra determinística
6. 🔍 Auditando seu stack atual e corrigindo os primitivos errados

Module 3-6 topics (Enterprise vs PME):
1. 📊 A diferença de dados entre startup, PME e enterprise
2. 🏚️ Sistemas legados: Oracle, SAP, migrações de sistema A para B
3. 🔒 SOC 2 compliance e o que muda na engenharia de dados
4. 🌊 Big Data real: Apache Spark e quando ele é necessário
5. 🗄️ NoSQL vs SQL — quando cada um faz sentido
6. 🎯 O que esperar ao entrar em um projeto enterprise pela primeira vez

---

## Task 8: Trilha 3 Módulos (modulo-3-1.html até modulo-3-6.html)

Color: purple. Breadcrumb: Início / Trilha 3 — Avançada / Módulo 3.X

**Modulo 3-1 — Skills Lean-Down:**
- Infographic: `../../doc/ChatGPT Image 14 de mai. de 2026, 02_04_42.png`
- Visual: before (15 overlapping skills) → after (5 skills + 3 rules)
- From skills transcript: audit-csv, audit-excel, audit-source → one `audit-source <path>` skill

**Modulo 3-2 — Devemos Construir um Sistema?:**
- Infographic: `../../doc/ChatGPT Image 14 de mai. de 2026, 02_04_35.png`
- Decision tree as timeline (MASTER 7.12)
- "O custo de sistemas prematuros: maior complexidade > menos velocidade > menor valor"

**Modulo 3-3 — Data Dictionary:**
- No infographic — boxes
- Example data dictionary table: field name, type, format, size, description, example
- Box Dados/Pesquisa: "Em empresas maiores, o Data Dictionary é exigido por lei para compliance"
- Prompt example for Claude Code to create one

**Modulo 3-4 — Text-to-SQL:**
- Architecture diagram as box
- Exact prompt: "Load all four into DuckDB engagement.duckdb. Run query top 5 clients by revenue."
- Box Alerta: "Text-to-SQL sobre dados sujos = respostas confiantes sobre mentiras"

**Modulo 3-5 — Primitivos Corretos:**
- Grid comparing Skill / Regra / Hook / Script
- From skills transcript: reverse meta prompting prompt example
- Box Dica: "Ask Claude Code: 'Reflect on this session. Critique the skill against what it got wrong, then propose a concrete edit.'"

**Modulo 3-6 — Enterprise vs PME:**
- Timeline: startup → PME com funding → enterprise
- Box Dados/Pesquisa: "Coca-Cola = 10 bilhões de linhas de dados. Apache Spark obrigatório."
- Box Alerta: "Quando uma empresa vai de 100 para 1.000 funcionários, o dado reflete esse caos."

- [ ] Build all 6 module pages
- [ ] Commit: `feat: trilha 3 modules`

---

## Task 9: GitHub Pages Publish

- [ ] Create GitHub Pages config (if needed)
```bash
# GitHub Pages serves from root of main branch
# No config needed — just push
```

- [ ] Final check — verify all links work:
```bash
# Check all href references exist
grep -r 'href="' /home/nmaldaner/projetos/engdadosai --include="*.html" | grep -v "http" | grep -v "#"
```

- [ ] Push to GitHub
```bash
git add -A
git commit -m "feat: complete course - 16 modules, 3 trilhas"
git branch -M main
git push -u origin main
```

- [ ] Enable GitHub Pages via API or gh CLI
```bash
gh api repos/inematds/engdadosai/pages \
  --method POST \
  -f source[branch]=main \
  -f source[path]=/ 2>/dev/null || echo "Pages already enabled or manual setup needed"
```

- [ ] Send Telegram notification
```bash
/home/nmaldaner/projetos/openpcbot/scripts/notify.sh "✅ Curso Engenharia de Dados com IA publicado!

🎓 16 módulos em 3 trilhas
🔗 https://inematds.github.io/engdadosai

📚 Trilha 1 - Fundamentos (4 módulos)
🔧 Trilha 2 - Técnica (6 módulos)  
🧠 Trilha 3 - Avançada (6 módulos)"
```

---

## Self-Review

**Spec coverage:**
- ✅ 20 pages: landing + 3 trilha indexes + 16 modules
- ✅ All 3 trilhas with correct colors (emerald/blue/purple)
- ✅ Min 6 topics per module
- ✅ 3 sections per topic (O que é / Por que / Conceitos-chave)
- ✅ Quick nav on every trilha index
- ✅ "Ver Completo" on every module card
- ✅ Modal with iframe on every index
- ✅ Light mode CSS on every page
- ✅ INEMA.CLUB link on every page
- ✅ Infographics mapped to correct modules
- ✅ GitHub Pages publish + Telegram notification

**No placeholders:** All module content specified with real text from transcripts.

**Type consistency:** All links use relative paths matching the file structure.

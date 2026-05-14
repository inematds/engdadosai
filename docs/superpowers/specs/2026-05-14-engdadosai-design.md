# Design Spec — Engenharia de Dados com IA
**Data:** 2026-05-14  
**Repo:** https://github.com/inematds/engdadosai  
**Publicação:** GitHub Pages

---

## Visão Geral

Curso técnico e profundo sobre Engenharia de Dados aplicada a sistemas de IA e Agentes. Construído no formato INEMA.CLUB com HTML estático publicado via GitHub Pages.

**Público-alvo:** Três perfis simultâneos, separados por trilha:
- Iniciantes em dados que querem entender a base antes de usar IA
- Praticantes técnicos que precisam de receitas e procedimentos prontos
- Experts que querem arquitetura avançada e visão de projetos reais

**Fonte de conteúdo:** Transcrições em `/doc/dataeng (1).txt` e `/doc/Texto colado (1).txt` + 10 infográficos em PT-BR já prontos.

---

## Arquitetura de Arquivos

```
engdadosai/
├── index.html                      # Landing page do curso
├── doc/                            # Ativos de conteúdo (imagens + transcrições)
└── curso/
    ├── trilha1/
    │   ├── index.html              # Index Trilha 1 — Fundamentos
    │   ├── modulo-1-1.html
    │   ├── modulo-1-2.html
    │   ├── modulo-1-3.html
    │   └── modulo-1-4.html
    ├── trilha2/
    │   ├── index.html              # Index Trilha 2 — Dicas e Procedimentos
    │   ├── modulo-2-1.html
    │   ├── modulo-2-2.html
    │   ├── modulo-2-3.html
    │   ├── modulo-2-4.html
    │   ├── modulo-2-5.html
    │   └── modulo-2-6.html
    └── trilha3/
        ├── index.html              # Index Trilha 3 — Visão Avançada
        ├── modulo-3-1.html
        ├── modulo-3-2.html
        ├── modulo-3-3.html
        ├── modulo-3-4.html
        ├── modulo-3-5.html
        └── modulo-3-6.html
```

**Total:** 1 landing + 3 index de trilha + 16 módulos = **20 páginas HTML**

---

## Trilhas e Módulos

### Trilha 1 — Fundamentos · Emerald

| Módulo | Título | Infográfico |
|--------|--------|-------------|
| 1-1 | O Que é Engenharia de Dados e Por Que Importa | `02_03_47`, `02_03_39` |
| 1-2 | O Stack Completo — As 5 Camadas do Agentic OS | `02_04_54`, `00_42_26` |
| 1-3 | A Pirâmide de Dados | `02_03_55` |
| 1-4 | Discreto vs Contínuo — As Lentes de Análise | `02_04_09` |

### Trilha 2 — Dicas e Procedimentos Técnicos · Blue

| Módulo | Título | Infográfico |
|--------|--------|-------------|
| 2-1 | Auditoria de 4 Eixos na Prática | `02_04_02` |
| 2-2 | A Regra das 100 Linhas — Amostragem que Revela Tudo | `02_04_16` |
| 2-3 | De Disparado para Unificado — Pipeline Passo a Passo | `02_04_29` |
| 2-4 | Tabelas-Resumo + DuckDB — Implementação Passo a Passo | `02_03_31` |
| 2-5 | Monitoramento e Gestão de Dados — Passo a Passo | — |
| 2-6 | Painel de Monitoramento e Alertas | — |

### Trilha 3 — Visão Avançada para Experts · Purple

| Módulo | Título | Infográfico |
|--------|--------|-------------|
| 3-1 | Skills Lean-Down — De 15 para 5 + 3 Regras | `02_04_42` |
| 3-2 | Devemos Construir um Sistema? | `02_04_35` |
| 3-3 | Data Dictionary — O Documento que Alimenta Agentes | — |
| 3-4 | Text-to-SQL — Agentes Conversando com Dados Limpos | — |
| 3-5 | Primitivos Corretos — Skill vs Regra vs Hook vs Script | — |
| 3-6 | Enterprise vs PME — Migrações, SOC 2 e Big Data | — |

---

## Design System

Formato INEMA.CLUB. Regras obrigatórias:

| Trilha | Cor | Classes Tailwind |
|--------|-----|-----------------|
| T1 Fundamentos | Emerald | `text-emerald-400`, `bg-emerald-500/20` |
| T2 Técnica | Blue | `text-blue-400`, `bg-blue-500/20` |
| T3 Avançada | Purple | `text-purple-400`, `bg-purple-500/20` |

- Mínimo 6 tópicos por módulo
- 3 seções por tópico: "O que é / Por que aprender / Conceitos-chave"
- Botões alinhados à esquerda (`justify-start`)
- Indicadores de tópico: número em círculo (não seta)
- Link INEMA.CLUB em `text-sky-400` em todas as páginas
- Navegação rápida obrigatória no index de cada trilha
- Botão "Ver Completo" em cada card de módulo
- Light mode CSS completo em todas as páginas
- Modal usa `<iframe src="modulo-X-X.html">` — nunca conteúdo duplicado

---

## Conteúdo por Módulo — Tópicos Mínimos

### Módulo 1-1 — O Que é Engenharia de Dados e Por Que Importa
1. A definição real de Engenharia de Dados (além do buzzword)
2. A metáfora do piso — "se o piso balança, a casa balança"
3. DE vs Data Science vs Analytics Engineering
4. Por que IA é inútil sem dados limpos
5. O que acontece quando você pula a DE (cases reais)
6. O papel do Engenheiro de Dados em projetos de IA hoje

### Módulo 1-2 — O Stack Completo
1. Camada 1: Fontes Brutas — o que são e onde vivem
2. Camada 2: Engenharia de Dados — auditoria, limpeza, modelagem
3. Camada 3: Resumos + Warehousing — DuckDB, Supabase, Postgres
4. Camada 4: Skills, Regras e Orquestração — o Agentic OS
5. Camada 5: Agentes, Briefs e Decisões — a parte visível
6. Por que 90% dos YouTubers só falam da camada 5

### Módulo 1-3 — A Pirâmide de Dados
1. Camada Base: Fontes Brutas (CSV, XLSX, PDF, exportações)
2. Camada 2: Auditoria — o que checar antes de tudo
3. Camada 3: Snippets — amostras representativas
4. Camada 4: Resumos — tabelas fato e dimensão
5. Topo: Briefs, Agentes e Decisões
6. Como cada camada alimenta a próxima

### Módulo 1-4 — Discreto vs Contínuo
1. O que é dado contínuo e quando ele aparece
2. O que é dado discreto e seus exemplos reais
3. Por que a distinção muda a auditoria que você faz
4. Operações válidas em cada tipo (min, max, median vs top-N)
5. Casos ambíguos: idade, tenure, dias desde último contato
6. Como Claude Code trata cada tipo ao analisar dados

### Módulo 2-1 — Auditoria de 4 Eixos na Prática
1. Eixo Volume — linhas, colunas, tamanho do arquivo
2. Eixo Schema — nomes, tipos, % de nulos
3. Eixo Snippet — a amostra de 100 linhas e o que ela revela
4. Eixo Distribuição — min, mediana, máx, categorias principais
5. Walkthrough real: BrightPath Advisory (Stripe, HubSpot, QuickBooks, Time Tracker)
6. O prompt exato para pedir a Claude Code fazer a auditoria

### Módulo 2-2 — A Regra das 100 Linhas
1. Por que 100 linhas e não 10 ou 1.000
2. Como amostrar: topo + meio aleatório + bordas estranhas
3. O que procurar: duplicatas, NAs, valores hard-coded, tipos errados
4. Casos reais de anomalias encontradas em 100 linhas
5. Quando escalar para 1.000 ou 10.000 linhas
6. Protegendo PII na amostra antes de compartilhar

### Módulo 2-3 — De Disparado para Unificado
1. O estado inicial: 5 fontes bagunçadas sem padrão
2. Passo 1 — Auditar cada fonte individualmente
3. Passo 2 — Normalizar tipos, datas e moedas
4. Passo 3 — Criar IDs de junção entre tabelas
5. Passo 4 — Eliminar colunas mortas de migrações antigas
6. Passo 5 — Entregar o warehouse limpo e documentado

### Módulo 2-4 — Tabelas-Resumo + DuckDB
1. O que é uma tabela-resumo e por que ela existe
2. Grain design — semana, mês, trimestre: como escolher
3. Dimensões vs Fatos — a estrutura de cada tabela
4. Passo a passo: carregar CSVs no DuckDB
5. Rodando SQL para responder perguntas de negócio
6. Conectando o agente ao DuckDB — arquitetura mínima

### Módulo 2-5 — Monitoramento e Gestão de Dados
1. O campo `generated_at` — por que toda tabela-resumo precisa dele
2. Versionamento de resumos — como rastrear reprocessamentos
3. Sinais de dado podre: como detectar antes que o agente detecte
4. SLA de dados — definindo frequência e qualidade mínima
5. Automando reprocessamento com Claude Code
6. Documentando o pipeline para o próximo engenheiro (ou agente)

### Módulo 2-6 — Painel de Monitoramento e Alertas
1. O que monitorar: volume, frescor, schema drift, nulos
2. Construindo um painel simples sobre DuckDB ou Supabase
3. Alertas por anomalia — threshold e lógica de disparo
4. Integrando alertas com agentes (notificação automática)
5. Dashboard mínimo viável vs dashboard completo
6. Casos onde o painel salvou um projeto antes que explodisse

### Módulo 3-1 — Skills Lean-Down
1. O problema do skill sprawl — 15 skills que se sobrepõem
2. Progressive disclosure — como segmentar um skill por seção
3. Nomes únicos e descrições trigger-heavy
4. Consolidando skills sobrepostos em um único bem estruturado
5. Testando skills com sub-agentes em paralelo
6. O processo de lean-down: de 15 para 5 skills + 3 regras

### Módulo 3-2 — Devemos Construir um Sistema?
1. A pergunta central: vale responder mais de uma vez?
2. A resposta muda conforme o negócio evolui?
3. Mais de uma pessoa (ou agente) vai usar isso?
4. O custo de sistemas prematuros: complexidade sem valor
5. Quando um script único é suficiente
6. O decision tree completo — skill vs regra vs tabela vs sistema

### Módulo 3-3 — Data Dictionary
1. O que é um Data Dictionary e por que grandes empresas exigem
2. Campos essenciais: nome, tipo, formato, descrição, exemplo
3. Como pedir o Data Dictionary a um cliente (e o que fazer se não existir)
4. Alimentando Claude Code com o dicionário para auditar melhor
5. Criando um Data Dictionary do zero com Claude Code
6. Data Dictionary como contrato entre engenheiro e agente

### Módulo 3-4 — Text-to-SQL com Agentes
1. O que é Text-to-SQL e onde ele falha sem dados limpos
2. Arquitetura: agente → SQL → DuckDB → resposta
3. Por que você não joga milhões de linhas no contexto
4. O prompt de auditoria como pré-requisito do Text-to-SQL
5. Exemplos reais: "top 5 clientes por receita" com Claude Code
6. Limites do Text-to-SQL e quando escalar para outra arquitetura

### Módulo 3-5 — Primitivos Corretos
1. O conceito de "wrong primitive" — ferramenta errada para o trabalho certo
2. Quando usar Skill vs Regra vs Hook vs Script Python
3. Reverse meta prompting — melhorando um skill depois de uma sessão ruim
4. O teste "run it cold" — como saber se o skill vai disparar certo
5. Skill como sugestão vs Hook como regra determinística
6. Auditando seu stack atual e corrigindo os primitivos errados

### Módulo 3-6 — Enterprise vs PME
1. A diferença de dados entre startup, PME e enterprise
2. Sistemas legados: Oracle, SAP, migrações de sistema A para B
3. SOC 2 compliance e o que muda na engenharia de dados
4. Big Data real: Apache Spark e quando ele é necessário
5. NoSQL vs SQL — quando cada um faz sentido
6. O que esperar ao entrar em um projeto enterprise pela primeira vez

---

## GitHub Pages

- Repositório: `inematds/engdadosai`
- Branch de publicação: `main` (raiz `/`)
- Sem framework, sem build step — HTML puro com Tailwind CDN
- Imagens do `/doc` referenciadas com caminho relativo

---

## Restrições

- Sem conteúdo além do que está nas transcrições e infográficos do `/doc`
- Sem frameworks JS (React, Vue) — HTML/CSS/JS vanilla
- Tailwind via CDN
- Cada módulo é autocontido — sem dependências entre páginas
- Mínimo absoluto: 6 tópicos por módulo, 3 seções por tópico

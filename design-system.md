# Design System — Lais Marques Studio da Beleza

Sistema visual da apostila "Design de Sobrancelhas Profissional — Método Lais Marques" e dos materiais complementares (digital e impresso).

Cores e proporções foram amostradas diretamente dos arquivos em `marca-lais-marques/` e validadas contra o brand board (`fef8e564-…png`). Fontes e estrutura cruzadas com a skill `ui-ux-pro-max`.

---

## 1. DNA da marca

| Eixo | Direção | Anti-direção |
|---|---|---|
| Mood | Premium, acolhedor, técnico | Infantil, "estética Canva", rosa choque |
| Vocabulário visual | Serifa editorial + cobre/champanhe + muito espaço | Ícones flat, gradientes neon, decoração sem função |
| Tom de voz visual | Professora calma e segura | Influencer entusiasmada |
| Referência mental | Editorial de spa premium, livro técnico bonito | Catálogo de procedimento, flyer promocional |

Os três pilares operacionais (do PRODUCT.md) traduzidos em regra de design:

1. **Clareza antes de impressionar** → hierarquia tipográfica forte, nunca enfeite que tira leitura.
2. **Premium sem frieza** → serifa elegante + cobre quente, nunca preto puro #000.
3. **Naturalidade como valor** → fotos sem filtro saturado, paleta terrosa, nunca cor artificial.

---

## 2. Tokens de cor

Amostrados diretamente dos PNGs do logo. Use os semânticos no produto; os primitivos só existem para alimentar os semânticos.

### 2.1 Primitivos

```css
/* Metal — gradiente do monograma LM */
--gold-50:  #F5C79C;  /* highlight do metal */
--gold-100: #E3B07F;
--gold-300: #B67750;  /* base — fundo "caramelo vivo" */
--gold-500: #9F7657;  /* mid — fundo "caramelo suave" */
--gold-700: #7A4F2C;
--gold-900: #653D1F;  /* deep — sombra do metal */

/* Cremes — derivados do champagne do metal */
--cream-50:  #FAF1E5;  /* page bg, light mode */
--cream-100: #F1E5D2;
--cream-200: #E8D4B6;
--cream-300: #D4B896;  /* divisores, texto secundário */

/* Tintas — escuros sempre quentes, nunca #000 puro */
--ink-900: #0C0D0D;  /* near-black do brand board */
--ink-800: #1C1C1C;  /* corpo de texto principal */
--ink-700: #2B2B2B;
--ink-500: #5C544C;  /* texto secundário sobre creme */
--ink-300: #8E867D;  /* legendas */

--white: #FFFFFF;
```

### 2.2 Semânticos (use só estes no produto)

```css
/* Light (apostila padrão, fundo creme) */
--bg:              var(--cream-50);    /* #FAF1E5 */
--surface:         var(--white);
--surface-muted:   var(--cream-100);
--text:            var(--ink-800);     /* corpo */
--text-muted:      var(--ink-500);     /* legendas */
--text-subtle:     var(--ink-300);
--brand:           var(--gold-300);    /* cobre vivo */
--brand-deep:      var(--gold-900);    /* sublinhados, marcadores */
--brand-soft:      var(--gold-500);
--divider:         var(--cream-300);
--accent-on-brand: var(--cream-50);    /* texto sobre cobre */

/* Dark (capa, contracapa, slides) */
--bg-dark:         var(--ink-900);
--text-on-dark:    var(--cream-50);
--brand-on-dark:   var(--gold-100);    /* metal mais claro pra contraste AA */
```

### 2.3 Contraste validado (WCAG 2.2)

| Combinação | Ratio | Uso |
|---|---|---|
| `--ink-800` sobre `--cream-50` | ≈ 14.2:1 | Corpo de texto. AAA. |
| `--gold-900` sobre `--cream-50` | ≈ 9.1:1 | Subtítulos em cobre. AAA. |
| `--gold-300` sobre `--cream-50` | ≈ 3.8:1 | **Só para texto ≥18pt bold** (AA Large). Nunca corpo. |
| `--gold-100` sobre `--ink-900` | ≈ 9.5:1 | Texto sobre fundo escuro. AAA. |
| `--ink-500` sobre `--cream-50` | ≈ 6.4:1 | Legendas. AA. |

**Regra prática:** cobre nunca sai de título/elemento gráfico. Texto corrido sempre `--text` (#1C1C1C) sobre creme.

### 2.4 Hierarquia de uso por superfície

| Superfície | BG | Texto | Acento |
|---|---|---|---|
| Página interna (padrão) | `--cream-50` | `--ink-800` | `--gold-900` (subtítulos), `--gold-300` (filetes, marcadores) |
| Abertura de capítulo | `--cream-100` | `--ink-800` | `--gold-300` para número do capítulo |
| Capa / contracapa | `--ink-900` | `--cream-50` | `--gold-100` (metal claro) |
| Callout de alerta | `--cream-100` com borda esquerda `--gold-900` 3px | `--ink-800` | — |
| Callout de dica | `--surface` (#FFF) com sombra suave | `--ink-800` | — |
| Tabela técnica | `--surface` | `--ink-800` | Linha header em `--gold-500` 1px |

---

## 3. Tipografia

Cruzada com `ui-ux-pro-max → typography "luxury serif editorial"`. Resultado: **Cormorant Garamond + Inter** — Cormorant tem a alta-contraste do monograma LM (mais delicado que Playfair), Inter dá legibilidade impecável em corpo impresso 10–11pt e em tela.

### 3.1 Famílias

```css
--font-display: 'Cormorant Garamond', 'Cormorant', Georgia, serif;
--font-body:    'Inter', -apple-system, 'Segoe UI', sans-serif;
--font-mono:    'JetBrains Mono', 'Consolas', monospace;  /* fichas técnicas */
```

Google Fonts (uma única chamada):

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;0,700;1,400&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

### 3.2 Escala — impresso (apostila A4)

Otimizada para leitura em papel offset, margens generosas, mancha de 12cm de largura.

| Token | Tamanho | Entrelinha | Peso | Tracking | Uso |
|---|---|---|---|---|---|
| `display` | 48pt | 52pt | Cormorant 500 italic | -10 | Capa, frases-âncora |
| `h1` (capítulo) | 32pt | 38pt | Cormorant 600 | -5 | Abertura de capítulo |
| `h2` (seção) | 22pt | 28pt | Cormorant 600 | 0 | Seções dentro do capítulo |
| `h3` (subseção) | 14pt | 20pt | Inter 600 uppercase | +120 | Subtítulos curtos |
| `eyebrow` | 9pt | 14pt | Inter 600 uppercase | +200 | "Capítulo 03 / Anatomia" |
| `body` | 10.5pt | 16pt | Inter 400 | 0 | Texto corrido |
| `body-emphasis` | 10.5pt | 16pt | Inter 500 | 0 | Termos técnicos |
| `caption` | 8.5pt | 12pt | Inter 400 italic | 0 | Legendas de imagem |
| `label` | 8pt | 12pt | Inter 600 uppercase | +150 | Tags ("PRÁTICA", "BIOSSEGURANÇA") |
| `pull-quote` | 18pt | 26pt | Cormorant 500 italic | -5 | Citações de página inteira |

**Mancha de texto:** máximo 65 caracteres por linha (≈ 12 cm com `body 10.5/16`). Acima disso a leitura cansa.

### 3.3 Escala — digital (rem, base 16px)

Para landing, slides ou PDF interativo em tela. Mantém a proporção da escala impressa.

| Token | rem | px | Linha | Uso |
|---|---|---|---|---|
| `text-display` | 4rem | 64 | 1.05 | Hero |
| `text-h1` | 2.5rem | 40 | 1.15 | Página |
| `text-h2` | 1.75rem | 28 | 1.25 | Seção |
| `text-h3` | 1.125rem | 18 | 1.4 | Subseção |
| `text-body` | 1rem | 16 | 1.6 | Corpo |
| `text-small` | 0.875rem | 14 | 1.5 | Legendas |
| `text-label` | 0.75rem | 12 | 1.4 | Tags, uppercase |

### 3.4 Regras tipográficas (não-negociáveis)

- Nunca usar Cormorant abaixo de 14pt — perde detalhe e fica frágil na impressão.
- Cormorant italic só em frases-âncora e nomes de procedimentos. Nunca corpo.
- Uppercase só em `eyebrow`, `label` e `h3`. Tracking obrigatório a partir de +120.
- Nunca centralizar parágrafo com mais de 3 linhas.
- Hífens automáticos OFF em títulos. ON em corpo justificado.

---

## 4. Layout e grid

### 4.1 Página A4 (apostila)

```
Formato:        210 × 297 mm
Margem superior: 22 mm
Margem inferior: 24 mm  (para número de página + rodapé)
Margem externa:  20 mm
Margem interna:  26 mm  (encadernação)
Mancha:          164 × 251 mm
Colunas:         1 (corpo) ou 2 (fichas práticas/comparativos)
Goteira:         6 mm
```

### 4.2 Grid base e ritmo vertical

- **Unidade base:** `4pt` (impresso) / `4px` (digital).
- **Ritmo vertical:** todo espaçamento é múltiplo de `4`. Headings ancoram em múltiplos de `8`.

```css
--space-1: 4px;
--space-2: 8px;
--space-3: 12px;
--space-4: 16px;
--space-6: 24px;
--space-8: 32px;
--space-12: 48px;
--space-16: 64px;
--space-24: 96px;  /* abertura de capítulo */
```

### 4.3 Raios e formas

A marca tem alta-contraste de serifa + monograma com terminais agudos. Formas devem ser **majoritariamente retas**, com raio sutil só em interativos digitais.

```css
--radius-none: 0;       /* tabelas, filetes, frames de imagem */
--radius-sm:   2px;     /* tags, badges */
--radius-md:   4px;     /* botões, inputs */
--radius-lg:   8px;     /* cards na versão digital */
--radius-full: 9999px;  /* só avatar e contador de páginas */
```

### 4.4 Sombras (digital)

Sombra é quente, nunca azul-cinza. Usar `--gold-900` com baixa opacidade como base.

```css
--shadow-sm: 0 1px 2px rgba(101, 61, 31, 0.08);
--shadow-md: 0 4px 12px rgba(101, 61, 31, 0.10);
--shadow-lg: 0 16px 40px rgba(101, 61, 31, 0.14);
```

Impresso: nunca usar sombra. Profundidade é dada por filete `--gold-500` 0.5pt ou por fundo `--cream-100`.

---

## 5. Filetes, ornamentos e o "fio Lais"

O monograma LM tem um filete decorativo abaixo do wordmark. Esse mesmo filete vira o ornamento-assinatura do sistema.

### 5.1 Fio horizontal de assinatura

```
[ — ━━━━━━━━━━━━ — ]
```

- Largura: 64pt (impresso) / 64px (digital)
- Espessura: 0.5pt
- Cor: `--gold-300`
- Termina com pontos pequenos em `--gold-900`
- Usar: abertura de capítulo, separador de seções importantes, abaixo do título da capa

### 5.2 Ornamento de star/sparkle

O brand board mostra um pequeno sparkle ao lado do monograma. Reservar para:
- Marcador de "dica da Lais" (callout)
- Item de checklist concluído
- Selo do certificado

Nunca decorar texto corrido com ele.

### 5.3 Proibições

- Não usar pattern ornamental em fundo (poluição).
- Não usar floreios serifa-renascentista (vinhetas, swashes externos ao logo).
- Não usar gradiente em texto corrido. Gradiente cobre só no monograma e em selos do certificado.

---

## 6. Componentes da apostila

### 6.1 Abertura de capítulo

```
┌────────────────────────────────────────┐
│                                        │
│  CAPÍTULO 03                           │  ← eyebrow, gold-300
│                                        │
│  Anatomia                              │  ← h1, ink-800, Cormorant 600
│  das sobrancelhas                      │
│                                        │
│  ━ ━━━━━━━━━━━━ ━                      │  ← fio Lais
│                                        │
│  Lead de 2 linhas em Cormorant 18pt    │  ← intro, ink-500 italic
│  italic, contextualizando o capítulo.  │
│                                        │
└────────────────────────────────────────┘
```

Sempre página direita (ímpar). Página esquerda anterior fica em branco ou com imagem full-bleed.

### 6.2 Callouts

Quatro tipos, com label uppercase + barra lateral. Nunca usar emoji como ícone.

| Tipo | Label | Cor da barra | BG | Quando usar |
|---|---|---|---|---|
| **Atenção** | `ATENÇÃO` | `--gold-900` | `--cream-100` | Biossegurança, contraindicação, limite técnico |
| **Dica da Lais** | `DICA DA LAIS` | `--gold-300` | `--surface` | Insight prático da professora |
| **Pratique** | `PRATIQUE` | `--ink-800` | `--cream-100` | Exercício curto inline |
| **Glossário** | `TERMO TÉCNICO` | `--gold-500` | `--surface` | Definição lateral |

Espec do callout:
- Barra lateral: 3pt de espessura, altura total do bloco
- Padding interno: 12pt vertical, 16pt horizontal
- Label: `text-label` em uppercase, separado do corpo por 6pt

### 6.3 Checklist (ficha prática)

```
☐  Higienizar bancada
☐  Posicionar cliente em 45°
☐  Marcar pontos áureos
✓  Aplicar henna (já demonstrado)
```

- Checkbox: quadrado 10×10pt, borda `--ink-800` 0.5pt, raio 0
- Marcado: substituir ☐ por sparkle dourado em `--gold-300`
- Espaçamento entre itens: 8pt
- Indentação se houver sub-item: 16pt

### 6.4 Tabela técnica

- Header: fundo `--cream-100`, texto `--gold-900` em `label` style
- Linhas: alternância sutil — par `--surface`, ímpar `--cream-50`
- Divisores horizontais apenas, `--cream-300` 0.5pt
- Sem bordas verticais
- Padding célula: 8pt vertical, 12pt horizontal

### 6.5 Imagem + legenda

- Sempre dentro de frame com filete `--gold-500` 0.5pt OU sangrada full-bleed (sem frame)
- Legenda abaixo, em `caption` italic, alinhada à esquerda da imagem
- Numeração opcional: "Fig. 03 — " em `label` antes da legenda
- Nunca sobrepor texto sobre foto sem máscara escura ≥40% opacidade

### 6.6 Frase-âncora (pull quote)

Página dupla a cada 2 capítulos. Tipografia em `pull-quote` style (Cormorant 18pt italic), centralizada vertical e horizontalmente, sobre `--cream-100`. Acima e abaixo: fio Lais.

### 6.7 Rodapé corrente

```
03                  Lais Marques Studio da Beleza        12
↑                          ↑                              ↑
nº capítulo            wordmark em label                 nº página
ink-300                ink-500                            ink-800
```

Aparece em todas as páginas internas exceto aberturas de capítulo e separadores full-bleed.

---

## 7. Componentes digitais (extensão)

Para landing/slides/PDF interativo. Mesmos tokens, ajustados pra tela.

### 7.1 Botão

```css
.btn-primary {
  background: var(--ink-900);
  color: var(--cream-50);
  font: 500 0.875rem/1 var(--font-body);
  letter-spacing: 0.15em;
  text-transform: uppercase;
  padding: 14px 28px;
  border-radius: var(--radius-md);
  border: none;
  transition: all 180ms ease-out;
}
.btn-primary:hover {
  background: var(--gold-900);
}

.btn-ghost {
  background: transparent;
  color: var(--ink-800);
  border-bottom: 1px solid var(--gold-300);
  padding: 8px 0;
  /* ... mesmo type que primary, sem padding lateral */
}
```

Nunca cobre como fundo de botão principal — sai com leitura ruim. Cobre é hover ou linha.

### 7.2 Input

```css
.input {
  background: var(--surface);
  border: none;
  border-bottom: 1px solid var(--cream-300);
  padding: 12px 0;
  font: 400 1rem/1.4 var(--font-body);
  color: var(--text);
}
.input:focus {
  border-bottom-color: var(--gold-300);
  outline: none;
}
```

Sem borda em volta. A marca é editorial — input flutua, não vira caixa.

### 7.3 Card de produto/módulo

```css
.card {
  background: var(--surface);
  padding: 32px 28px;
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-md);
  border-top: 2px solid var(--gold-300);
}
```

Sempre um filete cobre superior. Identifica a marca em qualquer card que apareça.

### 7.4 Navbar (landing)

- Altura: 72px
- Logo monograma à esquerda, alt. máx. 32px
- Links em `label` style, espaçados 32px
- Fundo: `--cream-50` com 90% opacidade + backdrop-blur(8px)
- Border-bottom 1px `--cream-300` quando rolar

---

## 8. Motion (digital)

Movimento deve parecer "gesto de tecido", nunca "salto mecânico".

```css
--ease-brand: cubic-bezier(0.32, 0.72, 0.24, 1);  /* curva levemente over-shoot */
--duration-fast: 180ms;     /* hover, focus */
--duration-base: 320ms;     /* aparições */
--duration-slow: 640ms;     /* reveal de hero */
```

- Fade-in + 8px de slide-up para reveals.
- Nunca rotação > 4°.
- Nunca spring overshoot agressivo (estética de app, não combina).
- Reduced motion: trocar tudo por fade 100ms.

---

## 9. Iconografia e fotografia

### 9.1 Ícones

- Estilo: **linha 1.5pt**, terminais arredondados, sem preenchimento.
- Cor: `--ink-800` ou `--gold-900` (nunca os dois no mesmo conjunto).
- Tamanhos: 16, 20, 24, 32px.
- Biblioteca recomendada: Lucide ou Phosphor (peso light/regular).
- Proibido: ícones flat coloridos, emoji decorativo.

### 9.2 Fotografia

Direção visual (cruzada com style "Nature Distilled" do ui-ux-pro-max):

- **Paleta:** tons de pele, madeira, neutros, cobre. Saturação baixa.
- **Iluminação:** luz natural lateral, sombra suave.
- **Composição:** ¾ ou close detalhado. Plano aberto só em ambiente do studio.
- **Pós:** grain sutil (opacidade 3%), sombras quentes, nunca azul.
- **Proibido:** filtro Instagram saturado, white balance frio, beleza estilizada artificial.

### 9.3 Tratamento de antes/depois

- Sempre lado a lado, mesma escala, mesma luz, mesmo ângulo.
- Label "ANTES" / "DEPOIS" em `text-label` sobre faixa `--cream-100`.
- Nunca usar seta dramática entre as duas.

---

## 10. Aplicações específicas

### 10.1 Capa da apostila

```
[ Fundo: --ink-900 ]

      ╱ monograma LM em metal gradient ╲
                  (alt. 110pt)

         L A I S   M A R Q U E S
         (eyebrow style, gold-100, +400 tracking)

         ━ ━━━━━━━━━━━━━━━━━━━━ ━

         Design de Sobrancelhas
              Profissional        ← display, cream-50, Cormorant italic

         Método Lais Marques       ← h2, gold-100, regular
```

### 10.2 Ficha de avaliação

Layout 2 colunas, com checklist + linha de assinatura ao final. Header sempre com fio Lais + nome do módulo em eyebrow.

### 10.3 Certificado

- A4 paisagem
- Fundo: `--cream-50` com sutil pattern de fio Lais nas 4 bordas
- Monograma LM no topo
- "CERTIFICADO" em eyebrow gigante (+400 tracking, 14pt)
- Nome da aluna em display 36pt italic
- Selo de sparkle dourado canto inferior direito
- Assinatura Lais + data

### 10.4 Instagram (se for usar)

- Grid 3×3 alterna: foto, frase em creme, foto, frase em ink, foto, foto, frase, foto, foto.
- Frases sempre em Cormorant italic, máximo 8 palavras.
- Nunca usar 2 fontes diferentes do sistema. Nunca emoji.

---

## 11. Do / Don't visual (regras rápidas)

✓ **Faça**
- Use o cobre como acento, não como protagonista de tela cheia.
- Deixe muito espaço em branco entre elementos. "Apertou? Tira metade."
- Combine 1 serifa + 1 sans + zero floreio.
- Trate foto com naturalidade — pele real, luz real.

✗ **Não faça**
- Não use rosa em nenhuma intensidade (anti-referência explícita do PRODUCT.md).
- Não use cobre como fundo de bloco grande de texto — cansa.
- Não misture mais de 3 pesos de fonte na mesma página.
- Não use ícones coloridos, emojis ou stickers.
- Não use `#000` puro — sempre `--ink-900` ou `--ink-800`.
- Não centralize parágrafos.

---

## 12. Arquivos de referência

| O quê | Onde |
|---|---|
| Logo principal | `marca-lais-marques/logo-lais-marques-fundo-branco.png` |
| Logo creme | `marca-lais-marques/logo-lais-marques-fundo-caramelo-suave.png` |
| Logo cobre | `marca-lais-marques/logo-lais-marques-fundo-caramelo-vivo.png` |
| Logo preto transparente | `marca-lais-marques/logo-lais-marques-preto-transparente.png` |
| Logo gold transparente | `marca-lais-marques/logo-lais-marques-transparente.png` |
| Brand board | `fef8e564-ba75-4e07-a618-7cc3949adb66.png` |
| Briefing do produto | `PRODUCT.md` |

---

## 13. Tokens em JSON (export pra Figma/Style Dictionary)

```json
{
  "color": {
    "gold": { "50": "#F5C79C", "100": "#E3B07F", "300": "#B67750", "500": "#9F7657", "700": "#7A4F2C", "900": "#653D1F" },
    "cream": { "50": "#FAF1E5", "100": "#F1E5D2", "200": "#E8D4B6", "300": "#D4B896" },
    "ink": { "900": "#0C0D0D", "800": "#1C1C1C", "700": "#2B2B2B", "500": "#5C544C", "300": "#8E867D" }
  },
  "font": {
    "display": "Cormorant Garamond",
    "body": "Inter",
    "mono": "JetBrains Mono"
  },
  "space": { "1": 4, "2": 8, "3": 12, "4": 16, "6": 24, "8": 32, "12": 48, "16": 64, "24": 96 },
  "radius": { "none": 0, "sm": 2, "md": 4, "lg": 8, "full": 9999 }
}
```

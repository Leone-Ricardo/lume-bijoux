# 💛 Lume Bijoux — Site Oficial

Site institucional e e-commerce leve para a **Lume Bijoux**, loja de bijuterias finas e semi-jóias localizada em Campo Grande, Rio de Janeiro.

> *"Brilho de bairro, cuidado de joia."*

---

## ✨ Sobre o projeto

Um site de página única (SPA estática) construído em **HTML5, CSS3 e JavaScript vanilla**, com foco em:

- **Elegância delicada** — identidade visual sofisticada sem esnobar
- **Proximidade** — tom de voz acolhedor, como uma amiga que entende de estilo
- **Conversão via WhatsApp** — todo o fluxo de compra termina em uma mensagem pronta para o WhatsApp da loja
- **Performance** — zero dependências pesadas, sem frameworks CSS/JS
- **Acessibilidade** — contraste AA, ARIA labels, foco visível, navegação por teclado

---

## 🚀 Como usar

Não precisa de build, npm ou servidor. É só abrir:

```bash
# Opção 1 — abrir direto no navegador
open index.html

# Opção 2 — servir localmente (recomendado para testar localStorage)
python3 -m http.server 8000
# ou
npx serve .
```

Depois acesse `http://localhost:8000`.

---

## 📁 Estrutura

```
.
├── index.html      ← arquivo único, com CSS e JS embutidos
└── README.md
```

Todo o CSS está dentro de `<style>` no `<head>` e todo o JavaScript dentro de `<script>` no fim do `<body>`. Organizado em blocos comentados por seção para facilitar manutenção.

---

## 🎨 Sistema de Design

### Cores (CSS custom properties)

| Token | Valor | Uso |
|---|---|---|
| `--cor-fundo` | `#FDF9F7` | Off-white rosado (fundo geral) |
| `--cor-texto` | `#2B2B2B` | Texto principal |
| `--cor-texto-suave` | `#7A6E6A` | Texto secundário |
| `--cor-primaria` | `#C9A227` | Dourado suave (destaques) |
| `--cor-secundaria` | `#B76E79` | Rosé (links, preços) |
| `--cor-destaque` | `#E8C4C4` | Rosa quartzo (badges) |
| `--cor-borda` | `#EDE3DF` | Bordas suaves |
| `--cor-hover` | `#A8841F` | Dourado escuro (hover) |
| `--cor-preto` | `#1A1A1A` | Footer, contraste |

### Tipografia

- **Títulos:** `Cormorant Garamond` (500/600/700), letter-spacing -0.01em
- **Corpo/UI:** `Inter` (300/400/500/600)
- **Escala fluida com `clamp()`** — h1 até 4.5rem, h2 até 2.8rem

### Espaçamento e Grid

- Container: `max-width: 1200px`
- Padding lateral: `1.5rem` (mobile) → `3rem` (desktop)
- Seções: `padding-block: clamp(3.5rem, 9vw, 7rem)`
- Grid de 12 colunas adaptado via CSS Grid + Flexbox

---

## 🧭 Estrutura da página

| # | Seção | Descrição |
|---|---|---|
| 1 | **Header fixo** | Transparente sobre o hero → fundo branco com blur ao rolar |
| 2 | **Hero full-screen** | Imagem editorial, dois CTAs, scroll indicator animado |
| 3 | **Marquee** | Faixa infinita com diferenciais (ouro 18k, prata 925, garantia) |
| 4 | **Manifesto** | Texto poético sobre curadoria e preço justo |
| 5 | **Coleções** | Grid de 6 categorias com hover dourado |
| 6 | **Destaques da semana** | 8 produtos com badge, preço e botões |
| 7 | **Semi-jóias** | Materiais + guia de conservação |
| 8 | **Sobre a loja** | Endereço, horário, mapa Google incorporado |
| 9 | **Depoimentos** | 3 clientes reais com bairros próximos |
| 10 | **Instagram** | Grid de 6 fotos com overlay |
| 11 | **Newsletter** | Fundo rosé→dourado com validação de e-mail |
| 12 | **Footer** | 4 colunas + linha final |

---

## 🛒 Fluxo de compra

```
[Card do produto]
     │
     ├── "Adicionar" → vai para a sacola (localStorage)
     │                     │
     │                     └── Drawer lateral com qty, remover, subtotal
     │
     └── "Comprar" → WhatsApp direto com a peça

[Sacola] → [Checkout modal] → [WhatsApp da loja]
```

### Carrinho

- Persistência em `localStorage` (chave: `lume_cart_v1`)
- **Sincronização entre abas** via evento `storage`
- Badge animado no ícone da sacola
- Dica dinâmica: *"Faltam R$ X para ganhar entrega local grátis"*

### Checkout

Formulário em 4 blocos:

1. **Seus dados** — nome e WhatsApp com máscara `(21) 99999-0000`
2. **Entrega** — retirada, entrega local ou Correios (endereço aparece só quando necessário)
3. **Pagamento** — Pix (5% off), Cartão ou Dinheiro
4. **Carinho especial** — observações + checkbox de embalagem de presente

O **resumo do pedido** é recalculado ao vivo a cada mudança.

### Regras de frete

| Modalidade | Valor | Grátis acima de |
|---|---|---|
| Retirada na loja | Grátis | — |
| Entrega local | R$ 12,00 | R$ 199,00 |
| Correios | R$ 24,90 | R$ 299,00 |
| **Desconto Pix** | **5%** | — |

### Mensagem WhatsApp gerada

O pedido é formatado com Markdown do WhatsApp:

```
*✨ Novo pedido — Lume Bijoux*

*🛍️ Itens*
• 2× Colar Quartzo Rosa — R$ 178,00
• 1× Brinco Argola Trançada — R$ 69,00

*💰 Valores*
Subtotal: R$ 247,00
Frete (Retirar na loja): Grátis
Desconto Pix (5%): − R$ 12,35
*Total: R$ 234,65*
...
```

---

## 📱 Responsividade

| Breakpoint | Comportamento |
|---|---|
| `< 640px` | 1 coluna, menu hamburguer, hero centralizado, produtos em 1 coluna |
| `640–767px` | 2 colunas em produtos, filtros inline |
| `768–1023px` | 3 colunas em categorias/testemunhos, hero alinhado à esquerda |
| `≥ 1024px` | Nav horizontal completa, grids 3-4 colunas, container 1200px |

Animações respeitam `prefers-reduced-motion`.

---

## ⚡ Funcionalidades JavaScript

| Recurso | Detalhes |
|---|---|
| **Carrinho** | Add, update qty, remove, persistência, sync entre abas |
| **Checkout** | Validação, máscara de telefone, cálculo de frete/desconto em tempo real |
| **Busca** | Filtro instantâneo (nome + descrição), normalização de acentos |
| **Quick View** | Modal com detalhes + seletor de quantidade |
| **Drawers** | Menu mobile e sacola com trap de foco e ESC |
| **Scroll reveal** | `IntersectionObserver` com delay escalonado |
| **Toasts** | Feedback visual não intrusivo |
| **Newsletter** | Validação de e-mail com regex |

---

## 🔧 Personalização

### Trocar o número do WhatsApp

No JavaScript, procure por:

```js
const LOJA = {
  whatsapp: '5521999990000',   // ← trocar aqui (formato internacional, só dígitos)
  ...
};
```

### Alterar produtos

Cada produto é um `<article class="product-card">` com `data-*`:

```html
<article class="product-card"
  data-id="p1"
  data-name="Colar Quartzo Rosa"
  data-price="89.00"
  data-image="https://..."
  data-desc="Descrição do produto...">
```

Para adicionar um novo produto, basta duplicar o bloco — o JavaScript já reconhece automaticamente.

### Ajustar regras de frete

```js
const FRETE = {
  retirada: { label: 'Retirar na loja', valor: 0, gratis: true },
  local:    { label: 'Entrega local', valor: 12, gratisAcima: 199 },
  correios: { label: 'Envio para todo o Brasil', valor: 24.9, gratisAcima: 299 }
};
```

### Trocar cores

Edite as variáveis em `:root` no início do `<style>`.

---

## 🌐 SEO e Metadados

- `<title>`, `description`, `keywords`, `canonical`
- **Open Graph** + **Twitter Card** para compartilhamento
- **Schema.org `JewelryStore`** com endereço, telefone e horário
- Hierarquia semântica correta de headings (h1 → h2 → h3)
- `alt` descritivo em todas as imagens
- `loading="lazy"` em imagens abaixo da dobra

---

## ♿ Acessibilidade

- Skip link para o conteúdo principal
- `:focus-visible` em todos os elementos interativos
- `aria-label`, `aria-expanded`, `aria-live`, `role="dialog"`
- Trap de foco em drawers e modais
- Fechamento com `ESC`
- Contraste compatível com WCAG AA
- Respeito a `prefers-reduced-motion`

---

## 🎯 Placeholders a substituir antes de ir ao ar

- [ ] Número do WhatsApp (`5521999990000` → número real)
- [ ] E-mail (`contato@lumebijoux.com.br`)
- [ ] Imagens do Unsplash → fotos reais dos produtos
- [ ] Mapa incorporado → endereço exato confirmado
- [ ] Depoimentos → relatos reais de clientes
- [ ] Handle do Instagram se for diferente de `@lumebijoux`
- [ ] Ano no footer (atualmente 2026)

---

## 📄 Licença

Projeto entregue sob medida para **Lume Bijoux**. Uso exclusivo da marca.

---

**Feito com carinho em Campo Grande. 💛**

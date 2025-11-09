## 🎨 Resumo Detalhado: Linguagem de Marcação e Estilos - CSS

## 1. Introdução ao CSS

### O que é CSS?
- **CSS** = Cascading Style Sheets (Folhas de Estilo em Cascata)
- Linguagem de estilo usada para controlar a **apresentação** de documentos HTML
- Responsável pelo **layout, cores, fontes, posicionamento** e outros aspectos visuais

### Objetivos da CSS
- Separar a estrutura (HTML) da apresentação (CSS)
- Oferecer controle total sobre o design e layout
- Permitir reutilização de estilos
- Facilitar a manutenção e consistência visual

---

## 2. Fundamentos da CSS

### Sintaxe Básica
```css
seletor {
    propriedade: valor;
}
```

**Componentes:**
- **Seletor**: Elemento HTML a ser estilizado
- **Propriedade**: Característica a ser alterada
- **Valor**: Configuração específica da propriedade

### Tipos de Seletores

#### Seletores Básicos
- **Por tag**: `p { }`, `h1 { }`
- **Por classe**: `.minha-classe { }`
- **Por ID**: `#meu-id { }`

#### Seletores de Atributo
- `[type="text"]` - Seleciona elementos com atributo específico
- `[checked]` - Seleciona elementos com atributo presente

#### Seletores Baseados em Relacionamento
- **Descendente**: `div p` - Todos os `<p>` dentro de `<div>`
- **Filho direto**: `div > p` - Apenas `<p>` filhos diretos de `<div>`
- **Irmão adjacente**: `h1 + p` - Primeiro `<p>` após `<h1>`
- **Irmãos gerais**: `h1 ~ p` - Todos `<p>` após `<h1>`

### Formas de Aplicar CSS

#### CSS Inline
```html
<p style="color: blue; font-size: 16px;">Texto</p>
```

#### CSS Interna
```html
<head>
    <style>
        p { color: blue; }
    </style>
</head>
```

#### CSS Externa
```html
<head>
    <link rel="stylesheet" type="text/css" href="estilos.css">
</head>
```

#### CSS em Escopo (HTML5)
```html
<div>
    <style scoped>
        p { color: blue; }
    </style>
    <p>Texto estilizado apenas dentro desta div</p>
</div>
```

### Propriedades CSS Comuns

| Categoria | Propriedades |
|-----------|--------------|
| **Texto** | `color`, `font-family`, `font-size`, `font-weight`, `text-align` |
| **Box Model** | `width`, `height`, `margin`, `padding`, `border` |
| **Posicionamento** | `position`, `top`, `left`, `right`, `bottom`, `z-index` |
| **Background** | `background-color`, `background-image`, `background-repeat` |
| **Listas** | `list-style`, `list-style-type`, `list-style-image` |

### Efeito Cascata e Especificidade

#### Herança
- Filhos herdam propriedades dos pais
- Nem todas as propriedades são herdáveis (ex: `margin`, `padding`)

#### Especificidade
**Ordem de precedência:**
1. `!important`
2. Estilos inline
3. IDs (`#id`)
4. Classes (`.classe`), atributos (`[type]`), pseudoclasses (`:hover`)
5. Elementos (`p`, `div`), pseudoelementos (`::before`)

#### Regra `!important`
```css
p {
    color: blue !important;
}
```

### Atalhos CSS (Shorthands)
```css
/* Margin individual vs atalho */
margin-top: 10px;
margin-right: 15px;
margin-bottom: 10px;
margin-left: 15px;
/* Equivale a: */
margin: 10px 15px;

/* Ordem: top, right, bottom, left */
margin: 10px 15px 10px 15px;
```

---

## 3. CSS3 - Recursos Avançados

### Cores em CSS3

#### Formas de Definir Cores
- **Palavras-chave**: `red`, `blue`, `transparent`
- **Hexadecimal**: `#FF0000`, `#F00`
- **RGB**: `rgb(255, 0, 0)`
- **RGBA**: `rgba(255, 0, 0, 0.5)` (com transparência)
- **HSL**: `hsl(0, 100%, 50%)` (Matiz, Saturação, Luminosidade)
- **HSLA**: `hsla(0, 100%, 50%, 0.5)` (com transparência)

#### Propriedades de Cor
- `color` - Cor do texto
- `background-color` - Cor de fundo
- `border-color` - Cor da borda
- `outline-color` - Cor do contorno

### Estilização de Textos

#### Alinhamento
```css
text-align: left | right | center | justify;
```

#### Espaçamento
```css
line-height: 1.5;        /* Espaçamento entre linhas */
letter-spacing: 2px;     /* Espaçamento entre letras */
word-spacing: 5px;       /* Espaçamento entre palavras */
```

### Fontes em CSS3

#### Propriedades de Fonte
```css
font-family: Arial, Verdana, sans-serif; /* Lista de fallback */
font-size: 16px | 1em | 100%;
font-style: normal | italic | oblique;
font-weight: normal | bold | 100-900;
```

#### Web Fontes
```css
@font-face {
    font-family: 'MinhaFonte';
    src: url('minha-fonte.woff2') format('woff2'),
         url('minha-fonte.woff') format('woff');
}

body {
    font-family: 'MinhaFonte', sans-serif;
}
```

**Formatos de Web Fontes:**
- **TTF/OTF**: Suporte amplo, arquivos maiores
- **WOFF/WOFF2**: Compactados, melhor performance
- **EOT**: Internet Explorer

---

## 4. Conceitos Avançados de CSS

### Box Model

**Componentes:**
- **Content**: Conteúdo real do elemento
- **Padding**: Espaço interno entre conteúdo e borda
- **Border**: Linha ao redor do padding
- **Margin**: Espaço externo entre elementos

**Cálculo de dimensões:**
```
Largura total = width + padding-left + padding-right + border-left + border-right
Altura total = height + padding-top + padding-bottom + border-top + border-bottom
```

### Pseudoclasses

Estilizam estados especiais dos elementos:
```css
a:hover { color: red; }          /* Mouse sobre */
a:active { color: blue; }        /* Clicado */
input:focus { border-color: yellow; } /* Focado */
li:first-child { font-weight: bold; } /* Primeiro filho */
li:last-child { color: gray; }   /* Último filho */
```

### Pseudoelementos

Estilizam partes específicas dos elementos:
```css
p::first-letter { font-size: 2em; }  /* Primeira letra */
p::first-line { font-weight: bold; } /* Primeira linha */
p::before { content: "→ "; }         /* Antes do conteúdo */
p::after { content: "!"; }           /* Depois do conteúdo */
::selection { background: yellow; }  /* Texto selecionado */
```

### Posicionamento

#### Propriedade `position`
```css
position: static | relative | absolute | fixed | sticky;
```

**Valores:**
- **static**: Padrão, fluxo normal do documento
- **relative**: Relativo à posição original
- **absolute**: Relativo ao ancestral posicionado mais próximo
- **fixed**: Relativo à viewport (fica fixo na tela)
- **sticky**: Híbrido entre relative e fixed

#### Propriedades de Coordenadas
```css
top: 10px;
right: 20px;
bottom: 30px;
left: 40px;
```

---

## 5. Frameworks CSS

### O que são Frameworks?
- Conjuntos de componentes CSS reutilizáveis
- Sistemas de grid pré-definidos
- Componentes UI prontos (botões, formulários, menus)
- Padronização e agilidade no desenvolvimento

### Frameworks Populares

#### Bootstrap
- **Mais popular**
- Sistema de grid de 12 colunas
- Abordagem mobile-first
- Componentes JavaScript integrados
- Requer jQuery

#### Foundation
- Foco em flexibilidade
- Sistema XY Grid
- Usa SASS como pré-processador
- Foundation for Emails

#### Semantic UI
- Sintaxe de linguagem natural
- Usa LESS como pré-processador
- Foco em semântica

#### Outros Frameworks
- **Pure.css**: Leve e minimalista
- **Bulma**: Baseado apenas em CSS (sem JavaScript)
- **Materialize**: Baseado no Material Design do Google
- **Skeleton**: Minimalista, apenas o essencial

### Vantagens dos Frameworks
- Padronização do código
- Economia de tempo
- Compatibilidade entre navegadores
- Comunidade ativa e documentação

### Desvantagens dos Frameworks
- Tamanho do arquivo (performance)
- Restrições de design
- Curva de aprendizado
- Perda de controle sobre o código

### Sistema de Grid (Bootstrap)

#### Estrutura Básica
```html
<div class="container">
    <div class="row">
        <div class="col-md-6">Coluna 1</div>
        <div class="col-md-6">Coluna 2</div>
    </div>
</div>
```

#### Breakpoints
- **Extra small**: `< 576px` (.col-)
- **Small**: `≥ 576px` (.col-sm-)
- **Medium**: `≥ 768px` (.col-md-)
- **Large**: `≥ 992px` (.col-lg-)
- **Extra large**: `≥ 1200px` (.col-xl-)

---

### Próximos Passos
- Praticar com projetos reais
- Explorar pré-processadores (SASS, LESS)
- Aprender CSS Grid e Flexbox
- Estudar design responsivo
- Explorar animações CSS

### Recursos Recomendados
- **W3Schools**: Tutoriais completos
- **Google Fonts**: Web fonts gratuitas
- **MDN Web Docs**: Documentação oficial
- **CodePen/JSFiddle**: Ambientes de prática online

---

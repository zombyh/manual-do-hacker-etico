
# 📘 Resumo Detalhado: Linguagem de Marcação de Hipertexto (HTML)

## 1. Introdução ao HTML

### O que é HTML?
- **HTML** = HyperText Markup Language
- Linguagem de marcação usada para **estruturar conteúdo** em páginas web.
- Composta por **elementos (tags)** que organizam textos, imagens, vídeos, tabelas, etc.

### Origem e Evolução
- Baseada em **SGML** (Standard Generalized Markup Language) e **HyTime**.
- Criada por **Tim Berners-Lee** em 1991.
- Mantida inicialmente pelo **IETF**, depois pelo **W3C**.
- Versões principais:
  - HTML (1991)
  - HTML 2.0 (1995)
  - HTML 3.2 (1997)
  - HTML 4.01 (1999)
  - XHTML (2000)
  - HTML5 (2014)
  - HTML 5.1 (2016) e 5.2 (2017)

---

## 2. Estrutura Básica de uma Página Web

### Doctype
- Define a **versão do HTML**.
- Na HTML5: `<!DOCTYPE html>`
- Antes da HTML5: usavam-se DTDs (Strict, Transitional, Frameset)

### Estrutura Obrigatória
```html
<!DOCTYPE html>
<html lang="pt">
<head>
  <meta charset="UTF-8">
  <title>Título da Página</title>
</head>
<body>
  Conteúdo visível da página
</body>
</html>
```

### Elementos Principais
- `<html>`: Raiz do documento.
- `<head>`: Contém metadados, título, links para CSS/JS.
- `<body>`: Contém o conteúdo visível.

### Seções Comuns em Páginas Web
- Cabeçalho (`<header>`)
- Navegação (`<nav>`)
- Conteúdo Principal (`<main>`)
- Barra Lateral (`<aside>`)
- Rodapé (`<footer>`)

---

## 3. Tags HTML Básicas

### Tipos de Tags
- **Estruturais**: `<div>`, `<span>`
- **Textuais**: `<p>`, `<h1>` a `<h6>`, `<a>`, `<img>`
- **Semânticas**: `<article>`, `<section>`, `<header>`, `<footer>`, `<nav>`

### Atributos Comuns
- `id`: Identificador único.
- `class`: Classe para estilização ou agrupamento.
- `src` e `alt` em `<img>`
- `href` em `<a>`

### Tags de Formatação
- `<b>` vs `<strong>`: ambos negrito, mas `<strong>` tem peso semântico.
- `<i>` vs `<em>`: ambos itálico, mas `<em>` tem ênfase semântica.

### Tags Obsoletas
- Exemplos: `<applet>`, `<center>`, `<font>`, `<image>`
- Substituídas por CSS ou novas tags semânticas.

---

## 4. Tags HTML Complexas

### Listas
- **Ordenadas**: `<ol>` + `<li>`
- **Não ordenadas**: `<ul>` + `<li>`
- **De definição**: `<dl>`, `<dt>` (termo), `<dd>` (descrição)

### Tabelas
```html
<table>
  <thead>
    <tr><th>Nome</th><th>Idade</th></tr>
  </thead>
  <tbody>
    <tr><td>João</td><td>30</td></tr>
  </tbody>
</table>
```
- Atributos para mesclagem: `rowspan` e `colspan`

### Mídias
- `<video>` e `<audio>`
- Atributos: `src`, `controls`, `autoplay`, `loop`

---

## 5. Formulários HTML

### Estrutura Básica
```html
<form action="/processar" method="post">
  <label for="nome">Nome:</label>
  <input type="text" id="nome" name="nome" required>
  <button type="submit">Enviar</button>
</form>
```

### Elementos de Formulário
- `<input>` (text, email, tel, date, number, etc.)
- `<textarea>`
- `<select>` + `<option>`
- `<button>`
- `<label>`
- `<fieldset>` e `<legend>`

### Atributos Importantes
- `required`: Campo obrigatório.
- `placeholder`: Texto de dica.
- `pattern`: Validação por regex.
- `autofocus`: Foco automático.
- `min` / `max`: Valores mínimos/máximos.

### Validação de Dados
- **Tipagem**: Verifica se o valor corresponde ao tipo (ex: email, url).
- **Obrigatoriedade**: Uso do `required`.
- **Padrão personalizado**: Uso do `pattern`.
- Validação nativa na HTML5, mas pode ser desativada com `novalidate`.

---

## 6. Conclusão

### O que você aprendeu?
- História e evolução do HTML.
- Estrutura básica e semântica de páginas web.
- Uso de tags para texto, mídia, listas, tabelas e formulários.
- Validação de formulários com HTML5.

### Próximos Passos
- Aplicar os conhecimentos em projetos práticos.
- Explorar CSS e JavaScript para complementar.
- Consultar referências como MDN e W3Schools.

---

### 🔗 Sugestões para Links no Obsidian:
- Linke tópicos como: `[[HTML]]`, `[[Formulários HTML]]`, `[[Tags Semânticas]]`, `[[Validação HTML5]]`
- Use tags como: `#html #web #frontend #estudos`

## 📘 Resumo: Linguagem JavaScript

## 1. Introdução ao JavaScript

- **Definição**: Linguagem de programação interpretada, multiparadigma (estruturada, orientada a objetos, funcional).
- **Uso principal**: Comportamento e interatividade em páginas web (client-side).
- **Ampliação**: Atualmente também usada no servidor (Node.js) e em desenvolvimento mobile.
- **Característica**: Linguagem fracamente tipada.

> 💡 **Curiosidade**: JavaScript ≠ Java. São linguagens distintas.

---

## 2. DOM (Document Object Model)

- **O que é**: Interface que representa a estrutura de um documento HTML/XML como uma árvore de objetos.
- **Função**: Permite manipular conteúdo, estrutura e estilo de páginas web via programação.
- **Componentes**:
  - **Nós**: elementos, atributos, textos.
  - **Métodos e propriedades**: Ex.: `getElementById`, `innerHTML`.

### Manipulação do DOM com JavaScript:
- Inserir, excluir ou modificar elementos.
- Alterar estilos CSS dinamicamente.
- As alterações são temporárias (durante a sessão).

---

## 3. Sintaxe Básica do JavaScript

### Variáveis:
- Declaradas com `var`, `let` ou `const`.
- Nomeação em **camelCase**.
- Tipagem dinâmica: não é necessário declarar o tipo.

### Comentários:
- Uma linha: `//`
- Múltiplas linhas: `/* ... */`

### Exemplo de estrutura:
```js
var nome = "João";
var idade = 30;
alert("Olá, " + nome);
```

### Incorporação do JS em HTML:
- Dentro da tag `<script>` no `<body>` ou `<head>`.
- Via arquivo externo: `<script src="script.js"></script>`.

> ⚠️ **Cuidado**: Scripts no `<head>` podem ser executados antes do DOM estar pronto.

---

## 4. Estruturas de Decisão

### if / else / else if:
```js
if (condição1 && condição2) {
  // executa se ambas verdadeiras
} else if (condição3) {
  // executa se condição3 for verdadeira
} else {
  // executa se nenhuma for verdadeira
}
```

### switch:
```js
switch (valor) {
  case 1:
    // instruções
    break;
  default:
    // instrução padrão
}
```

### Operadores Lógicos:
- `&&` (E)
- `||` (OU)
- `!` (NÃO)

---

## 5. Estruturas de Repetição

### for:
```js
for (let i = 0; i < 10; i++) {
  console.log(i);
}
```

### while:
```js
while (condição) {
  // executa enquanto verdadeiro
}
```

### do/while:
```js
do {
  // executa pelo menos uma vez
} while (condição);
```

### for/in (para objetos e arrays):
```js
for (let item in array) {
  console.log(array[item]);
}
```

---

## 6. Vetores (Arrays)

### Definição:
- Estrutura para armazenar coleções de dados.
- Podem conter tipos diferentes.

### Criação:
```js
var frutas = ["Maçã", "Banana", "Laranja"];
var numeros = new Array(1, 2, 3);
```

### Métodos Comuns:
- `push()`: adiciona ao final.
- `pop()`: remove do final.
- `shift()`: remove do início.
- `splice()`: adiciona/remove em posições específicas.
- `length`: retorna o tamanho.

### Acesso:
- Por índice: `frutas[0]` → "Maçã"

---

## 7. Requisições Assíncronas (AJAX) e JSON

### AJAX (Asynchronous JavaScript and XML):
- Permite atualizar partes da página sem recarregá-la.
- Tecnologias envolvidas: HTML, CSS, JS, DOM, XML/JSON.

### Objeto `XMLHttpRequest`:
```js
var xhr = new XMLHttpRequest();
xhr.open("GET", "url", true);
xhr.onreadystatechange = function() {
  if (xhr.readyState == 4 && xhr.status == 200) {
    console.log(xhr.responseText);
  }
};
xhr.send();
```

### API Fetch (moderna):
```js
fetch("url")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

### JSON (JavaScript Object Notation):
- Formato leve para troca de dados.
- Estrutura: pares `chave: valor`.
- Exemplo:
```json
{
  "nome": "João",
  "idade": 30
}
```

### Métodos JSON em JS:
- `JSON.parse()`: converte string JSON em objeto.
- `JSON.stringify()`: converte objeto em string JSON.

---

## 8. Boas Práticas e Observações

- Sempre declare variáveis antes de usar.
- Use `===` para comparação estrita (valor e tipo).
- Mova scripts para o final do `<body>` para melhor performance.
- Trate erros em requisições assíncronas.
- Evite manipular o DOM antes de ele estar completamente carregado.

---

## 9. Referências e Links Úteis

- [MDN Web Docs](https://developer.mozilla.org)
- [W3Schools](https://www.w3schools.com)
- [jQuery](https://jquery.com)
- [CodePen](https://codepen.io)
- [JSFiddle](https://jsfiddle.net)

---

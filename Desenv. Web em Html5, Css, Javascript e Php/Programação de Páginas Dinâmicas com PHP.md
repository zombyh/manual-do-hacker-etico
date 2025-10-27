
## 🐘 **Resumo: Programação de Páginas Dinâmicas com PHP**

### 1. **Introdução ao PHP**
- **PHP (Hypertext Preprocessor)**: Linguagem de script *open source* para desenvolvimento web no lado do servidor.
- **Características**:
  - Fracamente tipada.
  - Suporte a Programação Orientada a Objetos (POO).
  - Integração com diversos bancos de dados (MySQL, PostgreSQL, etc.).
  - Pode ser embutida diretamente no HTML.
- **Histórico**: Criada por Rasmus Lerdorf em 1994, inicialmente para interpretar formulários HTML.

---

### 2. **Sintaxe Básica do PHP**
- **Delimitadores**: `<?php ... ?>`
- **Finalização de instruções**: `;` (ponto e vírgula).
- **Comentários**:
  - Uma linha: `//` ou `#`
  - Múltiplas linhas: `/* ... */`
- **Variáveis**:
  - Iniciadas com `$` (ex: `$nome`).
  - *Case-sensitive*.
  - Não é necessário declarar tipo.
  - Boas práticas: usar padrão de nomenclatura (ex: `camelCase` ou `snake_case`).

---

### 3. **Recebendo Dados de Formulários (HTTP)**
- **Métodos de envio**:
  - **GET**: Dados visíveis na URL (via `$_GET`).
  - **POST**: Dados no corpo da requisição (via `$_POST`).
- **Variáveis Superglobais**:
  - `$_GET`, `$_POST`, `$_REQUEST` (para ambos).
- **Exemplo de uso**:
  ```php
  $nome = $_POST["nome"];
  $email = $_POST["email"];
  echo "Bem-vindo, $nome! Seu e-mail é $email.";
  ```

---

### 4. **Operadores em PHP**
- **Aritméticos**: `+`, `-`, `*`, `/`, `%` (módulo), `**` (exponenciação).
- **Atribuição**: `=`, `+=`, `-=`, `*=`, etc.
- **Comparação**: `==`, `===` (idêntico), `!=`, `!==`, `<`, `>`, `<=`, `>=`, `<=>` (spaceship).
- **Lógicos**: `and`, `or`, `xor`, `!`, `&&`, `||`.

---

### 5. **Estruturas de Decisão (Condicionais)**
- **if / else / elseif**:
  ```php
  if ($idade < 12) {
      echo "Criança";
  } elseif ($idade < 18) {
      echo "Adolescente";
  } else {
      echo "Adulto";
  }
  ```
- **switch**:
  ```php
  switch ($dia) {
      case 1: echo "Domingo"; break;
      default: echo "Dia inválido";
  }
  ```
- **Operador Ternário**:
  ```php
  $status = ($idade >= 18) ? "Maior" : "Menor";
  ```

---

### 6. **Estruturas de Repetição (Laços)**
- **while**:
  ```php
  while ($i <= 10) {
      echo $i;
      $i++;
  }
  ```
- **do-while** (executa ao menos uma vez).
- **for**:
  ```php
  for ($i = 1; $i <= 10; $i++) {
      echo $i;
  }
  ```
- **foreach** (para arrays):
  ```php
  foreach ($carros as $carro) {
      echo $carro;
  }
  ```

---

### 7. **Arrays (Vetores)**
- **Tipos**:
  - Numérico: `$frutas = ["maçã", "banana"];`
  - Associativo: `$pessoa = ["nome" => "João", "idade" => 30];`
  - Multidimensional: `$alunos = [ ["João", 8, 9], ["Maria", 7, 8] ];`
- **Funções úteis**:
  - `count()`: conta elementos.
  - `array_push()`: adiciona ao final.
  - `array_splice()`: remove e ajusta índices.
  - `unset()`: remove elemento (não reindexa).

---

### 8. **Funções**
- **Funções Definidas pelo Usuário**:
  ```php
  function soma($a, $b) {
      return $a + $b;
  }
  echo soma(5, 3); // 8
  ```
- **Funções Nativas**: Já incluídas no PHP (ex: `echo`, `print_r`, `count`).
- **Boas Práticas**:
  - Nomes claros e descritivos.
  - Indentar o código.
  - Escolher um padrão de nomenclatura.

---

### 9. **Exemplo Prático: Média de Notas com Array e Função**
```php
$alunos = [
    ["João", 8.7, 9.4],
    ["Maria", 9.2, 8.9]
];

function calc_media($n1, $n2) {
    return ($n1 + $n2) / 2;
}

foreach ($alunos as $aluno) {
    $media = calc_media($aluno[1], $aluno[2]);
    echo "{$aluno[0]}: Média = $media<br>";
}
```

---

### 10. **Conceitos-Chave para Revisão**
- PHP é executado no servidor → gera HTML.
- Variáveis superglobais: `$_GET`, `$_POST`, `$_REQUEST`.
- Estruturas de controle: `if`, `switch`, `for`, `foreach`, etc.
- Arrays e funções são fundamentais para organização e reuso.
- Boas práticas: nomenclatura, indentação, modularização.

---

### 11. **Links e Referências Úteis**
- **Manual do PHP**: php.net
- **W3Schools PHP**: Referência rápida para sintaxe e exemplos.
- **Zend Framework Coding Standards**: Boas práticas de codificação.
- **Editores Online**: PHPTester, Write PHP Online.

---

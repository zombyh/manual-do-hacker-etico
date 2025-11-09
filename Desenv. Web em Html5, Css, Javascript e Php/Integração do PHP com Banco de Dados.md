## 🗄️ **Resumo: Integração do PHP com Banco de Dados**

### 1. **Introdução à Integração PHP + BD**
- **Necessidade**: Aplicações web (bankline, redes sociais) precisam armazenar e recuperar dados.
- **PHP no servidor**: Processa credenciais, acessa BD e retorna páginas personalizadas.
- **SGBDs compatíveis**: MySQL, PostgreSQL, SQL Server, Oracle, etc.
- **Abordagem principal**: Uso da **classe PDO** (PHP Data Objects).

---

### 2. **PHP Data Objects (PDO)**
- **O que é**: Classe nativa do PHP para acesso a bancos de dados.
- **Vantagem**: **Camada de abstração** → mesmo código para diferentes SGBDs.
- **Driver**: Basta trocar o prefixo (ex: `mysql:` para `pgsql:`).
- **Conceito**: Interface única para múltiplos bancos.

#### Exemplo de Conexão:
```php
// MySQL
$dsn = new PDO("mysql:host=localhost;dbname=test", $user, $pass);

// PostgreSQL
$dsn = new PDO("pgsql:host=localhost;port=5432;dbname=test", $user, $pass);
```

---

### 3. **Tratamento de Exceções (Try/Catch)**
- **Objetivo**: Evitar quebras inesperadas na aplicação.
- **Sintaxe**:
  ```php
  try {
      $dsn = new PDO("pgsql:host=...", $user, $pass);
  } catch (PDOException $e) {
      echo "Erro: " . $e->getMessage();
  }
  ```

---

### 4. **Encerramento e Persistência de Conexões**
- **Encerrar**: `$dsn = null;`
- **Manter ativa**: Conexões persistentes (cache de conexão):
  ```php
  new PDO("pgsql:host=...", $user, $pass, [PDO::ATTR_PERSISTENT => true]);
  ```

---

### 5. **Métodos Principais da Classe PDO**

#### a) **`exec()`**
- Executa SQL e retorna número de linhas afetadas.
- Ideal para INSERT, UPDATE, DELETE.
- Exemplo:
  ```php
  $linhas = $dsn->exec("DELETE FROM cliente WHERE id = 1");
  echo "Linhas afetadas: " . $linhas;
  ```

#### b) **`query()`**
- Executa SQL e retorna `PDOStatement` (resultado).
- Ideal para SELECT.
- Exemplo:
  ```php
  $resultado = $dsn->query("SELECT * FROM cliente");
  while ($row = $resultado->fetch(PDO::FETCH_ASSOC)) {
      echo $row['nome'];
  }
  ```

#### c) **`prepare()` + `execute()`**
- **Previne SQL Injection**.
- Usa parâmetros nomeados ou `?`.
- Exemplo:
  ```php
  $stmt = $dsn->prepare("SELECT * FROM usuario WHERE login = :login");
  $stmt->execute([':login' => $login]);
  ```

---

### 6. **SQL Injection**
- **O que é**: Inserção de código SQL malicioso em formulários.
- **Exemplo de ataque**:
  ```sql
  Login: ' OR true = true; --
  Senha: qualquersenha
  ```
- **Prevenção**: Sempre usar `prepare()` e `execute()`.

---

### 7. **Programação Orientada a Objetos (POO) com PHP**
- **Classe**: Molde (ex: `Cliente`, `Produto`).
- **Objeto**: Instância da classe.
- **Exemplo**:
  ```php
  class Fruta {
      private $nome;
      public function setNome($nome) {
          $this->nome = $nome;
      }
      public function getNome() {
          return $this->nome;
      }
  }
  $fruta1 = new Fruta();
  $fruta1->setNome("Maçã");
  echo $fruta1->getNome();
  ```

---

### 8. **Exemplo Prático: Formulário HTML + PHP + PostgreSQL**

#### a) Tabela no PostgreSQL:
```sql
CREATE TABLE cliente (
    id_cliente SERIAL PRIMARY KEY,
    nome_cliente VARCHAR(255) NOT NULL,
    cpf_cliente VARCHAR(11) NOT NULL,
    email_cliente VARCHAR(255) NOT NULL,
    data_nascimento_cliente TIMESTAMP
);
```

#### b) Formulário HTML (com validação):
```html
<form action="cadastrar.php" method="POST">
    Nome: <input type="text" name="nome" required>
    CPF: <input type="text" name="cpf" minlength="11" maxlength="11" required>
    E-mail: <input type="email" name="email" required>
    Data Nasc.: <input type="date" name="nascimento" required>
    <input type="submit" value="Cadastrar">
</form>
```

#### c) Script PHP (`cadastrar.php`):
```php
<?php
try {
    $dsn = new PDO("pgsql:host=localhost;dbname=meubanco", $user, $pass);
    $stmt = $dsn->prepare("INSERT INTO cliente (nome_cliente, cpf_cliente, email_cliente, data_nascimento_cliente) VALUES (?, ?, ?, ?)");
    $stmt->execute([$_POST['nome'], $_POST['cpf'], $_POST['email'], $_POST['nascimento']]);
    echo "Cliente cadastrado!";
} catch (PDOException $e) {
    echo "Erro: " . $e->getMessage();
}
$dsn = null;
?>
```

---

### 9. **Listagem de Dados com PHP + PDO**
```php
$resultado = $dsn->query("SELECT * FROM cliente");
while ($row = $resultado->fetch(PDO::FETCH_ASSOC)) {
    echo "Nome: " . $row['nome_cliente'] . "<br>";
    echo "CPF: " . $row['cpf_cliente'] . "<br>";
    echo "E-mail: " . $row['email_cliente'] . "<br>";
    echo "Nascimento: " . $row['data_nascimento_cliente'] . "<br><br>";
}
```

---

### 10. **Validação de Dados**
- **Frontend (HTML5)**: `required`, `type="email"`, `minlength`, `maxlength`.
- **Backend (PHP)**: Verificar dados com `isset()`, `filter_var()`, `strlen()`.

---

### 11. **Boas Práticas**
- Use **PDO** em vez de funções específicas de cada SGBD.
- Sempre **trate exceções**.
- **Valide dados** no frontend e backend.
- Use **`prepare`/`execute`** para evitar SQL Injection.
- **Encerre conexões** quando não forem mais necessárias.

---

### 12. **Conceitos-Chave para Revisão**
- PDO é uma camada de abstração para bancos de dados.
- SQL Injection é um risco grave → use prepared statements.
- Try/Catch aumenta a robustez da aplicação.
- HTML + PHP + PDO = Aplicação web dinâmica e segura.

---

### 13. **Referências Úteis**
- **Manual do PHP**: php.net
- **PostgreSQL Documentation**: postgresql.org/docs
- **W3Schools PHP PDO**: Referência rápida

---

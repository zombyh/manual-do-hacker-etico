## 🗃️ Resumo: Python com Banco de Dados

### 1. Introdução
- Integração de programas Python com SGBDs.
- Operações: conexão, criação de tabelas, relacionamentos, inserção, consulta (incluindo JOIN).
- Objetivos:
  - Reconhecer frameworks e bibliotecas para gerenciamento de BD.
  - Empregar funcionalidades para conexão, acesso e criação de BD e tabelas.
  - Aplicar inserção, remoção e atualização de registros.
  - Recuperar registros com consultas simples e complexas.

---

### 2. Frameworks e Bibliotecas para Gerenciamento de Dados

#### 🔹 Conectores de Banco de Dados
- Seguem a especificação **PEP 249 (DB-API 2.0)**.
- Exemplos:
  - **PostgreSQL**: `psycopg2`
  - **MySQL**: `mysqlclient`, `PyMySQL`, `mysql-connector-python`
  - **SQLite**: `sqlite3` (já incluso no Python)

#### 🔹 Comparação entre Conectores
- `psycopg2`: alto desempenho, suporte a funcionalidades avançadas do PostgreSQL.
- `mysqlclient`: baseado em C, rápido, mas complexa instalação no Windows.
- `PyMySQL`: puro Python, fácil instalação, mas mais lento.
- `MySQL Connector`: oficial da Oracle, puro Python, boa compatibilidade.
- `sqlite3`: banco embutido, ideal para protótipos e aplicações leves.

---

### 3. Principais Métodos e Exceções

#### 🔹 Métodos dos Conectores
- `connect()`: estabelece conexão.
- `cursor()`: cria cursor para executar comandos.
- `execute()`: executa comando SQL.
- `fetchone()`, `fetchall()`: recuperam resultados.
- `commit()`, `rollback()`: gerenciam transações.
- `close()`: fecha cursor e conexão.

#### 🔹 Fluxo de Trabalho Típico
```python
conexao = connect(URL)
cursor = conexao.cursor()
cursor.execute("COMANDO SQL")
resultados = cursor.fetchall()
conexao.commit()
cursor.close()
conexao.close()
```

#### 🔹 Exceções Comuns
- `Error`: classe base.
- `IntegrityError`: violação de integridade (ex: chave estrangeira).
- `OperationalError`: problemas operacionais (ex: desconexão).
- `ProgrammingError`: erro de sintaxe SQL ou tabela inexistente.

---

### 4. Tipos de Dados no SQLite

#### 🔹 Classes de Armazenamento
- `NULL`
- `INTEGER`
- `REAL`
- `TEXT`
- `BLOB`

#### 🔹 Afinidades de Tipo
- `TEXT`, `NUMERIC`, `INTEGER`, `REAL`, `NONE`
- Permitem flexibilidade no armazenamento.
- Exemplo: `VARCHAR(n)` → `TEXT`

---

### 5. Conexão, Acesso e Criação de Banco de Dados

#### 🔹 Conectando ao SQLite
```python
import sqlite3
conexao = sqlite3.connect("meu_banco.db")
```

#### 🔹 Criando Tabelas
- Comando: `CREATE TABLE`
- Exemplo com chave primária e estrangeira:
```sql
CREATE TABLE Veiculo (
    placa CHARACTER(7) PRIMARY KEY,
    proprietario INTEGER,
    marca INTEGER,
    FOREIGN KEY(proprietario) REFERENCES Pessoa(cpf),
    FOREIGN KEY(marca) REFERENCES Marca(id)
);
```

#### 🔹 Alterando e Removendo Tabelas
- `ALTER TABLE`: adiciona/modifica colunas.
- `DROP TABLE`: remove tabela.

---

### 6. Inserção, Atualização e Remoção de Dados

#### 🔹 Inserção com `INSERT INTO`
```python
comando = "INSERT INTO Pessoa VALUES (?, ?, ?, ?)"
cursor.execute(comando, (cpf, nome, nascimento, oculos))
```

#### 🔹 Parâmetros Nomeados
```python
comando = "INSERT INTO Pessoa VALUES (:cpf, :nome, :nascimento, :oculos)"
cursor.execute(comando, vars(pessoa))
```

#### 🔹 Atualização com `UPDATE`
```python
comando = "UPDATE Pessoa SET oculos = ? WHERE cpf = ?"
cursor.execute(comando, (False, cpf))
```

#### 🔹 Remoção com `DELETE`
```python
comando = "DELETE FROM Pessoa WHERE cpf = ?"
cursor.execute(comando, (cpf,))
```

---

### 7. Recuperação de Registros

#### 🔹 Seleção com `SELECT`
```python
cursor.execute("SELECT * FROM Pessoa")
registros = cursor.fetchall()
```

#### 🔹 Filtros com `WHERE`
```python
cursor.execute("SELECT * FROM Pessoa WHERE oculos = ?", (True,))
```

#### 🔹 Junção com `JOIN`
```python
comando = """
SELECT Veiculo.placa, Marca.nome
FROM Veiculo JOIN Marca ON Veiculo.marca = Marca.id
"""
cursor.execute(comando)
```

---

### 8. Boas Práticas e Dicas

#### 🔹 Uso de `WITH` para Gerenciamento de Conexões
```python
with sqlite3.connect("meu_banco.db") as conexao:
    cursor = conexao.cursor()
    cursor.execute("...")
```

#### 🔹 Habilitando Chaves Estrangeiras no SQLite
```python
conexao.execute("PRAGMA foreign_keys = ON")
```

#### 🔹 Conversão de Tipos
- Registro de conversores personalizados:
```python
def conv_bool(dado):
    return True if dado == 1 else False

sqlite3.register_converter("BOOLEAN", conv_bool)
```

---

### 9. Exemplo Prático: Sistema de Gerenciamento de Eventos

#### 🔹 Estrutura
- Tabelas: `Eventos`, `Participantes`, `Locais`
- Relacionamentos via chaves estrangeiras.

#### 🔹 Código de Exemplo
```python
import sqlite3

def criar_tabelas(conexao):
    cursor = conexao.cursor()
    cursor.execute("""
        CREATE TABLE Locais (
            id INTEGER PRIMARY KEY AUTOINCREMENT,
            nome TEXT NOT NULL,
            endereco TEXT NOT NULL
        )
    """)
    # ... outras tabelas
    conexao.commit()
```

---

### 10. ORM (Object-Relational Mapping)
- Exemplos: SQLAlchemy, Peewee.
- Vantagem: abstrai SQL, usando métodos Python.
- Permite mapear classes para tabelas.

---

### 11. Referências e Exploração
- Documentação oficial:
  - `sqlite3`
  - `psycopg2`
  - `mysql-connector-python`
  - `PyMySQL`
- Ferramentas: DB Browser for SQLite.

---

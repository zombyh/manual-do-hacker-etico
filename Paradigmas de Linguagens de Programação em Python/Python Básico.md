
## 📘 Resumo: Python Básico (Estruturado)

### 🔹 Módulo 1: Linguagem Python
- **Python** é uma linguagem de **alto nível**, **multiparadigma** (estruturada, OO, funcional), **interpretada**, **portável** e **extensível**.
- Características principais:
  - Sintaxe simples e legível.
  - Não usa chaves; **blocos são definidos por indentação**.
  - Tipagem dinâmica.
  - Comunidade ativa com **PEPs** (Python Enhancement Proposals), como a **PEP8** (guia de estilo).

---

### 🔹 Módulo 2: Variáveis
- Variáveis não precisam ser declaradas com tipo.
- Identificadores podem conter letras, números e `_`, mas não podem começar com número.
- Palavras reservadas não podem ser usadas como identificadores.
- **Escopo**:
  - **Global**: definidas no nível do módulo.
  - **Local**: definidas dentro de funções.
- **Binding**: associação de variáveis a valores ou tipos (pode ser estático ou dinâmico).
- Constantes não existem nativamente; convenção: usar MAIÚSCULAS.

---

### 🔹 Módulo 3: Tipos de Dados e Expressões
#### Tipos numéricos:
- `int`: inteiros (ex: `10`, `1_000_000`)
- `float`: ponto flutuante (ex: `5.0`, `3.14`)
- `complex`: números complexos (ex: `2+5j`)
- `bool`: booleanos (`True` ou `False`)

#### Operadores:
- Aritméticos: `+`, `-`, `*`, `/`, `//`, `%`, `**`
- Comparação: `==`, `!=`, `<`, `>`, `<=`, `>=`
- Booleanos: `and`, `or`, `not`

#### Precedência de operadores:
1. Parênteses
2. Exponenciação (`**`)
3. Multiplicação, divisão, etc.
4. Adição, subtração
5. Operadores de comparação
6. Operadores booleanos

#### Conversões:
- Implícita: Python converte para o tipo mais abrangente.
- Explícita: usando `int()`, `float()`, `str()`, `bool()`, etc.

---

### 🔹 Módulo 4: Atribuição, Entrada e Saída de Dados

#### Atribuição:
- Simples: `x = 10`
- Múltipla: `x, y = 2, 5`
- Composta: `+=`, `-=`, `*=`, `/=`, `%=`

#### Entrada de dados:
- `input()`: lê string do usuário.
- `eval()`: avalia a string como expressão Python.

#### Saída de dados:
- `print()`: exibe valores.
- Formatação:
  - Concatenação: `print("Valor: " + str(x))`
  - `.format()`: `print("{}:{}".format(hora, minuto))`
  - f-string: `print(f"{hora}:{minuto}")`

#### Exemplo prático:
```python
nota1 = float(input("Digite a nota 1: "))
nota2 = float(input("Digite a nota 2: "))
media = (nota1 + nota2) / 2
print(f"Média: {media:.2f}")
```

---

### ✅ Dicas:
- Pratique a sintaxe de blocos por indentação.
- Entenda a diferença entre `=`, `==` e `!=`.
- Saiba converter tipos explicitamente.
- Domine a formatação de saída com `f-string` ou `.format()`.
- Lembre-se: `input()` sempre retorna string.

---

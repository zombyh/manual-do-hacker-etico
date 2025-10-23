
# 📘 Resumo para Prova de Concurso: Lógica Digital

## 📌 1. Introdução à Lógica Digital
- Computadores operam em **sistema binário (0 e 1)**.
- Circuitos eletrônicos representam 0 e 1 por meio de **níveis de tensão**:
  - **0 (Falso)**: tensão baixa
  - **1 (Verdadeiro)**: tensão alta
- A **álgebra booleana** é a base matemática para projetar e analisar circuitos lógicos.

---

## 🧮 2. Operações Básicas da Álgebra Booleana
### a) Porta OR (OU)
- Símbolo: `+`
- Expressão: $X = A + B$
- Saída é 1 se **pelo menos uma entrada for 1**.
- Tabela-verdade:

| A | B | X |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

### b) Porta AND (E)
- Símbolo: `·`
- Expressão: $X = A \cdot B$
- Saída é 1 **apenas se todas as entradas forem 1**.
- Tabela-verdade:

| A | B | X |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

### c) Porta NOT (NÃO / Inversor)
- Símbolo: `¯` ou `'`
- Expressão: $X = \overline{A}$
- Inverte o valor da entrada.
- Tabela-verdade:

| A | X |
|---|---|
| 0 | 1 |
| 1 | 0 |

---

## 🔁 3. Portas Lógicas Derivadas
### a) Porta NOR (NÃO OU)
- Símbolo: $X = \overline{A + B}$
- Saída é 1 **apenas se todas as entradas forem 0**.
- Tabela-verdade:

| A | B | X |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 0 |

### b) Porta NAND (NÃO E)
- Símbolo: $X = \overline{A \cdot B}$
- Saída é 0 **apenas se todas as entradas forem 1**.
- Tabela-verdade:

| A | B | X |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

### c) Porta XOR (OU Exclusivo)
- Símbolo: $X = A \oplus B$
- Saída é 1 **se as entradas forem diferentes**.
- Tabela-verdade:

| A | B | X |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

### d) Porta XNOR (Coincidência)
- Símbolo: $X = A \odot B$
- Saída é 1 **se as entradas forem iguais**.
- Tabela-verdade:

| A | B | X |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

---

## 🧠 4. Expressões Lógicas e Tabela-Verdade
- **Tabela-verdade**: lista todas as combinações de entradas e suas saídas.
- Número de linhas: $2^n$ (onde $n$ = número de entradas).
- Exemplo com 3 entradas: $2^3 = 8$ linhas.

### Ordem de Precedência:
1. NOT
2. AND
3. OR
4. Parênteses têm prioridade máxima.

---

## 🔁 5. Equivalência e Simplificação de Circuitos
- Duas expressões são equivalentes se possuem a **mesma tabela-verdade**.
- Simplificação usando **álgebra booleana** reduz o número de portas e custo.

### Regras Básicas da Álgebra Booleana:
| Regra        | Expressão                                                                                                  |
| ------------ | ---------------------------------------------------------------------------------------------------------- |
| Identidade   | $A + 0 = A$, $A \cdot 1 = A$                                                                               |
| Null         | $A + 1 = 1$, $A \cdot 0 = 0$                                                                               |
| Involução    | $\overline{\overline{A}} = A$                                                                              |
| Idempotência | $A + A = A$, $A \cdot A = A$                                                                               |
| Complemento  | $A + \overline{A} = 1$, $A \cdot \overline{A} = 0$                                                         |
| Comutativa   | $A + B = B + A$, $A \cdot B = B \cdot A$                                                                   |
| Associativa  | $A + (B + C) = (A + B) + C$                                                                                |
| Distributiva | $A \cdot (B + C) = A \cdot B + A \cdot C$                                                                  |
| Absorção     | $A + A \cdot B = A$, $A \cdot (A + B) = A$                                                                 |
| De Morgan    | $\overline{A + B} = \overline{A} \cdot \overline{B}$, $\overline{A \cdot B} = \overline{A} + \overline{B}$ |

---

## 🧩 6. Aplicação em Circuitos Lógicos
- Circuitos podem ser representados por **expressões booleanas**.
- Exemplo: $X = A + \overline{B} \cdot C$
  - Primeiro: NOT B
  - Depois: AND com C
  - Por fim: OR com A

---

## ✅ 7. Dicas
- Pratique a **construção de tabelas-verdade**.
- Treine a **simplificação de expressões** usando as regras booleanas.
- Entenda a **equivalência entre portas** (ex.: NAND + NOT = AND).
- Resolva exercícios com **operações bit a bit** (ex.: A = 1010, B = 1100, calcule A AND B).

---

## 📚 Material Complementar
- MONTEIRO, Mário. *Introdução à Organização de Computadores*.
- STALLINGS, William. *Arquitetura e Organização de Computadores*.
- TANENBAUM, Andrew. *Organização Estruturada de Computadores*.

---

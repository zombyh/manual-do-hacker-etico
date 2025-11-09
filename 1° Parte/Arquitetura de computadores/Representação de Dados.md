## 📘 Resumo Detalhado: Representação de Dados

### **Módulo 1: Sistemas de Computação**

#### **Unidades de Informação**
- **Bit**: menor unidade de informação (0 ou 1).
- **Byte**: conjunto de 8 bits.
- **Palavra**: conjunto ordenado de bytes.
- **Registro**: conjunto estruturado de palavras.
- **Arquivo**: conjunto organizado de registros.
- **Banco de dados**: conjunto organizado de arquivos.

#### **Conversão entre Unidades**
- De **bits para bytes**: divide por 8.
- De **bytes para bits**: multiplica por 8.

#### **Múltiplos e Submúltiplos**
- Prefixos comuns:
  - Kilo (K): $2^{10} = 1024$
  - Mega (M): $2^{20} = 1.048.576$
  - Giga (G): $2^{30} = 1.073.741.824$
  - Tera (T): $2^{40} = 1.099.511.627.776$

⚠️ **Atenção**: Em computação, os múltiplos são baseados em potências de 2, não de 10.

---

### **Módulo 2: Sistemas de Numeração e Operações Aritméticas**

#### **Bases Numéricas**
- **Decimal (base 10)**: 0 a 9
- **Binária (base 2)**: 0 e 1
- **Octal (base 8)**: 0 a 7
- **Hexadecimal (base 16)**: 0 a 9, A a F

#### **Sistemas Posicionais**
- Cada algarismo tem valor relativo à sua posição.
- Exemplo: $245_{10} = 2 \times 10^2 + 4 \times 10^1 + 5 \times 10^0$

#### **Operações Aritméticas**
- **Adição**:
  - Soma coluna a coluna.
  - Se resultado ≥ base, "vai 1".
- **Subtração**:
  - Se minuendo < subtraendo, "pede emprestado" da esquerda.

---

### **Módulo 3: Conversão entre Bases**

#### **Método Geral**
1. Converter da base X para base 10:
- $N = d_n \times b^n + d_{n-1} \times b^{n-1} + \ldots + d_0 \times b^0$

2. Converter da base 10 para base Y:
   - Divisões sucessivas pela base Y.

#### **Casos Especiais**
- **Binário para Octal**: agrupar de 3 em 3 bits.
- **Binário para Hexadecimal**: agrupar de 4 em 4 bits.
- **Octal/Hexa para Binário**: converter cada dígito para binário.

#### **Lógica Booleana**
- Valores: 0 (falso) e 1 (verdadeiro).
- Base para circuitos lógicos e operações computacionais.

---

### **Módulo 4: Representação de Dados**

#### **Tipos Primitivos de Dados**
- **Caractere**: símbolos não numéricos.
- **Lógico**: verdadeiro ou falso.
- **Numérico**: números.

#### **Tabelas de Codificação**
- **ASCII**:
  - 7 bits → 128 caracteres.
  - Inclui letras, números, pontuação, controle.
- **Unicode**:
  - 16 bits → 65.536 caracteres.
  - Suporta múltiplos idiomas, emojis, símbolos.

#### **Exemplo de Codificação**
- "ROMA" em ASCII (decimal para binário):
  - R: 82 → 1010010
  - O: 79 → 1001111
  - M: 77 → 1001101
  - A: 65 → 1000001

---

## 🧠 Dicas

1. **Pratique conversões** entre bases (especialmente binário, octal, hexadecimal).
2. **Memorize os prefixos** (K, M, G, T) e suas potências de 2.
3. **Entenda a lógica** por trás das operações aritméticas em bases não decimais.
4. **Conheça bem ASCII e Unicode** – diferenças, aplicações e exemplos.
5. **Resolva exercícios** de conversão de unidades (bits, bytes, etc.).

---

## 📚 Referências Sugeridas

- Tanenbaum, A. S. – *Organização Estruturada de Computadores*
- Patterson, D. A. – *Organização e Projeto de Computadores*
- Stallings, W. – *Arquitetura e Organização de Computadores*

---

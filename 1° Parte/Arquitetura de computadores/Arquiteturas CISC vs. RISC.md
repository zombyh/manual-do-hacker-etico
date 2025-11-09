## 📘 Resumo: Arquiteturas CISC vs. RISC

## 🔍 Introdução

As arquiteturas **CISC** (Complex Instruction Set Computer) e **RISC** (Reduced Instruction Set Computer) são dois modelos de conjuntos de instruções que definem como um processador executa operações. Atualmente, muitos processadores usam uma **abordagem híbrida**, combinando características de ambas.

---

## 🧠 1. Arquitetura CISC

### Características:
- **Instruções complexas** que realizam múltiplas operações em uma única instrução.
- **Múltiplos modos de endereçamento**: R-R (registrador-registrador), R-M (registrador-memória), M-M (memória-memória).
- **Unidade de Controle complexa** (microprogramada) para decodificar instruções.
- **Poucos registradores** (geralmente até 8).
- **Código de máquina mais compacto**, facilitando a compilação.

### Vantagens:
- Menor número de instruções no código.
- Facilidade para compiladores (uma linha de alto nível ≈ uma instrução).

### Desvantagens:
- Instruções com tempos de execução variáveis.
- Muitas instruções pouco utilizadas.
- Acesso frequente à memória, o que pode ser lento.

### Exemplos de processadores CISC:
- Intel 8008, 286, 386
- IBM 370
- VAX11

### Analogia da Hamburgueria CISC:
- Muitos tipos de lanches (instruções).
- Funcionários multifuncionais (Unidade de Controle complexa).
- Entregas em domicílio (acesso à memória) são lentas.

---

## 🧠 2. Arquitetura RISC

### Características:
- **Poucas instruções** (reduzidas e genéricas).
- **Instruções de tamanho fixo** (ex.: 4 bytes).
- **Operações apenas entre registradores** (exceto LOAD e STORE).
- **Unidade de Controle simples** (hardwired, sem microprograma).
- **Muitos registradores** (32 ou mais).
- **Pipeline eficiente** com estágios previsíveis.

### Vantagens:
- Execução rápida e previsível (1 instrução por ciclo no pipeline ideal).
- Maior número de registradores reduz acessos à memória.
- Facilidade de implementação de pipelines.

### Desvantagens:
- Código mais longo (mais instruções para mesma tarefa).
- Compilador precisa ser inteligente para otimizar acessos à memória.

### Exemplos de processadores RISC:
- MIPS, ARM, SPARC, PowerPC

### Analogia da Hamburgueria RISC:
- Poucos tipos de pedidos básicos.
- Funcionários especializados em etapas específicas (linha de montagem).
- Otimização para produzir vários pedidos de uma vez.

---

## ⚖️ 3. Comparação CISC vs. RISC

| Característica          | CISC                          | RISC                          |
|-------------------------|-------------------------------|-------------------------------|
| Conjunto de instruções  | Grande e complexo             | Pequeno e reduzido            |
| Modo de endereçamento   | Múltiplo (R-R, R-M, M-M)      | Principalmente R-R            |
| Registradores           | Poucos (até 8)                | Muitos (32+)                  |
| Unidade de Controle     | Complexa (microprogramada)    | Simples (hardwired)           |
| Acesso à memória        | Frequente                     | Minimizado (apenas LOAD/STORE)|
| Pipeline                | Complexo (até 31 estágios)    | Simples e eficiente           |
| Uso atual               | Híbrido (combinado com RISC)  | Híbrido e em dispositivos IoT |

---

## 🔁 4. Arquiteturas Híbridas

- Processadores modernos (como Intel x86) usam **microarquiteturas híbridas**.
- Internamente, instruções CISC são quebradas em **micro-operações RISC**.
- Exemplo: Intel Core, Broadwell, Skylake, etc.

---

## 🧩 5. Pipeline

### Estágios típicos:
1. BI – Busca da Instrução
2. DI – Decodificação da Instrução
3. EXE – Execução
4. AM – Acesso à Memória
5. WB – WriteBack (escrita no registrador)

### Pipeline ideal:
- 1 instrução concluída por ciclo de clock.
- No RISC, é mais fácil atingir essa meta.

---

## ✅ 6. Pontos-chave

- CISC: foco em reduzir o número de instruções no código.
- RISC: foco em reduzir o tempo de execução por instrução.
- LOAD e STORE são as únicas instruções que acessam memória no RISC.
- Compilador tem papel crucial na otimização de código RISC.
- Processadores modernos são híbridos.

---

## 📚 7. Referências Sugeridas

- David Patterson e John Hennessy (pioneiros em RISC).
- Manuais Intel: 8008, 286, 386.
- Livro: "Organização e Projeto de Computadores" (Patterson e Hennessy).

---

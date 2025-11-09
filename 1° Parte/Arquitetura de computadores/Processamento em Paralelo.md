## 📘 Resumo: Processamento em Paralelo

## 🧠 1. Computação de Alto Desempenho por Meio do Processamento em Paralelo

### Evolução dos Computadores
- Aumento de desempenho e capacidade com redução de custos.
- Exemplos: smartphones, tablets, notebooks com capacidade superior a mainframes dos anos 60/70.
- Aplicações que demandam alto processamento:
  - Processamento de imagem
  - Reconhecimento de linguagem
  - Videoconferência
  - Renderização 3D
  - Modelagem e simulação

### Paralelismo em Nível de Instruções
- **Pipeline**: Divisão da execução de instruções em estágios discretos. Várias instruções são executadas simultaneamente em estágios diferentes.
- **Superscalar**: Múltiplas instruções independentes são executadas ao mesmo tempo em unidades funcionais diferentes.
- **VLIW (Very Long Instruction Word)**: Compilador define quais instruções executar em paralelo.
- **Hyper-Threading (Intel)**: Cria dois processadores virtuais a partir de um físico, simulando multiprocessamento.

### Processadores Vetoriais e Matriciais
- **Vetoriais**: Executam a mesma operação em múltiplos dados (SIMD).
- **Matriciais (MPP)**: Múltiplas unidades de processamento executam a mesma instrução em paralelo (massivamente paralelos).

### Superpipeline vs. Superscalar
- **Superpipeline**: Estágios do pipeline executam tarefas em menos de meio ciclo de clock, permitindo clock interno mais rápido.
- **Superscalar**: Múltiplas unidades de execução em paralelo.

---

## ⚙️ 2. Tipos de Organizações de Processadores Paralelos

### Taxonomia de Flynn (1966)
Classificação baseada em fluxos de instruções e dados:

| | Fluxo Único de Instruções | Fluxo Múltiplo de Instruções |
|---|---|---|
| **Fluxo Único de Dados** | SISD (Von Neumann) | MISD (Teórico) |
| **Fluxo Múltiplo de Dados** | SIMD (Vetorial/Matricial) | MIMD (Multiprocessadores) |

- **SISD**: Computador sequencial tradicional.
- **SIMD**: Uma instrução opera sobre múltiplos dados (ex.: GPUs).
- **MIMD**: Múltiplos processadores independentes (ex.: clusters, SMP).

### Multiprocessadores Simétricos (SMP)
- Dois ou mais processadores similares.
- Compartilham memória principal e dispositivos de E/S.
- Controlados por um único SO.
- Vantagem: Balanceamento de carga e escalabilidade.

### Esquemas de Interconexão
- Barramentos compartilhados
- Redes de interconexão
- Coerência de cache: Protocolos para manter consistência entre caches (ex.: escuta de barramento).

### Arquiteturas de Acesso à Memória
- **UMA (Uniform Memory Access)**: Acesso uniforme à memória via barramento compartilhado.
- **NUMA (Non-Uniform Memory Access)**: Acesso à memória varia conforme a localização (mais rápido se local).
- **CC-NUMA (Cache Coherent NUMA)**: Mantém coerência de cache em sistemas NUMA.

---

## 🔧 3. Desempenho do Hardware e Computadores Multicore

### Limitações do Aumento de Clock
- Consumo de energia e geração de calor.
- Complexidade e custo de desenvolvimento.
- **Regra de Pollack**: Desempenho ∝ √(complexidade). Dobrar a complexidade resulta em ~40% de ganho.

### Solução: Arquiteturas Multicore
- Múltiplos núcleos (cores) em um único chip.
- Cada core tem componentes independentes (ULA, UC, cache L1).
- Compartilham cache L2/L3 e controladores de memória.

### Vantagens dos Multicore
- Melhor desempenho por watt.
- Maior eficiência energética.
- Potencial de escalabilidade quase linear (se software for paralelizável).

### Organização de Cache em Multicore
- **Cache L1 dedicada** por core.
- **Cache L2 dedicada ou compartilhada**.
- **Cache L3 compartilhada** (ex.: Intel Core i7).

### Multithreading Simultâneo (SMT / Hyper-Threading)
- Um core físico executa múltiplas threads simultaneamente.
- Aumenta a utilização dos recursos do core.
- Exemplo: Intel Core i7 com Hyper-Threading.

### Desempenho do Software em Multicore
- Aplicações devem ser paralelizáveis para aproveitar múltiplos cores.
- Exemplos:
  - Aplicações multithread (nível de thread)
  - Múltiplos processos (nível de processo)
  - Múltiplas instâncias de aplicação (nível de aplicação)

---

## ✅ 4. Pontos-Chave

- **Pipeline**: Reduz tempo de execução com estágios sobrepostos.
- **Superscalar**: Executa múltiplas instruções por ciclo.
- **Taxonomia de Flynn**: SISD, SIMD, MIMD, MISD.
- **SMP**: Multiprocessadores simétricos com memória compartilhada.
- **UMA vs NUMA**: Acesso uniforme vs. não uniforme à memória.
- **Multicore**: Múltiplos núcleos em um chip, com caches compartilhadas.
- **SMT/Hyper-Threading**: Execução simultânea de threads em um core.
- **Regra de Pollack**: Limitação do ganho de desempenho com aumento de complexidade.

---

## 📚 5. Referências Sugeridas

- Stallings, W. – *Arquitetura e Organização de Computadores*
- Tanenbaum, A. – *Sistemas Distribuídos*
- Monteiro, M. – *Introdução à Organização de Computadores*

---

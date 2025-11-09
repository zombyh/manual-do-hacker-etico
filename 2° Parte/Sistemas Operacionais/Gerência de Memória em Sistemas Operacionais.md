## 📘 Resumo: Gerência de Memória em Sistemas Operacionais

## 📌 Descrição Geral
A gerência de memória é uma função crítica do sistema operacional, envolvendo:
- Alocação e liberação de memória para processos.
- Proteção entre processos.
- Uso de memória virtual para expandir a capacidade de endereçamento.
- Implementação de políticas como paginação, segmentação e swapping.

---

## 🧠 Módulo 1: Como os Processos Enxergam a Memória

### Memória Física vs. Lógica
- **Memória física**: endereços reais do hardware.
- **Memória lógica**: endereços virtuais usados pelos processos.
- Processos só enxergam endereços lógicos, que são traduzidos para físicos pela **MMU (Memory Management Unit)**.

### Estrutura do Espaço de Endereçamento de um Processo
- **Text**: código do programa.
- **Data**: variáveis globais.
- **Heap**: alocação dinâmica.
- **Pilha**: chamadas de função, variáveis locais.
- Entre o heap e a pilha há uma **área livre** para crescimento.

### Proteção de Memória
- Usa dois registradores: **base** e **limite**.
- MMU verifica se o endereço lógico está dentro do intervalo permitido.
- Acesso inválido gera uma exceção (erro fatal).

### Relocação
- **Relocação estática**: endereços resolvidos no carregamento.
- **Relocação dinâmica**: endereços traduzidos durante a execução (usando registrador de relocação).

---

## 🧩 Módulo 2: Políticas de Alocação de Memória

### Alocação Contígua
- Processo ocupa um bloco contíguo de memória.
- Problema: fragmentação e limite de tamanho.

### Overlay
- Módulos do programa são carregados sobrescrevendo a mesma área.
- Exige que o programador defina a estrutura.

### Partições Fixas
- Memória dividida em partições de tamanho fixo.
- Pode haver **fragmentação interna**.

### Partições Variáveis
- Partições criadas conforme o tamanho do processo.
- Políticas de alocação:
  - **First-fit**: primeira partição que couber.
  - **Best-fit**: partição com tamanho mais próximo.
  - **Worst-fit**: maior partição disponível.

### Fragmentação
- **Externa**: espaços livres entre partições.
- **Interna**: espaço não usado dentro de uma partição alocada.

### Swapping
- Processos são movidos entre memória principal e secundária.
- Permite maior multiprogramação.
- Desvantagem: alto tempo de transferência.

### Gerenciamento de Espaço Livre
- **Mapa de bits**: cada bit representa se uma unidade está livre (0) ou ocupada (1).
- **Lista encadeada**: nós indicam segmentos livres (L) ou ocupados (P).

---

## 🔁 Módulo 3: Memória Virtual e Paginação

### Conceito de Memória Virtual
- Espaço de endereçamento virtual > memória física.
- Partes do processo ficam em disco e são carregadas sob demanda.

### Paginação
- Memória dividida em **páginas** (lógica) e **frames** (física).
- **Tabela de páginas** faz o mapeamento.
- **Page fault**: quando uma página não está na memória → é carregada do disco.

### Políticas de Substituição de Páginas
- **FIFO**: primeira a entrar, primeira a sair.
- **LRU (Least Recently Used)**: menos recentemente usada.
- **NRU (Not Recently Used)**: não usada recentemente.
- **LFU (Least Frequently Used)**: menos frequentemente usada.
- **Algoritmo do Relógio (Segunda Chance)**: aproximação do LRU com bit de referência.

### Segmentação
- Divisão lógica do programa (ex: código, dados, pilha).
- Usa **tabela de segmentos**.
- Endereço = (número do segmento, deslocamento).

---

## 🐧 Módulo 4: Gerência de Memória no Linux

### Zonas de Memória Física (x86 32 bits)
- **ZONE_DMA**: primeiros 16MB para dispositivos legados.
- **ZONE_NORMAL**: 16MB–896MB.
- **ZONE_HIGHMEM**: acima de 896MB.
- Em x86_64, só há **ZONE_DMA** e **ZONE_NORMAL**.

### Memória Virtual no Linux
- Cada processo tem:
  - **Visão lógica**: regiões de memória virtual.
  - **Visão física**: entradas na tabela de páginas.
- Regiões podem ser **compartilhadas** ou **privadas**.

### Carregamento de Programas
- **exec()**: substitui o espaço de endereçamento.
- **fork()**: duplica o espaço de endereçamento do pai.
- **Paginação sob demanda**: páginas são carregadas apenas quando necessárias.

### Vinculação de Bibliotecas
- **Estática**: código da biblioteca incluso no executável.
- **Dinâmica**: bibliotecas compartilhadas mapeadas em tempo de execução.

### Comandos Úteis no Linux
- `free`: uso da memória RAM e swap.
- `top` ou `htop`: processos e consumo de memória.
- `vmstat`: estatísticas de memória virtual.
- `swapon`: status do swap.
- `getconf PAGESIZE`: tamanho da página.

---

## ✅ Conclusão
- A gerência de memória é essencial para eficiência e segurança.
- Técnicas como paginação, segmentação e memória virtual permitem melhor uso dos recursos.
- O Linux implementa essas técnicas com sofisticação, aproveitando hardware moderno.

---

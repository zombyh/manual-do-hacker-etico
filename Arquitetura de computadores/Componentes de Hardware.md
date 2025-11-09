## 📘 Resumo: Componentes de Hardware

## 🧠 1. Estrutura Básica de um Computador

### Sistema de Computação
- Conjunto de partes coordenadas que realizam o objetivo de **processar dados**.
- Componentes fundamentais: **hardware** (físico) e **software** (lógico).

### Dados vs. Informação
- **Dados**: Fatos brutos.
- **Informação**: Conhecimento derivado dos dados.
- **Processamento de dados**: Transformação de dados em informação.

### Linguagens de Programação
- **Baixo nível**: Próxima do hardware (ex.: Assembly).
- **Alto nível**: Próxima da linguagem humana (ex.: C++, Python).

### Organização Funcional de um Sistema de Computação
1. **Dispositivos de entrada**: Teclado, mouse, etc.
2. **Processador (CPU)**: Cérebro do computador.
3. **Memória principal (RAM)**: Armazena programas e dados em execução.
4. **Memória secundária**: Armazenamento permanente (HD, SSD).
5. **Dispositivos de saída**: Monitor, impressora, etc.

### Arquitetura de von Neumann
- Programas e dados armazenados na mesma memória.
- Componentes:
  - Unidade de Controle (UC)
  - Unidade Lógica e Aritmética (ULA)
  - Memória
  - Entrada/Saída

### Barramentos
- Conjunto de fios que transportam sinais entre componentes.
- Tipos:
  - **Barramento de Dados (BD)**: Bidirecional.
  - **Barramento de Endereços (BE)**: Unidirecional.
  - **Barramento de Controle (BC)**: Sinais de controle.

### Processador (CPU)
- Funções:
  - **Processamento**: Executa operações.
  - **Controle**: Gerencia execução de instruções.
- **Ciclo de instrução**: Buscar → Decodificar → Executar.
- **Instruções de máquina**: Código binário que a CPU executa.

---

## ⚙️ 2. Subsistemas de Processamento, Memória e Entrada/Saída

### Hierarquia de Memória
1. **Registradores**: Dentro da CPU, mais rápidos.
2. **Cache L1/L2/L3**: Velocidade intermediária.
3. **Memória Principal (RAM)**: Volátil, acesso aleatório.
4. **Memória Secundária**: Não volátil (HD, SSD).

### Memória Principal (RAM)
- Organizada em células endereçáveis.
- Tipos:
  - **SRAM**: Mais rápida, cara (usada em cache).
  - **DRAM**: Mais lenta, barata (usada como RAM principal).
  - **DDR SDRAM**: Transfere dados na subida e descida do clock.

### Princípio da Localidade
- **Espacial**: Acessos consecutivos a endereços próximos.
- **Temporal**: Reutilização de dados recentes.

### Memória Secundária
- Exemplos: HD, SSD, pendrive.
- Características: Não volátil, grande capacidade, baixa velocidade.

### Subsistema de Entrada/Saída (E/S)
- **Periféricos**: Dispositivos de E/S (teclado, mouse, impressora).
- **Interface/Controlador**: Adapta periféricos ao sistema (ex.: placa de vídeo).
- **Técnicas de E/S**:
  - Controlada por programa
  - Controlada por interrupção
  - **DMA (Acesso Direto à Memória)**: Transferência sem CPU.

### Disco Magnético (HD)
- Estrutura: Pratos, trilhas, setores, cilindros.
- Cabeça de leitura/gravação.

### Transmissão de Dados
- **Paralela**: Vários bits simultaneamente (ex.: barramentos internos).
- **Serial**: Um bit por vez (ex.: USB, SATA).

---

## 🖥️ 3. Sistema Operacional (SO)

### Definição
- Programa que atua como intermediário entre usuário e hardware.
- Gerencia recursos: CPU, memória, dispositivos.

### Funções do SO
- Gerenciamento de processos
- Gerenciamento de memória
- Controle de dispositivos
- Sistema de arquivos

### Estrutura em Camadas
- **Hardware**: Camada física.
- **Kernel (Núcleo)**: Core do SO.
- **Aplicações**: Programas do usuário.

### Tipos de SO
1. **Monotarefa**: Executa um programa por vez (ex.: MS-DOS).
2. **Multitarefa**: Executa múltiplos programas (ex.: Windows, Linux).
3. **Tempo Real**: Resposta em tempo crítico (ex.: sistemas industriais).
4. **Multiprocessador**: Várias CPUs trabalhando juntas.

### Sistemas Multiprogramáveis
- **Batch**: Processamento em lote (sem interação).
- **Tempo Compartilhado**: Múltiplos usuários (ex.: terminais).
- **Tempo Real**: Resposta imediata.

### Tendências
- **Virtualização**: Múltiplos SOs em uma máquina física.
- **Contêineres**: Isolamento de aplicações (ex.: Docker).
- **Nuvem**: SO e aplicativos remotos.

---

## ✅ 4. Pontos-Chave

- **Barramentos**: BD, BE, BC.
- **Ciclo de instrução**: Buscar, decodificar, executar.
- **Hierarquia de memória**: Registradores → Cache → RAM → HD/SSD.
- **Tipos de RAM**: SRAM (cache), DRAM (principal), DDR (velocidade dupla).
- **DMA**: Transferência de dados sem CPU.
- **SO**: Kernel, multitarefa, tempo real, virtualização.

---

## 📚 5. Referências Sugeridas

- Monteiro, M. – *Introdução à Organização de Computadores*
- Patterson & Hennessy – *Organização e Projeto de Computadores*
- Tanenbaum – *Sistemas Operacionais Modernos*

---

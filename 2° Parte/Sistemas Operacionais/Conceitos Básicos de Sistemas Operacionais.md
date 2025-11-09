## 📘 Resumo: Conceitos Básicos de Sistemas Operacionais

## 📌 Visão Geral
- **Sistema Operacional**: Software que atua como intermediário entre hardware e aplicações.
- **Funções**: Gerenciar recursos, fornecer interface, garantir segurança e eficiência.
- **Componentes do Sistema Computacional**: Hardware, aplicativos, usuários e SO.

---

## 🕰️ Evolução Histórica dos Sistemas Operacionais

### [[Gerações de Computadores]]
- **Primeira Geração (1945-1955)**: Válvulas, programação por painéis físicos.
- **Segunda Geração (1955-1965)**: Transistores, sistemas em lote (*batch*).
- **Terceira Geração (1965-1980)**: Circuitos integrados, multiprogramação, *time-sharing*, surgimento do UNIX.
- **Quarta Geração (1980-atual)**: Microprocessadores, computadores pessoais, redes, interfaces gráficas, software livre.

### [[Sistemas Windows e Unix]]
- **Windows**: Evoluiu do MS-DOS para Windows NT, integrando linhas desktop e servidor.
- **Unix**: Desenvolvido a partir do MULTICS, reescrito em C, originou variantes como BSD e Linux.

---

## 🧩 Tipos de Sistemas Operacionais

### [[Classificação por Gerenciamento de Tarefas]]
- **Monoprogramáveis/Monotarefa**: Um programa por vez, recursos dedicados.
- **Multiprogramáveis/Multitarefa**: Múltiplos programas compartilham recursos.
  - **Time-sharing**: Múltiplos usuários interativos.
  - **Tempo real**: Resposta em tempo crítico ou não crítico.

### [[Sistemas com Múltiplos Processadores]]
- **Fortemente Acoplados**: Compartilham memória (SMP, NUMA).
- **Fracamente Acoplados**: Sistemas independentes conectados (redes).

### [[Classificação por Licença]]
- **Software Proprietário**: Código fechado, direitos exclusivos.
- **Software Livre**: Quatro liberdades (uso, estudo, redistribuição, melhoria).
- **Código Aberto**: Código disponível, mas nem sempre respeita todas as liberdades do software livre.

---

## 🏗️ Estrutura do Sistema Operacional

### [[Kernel (Núcleo)]]
- **Funções**: Gerenciar processos, memória, arquivos, E/S, redes, segurança.
- **Execução**: Concorrente, assíncrona, baseada em eventos.

### [[System Calls (Chamadas de Sistema)]]
- **Função**: Interface entre aplicações e kernel.
- **Exemplos**: `fork`, `waitpid`, `read`, `write`, `mkdir`.
- **Padrões**: POSIX (Unix-like) e Win32 (Windows).

### [[Modos de Acesso]]
- **Modo Kernel**: Instruções privilegiadas, acesso total ao hardware.
- **Modo Usuário**: Instruções não privilegiadas, acesso restrito.
- **Transição**: Via *system calls* com verificação de privilégios.

---

## 🏛️ Arquiteturas de Kernel

### [[Arquitetura Monolítica]]
- Todos os serviços no kernel.
- Vantagem: Desempenho.
- Desvantagem: Complexidade e instabilidade.

### [[Arquitetura em Camadas]]
- Serviços organizados em níveis.
- Vantagem: Isolamento e manutenção.
- Desvantagem: Overhead de comunicação.

### [[Microkernel]]
- Serviços essenciais no kernel; demais como processos de usuário.
- Vantagem: Confiabilidade e segurança.
- Exemplo: QNX, Minix.

### [[Máquinas Virtuais]]
- Virtualização do hardware.
- Hypervisors (Tipo 1: direto no hardware; Tipo 2: sobre um SO hospedeiro).

### [[Exokernel]]
- Alocação direta de recursos para máquinas virtuais.
- Elimina camadas de mapeamento.

---

## 🐧 Linux: Arquitetura, Instalação e Comandos

### [[Distribuições Linux]]
- Coleção de aplicativos + kernel.
- Exemplos: Ubuntu, Debian, Fedora.
- Modos: Instalação em disco ou *live*.

### [[Estrutura de Diretórios]]
- **/**: Raiz
- **/bin**, **/sbin**: Executáveis
- **/etc**: Configurações
- **/home**: Diretórios dos usuários
- **/var**: Arquivos variáveis (logs)
- **/tmp**: Arquivos temporários
- **/dev**: Dispositivos
- **/proc**: Informações de processos

### [[Comandos Básicos]]
- `pwd`: Mostra diretório atual
- `cd`: Altera diretório
- `ls`: Lista arquivos
- `mv`: Move ou renomeia
- `mkdir`: Cria diretório
- `rm`: Remove arquivos
- `./configure && make && make install`: Compila código-fonte

### [[Super Usuário (Root)]]
- Usuário com privilégios totais.
- Identificado por `#` no prompt.

---

## ✅ Conclusão
- SOs evoluíram para abstrair hardware e gerenciar recursos.
- Kernel, system calls e modos de acesso são fundamentais.
- Linux é um sistema Unix-like, modular e flexível.
- Compreender a estrutura do SO é essencial para administração e desenvolvimento.

---

## 🔗 Explore +
- **Open Source Initiative**
- **Linux From Scratch**
- **GNU Project**
- **POSIX Standard**
- **Virtualização e Containers**

---

## 📘 Resumo: Processos e Gerência de Processador

## 1. Introdução aos Processos
- **Processo**: programa em execução, incluindo valores de registradores, variáveis e espaço de endereçamento.
- **Thread**: unidade de execução dentro de um processo; compartilha o mesmo espaço de endereçamento.
- **Objetivo**: permitir concorrência e paralelismo, aproveitando sistemas multiprocessadores.

---

## 2. Criação e Encerramento de Processos
- **Criação** ocorre por:
  - Inicialização do sistema
  - Chamada de sistema (`fork()`)
  - Solicitação do usuário
  - Início de tarefa em lote
- **Encerramento** pode ser:
  - Voluntário (`exit()`)
  - Por erro fatal
  - Por solicitação de outro processo (`kill`)

### Exemplo em C:
```c
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    int pid = fork();
    if (pid == 0) {
        printf("Processo filho\n");
    } else {
        waitpid(pid, NULL, 0);
        printf("Processo pai\n");
    }
}
```

---

## 3. Estados de um Processo
- **Novo**
- **Pronto**
- **Executando**
- **Bloqueado**
- **Terminado**

> Transições entre estados são controladas pelo escalonador.

---

## 4. Threads
- **Vantagens**:
  - Menor custo de criação/troca
  - Compartilhamento de memória
- **Tipos**:
  - Threads de usuário (gerenciados pela biblioteca)
  - Threads de núcleo (gerenciados pelo SO)
- **Linux**: usa `clone()` para criar threads.

---

## 5. Comunicação e Sincronização
- **Problema**: condição de corrida (race condition)
- **Solução**: exclusão mútua com:
  - **Semáforos**: operações `down()` e `up()`
  - **Monitores**: estruturas de alto nível (ex.: `synchronized` no Java)
  - **Sinais**: comunicação assíncrona (ex.: `SIGKILL`, `SIGTERM`)
  - **Pipes**: comunicação entre processos (ex.: `cat arquivo | sort`)

### Exemplo com Semáforo:
```c
down(mutex);
// Região crítica
up(mutex);
```

---

## 6. Escalonamento de Processos
- **Objetivo**: decidir qual processo executar a seguir
- **Tipos**:
  - **Não preemptivo**: processo mantém a CPU até terminar
  - **Preemptivo**: processo pode ser interrompido

### Algoritmos de Escalonamento:
- **FIFO**: primeiro a chegar, primeiro a ser servido
- **SJF**: menor tarefa primeiro
- **Round Robin**: tempo dividido em quantums
- **Por Prioridade**: processos com maior prioridade executam primeiro
- **Múltiplas Filas**: diferentes filas para diferentes tipos de processo

---

## 7. Escalonamento no Linux
- **Classes de tarefas**:
  - FIFO em tempo real
  - Round Robin em tempo real
  - Tempo compartilhado
- **Prioridades**: 0–99 (tempo real), 100–139 (tempo compartilhado)
- **Comando** `nice`: altera prioridade de tarefas

---

## 8. Conceitos Importantes
- **PCB (Bloco de Controle de Processo)**: estrutura que armazena informações do processo
- **Mudança de Contexto**: troca de estado entre processos
- **Copy-on-Write**: técnica para economizar memória ao criar processos
- **CPU-bound vs I/O-bound**: tipos de processos conforme uso de CPU ou E/S

---

## 9. Aplicações Práticas
- Servidores web com multiprocessamento
- Programas concorrentes com threads
- Sincronização em sistemas de banco de dados
- Sistemas de tempo real com escalonamento rigoroso

---

## 10. Referências Sugeridas
- Tanenbaum, A. S. – *Sistemas Operacionais Modernos*
- Machado, F. B. – *Arquitetura de Sistemas Operacionais*
- DEITEL, H. M. – *Sistemas Operacionais*

---

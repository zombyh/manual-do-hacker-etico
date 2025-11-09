## 📘 Resumo: Identificação de Falsos Positivos e Exceções

### 📌 Visão Geral
- **Disciplina:** Gerenciamento de Vulnerabilidades  
- **Aula:** 8  
- **Tema:** Identificação de falsos positivos, falsos negativos e exceções no ciclo de remediação.

---

## 🎯 Objetivos da Aula
- Descrever o processo de **investigação de falsos positivos (FP)**.
- Identificar e entender o conceito de **exceções** no gerenciamento de vulnerabilidades.

---

## 🔍 O que são Falsos Positivos (FP) e Falsos Negativos (FN)?

| Conceito | Definição |
|----------|-----------|
| **Falso Positivo (FP)** | A ferramenta aponta uma vulnerabilidade que **não existe** no contexto do ambiente. |
| **Falso Negativo (FN)** | A ferramenta **não detecta** uma vulnerabilidade que **existe** no ambiente. |

---

## 💡 Por que Identificar Falsos Positivos é Importante?
- **Economia de tempo, recursos e mão de obra**.
- Evita que equipes de remediação gastem esforços em vulnerabilidades que **não representam risco real**.
- A confirmação de um FP pode ocorrer em **qualquer fase** do ciclo de gerenciamento.

---

## 🧩 Processo de Investigação de Falsos Positivos

### Características do Processo:
- **Contínuo**: Pode ocorrer da detecção até a validação.
- **Contextual**: Deve considerar o ambiente de rede, sistemas e negócio.
- **Estratégico**: Começa pelo mais simples (ex: logs, baixa criticidade) e avança para o complexo.

### Exemplo Prático:
- Se todos os servidores são **Linux**, uma vulnerabilidade reportada em **Windows** é um **falso positivo**.

---

## 🛠️ Como Reduzir Falsos Positivos?

### 1. **Varredura Autenticada**
- Acesso com credenciais permite verificar vulnerabilidades locais.
- Exemplo: OpenVas com login SSH evita FPs em versões de software já corrigidas.

### 2. **Uso de Filtros e Exclusões**
- Filtrar por **nível de risco** (ex: alto e médio).
- Configurar **listas de exclusão** para hosts ou serviços conhecidos.

### 3. **Funções Específicas nas Ferramentas**
- **Nessus**: “Avoid potential false alarms”
- **OpenVas**: Filtros por severidade (CVSS) e uso de *overrides* para descartar FPs automaticamente.

---

## 📊 Comparação: Varredura Automatizada vs. Pentest

| Aspecto | Varredura Automatizada | Pentest |
|---------|------------------------|---------|
| **Escopo** | Amplo (todos os ativos) | Focado (parte dos ativos) |
| **Frequência** | Contínua | Pontual |
| **Falsos Positivos** | Comuns | Raros |
| **Complexidade** | Identifica vulnerabilidades conhecidas | Encontra falhas complexas e explorações |

> ✅ **Ambos se complementam**, mas a **gestão contínua** deve ser priorizada.

---

## 🧪 Casos Práticos com OpenVas

### Exemplo de Falso Positivo:
- CVE-2010-0425 reportado em servidor **Linux** → vulnerabilidade só existe no **Windows**.

### Exemplo de Falso Negativo:
- Servidor Apache 2.2.8 vulnerável, mas reportado como **baixo risco** → deveria ser **médio/alto**.
- Banner FTP com credenciais expostas → risco **subestimado**.

---

## ✅ O que são Exceções?
- Vulnerabilidade que **existe**, mas **não pode ser remediada** por:
  - Dependência de serviço crítico.
  - Impossibilidade de interromper o sistema.
  - Uso em ambiente controlado (ex: laboratório).

### Exemplo de Exceção:
- Certificado autoassinado em rede interna para testes → ferramenta aponta como vulnerabilidade, mas é **aceitável no contexto**.

---

## 🧠 Dificuldades na Identificação
- Análise manual é **complexa e demorada**.
- Requer **experiência** e **conhecimento do ambiente**.
- Mesmo assim, **vale o esforço** para evitar retrabalho e custos desnecessários.

---

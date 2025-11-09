## 📚 Resumo: O Ciclo da Remediação

## 🎯 Objetivos da Aula
- Definir prioridades para a remediação de vulnerabilidades.
- Descrever o processo de realização da remediação.

---

## 🔁 Visão Geral do Ciclo de Remediação
A remediação é uma das fases mais críticas do gerenciamento de vulnerabilidades. Envolve:
- **Priorização** das vulnerabilidades.
- **Execução** de correções, mitigações ou aceitação de riscos.
- **Validação** e **monitoramento contínuo**.

---

## 🧩 Priorização de Vulnerabilidades

### 📌 Base da Priorização:
- Uso do **CVSS** (*Common Vulnerability Scoring System*) para classificação inicial.
- Além do CVSS, devem ser considerados:
  - Criticidade do ativo.
  - Impacto no negócio.
  - Tempo e custo da remediação.
  - Classificação da informação (ex: Dados Públicos vs. Top Secret).

### 🧠 Fatores Adicionais para Priorização:

| Fator | Descrição |
|-------|-----------|
| **Impacto no Negócio** | Qual o efeito na continuidade do negócio? |
| **Classificação da Informação** | Dados mais sensíveis = maior prioridade. |
| **Inteligência de Ameaças** | Vulnerabilidades com *exploits* ativos têm prioridade. |
| **Tempo de Remediação** | Prazo necessário para correção. |
| **Capacidade da Equipe** | Maturidade e velocidade da equipe de remediação. |

### 🚀 Priorização Preditiva:
- Nova metodologia que **prevê a probabilidade de exploração**.
- Combina CVSS com dados de ameaças e ciência de dados.
- Foca em **3% das vulnerabilidades** com maior risco real.
- Auxilia a equipe a priorizar com base em **risco efetivo**, não apenas no score.

---

## 🛠️ Processo de Remediação

### 📋 Plano de Mudanças (Plano de Ação):
- Documento que reúne:
  - Vulnerabilidades priorizadas.
  - Ações a serem tomadas (correção, mitigação ou aceite).
  - Prazos e responsáveis.
  - Possíveis interrupções de serviço.
  - *Rollback plan* (plano de reversão).

### ✅ Tipos de Ação na Remediação:

| Ação | Descrição | Exemplo |
|------|-----------|---------|
| **Correção** | Eliminar completamente a vulnerabilidade. | Aplicar *patch* de segurança. |
| **Mitigação** | Reduzir a probabilidade ou impacto. | Restringir acesso, usar *patch virtual*. |
| **Aceite do Risco** | Decisão consciente de não agir. | Risco baixo vs. custo alto da correção. |

---

## 🔄 Validação e Monitoramento

### ✅ Validação:
- Nova verificação (*scan*) para confirmar que a vulnerabilidade foi corrigida ou mitigada.
- Registro no plano de ação.
- Identificação de falsos positivos.

### 📈 Monitoramento Contínuo:
- Processo **cíclico e contínuo**.
- Novas varreduras periódicas.
- Atualização constante do plano de ação.
- Consolida a melhoria contínua da segurança.

---

## 💻 Caso Prático: Mitigação de FTP Anônimo

### Objetivo:
Desabilitar o login anônimo no FTP no Metasploitable 2.

### Passos:
1. Acessar o terminal com `sudo su`.
2. Editar o arquivo de configuração:  
   ```bash
   nano /etc/vsftpd.conf
   ```
3. Alterar:
   - `anonymous_enable=YES` → `NO`
   - `local_enable=YES` → `NO`
4. Reiniciar o serviço:
   ```bash
   /etc/init.d/proftpd restart
   ```
5. Validar com novo escaneamento.

---

## 🧩 Conceitos-Chave
- **CVSS**: Sistema de pontuação de vulnerabilidades.
- **Priorização Preditiva**: Técnica avançada baseada em probabilidade de exploração.
- **Plano de Mudanças**: Documento que orienta a execução da remediação.
- **Rollback**: Plano de reversão em caso de falha na correção.

---

## 🔗 Explore Mais
- Leitura: “Priorização Preditiva”
- Ferramentas: OpenVAS, Tenable, NVD
- Referência: CAIS-RNP – Ciclo de Atualização do Plano de Ação

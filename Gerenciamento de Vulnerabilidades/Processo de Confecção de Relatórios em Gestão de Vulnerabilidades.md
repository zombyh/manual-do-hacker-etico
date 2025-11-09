
## 📘 Resumo: Processo de Confecção de Relatórios em Gestão de Vulnerabilidades

### 1. **Trilhas de Auditoria**
- **O que é**: Registro sistemático de informações sobre operações em sistemas ou redes, com o objetivo de rastrear ações e detectar anomalias.
- **Finalidade**:
  - Acompanhar vulnerabilidades em ativos.
  - Permitir a responsabilização de ações.
  - Auxiliar na detecção de atividades maliciosas.
- **Informações registradas**:
  - Agente da operação.
  - Data e hora.
  - Motivação da operação.
  - Tipo de procedimento (humano ou automatizado).
- **Características de uma trilha efetiva**:
  - Imutabilidade.
  - Cópias seguras e automáticas.
  - Restrição de acesso.
  - Possibilidade de análise conjunta com outras trilhas.

---

### 2. **O que Armazenar em uma Trilha de Auditoria?**
- Nem tudo deve ser registrado → equilíbrio entre relevância e viabilidade.
- Estudo prévio necessário para definir:
  - Necessidade do negócio.
  - Ativos a serem monitorados.
  - Informações críticas.
- Uso de ferramentas como **SIEM** para automatizar coleta e análise de logs.

---

### 3. **Tipos de Trilhas de Auditoria (ABNT NBR 17799)**
- **Logs de administrador e operador**:
  - Logins/logoffs.
  - Tentativas de acesso.
  - Identificação de usuários e terminais.
- **Logs de falhas e erros**:
  - Registros de falhas de usuários ou sistemas.

---

### 4. **Integração com Gestão de Vulnerabilidades**
- A trilha de auditoria ajuda a identificar vulnerabilidades **não detectadas** por varreduras automáticas.
- Exemplo: Ataque via FTP + conexão reversa → correlação de eventos.
- Contribui para:
  - Prevenção de incidentes.
  - Melhoria contínua da segurança.
  - Conformidade (compliance).
  - Investigação forense.

---

### 5. **Frameworks para Trilhas de Auditoria**
- **Common Criteria (ISO/IEC 15408)**:
  - Geração de dados para auditoria.
  - Seleção de dados.
  - Revisão de dados.
- Critérios para construção da trilha:
  - Ativos prioritários.
  - Política de segurança.
  - Metodologias de ameaças.
  - Eventos para identificação de vulnerabilidades.

---

## 📋 Processo de Confecção de Relatórios

### 1. **Finalidade**
- Consolidar resultados da varredura.
- Comunicar vulnerabilidades de forma clara para diferentes públicos.
- Auxiliar na tomada de decisão técnica e gerencial.

---

### 2. **Tipos de Relatórios**
| Tipo de Relatório | Público-Alvo | Conteúdo |
|------------------|--------------|----------|
| **Técnico** | Equipes de TI | Detalhes de vulnerabilidades, meios de exploração, mitigação |
| **Executivo** | Gestores | Visão consolidada, riscos, custos, prazos |
| **Plano de Mitigação/Corretivo** | Equipes de correção | Passos para remediar vulnerabilidades |

---

### 3. **Modelos de Elaboração**
- **Análise Automatizada**: Relatórios gerados por ferramentas de escaneamento.
- **Análise Sob Demanda**: Relatórios customizados, mais detalhados, para suporte à decisão.

---

### 4. **Outros Relatórios**
- **Relatório Final**: Após a remediação, mostra vulnerabilidades tratadas.
- **Relatório Eventual**: Para vulnerabilidades críticas que exigem ação urgente.

---

### 5. **Boas Práticas**
- Personalizar relatórios conforme o público.
- Incluir hosts físicos e virtuais.
- Validar vulnerabilidades antes de incluir no relatório.
- Buscar modelos adaptáveis e melhorar continuamente.

---

## 🧠 Pontos-Chave para Revisão
- A trilha de auditoria é **proativa** e ajuda a identificar vulnerabilidades antes da exploração.
- Relatórios devem ser **claros, direcionados e acionáveis**.
- A gestão de vulnerabilidades está inserida na **gestão de riscos de segurança da informação**.

---

## 🔍 Explore Mais
- Leia o item **2.3 do Common Criteria (ISO/IEC 15408)**.
- Considere ferramentas como **SIEM** para automação de trilhas.

---

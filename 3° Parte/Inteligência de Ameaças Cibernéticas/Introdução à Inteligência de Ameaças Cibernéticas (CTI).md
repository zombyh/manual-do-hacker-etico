## 📘 Resumo: Introdução à Inteligência de Ameaças Cibernéticas (CTI)

## 📌 O que é CTI?
- **Cyber Threat Intelligence (CTI)** é a área responsável por coletar, analisar e transformar informações sobre ameaças cibernéticas em **produtos de inteligência** acionáveis.
- Objetivo: permitir que a organização entenda as ameaças atuais e futuras e tome decisões proativas de segurança.

---

## 🎯 Objetivos da Aula
- Definir CTI e seu papel na organização.
- Identificar as fases do **ciclo de vida do CTI**.

---

## 👥 Principais Ameaças Cibernéticas

| Tipo de Ameaça | Objetivo Principal |
|----------------|-------------------|
| **Governos Estrangeiros** | Espionagem, coleta de informações estratégicas |
| **Terroristas** | Ataques a infraestruturas críticas |
| **Crime Organizado** | Ganho financeiro (dados bancários, fraudes) |
| **Espionagem Industrial** | Roubo de segredos comerciais e propriedade intelectual |
| **Hacktivistas** | Propaganda política ou ideológica |
| **Hackers** | Variam desde script kiddies até especialistas em exploits |

---

## 🔁 Fluxos de Interação da CTI

### 1. **CTI → Outras áreas**
- Iniciativa parte da CTI.
- Exemplo: CTI identifica um exploit específico para Windows 10 em espanhol e alerta a área de TI.

### 2. **Outras áreas → CTI**
- Solicitação de apoio técnico.
- Exemplo: Monitoramento detecta comunicação com C2 e pede análise do IP suspeito.

---

## 🔄 Ciclo de Vida do CTI (5 Fases)

### 1. **Planejamento e Requerimentos**
- Identificação das necessidades das áreas "clientes".
- Definição de objetivos e expectativas.
- Criação de uma base de fontes de informação.

### 2. **Coleta e Processamento**
- Coleta de dados de fontes **OSINT** e outras.
- Foco em informações relevantes para os objetivos definidos.
- Exemplos de fontes:
  - Feeds RSS
  - Blogs de segurança
  - Honeypots
  - Relatórios de empresas de segurança
  - Fóruns na Dark Web

### 3. **Análise**
- Transformação de dados brutos em inteligência.
- Correlação de IOCs (Indicadores de Comprometimento).
- Exemplo: relacionar IP malicioso a domínios, scripts e outros IPs.

### 4. **Produção**
- Criação de produtos de inteligência em formatos adequados:
  - Relatórios
  - Alertas
  - E-mails diários
  - Apresentações
- **Actionable intelligence** para áreas técnicas.

### 5. **Disseminação**
- Entrega do produto certo, para a pessoa certa, no momento certo.
- Exemplo: alerta de DDoS deve chegar **antes** do ataque.

---

## 💡 Exemplo Prático: Análise de IOC
- IP malicioso: `192.168.1.2`
- Correlações encontradas:
  - Domínio: `virusdebanco.co.uk`
  - Outros IPs: `192.168.4.8`, `192.168.221.7`, etc.
  - Script executado: `malware.ps1` via PowerShell

---

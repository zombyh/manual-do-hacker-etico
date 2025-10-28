## 📘 Resumo: Plataformas de Threat Intelligence (TIP)

## 📌 O que é uma TIP?
- **Threat Intelligence Platform (TIP)** é uma plataforma usada para coletar, analisar, armazenar e compartilhar informações sobre ameaças cibernéticas.
- Facilita o trabalho do analista de inteligência, centralizando e organizando dados de ameaças.

---

## 🎯 Objetivos das TIPs
- Coletar informações de **OSINT** (Open Source Intelligence).
- Analisar e correlacionar indicadores de comprometimento (**IOCs**).
- Organizar e distribuir inteligência de ameaças para outras ferramentas, como **SIEMs**.

---

## 🧩 Funções Principais de uma TIP

### 1. **Coleta**
- Coleta de IOCs, relatórios de inteligência e outras fontes de dados.

### 2. **Análise**
- Análise de malware via **sandbox**.
- Correlação de eventos e indicadores.

### 3. **Compartilhamento / Disseminação**
- Exportação de dados para sistemas de monitoramento (ex.: SIEM).
- Geração de relatórios em formatos como **PDF**, **STIX**, **Snort**, etc.

---

## 🛠️ Exemplos de Plataformas TIP

| Plataforma | Empresa | Tipo de Licença |
|------------|---------|------------------|
| **Anomali Threat Platform** | Anomali | Paga |
| **ThreatConnect** | ThreatConnect | Gratuita e Paga |
| **ThreatQ** | Threat Quotient | Paga |
| **OpenTIP** | Kaspersky | Gratuita |
| **OTX AlienVault** | AlienVault | Gratuita |
| **MISP** | Open Source | Gratuita |

> Destaque para **MISP**, **ThreatConnect** e **OTX AlienVault** por possuírem versões gratuitas e ampla adoção.

---

## 🔍 Casos de Uso e Funcionalidades

### ThreatConnect
- Busca por IOCs (IP, domínio, e-mail, hash, etc.).
- **Pivoteamento**: partir de um indicador e buscar informações correlacionadas.
- Exemplo: consulta de IP malicioso vinculado a relatórios de malware.

### AlienVault OTX
- Interface similar à ThreatConnect.
- **Pulses**: eventos de ameaça atualizados automaticamente.
- Enriquecimento automático de IOCs com base em feeds.

### MISP
- Plataforma open source para compartilhamento de IOCs.
- Suporte a **STIX**, **Snort**, **Suricata**, **Bro**.
- Integração com feeds de ameaças (ex.: CIRCL, Abuse.ch).
- Geração de regras de IDS a partir de eventos.

---

## 📥 Fontes de Informação: Feeds
- TIPs podem ser alimentadas por **feeds de ameaças**.
- Exemplos de feeds no MISP:
  - CIRCL OSINT Feed
  - Zeus Tracker
  - Emerging Threats
  - Malware Domain List

---

## ✅ Vantagens de Usar uma TIP
- Centralização de inteligência de ameaças.
- Automação da coleta e correlação de IOCs.
- Integração com ferramentas de segurança (SIEM, IDS).
- Redução da sobrecarga do analista.
- Melhoria na resposta a incidentes.

---

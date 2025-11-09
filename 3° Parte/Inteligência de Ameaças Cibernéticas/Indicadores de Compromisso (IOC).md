## 📘 Resumo: Indicadores de Compromisso (IOC)

### 🔍 **O que é um IOC?**
- **IOC** = *Indicator of Compromise* (Indicador de Compromisso).
- São **artefatos ou dados** que permitem identificar atividades maliciosas em um sistema ou rede.
- Servem como **pontos de partida** para investigações de segurança.

---

## 🧩 **Tipos de IOC**

### 1. **IOCs por Comportamento**
- Baseados em **padrões de comportamento** anômalos, não em dados pontuais.
- Exemplos:
  - Tráfego para **regiões incomuns** (ex.: Brasil → Leste Europeu sem motivo).
  - Tráfego em **portas incomuns** (ex.: HTTP na porta 5533).
  - Tráfego **fora do padrão do protocolo** (ex.: campos HTTP ausentes ou malformados).

### 2. **IOCs Nominais**
- Dados **pontuais e específicos** sobre um evento ou artefato.
- Exemplos:
  - Endereços IP
  - Domínios/Subdomínios
  - Hashes criptográficos (MD5, SHA-1, SHA-256)
  - URLs
  - Alterações em registro ou arquivos do sistema

---

## 🛠️ **Ferramentas para Coleta de IOCs**

### 🔎 **Análise de Tráfego de Rede**
| Ferramenta | Descrição |
|------------|-----------|
| Wireshark | Interface gráfica para análise de pacotes (Windows, Linux, Mac) |
| TCPDump | Linha de comando para captura de pacotes (Linux, Mac) |
| Microsoft Message Analyzer | Análise visual de pacotes (Windows) |
| Fiddler | Especializado em tráfego HTTP (Multiplataforma) |
| Network Miner | Foca na extração de artefatos (imagens, arquivos, etc.) |

### 🧪 **Sandbox (Análise Controlada)**
- Executam arquivos suspeitos em ambiente isolado.
- Exemplos:
  - **Hybrid-Analysis**
  - **Any.run**
  - **VirusTotal**
  - **Analyz IO**

---

## 📋 **Exemplos de IOCs Nominais**
- **IP**: `8.8.8[.]8`
- **Domínio**: `malware.cnn[.]com`
- **Hash MD5**: `c6cc8094c2dc07b700ffcc36d64e2138`
- **URL**: `http://g-wyatt[.]com/wp-login.php`
- **Alteração de arquivo**: Criação de `%TEMP%\4KPV6A~1\lock`

> 💡 **Dica**: Use `[.]` no lugar do ponto em URLs e IPs para evitar cliques acidentais.

---

## 🧪 **Estudos de Caso**

### Caso 1: Tráfego HTTP Suspeito
- **Host**: `detectorortal.firefox[.]com`
- **User-Agent**: `Mozilla/5.0 (Windows NT 6.1; Win64; x64; rv:68.0) Gecko/20100101 Firefox/68.0`
- **Análise WHOIS**: Domínio registrado pela Mozilla em 1998 → **não malicioso**.
- **Conclusão**: IOCs comuns, sem indício de malícia.

### Caso 2: Tráfego com Domínio Malicioso
- **Host**: `www.unlimitedgiveaways[.]net`
- **Falta de User-Agent** → Comportamento suspeito.
- **VirusTotal**: 40/61 detecções como malicioso.
- **Conclusão**: Domínio malicioso confirmado.

### Caso 3: Relatório de Sandbox (Any.run)
- **Artefato**: `ruslan4.exe`
- **Hashes** (SHA256, SHA1, MD5)
- **Conexões suspeitas** para IPs na Rússia e Alemanha.
- **URLs de C&C**: `http://rtsdytucgi.temp.swtest[.]ru/gate.php...`

---

## ✅ **Boas Práticas**
- **Sempre “desarme” IOCs** em relatórios usando `[.]`.
- **Valide IOCs** com ferramentas como:
  - `whois` (data de criação é confiável)
  - `VirusTotal`
  - `WhatIsMyBrowser` (para User-Agents)

---

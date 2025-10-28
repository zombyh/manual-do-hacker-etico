## 📘 Resumo: O que é um Indicador de Compromisso (IOC)

## 📌 Apresentação
Esta aula introduz o conceito de **Indicadores de Compromisso (IOCs)** – elementos cruciais para a geração de relatórios de inteligência de ameaças cibernéticas. Aborda tipos de IOCs, uso de sandboxes e enriquecimento de informações.

---

## 🎯 Objetivos
- Identificar o que são IOCs e seus tipos.
- Explicar como **enriquecer IOCs** com dados da internet e sandboxes.
- Descrever como IOCs são usados em **relatórios de inteligência**.

---

## 🔍 O que são IOCs?
IOCs são **dados que identificam atividades maliciosas** em sistemas ou redes. Servem como pontos de partida para investigação e detecção de comprometimentos.

---

## 🧩 Categorias de IOCs

### 1. IOCs por Comportamento
Indicadores baseados em **padrões de comportamento anômalo**, não em dados pontuais.

Exemplos:
- Tráfego para regiões incomuns (ex.: Leste Europeu para um serviço brasileiro).
- Tráfego em **portas não padrão** (ex.: HTTP na porta 5533).
- Tráfego fora do padrão do protocolo (ex.: cabeçalhos HTTP malformados).

### 2. IOCs Nominais
Indicadores **pontuais e específicos** sobre eventos ou artefatos.

Exemplos:
- IPs, domínios, hashes (MD5, SHA-1, SHA-256).
- URLs, tráfego de rede (IP:porta:protocolo).
- Alterações em registro ou arquivos do sistema.

---

## 🛠️ Ferramentas para Coleta de IOCs

### Análise de Tráfego de Rede
| Ferramenta               | Descrição |
|--------------------------|-----------|
| Wireshark                | Analisador gráfico de pacotes (multi-plataforma) |
| TCPDump                  | Linha de comando para captura de pacotes (Linux/Mac) |
| Microsoft Message Analyzer | Análise visual de pacotes (Windows) |
| Fiddler                  | Especializado em tráfego HTTP (multi-plataforma) |
| Network Miner            | Extrai artefatos de tráfego (imagens, arquivos) |

### Sandboxes (Análise Controlada)
- **Hybrid-Analysis**
- **Analyz IO**
- **Any.Run**
- **VirusTotal**

---

## 🛡️ Boas Práticas com IOCs

### “Desarmar” IOCs
Inserir `[ ]` no lugar de `.` em URLs e IPs para evitar cliques acidentais.

Exemplo:
- `site[.]exemplo[.]com`
- `8.8.8[.]8`

---

## 🔎 Estudos de Caso

### Caso 1: Tráfego HTTP – Firefox
- **IOCs Extraídos**:
  - Domínio: `detectportal.firefox[.]com`
  - User-Agent: `Mozilla/5.0 (Windows NT 6.1; Win64; x64; rv:68.0) Gecko/20100101 Firefox/68.0`
- **Análise**:
  - WHOIS confirmou domínio legítimo da Mozilla.
  - User-Agent comum → **IOC não malicioso**.

### Caso 2: Tráfego HTTP – UnlimitedGiveaways
- **IOCs**:
  - Domínio: `www.unlimitedgiveaways[.]net`
  - Ausência de User-Agent
- **Análise**:
  - VirusTotal mostrou associação com malware.
  - Ausência de User-Agent → **comportamento suspeito**.

### Caso 3: Relatório de Sandbox (Any.Run)
- **Artefato**: `ruslan4.exe`
- **IOCs Coletados**:
  - Hashes (SHA256, MD5, SHA1)
  - Domínios DNS: `ip-api[.]com`, `rtstyfuqj.temp.swtest[.]ru`
  - Conexões TCP para IPs suspeitos
  - Requisições HTTP para URLs de C&C

---

## ✅ Conclusões
- IOCs são **essenciais para detecção proativa**.
- Devem ser **contextualizados** e **validados**.
- Ferramentas como **WHOIS**, **VirusTotal** e **sandboxes** são fundamentais.
- IOCs nominais e comportamentais se complementam.

---

## 📚 Referências
- [VirusTotal](https://www.virustotal.com/)
- [Hybrid Analysis](https://www.hybrid-analysis.com/)
- [Any.Run](https://any.run/)
- [WhatIsMyBrowser](https://www.whatismybrowser.com/)
- [WHOIS – Registro.br](https://registro.br/tecnologia/ferramentas/whois/)
- [Wireshark](https://www.wireshark.org/)

---

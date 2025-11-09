## 🎯 Resumo: Aula 09 – Modelo MITRE ATT&CK

### 📌 Objetivos da Aula
- Apresentar o modelo **MITRE ATT&CK** e sua aplicação em CTI.
- Descrever as áreas, táticas e técnicas do modelo.
- Analisar técnicas comuns em cada fase de um ataque cibernético.

---

## 🧩 O que é o MITRE ATT&CK?

- **ATT&CK** = **Adversarial Tactics, Techniques, and Common Knowledge**
- Base de conhecimento pública com **táticas e técnicas** observadas em ataques reais.
- Criado pela **MITRE Corporation** (mesma organização por trás do **CVE**).
- Foco em **comportamento do adversário**, não apenas em vulnerabilidades.

---

## 🗂️ Áreas do ATT&CK

| Área | Descrição |
|------|-----------|
| **Pre-ATT&CK** | Fases pré-ataque: reconhecimento, preparação, desenvolvimento de capacidades. |
| **ATT&CK Enterprise** | Táticas e técnicas para redes corporativas (Windows, Linux, macOS). |
| **ATT&CK Mobile** | Ataques voltados para dispositivos móveis. |
| **ATT&CK Cloud** | Técnicas para ambientes cloud (AWS, Azure, GCP, Office 365). |

> ✅ Foco principal da aula: **ATT&CK Enterprise**

---

## 🧠 Táticas do ATT&CK Enterprise

| Tática | Descrição |
|--------|-----------|
| **Initial Access** | Primeiro acesso ao ambiente (ex.: phishing, exploit público). |
| **Execution** | Executar código malicioso no sistema. |
| **Persistence** | Manter acesso após reinicialização ou troca de senha. |
| **Privilege Escalation** | Obter privilégios mais altos (ex.: admin). |
| **Defense Evasion** | Evitar detecção por ferramentas de segurança. |
| **Credential Access** | Roubar credenciais (senhas, tokens). |
| **Discovery** | Coletar informações sobre o ambiente. |
| **Lateral Movement** | Movimentar-se para outros sistemas na rede. |
| **Collection** | Coletar dados sensíveis para exfiltração. |
| **Exfiltration** | Enviar dados para fora da rede. |
| **Command & Control** | Comunicar-se com servidores do atacante. |

---

## 🔍 Exemplos de Técnicas por Tática

### 🚪 Initial Access
- **T1193 – Spearphishing Attachment**: Phishing com anexo malicioso.
- **T1189 – Drive-by Compromise**: Comprometimento ao visitar site.

### ⚙️ Execution
- **T1053 – Scheduled Task**: Executar via agendador de tarefas.
- **T1086 – PowerShell**: Usar PowerShell para execução de código.

### 🔒 Persistence
- **T1176 – Browser Extensions**: Extensões maliciosas no navegador.
- **T1136 – Create Account**: Criar conta no sistema.

### 🛡️ Defense Evasion
- **T1089 – Disable Security Tools**: Desativar antivírus/ferramentas.
- **T1146 – Clear Logs**: Apagar registros de atividades.

### 🔑 Credential Access
- **T1056 – Keylogging**: Capturar teclas digitadas.
- **T1003 – Credential Dumping**: Extrair credenciais da memória.

### 🌐 Lateral Movement
- **T1075 – Pass the Hash**: Reutilizar hashes de senha.
- **T1076 – Remote Desktop Protocol**: Usar RDP para acessar outros sistemas.

### 📦 Exfiltration
- **T1002 – Data Compression**: Comprimir dados antes do envio.
- **T1041 – Exfiltration Over C2 Channel**: Enviar dados via canal de C2.

### 🕶️ Command & Control
- **T1043 – Common Ports**: Usar portas comuns para evitar suspeita.
- **T1090 – Proxy**: Usar proxies para ocultar tráfego.

---

## 🧪 Estrutura de uma Técnica no ATT&CK

Cada técnica possui:

- **ID**: Ex: T1193
- **Tática**: Ex: Initial Access
- **Plataforma**: Windows, Linux, macOS, etc.
- **Fontes de Dados**: Como detectar (logs, monitoramento, etc.)
- **Mitigação**: Como se proteger
- **Detecção**: Como identificar a técnica
- **Referências**: Links para ataques reais

---

## 🔗 Referências Principais

- [Site Oficial do MITRE ATT&CK](https://attack.mitre.org/)
- [CVE – Common Vulnerabilities and Exposures](https://cve.mitre.org/)
- [ATT&CK for Mobile](https://attack.mitre.org/resources/mobile-introduction/)
- [ATT&CK Roadmap](https://attack.mitre.org/docs/attack_roadmap.pdf)

---

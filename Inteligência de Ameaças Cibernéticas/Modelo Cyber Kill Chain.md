
## 🗡️ Resumo: Modelo Cyber Kill Chain

### 🎯 **O que é o Cyber Kill Chain?**
- Modelo criado pela **Lockheed Martin** em 2011.
- Descreve os **estágios sequenciais** de um ataque cibernético.
- Objetivo: **Compreender e interromper** o ataque em suas fases iniciais.

---

## 🔁 **As 7 Fases do Cyber Kill Chain**

### 1. **Reconhecimento (Reconnaissance)**
- Coleta de informações sobre o alvo (ex.: redes sociais, LinkedIn, Shodan).
- **Objetivo do atacante**: Identificar funcionários, infraestrutura, tecnologias.

### 2. **Armamento (Weaponization)**
- Criação da ameaça: **malware, exploit, payload**.
- Customizado com base nas informações da fase de reconhecimento.

### 3. **Entrega (Delivery)**
- Envio do artefato malicioso para a vítima.
- **Meios comuns**: e-mail de phishing, USB drops, links maliciosos.

### 4. **Exploração (Exploitation)**
- Execução do código malicioso no sistema da vítima.
- Explora vulnerabilidades em software ou engenharia social.

### 5. **Instalação (Installation)**
- Instalação do malware no sistema (ex.: backdoor, trojan).
- Persistência: registro, serviços, arquivos ocultos.

### 6. **Comando e Controle (Command & Control - C2)**
- Estabelecimento de comunicação com servidor remoto.
- O atacante envia comandos e recebe dados.

### 7. **Ações nos Objetivos (Actions on Objectives)**
- Execução do objetivo final: roubo de dados, espionagem, destruição.

---

## 🛡️ **Aplicando Defesa com o Curso de Ações (Course of Action)**

Cada fase do Kill Chain pode ser combatida com ferramentas e táticas específicas:

| Fase | Detectar | Negar | Interromper | Atrasar | Enganar | Conter |
|------|----------|-------|-------------|---------|---------|--------|
| **Reconhecimento** | Web Analytics, IDS | Firewall ACL | - | - | Honeypots | - |
| **Armamento** | NIDS | NIPS | - | - | - | - |
| **Entrega** | Usuário (treinamento) | Anti-spam, Proxy | Sandbox | - | - | - |
| **Exploração** | HIDS | Patch, HIPS | DEP, ASLR | - | - | - |
| **Instalação** | EDR, HIDS | chroot jail | Antivírus | - | - | - |
| **C&C** | NIDS | Proxy, NIPS | EDR | Tarpit | DNS Redirect | Trust Zones |
| **Ações Finais** | EDR, NIDS | DLP, ACL | EDR | - | Honeypot | Segregação de redes |

---

## 🧪 **Exemplo de Caso: Ataque à Empresa ACME**

### Fase 1 – Reconhecimento
- **Ferramentas de defesa**: Shodan, IDS, Honeypots.

### Fase 2 – Weaponization
- **Sem defesa direta** (ocorre no lado do atacante).

### Fase 3 – Delivery
- **Ferramentas**: Treinamento de usuários, anti-spam, proxy, sandbox.

### Fase 4 – Exploitation
- **Ferramentas**: Antivírus, HIPS, patches, DEP/ASLR.

### Fase 5 – Installation
- **Ferramentas**: EDR, antivírus, restrições de acesso.

### Fase 6 – Command & Control
- **Ferramentas**: NIDS, NIPS, proxy, EDR.

### Fase 7 – Actions on Objectives
- **Ferramentas**: EDR, DLP, honeypots, segregação de redes.

---

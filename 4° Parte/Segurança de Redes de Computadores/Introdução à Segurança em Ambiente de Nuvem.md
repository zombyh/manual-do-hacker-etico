## ☁️ Resumo: Introdução à Segurança em Ambiente de Nuvem

### 🏢 1. Data Center vs. Computação em Nuvem

#### 📍 Data Center Tradicional
- Infraestrutura física com servidores e storage.
- Localização geográfica definida.
- Pode ser interno (on-premises) ou externo (terceirizado).
- Custo elevado com hardware, energia, refrigeração e mão de obra.

#### 🌐 Cloud Computing
- Independência geográfica: dados replicados em múltiplos locais.
- Alta disponibilidade e tolerância a falhas.
- Modelo sob demanda: paga-se pelo uso.
- Tipos: **nuvem pública**, **privada** e **híbrida**.

---

### 📦 2. Modelos de Serviço em Nuvem

#### 🧩 IaaS (Infraestrutura como Serviço)
- Oferece infraestrutura virtualizada (servidores, rede, armazenamento).
- Exemplos: AWS EC2, Azure VMs.
- Indicado para:
  - Empresas em crescimento rápido.
  - Demanda volátil (picos de acesso).
- Contraindicado quando há restrições legais para armazenamento externo.

#### 🧩 PaaS (Plataforma como Serviço)
- Ambiente para desenvolvimento e gestão de aplicações.
- Exemplos: Google App Engine, Heroku.
- Ideal para:
  - Desenvolvimento colaborativo.
  - Integração com bancos de dados.
  - Ambientes complexos de aplicação.

#### 🧩 SaaS (Software como Serviço)
- Software acessado via navegador ou app.
- Exemplos: G Suite, Microsoft 365.
- Características:
  - Gerenciamento centralizado.
  - Modelo “um para muitos”.
  - Personalização via APIs.

---

### 🧠 3. Hierarquia da Computação em Nuvem

| Nível            | Descrição                                                                 |
|------------------|---------------------------------------------------------------------------|
| **Cloud Computing** | Data centers centralizados, processamento em larga escala.              |
| **Fog Computing**   | Camada intermediária para pré-processamento, próxima aos dispositivos.   |
| **Edge Computing**  | Processamento no local de origem dos dados (ex.: dispositivos IoT).      |

- **Vantagens**: Redução de latência, melhor uso da banda, processamento local.

---

### 🔐 4. Segurança em Nuvem: Os 7 Pecados Capitais

1. **Perda ou vazamento de dados**
   - Falhas em APIs, gestão de chaves, políticas de destruição.

2. **Vulnerabilidades em tecnologias compartilhadas**
   - Configurações incorretas replicadas em VMs.

3. **Funcionários internos maliciosos**
   - Acesso privilegiado mal gerido.

4. **Desvio de tráfego e sequestro de contas**
   - Ataques a contas de cliente ou administrador.

5. **APIs inseguras**
   - Falhas em interfaces de integração.

6. **Uso indevido da nuvem**
   - Cadastro malicioso, uso para ataques.

7. **Perfil de risco desconhecido**
   - Falta de transparência sobre a infraestrutura.

---

### 🛡️ 5. Categorias de Segurança na Nuvem (CSA)

#### A. Segurança Tradicional
- Ameaças comuns amplificadas na nuvem:
  - Ataques a VMs, phishing, superfície de ataque expandida.
  - Autenticação, autorização e forense.

#### B. Disponibilidade
- Foco em:
  - Uptime, evitar ponto único de falha, integridade computacional.

#### C. Controle de Dados por Terceiros
- Preocupações:
  - Auditabilidade, espionagem, bloqueio de dados (lock-in), transparência.

---

### 🔑 6. Autenticação e Controle de Acesso (AAA)

| Conceito         | Descrição                                                                 |
|------------------|---------------------------------------------------------------------------|
| **Autenticação** | Verifica a identidade do usuário.                                         |
| **Autorização**  | Define o que o usuário pode fazer.                                        |
| **Auditoria**    | Registra e rastreia ações do usuário.                                     |

---

### 🧱 7. Hardware de Segurança em Nuvem

- Uso de:
  - Firewalls de próxima geração (NGFW)
  - IDS/IPS
  - WAF (Web Application Firewall)
  - HSM (Hardware Security Module)
  - DMZ (Zona Desmilitarizada)
  - Sistemas de DDoS Protection

---

### 📚 Referências
- AUGUSTO (2019) – SaaS, PaaS, IaaS
- ZANUTTO – Segurança em Cloud Computing
- KUROSE & ROSS; STALLINGS – Redes e Criptografia

---

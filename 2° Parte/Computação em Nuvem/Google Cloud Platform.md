## 📘 Resumo: – Google Cloud Platform (GCP)

---

### **1. Conceitos Fundamentais do Google Cloud**

#### **O que é Computação em Nuvem?**
- Modelo sob demanda: paga-se apenas pelo que é usado (CPU, memória, armazenamento).
- Elimina a necessidade de gerenciar infraestrutura física (servidores, energia, refrigeração, espaço).
- Oferece escalabilidade e flexibilidade.

#### **Modelos de Serviço:**
- **IaaS (Infraestrutura como Serviço)**: Controle sobre SO, rede, armazenamento. Ex: Compute Engine.
- **PaaS (Plataforma como Serviço)**: Foco no desenvolvimento, sem gerenciar infraestrutura. Ex: Cloud Run, App Engine.
- **SaaS (Software como Serviço)**: Software completo gerenciado pelo provedor. Ex: Gmail, Google Drive.

#### **Regiões e Zonas:**
- **Regiões**: Localizações geográficas com datacenters. Ex: `southamerica-east1` (São Paulo).
- **Zonas**: Divisões dentro de uma região (ex: `a`, `b`, `c`) para alta disponibilidade e redundância.
- **Rede Global Proprietária**: Cabos submarinos do Google conectam datacenters globalmente com alta velocidade e segurança.

---

### **2. Infraestrutura e Aplicações no GCP**

#### **Rede Virtual (VPC – Virtual Private Cloud):**
- Rede global e segura para conectar recursos do GCP.
- **Sub-redes (Subnets)**: Divisões regionais dentro da VPC para organizar IPs e políticas.
- Estratégias:
  - **Acesso por geolocalização**: Usuários acessam o servidor mais próximo.
  - **Disaster Recovery**: Réplicas em múltiplas regiões para tolerância a falhas.

#### **Máquinas Virtuais (Compute Engine):**
- **Famílias de VMs**:
  - **E2**: Econômica (aplicações web, front-end, pequenos bancos).
  - **N2/N1**: Equilibrada (APIs, microsserviços, bancos médios).
  - **Tau T2D**: Otimizada para escalabilidade horizontal.
  - **M1/M2/M3**: Otimizada para memória (bancos em memória, SQL Server).
  - **C2/C**: Otimizada para computação (cargas intensivas).
- **Responsabilidade Compartilhada**:
  - Google: hardware, energia, rede física.
  - Usuário: SO, aplicações, segurança do software.

#### **Aplicações Nativas da Nuvem (Cloud Native):**
- **Stateless**: Sem estado, armazenamento externo (ideal para serverless).
- **Stateful**: Com estado, dados armazenados localmente (requer cuidado com consistência).
- **Serverless**: Cloud Run (PaaS) – escalável sob demanda, pago apenas pelo uso.

---

### **3. Segurança no GCP**

#### **Modelo de Responsabilidade Compartilhada:**
- **IaaS**: Google gerencia hardware; usuário gerencia SO, rede, aplicação.
- **PaaS**: Google gerencia infraestrutura e plataforma; usuário gerencia aplicação.
- **SaaS**: Google gerencia tudo; usuário apenas usa o software.

#### **Ferramentas de Segurança:**
- **IAM (Identity and Access Management)**: Controle de acesso baseado em funções (RBAC).
- **Autenticação Multifator (MFA)**: Camada extra de segurança (SMS, token).
- **Cloud Armor**: Proteção contra DDoS e ataques baseada em IA.
- **reCAPTCHA**: Distingue acesso humano vs. bot.
- **Listas de Bloqueio (Blocklist)**: Restringe acesso por IP ou região.

#### **Conformidade:**
- LGPD, ISO 27001, e outras certificações.
- Datacenters com seis camadas de segurança física.

---

### **4. Operações e Monitoramento**

#### **Monitoramento (Cloud Monitoring):**
- Coleta de métricas (latência, CPU, memória, requisições).
- Logs para auditoria e troubleshooting.
- Alertas e dashboards para prevenção e ação rápida.

#### **DevOps no GCP:**
- **Cloud Build**: CI/CD automatizado.
- **Cloud Deploy**: Entrega contínua.
- **Cloud Repository**: Versionamento de código (Git).

---

### **5. Aplicações Práticas**

#### **Arquitetura de Infraestrutura:**
1. Criar VPC global.
2. Definir sub-redes em regiões.
3. Associar zonas de disponibilidade.
4. Implantar VMs nas sub-redes.

#### **Exemplo: E-commerce com GCP**
- **Banco de Dados**: Cloud SQL (gerenciado, escalável).
- **Checkout Assíncrono**: Pub/Sub para mensageria entre sistemas (estoque, NF, entrega).
- **Vantagem**: Tolerância a falhas, escalabilidade, experiência do usuário.

---

### **7. Considerações Finais**

- O GCP oferece agilidade, escalabilidade e segurança com pagamento por uso.
- Use VPCs globais e sub-redes regionais para alta disponibilidade.
- Adote aplicações stateless e serverless para melhor custo-benefício.
- Monitore recursos com Cloud Monitoring e adote práticas DevOps.

---

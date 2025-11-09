## 📘 Resumo: Segurança em Computação em Nuvem

---

### 1. **Introdução à Segurança em Nuvem**
- **Contexto**: Migração de infraestrutura local (*on-premise*) para nuvem, com terceirização de serviços.
- **Desafio**: Manter princípios de segurança (confidencialidade, integridade, disponibilidade) em ambiente distribuído.
- **Vantagem**: Provedores investem pesado em segurança devido à escala e à necessidade de confiança.

---

### 2. **Fundamentos da Computação em Nuvem (NIST)**
#### Características Essenciais:
1. **On-demand self-service**: Provisionamento automático de recursos.
2. **Broad network access**: Acesso via internet de qualquer dispositivo.
3. **Resource pooling**: Recursos compartilhados e alocados dinamicamente.
4. **Rapid elasticity**: Escalabilidade automática conforme demanda.
5. **Measured service**: Cobrança pelo uso efetivo.

#### Modelos de Serviço:
- **SaaS**: Software como serviço (ex.: Gmail, Salesforce).
- **PaaS**: Plataforma como serviço (ex.: Google App Engine, Azure App Service).
- **IaaS**: Infraestrutura como serviço (ex.: AWS EC2, Azure VM).

#### Modelos de Implantação:
- **Nuvem pública**: Recursos compartilhados (ex.: AWS, Azure, GCP).
- **Nuvem privada**: Uso exclusivo de uma organização.
- **Nuvem híbrida**: Combinação de pública e privada.
- **Nuvem comunitária**: Compartilhada por organizações com interesses comuns.

---

### 3. **Modelo de Responsabilidade Compartilhada**
- **SaaS**: Provedor responsável por quase tudo; cliente cuida de credenciais e acesso.
- **PaaS**: Provedor gerencia plataforma; cliente cuida de aplicações e dados.
- **IaaS**: Provedor gerencia infraestrutura física; cliente cuida de SO, aplicações e dados.

#### Exemplos:
- **SaaS**: Microsoft 365, Google Workspace.
- **PaaS**: AWS Elastic Beanstalk, Azure App Service.
- **IaaS**: Amazon EC2, Google Compute Engine.

---

### 4. **Serviços de Nuvem e Suas Seguranças**
#### a) **Máquinas Virtuais (VMs)**
- Cliente escolhe SO, tamanho da VM, configura rede e armazenamento.
- Responsável por aplicar patches e gerenciar aplicações.

#### b) **Containerização**
- Leve, portátil, rápido (ex.: Docker, Kubernetes).
- Menor overhead que VMs.
- Segurança: Isolamento via namespaces e cgroups.

#### c) **Serverless (FaaS)**
- Ex.: AWS Lambda, Azure Functions.
- Cliente só fornece código; provedor gerencia execução.
- Orientado a eventos.

#### d) **Bancos de Dados Gerenciados**
- Ex.: Amazon RDS, Azure SQL Database.
- Provedor cuida de patches, backups, alta disponibilidade.
- Cliente configura acesso e monitoramento.

#### e) **Armazenamento**
- **Bloco**: Discos virtuais (ex.: Amazon EBS).
- **Arquivo**: Sistemas de arquivos compartilhados (ex.: Amazon EFS).
- **Objeto**: Armazenamento escalável (ex.: Amazon S3).
- **CSI**: Interface para containers (ex.: Kubernetes CSI).

#### f) **Rede**
- **DNS**: Tradução de nomes (ex.: Route 53).
- **CDN**: Entrega de conteúdo (ex.: CloudFront).
- **VPN**: Conexão segura (ex.: Azure VPN Gateway).
- **WAF**: Firewall de aplicação web (ex.: AWS WAF).
- **Proteção DDoS**: Mitigação de ataques (ex.: AWS Shield).

#### g) **Monitoramento e Auditoria**
- **Logs**: Registro de eventos (ex.: AWS CloudTrail).
- **SIEM**: Correlação de eventos (ex.: Splunk, Azure Sentinel).
- **Alertas**: Notificações baseadas em regras.

---

### 5. **Orientações da Cloud Security Alliance (CSA)**
#### Domínios da CSA (v4.0):
1. **Conceitos e Arquiteturas**: Fundamentos e modelos de nuvem.
2. **Governança e Gestão de Risco**: Avaliação de riscos e conformidade.
3. **Aspectos Legais e Contratuais**: Jurisdição, privacidade, LGPD.
4. **Conformidade e Auditoria**: Atendimento a normas e regulamentos.
5. **Governança da Informação**: Controle de dados na nuvem.
6. **BCM e DRP**: Continuidade de negócios e recuperação de desastres.
7. **Segurança de Infraestrutura**: Segurança física e lógica.
8. **Virtualização e Contêineres**: Segurança de hypervisors e containers.
9. **Resposta a Incidentes**: Detecção, resposta e forense.
10. **Segurança de Aplicações**: Desenvolvimento seguro para nuvem.
11. **Criptografia e Dados**: Proteção de dados em repouso e trânsito.
12. **IAM**: Gerenciamento de identidade e acesso.
13. **Segurança como Serviço**: Terceirização de segurança.
14. **Tecnologias Emergentes**: IoT, Big Data, IA.

#### Pilares Arquiteturais da CSA:
- **Infraestrutura**: Computação, rede, armazenamento.
- **Metaestrutura**: Orchestration e gerenciamento.
- **Applistrutura**: Aplicações e serviços.
- **Infoestrutura**: Dados e informações.

---

### 6. **Principais Ameaças e Contramedidas**
#### Ameaças Comuns:
- Acesso não autorizado
- Vazamento de dados
- Ataques DDoS
- Injeção de código
- Configurações inadequadas

#### Contramedidas:
- **Criptografia**: Dados em trânsito e em repouso.
- **IAM**: Controle de acesso granular.
- **Firewalls e WAFs**: Filtragem de tráfego.
- **Backups e Snapshots**: Recuperação de dados.
- **Monitoramento Contínuo**: Detecção de anomalias.

---

### 7. **Dicas**
- Entenda bem o **modelo de responsabilidade compartilhada** por tipo de serviço.
- Saiba diferenciar **SaaS, PaaS, IaaS** e seus níveis de responsabilidade.
- Conheça os **serviços de armazenamento** (bloco, arquivo, objeto).
- Domine os **conceitos de segurança** (CIA: Confidencialidade, Integridade, Disponibilidade).
- Familiarize-se com os **domínios da CSA** e seus focos.
---

### 🧠 Exemplos de Aplicação:
- **IaaS**: Você gerencia o SO; provedor gerencia o hypervisor.
- **PaaS**: Você gerencia o código; provedor gerencia o runtime.
- **SaaS**: Você só usa o software; provedor gerencia tudo.

---

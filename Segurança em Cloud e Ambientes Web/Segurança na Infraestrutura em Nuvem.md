## 🛡️ Segurança na Infraestrutura em Nuvem – Resumo Estruturado

## 📌 Introdução
- A computação em nuvem representa uma **mudança de paradigma** na forma como a TI e a segurança da informação são abordadas.
- Há uma **alta demanda** por profissionais com conhecimentos em nuvem e segurança.
- É essencial compreender modelos de entrega, proteção de dados, identidades, acessos, aspectos legais e conformidade.

---

## ☁️ Fundamentos de Arquitetura em Nuvem

### Definição de Nuvem (NIST)
- Modelo que permite acesso **sob demanda** a recursos compartilhados (redes, servidores, armazenamento, aplicações).
- Características: **escalabilidade**, **flexibilidade**, **custo reduzido**.

### Modelos de Implantação
| Modelo | Descrição | Controle | Riscos Principais |
|--------|------------|----------|-------------------|
| **Pública** | Aberta ao público, custo acessível, pagamento por uso | Baixo | Lock-in, conformidade, exclusão do provedor |
| **Privada** | Infraestrutura dedicada a uma única organização | Total | Custos, complexidade, ataques internos/externos |
| **Comunitária** | Compartilhada por organizações com interesses comuns | Compartilhado | Conformidade, governança, riscos compartilhados |
| **Híbrida** | Combina dois ou mais modelos (ex: público + privado) | Variável | Dificuldade em políticas consistentes, integração complexa |

---

## 🧩 Modelos de Entrega de Serviço

### IaaS (Infrastructure as a Service)
- Cliente controla: **SO, aplicações, dados**.
- Provedor controla: **infraestrutura física**.
- Exemplo: AWS EC2, Azure VMs.

### PaaS (Platform as a Service)
- Cliente controla: **aplicações e dados**.
- Provedor controla: **plataforma, SO, rede**.
- Exemplo: Google App Engine, Heroku.

### SaaS (Software as a Service)
- Cliente controla: **dados e configurações**.
- Provedor controla: **tudo mais**.
- Exemplo: Gmail, Salesforce.

### 🧩 Responsabilidade Compartilhada
- Em todos os modelos, o cliente é **sempre responsável pelos dados e identidades**.
- O provedor é responsável pela **infraestrutura física e plataforma**, conforme o modelo.

---

## 🔐 Conceitos de Segurança em Nuvem

### Criptografia
- Protege dados **em repouso**, **em trânsito** e **em uso**.
- Sem criptografia, o uso da nuvem seria **inviável**.

### Virtualização
- Permite **escalabilidade**, **portabilidade**, **multilocação**.
- Riscos: segurança do **hipervisor**.

### Gestão de Identidades e Acessos (IAM)
- Autenticação, autorização e accounting.
- **Identidade federada**: SSO, SAML, OAuth, OpenID.
- **Autenticação multifatorial**: algo que você sabe, tem, é ou onde está.

### CASB (Cloud Access Security Broker)
- Gateway de segurança entre usuários e nuvem.
- Funções: firewall, DLP, autenticação.

### Auditoria e Conformidade
- Provedores relutam em compartilhar detalhes internos.
- Utilizam **relatórios de auditoria de terceiros**.

### Segurança de Redes
- Segmentação é crucial em ambientes multitenant.
- Controles devem ser **escaláveis** e **monitorados**.

### SLA (Acordo de Nível de Serviço)
- Define metas de serviço e penalidades por descumprimento.

---

## 🗃️ Segurança de Dados em Nuvem

### Ciclo de Vida dos Dados
1. **Criação**: classificação inicial dos dados.
2. **Armazenamento**: controles de acesso, criptografia, backup.
3. **Uso/Manipulação**: monitoramento, controle de acesso.
4. **Compartilhamento**: DLP, IRM.
5. **Arquivamento**: criptografia, gestão de chaves.
6. **Destruição**: sobrescrita, cryptoshredding.

### Classificação de Dados
- Processo de analisar dados para aplicar políticas de segurança.
- Mais crítica na nuvem devido ao ambiente compartilhado.

### Data Mapping
- Identifica onde os dados sensíveis estão armazenados.
- Essencial para conformidade (ex: LGPD, GDPR).

### Data Labeling (Rotulagem)
- Atribuição de categorias aos dados para tratamento adequado.

---

## 🛠️ Tecnologias de Segurança de Dados

| Técnica | Descrição |
|---------|-----------|
| **Criptografia** | Proteção de dados em todos os estados |
| **Gerenciamento de Chaves** | Controle e proteção das chaves criptográficas |
| **Hashing** | Verificação de integridade dos dados |
| **Tokenization** | Substitui dados sensíveis por tokens não sensíveis |
| **DLP** | Prevenção de vazamento de dados |

---

## 👤 Gerenciamento de Identidades e Acessos

### Componentes do IAM
- **Provedores de identidade**: autenticam e autorizam.
- **Serviços de diretório**: gerenciam funções e permissões.

### Conceitos Chave
- **Identificação**: quem você é (ex: usuário).
- **Autenticação**: prova de identidade (ex: senha, biometria).
- **Autorização**: o que você pode acessar.

### SSO (Single Sign-On)
- Login único para múltiplos serviços.
- Usa tokens para autorização.

---

## ⚖️ Aspectos Legais, Riscos e Conformidade

### Legislação Brasileira Relevante
- **LGPD** (Lei Geral de Proteção de Dados)
- **Marco Civil da Internet**
- **Lei dos Crimes Cibernéticos** (Lei Carolina Dieckmann)
- **Lei do Cadastro Positivo**
- **Resolução BC 4.893/2021** (segurança cibernética no setor financeiro)

### Riscos em Nuvem
- Violação de dados
- Conformidade regulatória
- Dependência de um único fornecedor (*vendor lock-in*)
- Interrupção de serviços
- Perda de dados
- Problemas na migração

### Conceitos de Conformidade
- **Residência dos dados**: local físico de armazenamento.
- **Soberania dos dados**: leis do local onde os dados estão.
- **Privacidade dos dados**: proteção de dados pessoais.

---

### Recomendações:
- Estudar a norma **ABNT NBR ISO/IEC 17788:2015**
- Explorar soluções de segurança dos principais provedores (AWS, Azure, GCP)

---

## 📘 Resumo: Segurança em Computação em Nuvem (AWS, Azure & Hardening)

#### **1. Princípios Fundamentais da Segurança em Nuvem (O "Tripé de Ouro")**

A segurança na nuvem é construída sobre três pilares, frequentemente chamados de "Tripé da CIA":
*   **Confidencialidade:** Garantir que os dados só sejam acessíveis por pessoas/autorizações previstas. *Como?* Criptografia, controle de acesso, segredos.
*   **Integridade:** Garantir que os dados e sistemas não sejam alterados de forma não autorizada. *Como?* Hashs, assinaturas digitais, logging e monitoramento.
*   **Disponibilidade:** Garantir que os dados e sistemas estejam acessíveis quando necessários. *Como?* Tolerância a falhas, escalabilidade, proteção contra DDoS.

Além do CIA, dois conceitos são **CRUCIAIS** para provas:
*   **Modelo de Responsabilidade Compartilhada:** Define o que é de responsabilidade do provedor de nuvem (Cloud Provider) e o que é do cliente (Você/Procergs).
    *   **Provedor (AWS/Azure):** Segurança **DA** nuvem (Infraestrutura física, hardware, rede, hipervisor).
    *   **Cliente:** Segurança **NA** nuvem (Dados, sistemas operacionais, configurações de rede, gerenciamento de acesso, criptografia de dados do cliente).
    *   *Você SEMPRE será responsável pelos seus dados e por quem tem acesso a eles.*

*   **Postura de Segurança:** É a avaliação contínua e o aperfeiçoamento da segurança do seu ambiente para mitigar riscos. Envolve conformidade, hardening e monitoramento.

---

#### **2. Tópicos Comuns a AWS e Azure**

*   **Identity and Access Management (IAM):** O centro de tudo. "A identidade é o novo perímetro".
    *   **Princípio do Privilégio Mínimo:** Conceder apenas as permissões estritamente necessárias para realizar uma tarefa.
    *   **Autenticação Multifator (MFA):** Obrigatório para usuários privilegiados (root/admin).
    *   **Auditoria:** Logs de quem fez o quê, quando e de onde (CloudTrail / Azure Activity Log).

*   **Rede e Segurança de Rede:**
    *   **Firewalls:** Security Groups (AWS) e Network Security Groups (NSG - Azure) atuam como firewalls virtuais para instâncias/VMs.
    *   **Segmentação de Rede:** Usar VPC (AWS) / VNet (Azure) para isolar ambientes (ex: produção, desenvolvimento).
    *   **Proteção DDoS:** Serviços nativos como AWS Shield e Azure DDoS Protection.

*   **Criptografia:**
    *   **Em Repouso:** Criptografar dados em discos (EBS, S3) e bancos de dados usando chaves gerenciadas pelo provedor (AWS KMS / Azure Key Vault) ou chaves próprias (Customer-Managed Keys - CMK).
    *   **Em Trânsito:** Usar TLS/SSL para proteger a comunicação entre serviços e usuários.

*   **Logging e Monitoramento:**
    *   **AWS:** Amazon CloudWatch (métricas e logs) + AWS CloudTrail (logs de auditoria de API).
    *   **Azure:** Azure Monitor + Azure Activity Log.
    *   **SIEM:** Integrar esses logs com ferramentas de SIEM para correlação e detecção de ameaças.

*   **Conformidade:** AWS e Azure possuem certificações como SOC 2, ISO 27001, PCI DSS, LGPD/GDPR. A infraestrutura deles é compatível, mas a configuração do *seu* ambiente é sua responsabilidade para estar em conformidade.

---

#### **3. AWS (Amazon Web Services) - Foco em Serviços de Segurança**

*   **IAM (Identity and Access Management):** Gerencia usuários, grupos, roles e políticas.
*   **AWS Organizations:** Para gerenciar múltiplas contas AWS, centralizar políticas (SCP - Service Control Policies) e billing.
*   **Amazon GuardDuty:** Serviço de detecção de ameaças inteligente e contínua que monitora atividades maliciosas.
*   **AWS Shield:** Proteção contra DDoS (Standard é gratuito, Advanced é pago).
*   **AWS WAF (Web Application Firewall):** Protege aplicações web de exploits comuns (SQL Injection, XSS).
*   **Amazon Macie:** Descobre e protege dados sensíveis (ex: PII) usando Machine Learning.
*   **AWS KMS (Key Management Service) & CloudHSM:** Gerenciamento de chaves de criptografia.
*   **AWS Config:** Avalia a configuração dos recursos contra regras definidas (ex: "todo bucket S3 deve ser privado"). Auditagem contínua.
*   **AWS Security Hub:** Agrega findings de diversos serviços de segurança (GuardDuty, Macie, Inspector, etc.) em um painel central.

---

#### **4. Microsoft Azure - Foco em Serviços de Segurança**

*   **Azure Active Directory (Azure AD):** Serviço central de identidade. Vai além do IAM tradicional, com features como Conditional Access e Identity Protection.
*   **Azure Policy:** Similar ao AWS Config, impõe regras organizacionais para recursos (ex: "só permitir VMs de um tamanho específico").
*   **Microsoft Defender for Cloud (antigo Azure Security Center):** Serviço UNIFICADO de segurança. Oferece:
    *   **CSPM (Cloud Security Posture Management):** Recomendações de hardening (baseadas em benchmarks como CIS).
    *   **CWP (Cloud Workload Protection):** Proteção contra ameaças para servidores, App Services, SQL, etc.
*   **Azure Key Vault:** Armazena e gerencia segredos, chaves de criptografia e certificados.
*   **Azure Sentinel:** SIEM nativo na nuvem, com SOAR (orquestração e resposta automatizada).
*   **Azure DDoS Protection:** Proteção contra ataques DDoS (Standard é a versão robusta e paga).
*   **Azure Firewall:** Firewall gerenciado e de alto escalão para proteger redes virtuais.

---

#### **5. Hardening de Ambientes Cloud**

Hardening é o processo de tornar um sistema mais seguro ao eliminar vulnerabilidades e reduzir sua superfície de ataque.

*   **Hardening do Sistema Operacional:**
    *   Seguir benchmarks de segurança reconhecidos (ex: **CIS Benchmarks**).
    *   Remover software e serviços desnecessários.
    *   Aplicar patches de segurança regularmente (usar serviços como **AWS Systems Manager** ou **Azure Update Management**).
    *   Desativar contas padrão e usar senhas complexas.

*   **Hardening de Rede:**
    *   **Princípio do Menor Privilégio em NSGs/Security Groups:** Não usar regras como `0.0.0.0/0` para portas críticas (SSH 22, RDP 3389). Restringir ao máximo o acesso.
    *   Usar **NACLs (AWS)** para uma camada adicional de controle de rede (estático e stateless).
    *   Implementar arquiteturas de rede seguras, como o **padrão de 3 camadas (web, app, data)** com sub-redes distintas.

*   **Hardening de Serviços e Dados:**
    *   **Buckets S3 / Blobs de Armazenamento Azure:** **NUNCA** deixar públicos sem uma necessidade explícita. Usar políticas de bucket e ACLs corretamente.
    *   **Bancos de Dados:** Não expor publicamente. Usar apenas conexões criptografadas. Aplicar autenticação forte.
    *   **Gerenciamento de Segredos:** **NUNCA** armazenar senhas ou chaves API em código ou em repositórios. Usar sempre **AWS Secrets Manager**, **Azure Key Vault** ou serviços similares.

*   **Ferramentas Automatizadas:**
    *   Usar **AWS Config Rules** ou **Azure Policy** para auditar e impor automaticamente configurações seguras.
    *   Scanners de vulnerabilidades: **Amazon Inspector** (AWS) e **Microsoft Defender for Cloud** (Azure) escaneiam instâncias/VMs em busca de vulnerabilidades.

---

#### **6. Dicas:**

1.  **Foque no Modelo de Responsabilidade Compartilhada:** Saiba exatamente onde termina a responsabilidade da AWS/Azure e começa a sua.
2.  **Entenda IAM/Azure AD:** Saber a diferença entre usuário, grupo, role (AWS) e entidade de serviço (Azure) é fundamental.
3.  **Privilégio Mínimo:** Este princípio guia quase todas as melhores práticas de segurança.
4.  **Conheça os Serviços Nativos:** Não é necessário decorar todos, mas saiba a finalidade dos principais: GuardDuty, Defender for Cloud, WAF, KMS/Key Vault.
5.  **Hardening Baseado em CIS:** Aprenda sobre o CIS Benchmark como referência de hardening, para aprofundar seus conhecimentos.
6.  **Pense em Conformidade (LGPD):** Como a nuvem ajuda a estar em conformidade com a LGPD? (Através de criptografia, controle de acesso e auditoria).


## 📘 Resumo para Prova de Concurso – Microsoft Azure (Procergs)

---

### **1. Conceitos Fundamentais do Azure**

#### **Modelos de Nuvem:**
- **Nuvem Pública**: Serviços oferecidos por provedores (Microsoft, Amazon, Google). ✅ Vantagens: custo reduzido, escalabilidade, acesso rápido.
- **Nuvem Privada**: Infraestrutura dedicada a uma única organização. ✅ Maior controle, mas custo mais alto.
- **Nuvem Híbrida**: Combina nuvem pública e privada. ✅ Flexibilidade, extensão da infraestrutura local.
- **Multicloud**: Uso de múltiplos provedores de nuvem. ✅ Evita vendor lock-in, maior resiliência.

#### **Tipos de Serviço:**
- **IaaS (Infraestrutura como Serviço)**: Controle total sobre SO, rede, armazenamento. Ex: VMs Azure.
- **PaaS (Plataforma como Serviço)**: Foco no desenvolvimento, sem gerenciar infraestrutura. Ex: Azure App Service.
- **SaaS (Software como Serviço)**: Software completo gerenciado pelo provedor. Ex: Office 365.

#### **Modelo de Responsabilidade Compartilhada:**
- **Cliente**: Dados, dispositivos, identidades, acesso.
- **Provedor (Azure)**: Infraestrutura física, rede, hosts, datacenters.

---

### **2. Arquitetura e Serviços do Azure**

#### **Contas e Assinaturas:**
- **Assinatura**: Unidade lógica de cobrança e acesso.
- **Grupos de Recursos**: Container para organizar recursos (ex: VMs, redes, bancos). Um recurso pertence a apenas um grupo.
- **Regiões e Zonas de Disponibilidade**:
  - **Regiões**: Áreas geográficas com um ou mais datacenters.
  - **Zonas de Disponibilidade**: Datacenters fisicamente separados dentro de uma região (alta disponibilidade).
  - **Pares de Regiões**: Replicação de dados entre regiões para disaster recovery.

#### **Serviços de Computação:**
- **Máquinas Virtuais (VMs)**: IaaS, controle total do SO.
- **Conjuntos de Escala de VM**: Grupo de VMs idênticas com balanceamento de carga.
- **Azure Functions**: Computação serverless orientada a eventos.
- **Azure App Service**: PaaS para hospedar aplicativos web, APIs, móveis.
- **Contêineres (Azure Container Instances, AKS)**: Leves, escaláveis, ideais para microsserviços.

#### **Serviços de Rede:**
- **Rede Virtual (VNet)**: Rede isolada no Azure.
- **VPN Gateway**: Conexão segura entre redes locais e Azure.
- **ExpressRoute**: Conexão privada e dedicada com a Microsoft.
- **DNS do Azure**: Hospedagem de domínios e resolução de nomes.

#### **Serviços de Armazenamento:**
- **Contas de Armazenamento**: Namespace único para dados (HTTP/HTTPS).
- **Tipos de Conta**:
  - **Uso Geral v2**: Blobs, arquivos, filas, tabelas.
  - **Blobs de Blocos Premium**: Alta performance.
  - **Compartilhamentos de Arquivos Premium**: SMB/NFS.
- **Redundância**:
  - **LRS** (Local): 3 cópias no mesmo datacenter (11 noves).
  - **ZRS** (Zona): 3 zonas na mesma região (12 noves).
  - **GRS/GZRS** (Geográfica): Entre regiões (16 noves).
- **Camadas de Blob**:
  - **Quente**: Acesso frequente.
  - **Frio**: Acesso infrequente (>30 dias).
  - **Arquivo**: Acesso raro (>180 dias).

#### **Identidade e Segurança:**
- **Azure Active Directory (AD)**:
  - Autenticação, SSO, gerenciamento de dispositivos.
  - Integração com AD local.
- **RBAC (Controle de Acesso Baseado em Função)**:
  - Define permissões por função (ex: leitor, contribuidor).
- **Defesa em Profundidade**:
  - Múltiplas camadas de segurança (física, rede, aplicação, dados).

---

### **3. Gerenciamento, Governança e Monitoramento**

#### **Gerenciamento de Custos:**
- **Calculadora de Preços**: Estima custos de recursos.
- **Calculadora de TCO**: Compara custos locais vs. nuvem.
- **Orçamentos e Alertas**: Monitora gastos e evita surpresas.
- **Marcas (Tags)**: Metadados para organizar recursos e custos.

#### **Governança:**
- **Azure Policy**: Define regras de conformidade para recursos.
- **Bloqueios de Recursos**:
  - **CanNotDelete**: Impede exclusão.
  - **ReadOnly**: Impede modificações.
- **Portal de Confiança do Serviço**: Documentação de conformidade (ex: ISO 27001, NIST).

#### **Monitoramento:**
- **Azure Advisor**: Recomendações em custo, segurança, performance.
- **Integridade do Serviço**:
  - **Status do Azure**: Status global dos serviços.
  - **Resource Health**: Saúde individual dos recursos.
- **Azure Monitor**: Coleta, analisa e age sobre dados de recursos.

---

### **4. Aplicações Práticas**

#### **Migrações para o Azure:**
- **Azure Migrate**:
  - Avaliação e migração de servidores, bancos, aplicativos.
  - Integração com ferramentas de terceiros.
  - Migração para VMs, AKS, App Service, etc.

#### **Azure App Service:**
- Hospedagem de aplicativos web, APIs, móveis.
- Suporte a .NET, Java, Node.js, PHP, Python.
- **Vantagens**:
  - Gerenciamento totalmente automatizado.
  - CI/CD integrado.
  - Conformidade com padrões de segurança.

#### **Planos de Serviço (Service Plans):**
- Define poder computacional e recursos para aplicativos.
- Exemplos: B1, S1, P1v3 (com limites de apps por plano).

---

### **5. Verificação de Aprendizado (Respostas)**

1. **Qual modelo de nuvem combina público e privado?**  
   → **Nuvem Híbrida (A)**

2. **Onde uma solução de controle de finanças se enquadra?**  
   → **SaaS (B)**

3. **Quantos grupos de recursos um recurso pode pertencer?**  
   → **Apenas um (A)**

4. **Qual redundância oferece 16 noves de durabilidade?**  
   → **GRS/GZRS (C)**

5. **O que ajuda a organizar recursos por metadados?**  
   → **Marcas (Tags) (A)**

6. **Qual serviço mostra a saúde individual de um recurso?**  
   → **Resource Health (C)**

7. **O que NÃO pode ser migrado com Azure Migrate?**  
   → **Azure AD (A)**

8. **Vantagem do Azure App Service?**  
   → **Serviço totalmente gerenciado (C)**

---

### **6. Considerações Finais**

- O Azure oferece flexibilidade, escalabilidade e economia com modelo OpEx.
- Entenda o modelo de responsabilidade compartilhada para cada serviço.
- Use ferramentas como Azure Policy, Advisor e Monitor para governança e otimização.
- Pratique com a conta gratuita do Azure e explore a documentação oficial.

---

## 📘 Resumo: Arquitetura de Computação em Nuvem

---

### 1. **Introdução à Computação em Nuvem**
- **Definição**: Modelo de serviço que fornece recursos computacionais (armazenamento, processamento, aplicativos) via internet, sob demanda.
- **Vantagens**: Redução de custos, escalabilidade, flexibilidade, acesso remoto.
- **Provedores conhecidos**: AWS, Microsoft Azure, Google Cloud Platform.

---

### 2. **Arquitetura Básica da Nuvem**
A arquitetura é dividida em dois grandes grupos:

#### a) **Front-end**
- Interface do usuário para acessar a nuvem.
- Exemplos: navegadores, dispositivos móveis, tablets.

#### b) **Back-end**
- A própria nuvem, composta por:
  - Servidores
  - Armazenamento
  - Aplicações
  - Serviços de segurança e gerenciamento
  - Cloud runtime (ambiente de execução com hypervisors)
- A comunicação entre front-end e back-end ocorre via internet.

---

### 3. **Componentes da Infraestrutura em Nuvem**
- **Hardware de servidor**: Base física ou virtualizada.
- **Virtualização**: Permite múltiplos ambientes isolados no mesmo hardware.
- **Modelos de serviço**:
  - **IaaS** (Infraestrutura como Serviço)
  - **PaaS** (Plataforma como Serviço)
  - **SaaS** (Software como Serviço)
- **Gerenciamento de nuvem**: Alocação e otimização de recursos.
- **Redes em nuvem**: Conectividade e suporte a aplicações.
- **Segurança**: Criptografia, controle de acesso, proteção de dados.

---

### 4. **Datacenters**
- **Função**: Abrigar servidores, armazenamento e redes de alta performance.
- **Organização física e lógica**: Equipamentos interconectados com redundância e segurança.
- **Exemplos de tecnologias**: NAS (Network Attached Storage), SSDs, HDs, Optane.

---

### 5. **Camada de Servidores**
- **Função**: Hospedar aplicações, serviços e dados.
- **Administração**: Monitoramento, configuração, patches de segurança, backups.
- **Ferramentas**: CloudWatch (AWS), Azure Monitor, Google Cloud Monitoring.
- **Importância**: Garantir alta disponibilidade, desempenho e segurança.

---

### 6. **Modelos de Serviços em Nuvem**
- **Armazenamento**: Ex.: Amazon S3, Google Drive
- **Computação**: Máquinas virtuais, clusters
- **Plataforma**: Ambientes de desenvolvimento (PaaS)
- **Análise de dados**: Big Data, IA, machine learning
- **Desenvolvimento**: APIs, serverless

---

### 7. **IaaS (Infraestrutura como Serviço)**
- Fornece infraestrutura completa: servidores, rede, armazenamento.
- **Cenários comuns**:
  - **Elasticidade**: Ajuste dinâmico de recursos conforme demanda.
  - **Balanceamento de carga**: Distribuição de tráfego para alta disponibilidade.
  - **Alta disponibilidade**: Redundância, replicação, monitoramento.
  - **Multicloud**: Uso de múltiplos provedores.
  - **Nuvem híbrida**: Combina nuvem pública e privada.

---

### 8. **Edge Computing**
- **Conceito**: Processamento de dados próximo à origem (na "borda" da rede).
- **Vantagens**: Redução de latência, economia de banda, resposta em tempo real.
- **Aplicações**: IoT, reconhecimento facial, jogos, realidade aumentada.
- **Relacionamento com Serverless**: Permite execução de funções sem gerenciamento de infraestrutura.

---

### 9. **Estratégias de Migração para a Nuvem (7Rs)**
1. **Rehost** ( Lift and Shift ): Migração sem alterações.
2. **Replatform**: Pequenas adaptações para compatibilidade.
3. **Repurchase** ( Drop and Shop ): Substituição por SaaS.
4. **Refactor/Re-architect**: Reescrever para ser nativo da nuvem.
5. **Retire**: Desativar sistemas desnecessários.
6. **Retain**: Manter localmente temporariamente.
7. **Relocate**: Migração de VMs sem alterações.

---

### 10. **Conclusão e Considerações Finais**
- A nuvem oferece **escalabilidade, elasticidade e pagamento por uso**.
- É mais **econômica, segura e flexível** que infraestrutura local.
- Arquiteturas bem planejadas permitem alta disponibilidade e desempenho.
- Migração exige planejamento e escolha da estratégia correta.

---

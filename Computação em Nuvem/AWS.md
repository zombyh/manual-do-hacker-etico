
## 📘 Resumo para Prova de Concurso – AWS (Procergs)

---

### **1. Introdução à AWS**
- A AWS é a principal plataforma de computação em nuvem do mundo.
- Modelo de **responsabilidade compartilhada**: a AWS cuida da infraestrutura física; o usuário, dos recursos provisionados.
- A infraestrutura global é organizada em **Regiões** e **Zonas de Disponibilidade (AZs)**.
- Recomenda-se usar **pelo menos duas AZs** para alta disponibilidade.

---

### **2. Computação na AWS**

#### **Opções de Computação:**
- **EC2 (Máquinas Virtuais)**: IaaS, controle total, ideal para aplicações monolíticas.
- **ECS/EKS (Containers)**: CaaS, ideal para microsserviços e escalabilidade.
- **Lambda (Serverless)**: FaaS, execução por evento, sem gerenciamento de servidor.

#### **Amazon EC2:**
- **AMI (Amazon Machine Image)**: Template com SO e software pré-instalado.
  - Pode ser customizada e reutilizada.
  - Custo apenas dos snapshots associados.
- **Tipos de Instâncias**:
  - **Uso Geral**: t4g, m5, m6i (balanceamento entre CPU e memória).
  - **Otimizadas para Computação**: c5, c6g (alta performance de CPU).
  - **Otimizadas para Memória**: r5, r6g (grandes volumes de dados em memória).
- **Par de Chaves**: usado para acesso SSH (Linux) ou descriptografia de senha (Windows).
- **Security Groups**: firewall virtual que controla tráfego de entrada e saída.
- **User Data**: script executado no primeiro boot da instância.

---

### **3. Armazenamento na AWS**

#### **Amazon EBS (Block Storage):**
- Volumes persistentes anexados a instâncias EC2.
- **Tipos**:
  - **SSD**: io1/io2 (alta IOPS), gp3/gp2 (uso geral).
  - **HDD**: st1 (throughput), sc1 (cold storage).
- **Snapshots**: backups incrementais armazenados no S3.

#### **Amazon S3 (Object Storage):**
- Armazenamento ilimitado, altamente durável (99,999999999%).
- **Buckets**: contêineres para objetos.
- **Versionamento**: mantém múltiplas versões de um objeto.
- **Classes de Armazenamento**:
  - **Standard**: acesso frequente.
  - **Standard-IA**: acesso infrequente.
  - **Glacier**: archive (Instant, Flexible, Deep Archive).

#### **Amazon EFS (File Storage):**
- Sistema de arquivos escalável e compartilhado entre múltiplas instâncias.

---

### **4. Rede e Conectividade**

#### **Amazon VPC (Virtual Private Cloud):**
- Rede virtual isolada dentro da AWS.
- **Sub-redes**: divisões dentro de uma VPC (públicas ou privadas).
- **IPs Reservados**: 5 endereços reservados por sub-rede (ex.: 10.0.0.1 para roteador).
- **Gateway de Internet**: permite acesso à internet para recursos em sub-redes públicas.
- **NAT Gateway**: permite que instâncias em sub-redes privadas acessem a internet.

#### **IP Elástico:**
- Endereço IPv4 público estático e reassociável.
- Cobrado se não estiver associado a uma instância em execução.

#### **Tabelas de Rota:**
- Definem para onde o tráfego de rede é direcionado.
- Rota padrão: `0.0.0.0/0` → Gateway de Internet.

---

### **5. Aplicações Práticas**

#### **Site Estático com S3:**
- Hospedagem de arquivos HTML, CSS, JS.
- Configuração:
  - Habilitar "Static website hosting".
  - Liberar acesso público via bucket policy.
  - Fazer upload dos arquivos.

#### **Site Dinâmico com EC2:**
- Usar AMI pré-configurada (ex.: Wordpress da Bitnami).
- Configurar Security Group para portas 80 (HTTP) e 443 (HTTPS).
- Acessar via DNS público da instância.

---

### **6. Boas Práticas e Dicas**
- Use pelo menos **2 AZs** para alta disponibilidade.
- Prefira **AMIs validadas** pela AWS ou parceiros.
- Restrinja regras de Security Group para IPs conhecidos.
- Use **snapshots** para backup de volumes EBS.
- Monitore custos e utilize classes de armazenamento adequadas no S3.

---

### **7. Verificação de Aprendizado (Respostas)**
1. **Tipos de instâncias de uso geral**: t4g, m6i, m4 (Alternativa D).
2. **Definição de AMI**: Imagem para instanciar VMs na AWS (Alternativa A).
3. **Classe de EBS gp3**: Volumes de boot, aplicações de baixa latência (Alternativa A).
4. **Durabilidade do S3**: 99,999999999% (Alternativa E).
5. **IP utilizável em sub-rede /24**: 10.0.0.254 (Alternativa B).
6. **Mínimo de AZs para alta disponibilidade**: 2 (Alternativa B).
7. **S3 hospeda apenas sites estáticos** (Alternativa C).
8. **Vantagem de AMIs verificadas**: Garantia de origem confiável (Alternativa C).

---

### **8. Conclusão**
- A AWS oferece flexibilidade, escalabilidade e economia.
- Mantenha-se atualizado: novos serviços e preços são lançados frequentemente.
- Estude complementos como **RDS**, **Aurora**, e **CodeDeploy** para arquiteturas avançadas.

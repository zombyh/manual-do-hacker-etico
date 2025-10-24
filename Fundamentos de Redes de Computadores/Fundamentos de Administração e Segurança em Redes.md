
## 📘 Resumo para Estudo – Fundamentos de Administração e Segurança em Redes

---

### 1. **Riscos de Segurança em Redes de Computadores**

#### **Conceitos Fundamentais (ABNT NBR ISO/IEC 27001:2013)**
- **Ameaça**: Causa potencial de um incidente indesejado.
- **Ativo**: Qualquer coisa com valor para uma organização (dados, equipamentos, pessoas).
- **Ataque**: Ação que tenta destruir, alterar, roubar ou acessar indevidamente um ativo.

#### **Propriedades da Segurança da Informação (CID +)**
- **Confidencialidade**: Informação acessível apenas a autorizados.
- **Integridade**: Dados precisos e completos, sem adulteração.
- **Disponibilidade**: Acesso aos dados quando necessário.
- **Autenticidade**: Garantia da identidade do emissor/receptor.
- **Não repúdio**: Impossibilidade de negar autoria.
- **Confiabilidade**: Comportamento esperado do sistema.
- **Legalidade**: Conformidade com leis (ex.: LGPD, Marco Civil da Internet).

#### **Tipos de Ataques**
- **Ativos**: Alteram recursos do sistema (interrupção, modificação, fabricação, repetição).
- **Passivos**: Interceptam informações sem alterá-las.
- **Classificação por:**
  - **Ponto de iniciação**: Interno ou externo.
  - **Método de entrega**: Direto ou indireto (com terceiros).
  - **Objetivo**: Interceptação, interrupção, modificação, etc.

#### **Etapas de um Ataque (Ciberkill Chain)**
1. **Reconhecimento**: Coleta de informações.
2. **Armamento**: Desenvolvimento da arma (exploit).
3. **Entrega**: Envio do exploit (ex.: e-mail, USB).
4. **Exploração**: Exploração de vulnerabilidade.
5. **Instalação**: Instalação de backdoor (RAT).
6. **Comando e Controle**: Comunicação com o sistema infectado.
7. **Ações no Objetivo**: Roubo de dados, ataques, etc.

---

### 2. **Softwares e Equipamentos para Diminuir Riscos**

#### **Segurança Física**
- Objetivo: Proteger instalações e equipamentos.
- Exemplos:
  - Sistemas de refrigeração e combate a incêndio.
  - Sala-cofre.
  - No-breaks e geradores.
  - Proteção contra alagamento.

#### **Segurança Lógica**
Mecanismos baseados em software para garantir CID:

1. **Autenticação**: Senhas, tokens, biometria, autenticação de dois fatores.
2. **Controle de Acesso**: Restringe acesso a usuários autorizados.
3. **Criptografia**:
   - **Simétrica**: mesma chave (ex.: AES).
   - **Assimétrica**: chave pública e privada (ex.: RSA).
4. **Funções de Hash**: Garantem integridade (ex.: MD5, SHA).
5. **Assinatura Digital**: Combina hash e criptografia assimétrica.
6. **Certificado Digital**: Vincula chave pública a uma entidade (AC → ICP-Brasil).
7. **VPN**: Túnel criptografado para comunicação segura.
8. **Firewall, IDS/IPS, Antivírus**: Proteção contra invasões e malwares.

---

### 3. **Arquitetura de Gerenciamento de Redes (FCAPS)**

Modelo ISO para gerenciamento de redes:

#### **F – Fault (Falhas)**
- Detecção, isolamento e correção de falhas.
- Subsistemas: reativo e proativo.

#### **C – Configuration (Configuração)**
- Controle de configurações de hardware e software.
- Documentação e versionamento.

#### **A – Accounting (Contabilidade)**
- Controle de uso de recursos (ex.: franquia de internet).
- Evita monopolização de recursos.

#### **P – Performance (Desempenho)**
- Monitoramento de capacidade, tráfego, throughput.
- Avaliação de diagnóstico e tendências.

#### **S – Security (Segurança)**
- Controle de acesso e conformidade com política de segurança.
- Envolve todas as camadas da rede.

---

### 4. **Conclusão e Recomendações**

- A segurança e o gerenciamento de redes são **essenciais** para garantir operação contínua e confiável.
- É necessário combinar **mecanismos físicos e lógicos**.
- Use ferramentas de gerenciamento baseadas no modelo **FCAPS**.
- Mantenha-se atualizado com normas, boas práticas e incidentes reportados (ex.: CERT.br).

---

### 📚 Materiais de Apoio (Recomendados no Documento)
- Cartilha de Segurança para Internet (CERT.br)
- White Paper da Cisco sobre gerenciamento de redes
- ITIL – Boas práticas para gerenciamento de serviços de TI
- Normas ABNT NBR ISO/IEC 27001 e 27002

---

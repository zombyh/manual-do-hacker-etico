
## 📘 Resumo: Princípios da Segurança e Ciclo de Vida da Informação

### 1. **Conceitos Básicos: Dado vs. Informação**
- **Dado**: Valor bruto, sem contexto (ex.: números, textos isolados).
- **Informação**: Dado contextualizado, com valor agregado (ex.: relatório analítico, gráfico com interpretação).
- **Valor da informação**: Surge a partir do contexto e da aplicabilidade.

---

### 2. **Ciclo de Vida da Informação**
A informação passa por quatro etapas, todas requiring proteção:
1. **Criação**: Geração da informação.
2. **Transporte**: Movimentação entre locais ou sistemas.
3. **Manuseio**: Uso, modificação ou processamento.
4. **Descarte**: Eliminação segura (ex.: trituração, sobregravação).

📌 **Exemplo de falha**: Roubo de laptop com dados não criptografados de veteranos dos EUA (falha no manuseio).

---

### 3. **Pilares da Segurança da Informação (CID)**
- **Confidencialidade**: Acesso apenas a autorizados.
- **Integridade**: Dados precisos e completos, sem alterações não autorizadas.
- **Disponibilidade**: Acesso quando necessário.

#### Aspectos Complementares:
- **Autenticidade**: Garantia de origem legítima.
- **Legalidade**: Conformidade com leis e normas.
- **Não repúdio (Irretratabilidade)**: Impossibilidade de negar autoria.

---

### 4. **Segurança Física**
- **Objetivo**: Proteger equipamentos, infraestrutura e ambientes contra acesso não autorizado ou danos.
- **Exemplos de controles**:
  - Cancelas, catracas, crachás, RFID.
  - Biometria (digital, facial).
  - Câmeras, extintores, sprinklers.
  - Geradores, nobreaks, redundância de conexão.
  - BIOS com senha, bloqueio de boot.

📌 **Camadas de segurança**: Como uma "cebola", com múltiplas barreiras físicas justapostas.

---

### 5. **Segurança Lógica**
- **Objetivo**: Proteger dados e sistemas por meio de software e algoritmos.
- **Exemplos de controles**:
  - Senhas, listas de controle de acesso (ACL).
  - Criptografia (simétrica e assimétrica).
  - Firewalls, IDS/IPS, VPNs.
  - Funções de hash (verificação de integridade).

#### Criptografia:
- **Simétrica**: mesma chave para cifrar e decifrar (ex.: AES, Blowfish).
- **Assimétrica**: chave pública e privada (ex.: RSA, Diffie-Hellman).

#### Firewalls:
- Políticas:
  - **Negar por padrão**: Só permite tráfego explicitamente autorizado.
  - **Zonas de segurança**: Ex.: DMZ (área desmilitarizada) para servidores web.

---

### 6. **Controle de Acesso**
- **Objetivo**: Garantir que apenas usuários autorizados acessem recursos.
- **Mecanismos**:
  - Autenticação (senhas, biometria, tokens).
  - Autorização (permissões baseadas em papéis – RBAC).
  - Auditoria (logs de acesso).

---

### 7. **Exemplos de Aplicação Prática**
- **Criptografia em pen drives**: Compactar com senha (ex.: 7-zip) para proteger confidencialidade.
- **Descarte seguro**: Trituração de mídias magnéticas.
- **Redundância**: Múltiplos links de internet e geradores para garantir disponibilidade.
- **Firewall com DMZ**: Isolar servidores web para reduzir riscos.

---

### 8. **Conclusão**
- A segurança da informação deve ser aplicada em **todas as etapas** do ciclo de vida da informação.
- **Segurança física** e **lógica** são complementares e devem ser implementadas em camadas.
- Controles como criptografia, firewalls, biometria e políticas de acesso são essenciais para proteger os pilares da segurança (CID).

---

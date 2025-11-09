## 📘 Resumo: Criptografia II – Segurança de Redes I

### 🔑 1. Processo de Proteção no Envio de Chaves
- A criptografia visa **codificar dados** para garantir **confidencialidade** e **integridade**.
- Dois tipos principais:
  - **Criptografia Simétrica**: mesma chave para cifrar e decifrar.
  - **Criptografia Assimétrica**: utiliza par de chaves (pública e privada).

---

### ⚖️ 2. Prós e Contras dos Processos de Criptografia

#### 🔁 Criptografia Simétrica
- **Prós**:
  - Mais rápida e simples.
  - Ideal para transações online.
- **Contras**:
  - Se a chave for interceptada, todas as mensagens são comprometidas.
  - Algoritmos mais simples → menor poder de processamento necessário.
- **Exemplos**: AES, Blowfish, RC4, 3DES, IDEA.

#### 🔄 Criptografia Assimétrica
- **Prós**:
  - Mais segura.
  - Chave pública é distribuída; chave privada é mantida em segredo.
- **Contras**:
  - Mais lenta e exige maior poder de processamento.
- **Exemplos**: RSA, DSA, ECC, Diffie-Hellman.

---

### 📜 3. Outros Processos de Criptografia

#### ✍️ Assinatura Digital
- Substitui a assinatura física.
- Propriedades essenciais:
  - Autenticidade
  - Integridade
  - Irretratabilidade (não repúdio)

#### 🏛️ Certificado Digital
- Arquivo eletrônico que associa uma entidade à sua chave pública.
- Emitido por uma **Autoridade Certificadora (AC)**.
- Funciona como uma “identidade digital”.
- Contém:
  - Dados do emissor e do dono
  - Chave pública
  - Validade
  - Assinatura digital da AC

#### 🔗 Cadeia de Certificados
- Hierarquia de confiança:
  - **AC Raiz** → **AC Intermediária** → **AC Emissora**
- Certificados autoassinados podem ser usados de forma legítima ou maliciosa.

#### 🌐 PKI (Public Key Infrastructure)
- Infraestrutura que gerencia certificados e chaves públicas.
- Inclui:
  - Emissão, validação e revogação de certificados.
  - Padrões como X.509.

---

### 🔒 4. SSL e TLS
- Protocolos para comunicação segura na internet.
- **HTTPS** = HTTP + SSL/TLS (dados criptografados).
- **HTTP** = texto trafega em claro (sem segurança).

---

### 💾 5. Criptografia de Máquinas Virtuais (VMs)
- Discos virtuais podem ser criptografados.
- Chaves são armazenadas em **HSMs (Hardware Security Module)**.
- Fluxo típico:
  1. Criação da chave no cofre
  2. Configuração da criptografia
  3. Ativação da criptografia nos discos

---

### 🗃️ 6. Cofres de Senhas (HSM)
- Hardware para armazenamento seguro de chaves criptográficas.
- Funções principais:
  - Geração e armazenamento seguro de chaves
  - Blindagem contra exposição
  - Suporte a funções criptográficas (assinatura, criptografia, etc.)

#### 🛡️ Capacidades de Segurança
- Autodestruição em caso de violação.
- Atende a padrões como **FIPS 140-2 Nível 3**.

#### 🔄 Alta Disponibilidade
- Fontes redundantes
- Componentes substituíveis
- Balanceamento de carga

#### 🔐 Aplicações que Usam HSM
- Sistemas com SSL/TLS
- Assinatura de código e documentos
- Bancos de dados
- Máquinas virtuais
- Criptografia de dados

---

### 📌 7. Padrões e Algoritmos em HSMs
- **Padrões**: FIPS 140-2, FIPS 186-4, MCT-7 (ICP-Brasil)
- **Algoritmos Suportados**:
  - Assimétricos: RSA, DSA, Diffie-Hellman, ECC
  - Simétricos: AES, DES, 3DES, RC2, RC4, RC5
  - Hash: SHA-1, SHA-2

---

### ❓ Perguntas de Revisão (Atividade)
1. O que é um certificado digital?
2. O que acontece com um HSM em tentativa de violação?
3. O que é uma PKI?
4. O que a AC faz com um certificado não confiável?
5. Quais aplicações usam cofre de senha?

---

### 📚 Referências
- CERT.br – Cartilha de Segurança para Internet
- Microsoft Docs – Criptografia de Discos em VMs
- Kurose & Ross; Stallings – Criptografia e Segurança de Redes

---

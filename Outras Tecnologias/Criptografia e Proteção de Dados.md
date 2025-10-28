
## 📘 Resumo: Criptografia e Proteção de Dados

#### **1. Conceitos Fundamentais de Criptografia**

*   **O que é:** Ciência e arte de escrever ou resolver códigos. Seu objetivo é proteger a **confidencialidade**, **integridade** e **autenticidade** da informação.
*   **Dados em Repouso (Data at Rest):** Dados armazenados (ex: em um banco de dados, disco rígido, NAS). São protegidos por criptografia de disco, TDE (Transparent Data Encryption), etc.
*   **Dados em Trânsito (Data in Transit):** Dados trafegando pela rede (ex: entre o navegador e o servidor, entre dois servidores). São protegidos por protocolos como TLS/SSL, VPNs, SSH.
*   **Criptografia Simétrica vs. Assimétrica:** A distinção mais importante a ser entendida.

---

#### **2. Criptografia Simétrica (Chave Secreta)**

*   **Conceito:** Usa a **mesma chave** para cifrar (criptografar) e decifrar (descriptografar). A segurança depende totalmente de que a chave permaneça secreta.
*   **Vantagem:** Muito **rápida** e eficiente para criptografar grandes volumes de dados.
*   **Desvantagem:** **Problema da Distribuição de Chaves** - Como compartilhar a chave secreta de forma segura com a outra parte?
*   **Algoritmo mais importante:**
    *   **AES (Advanced Encryption Standard):**
        *   É o padrão ouro atual e amplamente adotado mundialmente.
        *   Usa tamanhos de chave de **128, 192 ou 256 bits**. AES-256 é considerado extremamente robusto e é usado para proteger informações ultrassecretas.
        *   É um algoritmo de **bloco** (opera em blocos de dados de 128 bits).
        *   **Uso Comum:** Criptografia de dados em repouso (ex: arquivos, discos, bancos de dados) e também é a base para criptografar o canal em protocolos como TLS (para dados em trânsito).

---

#### **3. Criptografia Assimétrica (Chave Pública/Privada)**

*   **Conceito:** Utiliza um **par de chaves** matematicamente vinculadas: uma **Chave Pública** (que pode ser compartilhada com todos) e uma **Chave Privada** (que deve ser guardada em segredo pelo dono).
    *   O que é criptografado com a **Chave Pública** só pode ser descriptografado com a **Chave Privada** correspondente.
    *   O que é criptografado com a **Chave Privada** (chamado de "assinatura") só pode ser descriptografado/verificado com a **Chave Pública** correspondente.
*   **Vantagem:** Resolve o **problema da distribuição de chaves**. Não é necessário compartilhar um segredo previamente.
*   **Desvantagem:** É **computacionalmente lenta** (pode ser de 100 a 1000 vezes mais lenta que a simétrica). Não é prática para criptografar grandes volumes de dados diretamente.
*   **Algoritmo mais importante:**
    *   **RSA (Rivest–Shamir–Adleman):**
        *   O algoritmo de criptografia assimétrica mais comum.
        *   Sua segurança baseia-se na dificuldade de fatorar grandes números primos.
        *   **Tamanhos de chave típicos:** 2048 ou 4096 bits. Chaves menores que 2048 bits são consideradas inseguras hoje em dia.
*   **Principais Usos:**
    1.  **Estabelecimento Seguro de Sessão (TLS/SSL):** Para negociar e trocar uma chave simétrica de forma segura, que será usada para a comunicação principal (o "melhor dos dois mundos").
    2.  **Assinatura Digital:** Garantir a **autenticidade** e **integridade** de uma mensagem ou software. (Ex: "Este documento foi realmente enviado por João e não foi alterado").
    3.  **Criptografia de Pequenos Dados:** Como enviar uma chave simétrica de forma segura.

---

#### **4. Infraestrutura de Chaves Públicas (PKI - Public Key Infrastructure)**

*   **O que é:** Um conjunto de hardware, software, políticas e procedimentos necessários para criar, gerenciar, distribuir, usar, armazenar e revogar **Certificados Digitais**.
*   **Problema que resolve:** Como ter certeza de que uma **Chave Pública** realmente pertence à pessoa/entidade que diz ser? A PKI resolve isso com **Autoridades Certificadoras**.
*   **Componentes Principais:**
    *   **Autoridade Certificadora (CA - Certificate Authority):** Entidade confiável de terceiros (ex: Let's Encrypt, DigiCert, Sectigo) ou própria (CA interna) que **emite** e **assina** certificados digitais. Ela é a âncora de confiança.
    *   **Certificado Digital:** É um documento eletrônico que associa uma identidade (ex: `www.procergs.rs.gov.br`) a uma **Chave Pública**. Ele é **assinado digitalmente** pela CA, atestando sua validade.
    *   **Autoridade de Registro (RA - Registration Authority):** Responsável por verificar a identidade de quem solicita um certificado antes de a CA emitir.
    *   **Lista de Certificados Revogados (CRL - Certificate Revocation List):** Uma lista, mantida pela CA, de certificados que foram revogados (cancelados) antes de sua data de expiração. Protocolos como **OCSP (Online Certificate Status Protocol)** são usados para verificar em tempo real se um certificado é válido.

---

#### **5. Resumo Prático: Como Tudo Se Conecta (Exemplo: HTTPS)**

Quando você acessa um site com `https://`, acontece o seguinte ("SSL/TLS Handshake"):

1.  **O cliente conecta ao servidor** e solicita sua identidade.
2.  **O servidor envia seu Certificado Digital** (que contém sua chave pública e é assinado por uma CA confiável).
3.  **O navegador verifica o certificado:**
    *   A assinatura da CA é válida?
    *   O certificado está na CRL/é válido no OCSP?
    *   O nome do site no certificado confere com o que foi acessado?
4.  **Criptografia Assimétrica (RSA):** Se o certificado for válido, o navegador **gera uma chave simétrica aleatória** (chamada de "session key") e a **criptografa usando a Chave Pública do servidor** do certificado. Só o servidor, com sua Chave Privada, pode descriptografar isso.
5.  **Criptografia Simétrica (AES):** Agora que ambos (navegador e servidor) possuem a mesma **chave simétrica de sessão**, eles trocam todos os dados da navegação usando um algoritmo rápido como o **AES**. A conexão segura está estabelecida.

---

### **Dicas para a Prova (Criptografia):**

*   **Memorize a Diferença Chave:**
    *   **Simétrica:** **1 chave** (AES) -> **RÁPIDA** -> para **dados**.
    *   **Assimétrica:** **2 chaves** (RSA) -> **LENTA** -> para **chaves, autenticação e assinaturas**.
*   **Entenda o Papel de Cada Algoritmo:**
    *   **AES:** O "trabalho pesado" de criptografar a comunicação.
    *   **RSA:** O "porteiro seguro" que permite a troca da chave do AES de forma segura.
*   **Saiba o que é a PKI:** Foque em entender o papel da **Autoridade Certificadora (CA)** e do **Certificado Digital**. A CA é quem garante a confiança na internet.
*   **Relacione os Conceitos:** Pense em como a criptografia protege tanto **dados em trânsito** (TLS, que usa AES e RSA) quanto **dados em repouso** (criptografia de disco, que geralmente usa AES).

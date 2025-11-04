
# 🔐 Resumo: Criptografia I

## 🎯 Objetivos da Aula
- Definir criptografia e seu funcionamento.
- Identificar onde a criptografia é aplicada.
- Explicar processos de cifragem, decifragem e codificação.

---

## ❓ O que é Criptografia?
- **Definição**: Sistema de algoritmos matemáticos que codificam dados para que apenas o destinatário possa ler.
- **Objetivo**: Garantir **confidencialidade, integridade e autenticidade** da informação.
- **Contexto**: Necessidade de proteção em um mundo cada vez mais conectado.

> 💡 *“A criptografia é um dos melhores métodos para protegermos a privacidade.”* – Fiorim (2015)

---

## 🧠 Como Funciona a Criptografia?
- **Chave**: Elemento essencial para cifrar e decifrar.
- **Processo**:
  - **Texto simples** → **Cifragem** → **Texto cifrado** → **Decifragem** → **Texto original**
- **Sem a chave**, a mensagem é ilegível.

---

## 🔑 Tipos de Criptografia

### 1. Criptografia Simétrica
- **Mesma chave** para cifrar e decifrar.
- Também chamada de **criptografia de chave secreta**.
- **Exemplos**: AES, DES, 3DES.

### 2. Criptografia Assimétrica
- Usa um **par de chaves**: pública e privada.
- **Chave pública**: cifra a mensagem.
- **Chave privada**: decifra a mensagem.
- **Exemplos**: RSA, Diffie-Hellman.

### 3. Função Resumo (Hash)
- Gera um **valor único e fixo** a partir de qualquer informação.
- **Irreversível**: não é possível obter o original a partir do hash.
- **Usos**: verificação de integridade, assinaturas digitais.
- **Exemplos**: SHA-1, SHA-256, MD5.

---

## 🌍 Onde a Criptografia é Usada?
| Aplicação | Exemplo |
|-----------|---------|
| **Internet Banking** | Transações seguras via HTTPS |
| **Mensagens** | WhatsApp (criptografia de ponta a ponta) |
| **Dispositivos** | iPhone (criptografia de dados) |
| **Redes Sociais** | Autenticação de sessão |
| **Conexões** | Wi-Fi, VPNs |

---

## 📜 Evolução Histórica da Criptografia
- **Egito (1900 a.C.)**: Uso de hieróglifos fora do padrão.
- **Cifra de César**: Substituição de letras (3 posições).
- **Máquina Enigma**: Usada na Segunda Guerra.
- **Colossus**: Primeiro computador para quebra de códigos.
- **1976**: Diffie e Hellman criam a criptografia de chave pública.
- **Anos 90**: Surgem RSA, AES, SHA.

---

## ⚠️ Ameaças e Violações Comuns
1. **Interceptação**: Terceiro captura a mensagem.
2. **Modificação**: Conteúdo é alterado durante o trânsito.
3. **Falsificação**: Ator malicioso se passa por um sistema legítimo.
4. **Negação**: Remetente nega o envio da mensagem.

---

## 🛡️ Por que Precisamos de Criptografia?
- Proteger **identidade e privacidade**.
- Garantir **integridade dos dados**.
- Assegurar **autenticidade e não repúdio**.
- **Ativar sempre**: A criptografia deve estar sempre ligada, não apenas quando “necessário”.

---

## 🔐 Protocolos e Algoritmos por Área (Stallings, 2014)

| Área | Finalidade | Exemplos |
|------|------------|----------|
| **Criptografia Simétrica** | Proteger conteúdo de mensagens | AES, DES |
| **Criptografia Assimétrica** | Proteger chaves e assinaturas | RSA, ECC |
| **Algoritmos de Integridade** | Proteger contra alterações | SHA-256, MD5 |
| **Protocolos de Autenticação** | Verificar identidade | CHAP, OAuth |

---

## ✅ Conceitos-Chave
- **Cifragem (E)**: \( E(M) = C \)
- **Decifragem (D)**: \( D(C) = M \)
- **Texto Simples**: Mensagem original.
- **Texto Cifrado**: Mensagem codificada.
- **Algoritmo (Cifra)**: Função matemática para cifrar/decifrar.

---

## 🧩 Modelo AAA (Autenticação, Autorização, Auditoria)
- **Autenticação**: Verificar identidade.
- **Autorização**: Definir permissões.
- **Auditoria**: Registrar ações (logs).

---

## 📚 Referências
- FIORIM (2015) – Criptografia para Iniciantes
- STALLINGS (2014) – Criptografia e Segurança de Redes
- CERT.br – Cartilha de Segurança para Internet

---

## 🎬 Indicação Cultural
- **Filme**: *O Jogo da Imitação* (Enigma) – sobre Alan Turing e a quebra da cifra nazista.

---

### 🧠 Próximos Temas:
- Programas de criptografia
- Protocolos de segurança
- Assinatura digital
- Certificado digital

---

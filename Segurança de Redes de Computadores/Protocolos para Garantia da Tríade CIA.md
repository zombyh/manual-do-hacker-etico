
## Resumo: Protocolos para Garantia da Tríade CIA

## 🎯 Objetivo da Aula
- Analisar e empregar protocolos de segurança.
- Explicar como os protocolos garantem **Confidencialidade, Integridade e Disponibilidade (CIA)**.

---

## 📡 O que é um Protocolo?
- Conjunto de regras que controla a comunicação entre sistemas.
- Pode ser implementado via hardware, software ou ambos.
- Propriedades típicas:
  - Detecção de conexão física.
  - Handshaking.
  - Formatação de mensagens.
  - Controle de erros e término de sessão.

---

## 🌐 Pilha de Protocolos TCP/IP
| Camada          | Exemplos de Protocolos                          |
|------------------|-------------------------------------------------|
| Aplicação        | HTTP, HTTPS, DNS, FTP, SSH, SMTP, SNMP         |
| Transporte       | TCP, UDP, SCTP                                  |
| Rede             | IP, ICMP, IPsec                                 |
| Física/Enlace    | Ethernet, Wi-Fi, PPP                            |

---

## 🔒 Protocolos de Segurança por Camada

### 🛡️ Camada de Rede
#### **IPsec (Internet Protocol Security)**
- Fornece **privacidade**, **autenticidade** e **integridade** no nível IP.
- **Modos de operação**:
  - **Transporte**: Criptografa apenas o payload.
  - **Tunelamento**: Criptografa o pacote inteiro (cabeçalho + payload).
- Usa **AH (Authentication Header)** e **ESP (Encapsulating Security Payload)**.

#### **ICMP (Internet Control Message Protocol)**
- Usado para relatórios de erro e testes de conectividade (ex: `ping`).

---

### 🔐 Camada de Transporte/Aplicação

#### **SSL/TLS**
- Fornece comunicação segura entre cliente e servidor.
- Usa **certificados digitais** e criptografia de chave pública.
- Base do **HTTPS**.

#### **SSH (Secure Shell)**
- Acesso remoto criptografado (substituto seguro do Telnet).
- Usado também para transferência segura de arquivos (**SFTP**).

#### **HTTPS (HTTP Secure)**
- HTTP sobre SSL/TLS.
- Porta 443.
- Garante **confidencialidade** e **integridade** na web.

#### **SFTP (SSH File Transfer Protocol)**
- Transferência de arquivos sobre túnel SSH.
- Porta 22.

#### **FTPS (FTP Secure)**
- FTP com SSL/TLS.
- Usa certificados digitais.

---

## 🧩 Protocolos de Autenticação e Gerência

### **RADIUS**
- Fornece **AAA**: Autenticação, Autorização e Contabilização.
- Usado em ISPs e redes corporativas.
- Portas: 1812 (autenticação), 1813 (contabilização).

### **TACACS+**
- Protocolo de autenticação para dispositivos de rede.
- Usa porta **TCP 49**.

---

## 🧠 Mecanismos de Garantia da CIA

### 🔏 Confidencialidade
- **Criptografia**:
  - Dados em trânsito: SSL/TLS, SSH, IPsec.
  - Dados em repouso: OpenPGP, criptografia de disco.
- **Autenticação**: Dois fatores, certificados digitais.

### ✅ Integridade
- **Funções de hash** e **assinaturas digitais**.
- Protocolos: FTPS, HTTPS, SFTP, WebDAVs.

### 📈 Disponibilidade
- **Clusters de Alta Disponibilidade (HA)**:
  - Ativo-Passivo: Servidor de failover.
  - Ativo-Ativo: Balanceamento de carga.

---

## 🧪 Exemplos de Ferramentas
- **JSCAPE MFT Server**: Solução integrada com suporte a FTPS, SFTP, HTTPS, OpenPGP, autenticação de dois fatores, DLP e HA.

---

## ❓Atividade de Revisão (Respostas Sugeridas)
1. **SFTP**: Usa criptografia via túnel SSH.
2. **SSH**: Oferece acesso remoto criptografado, substituindo Telnet.
3. **IPsec**: Tunelamento seguro com modos de transporte e túnel.
4. **SSH**: Usa criptografia simétrica, assimétrica e de chave pública.
5. **TACACS**: Usa **TCP porta 49**.

---

## 📚 Referências Principais
- KUROSE, J.; ROSS, K. *Redes de Computadores e a Internet*.
- STALLINGS, W. *Criptografia e Segurança de Redes*.
- RFCs: 1180 (TCP/IP), 6071 (IPsec), 1492 (TACACS).

---

## 🧩 Palavras-Chave para Obsidian
```
#redes #segurança #protocolos #CIA #criptografia #IPsec #SSH #HTTPS #RADIUS #TACACS #alta-disponibilidade #TCP-IP
```

---

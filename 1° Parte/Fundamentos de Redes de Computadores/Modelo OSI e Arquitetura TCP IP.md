## 📘 Resumo: Modelo OSI e Arquitetura TCP/IP

---

### 1. **Divisão da Estrutura das Redes em Camadas**

#### **Objetivo**
Facilitar a complexidade da comunicação em redes dividindo as funções em **camadas**, cada uma com responsabilidades específicas.

#### **Elementos de uma Camada**
- **Serviço**: O que a camada faz (ex.: verificação de erros).
- **Interface**: Ponto de comunicação entre camadas adjacentes.
- **Protocolo**: Como a camada executa o serviço (regras implementadas).

#### **Comunicação**
- **Vertical**: Dados descem (origem) ou sobem (destino) pela pilha de camadas.
- **Horizontal**: Comunicação virtual entre camadas do mesmo nível em dispositivos diferentes, por meio de **cabeçalhos**.

#### **Encapsulamento**
Cada camada adiciona um cabeçalho à unidade de dados recebida da camada superior, formando uma **PDU** (Unidade de Dados de Protocolo). No destino, ocorre o **desencapsulamento**.

---

### 2. **Modelo OSI (Open Systems Interconnection)**

#### **7 Camadas** (da mais alta para a mais baixa):

| Camada          | Função Principal                                                                 | Exemplos de Protocolos/Serviços                     |
|------------------|----------------------------------------------------------------------------------|-----------------------------------------------------|
| **Aplicação**    | Interface com o usuário; serviços de rede (web, e-mail, FTP)                    | HTTP, SMTP, FTP, DNS                                |
| **Apresentação** | Tradução, criptografia, compressão de dados                                      | SSL/TLS, MPEG, JPEG                                 |
| **Sessão**       | Estabelece, gerencia e encerra sessões; controle de diálogo e sincronização      | NetBIOS, RPC                                        |
| **Transporte**   | Entrega processo a processo; controle de erro, fluxo e conexão                   | TCP, UDP                                            |
| **Rede**         | Roteamento; entrega host a host; endereçamento lógico                           | IP, ICMP, OSPF                                      |
| **Enlace**       | Entrega nó a nó; controle de erro, fluxo e acesso ao meio; endereçamento físico | Ethernet, PPP, Wi-Fi (IEEE 802.11)                  |
| **Física**       | Transmissão de bits pelo meio; especificações elétricas e físicas               | Cabos, fibras, rádio, modulação                     |

#### **Divisão em Grupos**
- **Camadas superiores (5–7)**: Suporte ao usuário.
- **Camada de transporte (4)**: Conexão entre usuário e rede.
- **Camadas inferiores (1–3)**: Operações de rede.

---

### 3. **Arquitetura TCP/IP**

#### **4 Camadas** (simplificada):

| Camada             | Função Principal                                     | Protocolos Principais                         |
|---------------------|------------------------------------------------------|-----------------------------------------------|
| **Aplicação**       | Equivalentes às camadas 5–7 do OSI                   | HTTP, DNS, SMTP, FTP, DHCP                    |
| **Transporte**      | Entrega processo a processo                           | TCP (confiável) e UDP (não confiável)         |
| **Internet**        | Roteamento e endereçamento lógico                    | IPv4, IPv6, ICMP, ARP                         |
| **Acesso à Rede**   | Equivalentes às camadas 1–2 do OSI                   | Ethernet, Wi-Fi, PPP                          |

#### **Comparação com o OSI**
- O TCP/IP é mais prático e focado em protocolos.
- As funções das camadas de **apresentação** e **sessão** são absorvidas pela camada de **aplicação**.
- A camada de **acesso à rede** engloba as funções de **enlace** e **física**.

#### **Principais Protocolos**
- **TCP**: Orientado à conexão, confiável, com controle de fluxo e erro.
- **UDP**: Não orientado à conexão, sem confiabilidade, ideal para aplicações em tempo real.
- **IP**: Serviço de melhor esforço (não confiável), responsável pelo roteamento.

---

### 4. **Conceitos-Chave para a Prova**

#### **PDUs por Camada**
- Aplicação: **Mensagem**
- Transporte: **Segmento** (TCP) ou **Datagrama** (UDP)
- Rede: **Pacote**
- Enlace: **Quadro**
- Física: **Bits**

#### **Endereçamento**
- **Porta**: Identifica processos (camada de transporte).
- **IP**: Endereço lógico (camada de rede).
- **MAC**: Endereço físico (camada de enlace).

#### **Modos de Transmissão**
- **Simplex**: Um sentido.
- **Half-Duplex**: Dois sentidos, mas não simultaneamente.
- **Full-Duplex**: Dois sentidos simultaneamente.

---

### 📚 Materiais de Apoio
- ITU (International Telecommunication Union)
- IEEE 802 (Ethernet, Wi-Fi)
- Livro: "Redes de Computadores" – Behrouz Forouzan
- RFCs e documentação do IETF

---

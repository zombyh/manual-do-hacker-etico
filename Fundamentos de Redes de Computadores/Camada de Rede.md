
# 📘 Camada de Rede

---

## 📌 1. Introdução

A camada de rede é responsável pelo **roteamento** de pacotes da origem ao destino em redes de computadores. Ela define endereçamento, escolhe rotas e lida com a interconexão de redes heterogêneas.

---

## 🌐 2. Conceitos Básicos da Camada de Rede

### 🧠 Funções Principais
- **Endereçamento**: define um esquema universal (ex.: IP).
- **Roteamento**: escolhe o melhor caminho para os pacotes.
- **Comutação**: encaminhamento de pacotes em roteadores.

### 📦 Unidade de Dados
- **Pacote**: unidade de dados da camada de rede (cabeçalho + dados).

### 🔁 Comutação de Pacotes
- **Store-and-Forward**: roteador recebe o pacote completo antes de encaminhar.
- **Repasse (forwarding)**: decisão local (por interface) com base na tabela de repasse.
- **Roteamento (routing)**: decisão global (algoritmos) para preencher a tabela de repasse.

### 🧩 Circuitos Virtuais vs. Datagramas
| **Circuito Virtual (CV)** | **Datagrama** |
|---------------------------|---------------|
| Orientado à conexão | Sem conexão |
| Rota pré-definida | Rota dinâmica |
| Pacotes chegam em ordem | Pacotes podem chegar fora de ordem |
| Ex.: ATM, MPLS | Ex.: IP |

---

## 🔢 3. Endereçamento IP

### 📍 Endereço IPv4
- 32 bits (ex.: `192.168.1.1`)
- Notação decimal pontuada.

### 🧱 CIDR (Classless Inter-Domain Routing)
- Notação: `A.B.C.D/X` (ex.: `192.168.1.0/24`)
- `X`: número de bits do prefixo de rede.
- Permite alocação flexível de endereços.

### 🧮 Máscara de Rede
- Define quais bits são de rede e quais são de host.
- Ex.: `255.255.255.0` = `/24`

### 🏷️ Endereços Especiais
- **Rede**: todos os bits de host = 0 (ex.: `192.168.1.0`)
- **Broadcast**: todos os bits de host = 1 (ex.: `192.168.1.255`)
- **Privados**: `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`

### 🔄 NAT (Network Address Translation)
- Traduz endereços privados para públicos.
- Permite que vários hosts usem um único IP público.
- Tabela de mapeamento mantida pelo roteador.

---

## 🔧 4. Protocolos de Controle

### 🔍 ARP (Address Resolution Protocol)
- Mapeia IP para endereço MAC (camada de enlace).
- Broadcast: “Quem tem o IP X?”
- Resposta: “Eu tenho, MAC Y.”

### 🛠️ DHCP (Dynamic Host Configuration Protocol)
- Atribui configurações de rede automaticamente:
  - IP, máscara, gateway, DNS.
- Estados do cliente: INIT, SELECTING, REQUESTING, BOUND, RENEWING, REBINDING.

### 📡 ICMP (Internet Control Message Protocol)
- Mensagens de controle e erro.
- Exemplos:
  - `Echo Request/Reply` (ping)
  - `Destination Unreachable`
  - `Time Exceeded`
  - `Redirect`

---

## 🧭 5. Algoritmos de Roteamento

### 📈 Classificação
- **Adaptativos**: dinâmicos, respondem a mudanças.
- **Não adaptativos**: estáticos, rotas pré-definidas.
- **Globais**: conhecimento completo da rede (ex.: OSPF).
- **Descentralizados**: apenas informações locais (ex.: RIP).

### 🧠 Dijkstra (Estado de Enlace)
- Calcula caminhos mais curtos a partir de um nó.
- Usa custos (hops, delay, etc.).
- Cada roteador conhece a topologia completa.

### 📊 Vetor de Distância (ex.: RIP)
- Cada roteador compartilha sua tabela com vizinhos.
- Atualizações periódicas.
- Pode sofrer com convergência lenta e loops.

### 🏢 Roteamento Hierárquico
- Divide rede em regiões.
- Reduz tamanho das tabelas de roteamento.
- Ex.: BGP (Border Gateway Protocol) na Internet.

---

## ✅ 6. Pontos Importantes

- **CIDR** permite alocação eficiente de IPs.
- **NAT** resolve escassez de IPv4.
- **ARP** resolve IP → MAC.
- **DHCP** automatiza configuração de rede.
- **ICMP** é usado para diagnóstico (ping, traceroute).
- **Dijkstra** é usado em OSPF (estado de enlace).
- **RIP** é um protocolo de vetor de distância.
- **BGP** é usado para roteamento entre sistemas autônomos.

---

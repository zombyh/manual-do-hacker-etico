
# 📘 Resumo: Camadas de Aplicação e Transporte

---

## 📌 1. Introdução

As camadas de **aplicação** e **transporte** são fundamentais para a comunicação em redes. Enquanto a camada de aplicação lida com os processos dos usuários (e-mails, navegação, etc.), a camada de transporte garante a entrega confiável ou rápida dos dados.

---

## 🏗️ 2. Arquiteturas de Aplicação

### 👥 Cliente-Servidor
- **Cliente**: solicita serviços.
- **Servidor**: fornece serviços.
- Exemplos: HTTP, SMTP, FTP.
- Pode haver múltiplos clientes e um ou poucos servidores.

### 🔄 P2P (Peer-to-Peer)
- Todos os nós são igualmente capazes (clientes e servidores).
- Exemplos: BitTorrent, Skype.
- Escalável e descentralizado.

---

## 🌐 3. Protocolos da Camada de Aplicação

### 🔍 Definição
Um protocolo de aplicação define:
- Tipos de mensagens (requisição, resposta).
- Sintaxe dos campos.
- Semântica dos campos.
- Regras de envio e resposta.

### 📡 Exemplos de Protocolos
- **HTTP**: transferência de páginas web.
- **SMTP**: envio de e-mails.
- **POP3/IMAP**: recebimento de e-mails.
- **DNS**: resolução de nomes para IPs.
- **FTP**: transferência de arquivos.

---

## 📧 4. Serviços de Aplicação na Internet

### 🌍 HTTP (HyperText Transfer Protocol)
- Usa TCP.
- Sem estado (stateless).
- Mensagens: GET, POST, PUT, DELETE, etc.
- Códigos de resposta: 200 (OK), 404 (Not Found), etc.

### 📨 SMTP (Simple Mail Transfer Protocol)
- Envio de e-mails.
- Usa TCP.
- Comandos: HELO, MAIL FROM, RCPT TO, DATA.

### 📥 POP3 e IMAP
- **POP3**: baixa e-mails para o cliente (remove do servidor).
- **IMAP**: mantém e-mails no servidor (acesso remoto).

### 🔤 DNS (Domain Name System)
- Traduz nomes (ex: `google.com`) em IPs.
- Estrutura hierárquica: `.com`, `.org`, `.br`, etc.
- Usa UDP para consultas.
- Tipos de registros: A, MX, CNAME, NS.

---

## 🚚 5. Camada de Transporte

### 🎯 Objetivo
- Oferecer comunicação **fim a fim** entre processos.
- Dois serviços principais:
  - **Orientado à conexão** (TCP): confiável.
  - **Sem conexão** (UDP): rápido.

### 🔗 Multiplexação e Demultiplexação
- **Multiplexação**: vários processos usando a mesma conexão.
- **Demultiplexação**: entrega dos dados ao processo correto via **portas**.

### 🧾 Portas
- Números de 16 bits (0–65535).
- **Portas conhecidas**: 0–1023 (ex: 80 HTTP, 25 SMTP).
- **Portas registradas**: 1024–49151.
- **Portas dinâmicas**: 49152–65535.

---

## 📦 6. Protocolos de Transporte

### 🚀 UDP (User Datagram Protocol)
- **Sem conexão**.
- **Rápido**, mas não confiável.
- Cabeçalho simples: porta origem, porta destino, tamanho, checksum.
- Usado em: DNS, VoIP, streaming.

### 🔒 TCP (Transmission Control Protocol)
- **Orientado à conexão**.
- **Confiável**: controle de fluxo, congestionamento, retransmissão.
- **Full-duplex** e **ponto a ponto**.
- Estabelece conexão com **three-way handshake** (SYN, SYN-ACK, ACK).
- Usa **janela deslizante** para controle de fluxo.

#### 🧩 Cabeçalho TCP
- Porta origem e destino.
- Número de sequência e confirmação.
- Flags: SYN, ACK, FIN, RST, PSH, URG.
- Tamanho da janela, checksum, opções.

#### ⚙️ Controle de Congestionamento
- Algoritmos: **Slow Start**, **Congestion Avoidance**, **Fast Retransmit**.

---

## ✅ 7. Pontos Importantes

- **HTTP**: stateless, métodos GET/POST, códigos de status.
- **SMTP**: comando DATA, envio de e-mails.
- **DNS**: consultas iterativas/recursivas, registros A/MX.
- **TCP vs UDP**: confiabilidade vs velocidade.
- **Portas**: 80 (HTTP), 443 (HTTPS), 25 (SMTP), 53 (DNS).
- **Three-way handshake**: SYN, SYN-ACK, ACK.
- **Janela deslizante**: controle de fluxo no TCP.

---

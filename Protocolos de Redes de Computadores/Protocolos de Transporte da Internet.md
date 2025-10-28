## 🧠 Resumo: Protocolos de Transporte da Internet

## 📌 Introdução
- **Objetivo**: Compreender o funcionamento dos protocolos de transporte (TCP e UDP), sua análise e aplicação em redes e sistemas distribuídos.
- **Público-alvo**: Administradores de rede, desenvolvedores de sistemas distribuídos.
- **Ferramentas sugeridas**: Wireshark para captura e análise de pacotes.

---

## 🌐 Camada de Transporte

### Função e Posição no Modelo de Rede
- Localiza-se entre a camada de aplicação e a camada de rede.
- Oferece comunicação **fim a fim** entre processos em hospedeiros distintos.
- **Modelos de referência**:
  - **OSI**: Camada 4 (entre sessão e rede).
  - **TCP/IP**: Presta serviços diretamente à aplicação.

### Serviços Oferecidos
- **Comunicação fim a fim**: Abstrai a complexidade da rede.
- **Multiplexação/demultiplexação**: Vários processos compartilham a mesma conexão de rede.
- **Controle de fluxo e erro**.
- **Tipos de serviço**:
  - **Orientado à conexão** (ex: TCP): Confiável, com estabelecimento e encerramento de conexão.
  - **Sem conexão** (ex: UDP): Rápido, sem garantias.

---

## 🔁 Multiplexação e Demultiplexação
- **Portas**: Identificadores de processos (ex: 80 para HTTP, 53 para DNS).
- **Multiplexação**: Várias aplicações enviam dados pela mesma conexão.
- **Demultiplexação**: Entrega dos dados ao processo correto no destino.

---

## 📦 UDP – User Datagram Protocol

### Características
- **Sem conexão**, não confiável.
- **Rápido**, baixo overhead.
- **Orientado a mensagens**: Preserva limites das mensagens.
- **Cabeçalho**: 8 bytes.
  - Campos: Porta de origem, porta de destino, tamanho, checksum.

### Aplicações Típicas
- DNS, SNMP, TFTP, VoIP, streaming.

### Limitações
- Tamanho máximo do segmento: 65.515 bytes.
- Sem controle de fluxo, congestionamento ou retransmissão.

---

## 🔗 TCP – Transmission Control Protocol

### Características
- **Orientado à conexão**.
- **Confiável**: Entrega garantida, ordenada e sem erros.
- **Full-duplex**: Transmissão bidirecional simultânea.
- **Fluxo de bytes**: Não preserva limites de mensagens.
- **Controle de fluxo e congestionamento**.

### Formato do Segmento
- **Cabeçalho**: 20 bytes + opções.
- **Campos principais**:
  - Portas de origem e destino
  - Número de sequência e confirmação
  - Flags: SYN, ACK, FIN, RST, PSH, URG
  - Tamanho da janela
  - Checksum

---

## 🤝 Estabelecimento e Encerramento de Conexão TCP

### Three-Way Handshake
1. **Cliente → Servidor**: SYN, SEQ = X
2. **Servidor → Cliente**: SYN + ACK, SEQ = Y, ACK = X+1
3. **Cliente → Servidor**: ACK, SEQ = X+1, ACK = Y+1

### Encerramento (Four-Way Handshake)
- Cada lado envia FIN e recebe ACK.
- Conexões são encerradas independentemente em cada sentido.

---

## 📡 Política de Transmissão do TCP

### Números de Sequência e Confirmação
- **Número de sequência**: Posição do primeiro byte no fluxo.
- **Número de confirmação**: Próximo byte esperado (confirmação cumulativa).

### Retransmissão
- **Timeout**: Retransmissão após temporizador expirar.
- **Duplicatas**: Três ACKs duplicados disparam retransmissão rápida.

---

## 🚦 Controle de Fluxo no TCP

### Janela Deslizante
- **Tamanho da janela**: Quantidade de bytes que podem ser enviados sem confirmação.
- **Evita estouro de buffer no receptor**.
- **Window probes**: Evitam bloqueio eterno.

---

## 🚨 Controle de Congestionamento no TCP

### Objetivo
- Evitar sobrecarga da rede.
- Balancear uso de banda e evitar perdas.

### Mecanismos
- **Janela de congestionamento (cwnd)**: Limita tráfego com base na rede.
- **Partida lenta (Slow Start)**: cwnd dobra a cada RTT até perda ou ssthresh.
- **Prevenção de congestionamento**: Aumento linear de cwnd.
- **Recuperação rápida**: Após 3 ACKs duplicados.

### Algoritmo
- **Slow Start → Congestion Avoidance → Fast Recovery**.
- **Gráfico "dentes de serra"**: Aumento até perda, depois recomeça.

---

## 🛠️ Análise com Wireshark

### UDP
- Cabeçalho simples, sem flags.
- Fácil identificação de portas e checksum.

### TCP
- Identificar handshake, números de sequência, flags, janelas.
- Analisar retransmissões e controle de fluxo.

### Casos de Estudo
- Transferência de arquivos.
- Tentativa de conexão com porta fechada (RST).
- Estabelecimento e encerramento de conexões.

---

## ✅ Conclusão

- **UDP**: Ideal para aplicações que priorizam velocidade e simplicidade.
- **TCP**: Garante confiabilidade, ordem e controle de fluxo/congestionamento.
- **Wireshark**: Ferramenta essencial para análise e troubleshooting.
- **Controle de congestionamento**: Fundamental para a saúde da rede.

---

## 🔗 Tópicos para Explorar
- RFC 768 (UDP)
- RFCs 793, 1122, 1323, 2018, 2581 (TCP)
- RFC 5681 (Controle de Congestionamento TCP)
- Algoritmos Go-Back-N e Repetição Seletiva
- Wireshark: filtros, análise de fluxos, estatísticas.

---

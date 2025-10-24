
## 📘 Resumo para Concurso – Redes de Computadores e Internet

---

### 1. **Introdução à Internet**
- A internet é uma rede global que conecta bilhões de dispositivos (notebooks, smartphones, sensores, etc.).
- Revolucionou a comunicação, trabalho, comércio e entretenimento.
- É composta por:
  - **Sistemas finais (hosts)**: dispositivos dos usuários (clientes e servidores).
  - **Redes de acesso**: conectam os sistemas finais ao primeiro roteador.
  - **Núcleo da rede**: roteadores e enlaces de alta velocidade que interconectam as redes.

---

### 2. **Sistemas Finais (Hosts)**
- **Clientes**: dispositivos dos usuários (ex: PCs, smartphones).
- **Servidores**: máquinas que fornecem serviços (ex: web, e-mail, streaming).
- O que define um servidor é o **software**, não o hardware.

---

### 3. **Redes de Acesso**
- Conectam os hosts ao roteador de borda.
- Tipos:
  - **Meios guiados**: cabos (fibra ótica, par trançado, coaxial).
  - **Meios não guiados**: wireless (Wi-Fi, celular, satélite).
- Exemplos de tecnologias:
  - DSL (linha telefônica)
  - Cabo coaxial (TV a cabo)
  - FTTH (fibra até a casa)
  - Acesso discado (obsoleto)
  - Redes sem fio (Wi-Fi, 4G/5G)

---

### 4. **Núcleo da Rede**
- Composto por roteadores e enlaces de alta velocidade.
- Organizado por **Provedores de Serviço de Internet (ISPs)**:
  - **ISP local**: atende uma área pequena (cidade).
  - **ISP regional**: conecta vários ISPs locais.
  - **ISP de nível 1**: abrangência nacional/global.
- **Ponto de Presença (PoP)**: local onde ISPs se interconectam.
- **Multi-homing**: ISP se conecta a mais de um provedor para redundância.
- **IXP (Internet Exchange Point)**: local onde ISPs trocam tráfego diretamente (ex: ix.br no Brasil).

---

### 5. **Parâmetros de Avaliação de Redes**

#### A. **Atrasos**
- **Atraso de processamento**: tempo para examinar o cabeçalho do pacote.
- **Atraso de fila**: tempo de espera no buffer do roteador.
- **Atraso de transmissão**: tempo para enviar todos os bits pelo enlace.
- **Atraso de propagação**: tempo para o bit percorrer o meio físico.
- **Atraso total**: soma de todos os atrasos.

#### B. **Perda de Pacotes**
- Ocorre quando o buffer do roteador está cheio → pacote é descartado.
- Aplicações como streaming toleram perdas; transferência de arquivos, não.

#### C. **Vazão (Throughput)**
- Taxa de transferência de dados (bits/segundo).
- Depende da capacidade do enlace e do tráfego concorrente.

#### D. **Ferramentas de Diagnóstico**
- **Traceroute (Tracert)**: mostra rota e atrasos entre origem e destino.

---

### 6. **Arquitetura em Camadas**

#### Modelo OSI (7 camadas)
1. **Aplicação**: serviços de rede (HTTP, SMTP, DNS).
2. **Apresentação**: tradução, criptografia, compressão.
3. **Sessão**: controle de sessão e sincronização.
4. **Transporte**: entrega confiável (TCP, UDP).
5. **Rede**: roteamento e endereçamento lógico (IP).
6. **Enlace**: comunicação entre nós adjacentes (Ethernet, Wi-Fi).
7. **Física**: transmissão de bits (sinais elétricos, óticos).

#### Arquitetura TCP/IP (5 camadas)
1. Aplicação
2. Transporte
3. Rede
4. Enlace
5. Física

#### Encapsulamento
- Cada camada adiciona um cabeçalho ao pacote:
  - Aplicação → mensagem
  - Transporte → segmento
  - Rede → datagrama
  - Enlace → quadro
  - Física → bits

---

### 7. **Histórico da Internet**
- **Década de 1960**: ARPANET (comutação de pacotes), primeiro e-mail.
- **Década de 1970**: TCP/IP desenvolvido por Vinton Cerf e Robert Kahn.
- **Década de 1980**: DNS, domínios (.com, .org), NSFNET.
- **Década de 1990**: World Wide Web (Tim Berners-Lee), navegadores, comércio eletrônico.
- **Anos 2000**: banda larga, redes sociais, cloud computing.
- **Anos 2010–2020**: IoT, 5G, satélites Starlink.

---

### 8. **Conceitos-Chave para a Prova**
- **Internet**: rede de redes baseada em TCP/IP.
- **ISP**: provedor de acesso à internet.
- **Protocolos**: TCP (confiável), UDP (não confiável), IP (endereçamento).
- **Atrasos**: conhecer os 4 tipos e impactos nas aplicações.
- **Camadas OSI e TCP/IP**: funções de cada camada e encapsulamento.
- **História**: ARPANET, TCP/IP, WWW.

---

### 9. **Referências Sugeridas (do documento)**
- FOROUZAN, B. A. *Comunicação de dados e redes de computadores*
- KUROSE, J. F.; ROSS, K. W. *Redes de computadores e a internet*
- TANENBAUM, A. S.; WETHERALL, D. *Redes de computadores*

---

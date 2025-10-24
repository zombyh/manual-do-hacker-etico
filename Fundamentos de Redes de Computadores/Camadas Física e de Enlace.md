
# 📘 Resumo para Prova: Camadas Física e de Enlace

---

## 📌 1. Introdução

As camadas **física** e **de enlace** são fundamentais para a infraestrutura de redes. Enquanto a camada física lida com a transmissão bruta de bits, a camada de enlace cuida da organização desses bits em quadros, controle de erros, fluxo e acesso ao meio.

---

## 🔌 2. Camada Física

### 📡 Função
- Responsável pela transmissão física de bits através de meios como cabos (par trançado, coaxial, fibra óptica) ou sem fio (ondas de rádio, micro-ondas, infravermelho).

### 🧠 Conceitos Chave
- **Sinais**: analógicos (variação contínua) e digitais (discretos, com transições abruptas).
- **Sinal Periódico**: repete-se em um período \( T \). Frequência \( f = 1/T \) (Hz).
- **Banda Passante**: faixa de frequências que o meio permite passar sem grande atenuação.
- **Taxa de Transmissão**: medida em bps, Kbps, Mbps, Gbps.
- **Atenuação**: perda de potência do sinal com a distância.
- **Ruído**: interfere no sinal (ex.: ruído térmico, presente em todos os sistemas).

### 📶 Meios de Transmissão
#### Guiados:
- **Par Trançado**: barato, flexível, sujeito a interferências.
- **Coaxial**: mais imune a interferências, usado em TV a cabo.
- **Fibra Óptica**: alta taxa de transmissão, imune a interferências, baixa atenuação, mas frágil e cara.

#### Não Guiados:
- **Ondas de Rádio**: AM, FM, TV, celular, Wi-Fi (2,4 GHz e 5 GHz).
- **Micro-ondas**: exigem linha de visada, usadas em satélites.
- **Infravermelho**: curto alcance, não ultrapassa obstáculos.

---

## 🔗 3. Camada de Enlace

### 🛠️ Funções
- **Delimitação de quadros**
- **Controle de erros**
- **Controle de fluxo**
- **Controle de acesso ao meio**

### 🧩 Subcamadas
- **LLC (Logical Link Control)**: controle de fluxo e erro.
- **MAC (Medium Access Control)**: controle de acesso ao meio (multiponto).

### 🧷 Técnicas de Enquadramento
1. **Contagem de Caracteres**: campo inicial indica tamanho do quadro (frágil a erros).
2. **Enquadramento por Caractere**: usa caracteres especiais (STX, ETX, DLE) para delimitar.
3. **Enquadramento por Bit**: usa flag (ex.: 01111110) e bit stuffing.
4. **Violação de Código Físico**: usa sinais não utilizados na codificação (ex.: Manchester).

### 🔁 Controle de Erros
- **Open Loop (FEC)**: correção no receptor (ex.: código Hamming).
- **Feedback (ARQ)**: detecção e retransmissão (ex.: bit de paridade, CRC).

### ⏯️ Controle de Fluxo
- Evita sobrecarga do receptor (ex.: retardar ACKs no ARQ).

---

## 📡 4. Subcamada MAC (Acesso ao Meio)

### 🎯 Problema
- Compartilhamento de enlaces multiponto → risco de colisões.

### 🧩 Soluções
#### a) Alocação Estática
- **FDMA**: divisão por frequência.
- **TDMA**: divisão por tempo.
- Vantagem: sem colisões.
- Desvantagem: desperdício de recurso se estação não transmite.

#### b) Contenção
- **ALOHA**: transmite e espera ACK; se colidir, espera tempo aleatório → baixo desempenho (18%).
- **S-ALOHA**: transmite apenas no início do slot → desempenho melhor.
- **CSMA**: "escuta" o meio antes de transmitir.
- **CSMA/CD**: detecta colisão durante transmissão (usado na Ethernet).

#### c) Acesso Ordenado
- **Token Ring**: permissão circula em anel.
- **Token Bus**: permissão circula logicamente em barramento físico.
- Vantagem: sem colisões, justo.
- Desvantagem: complexidade.

---

## ✅ 5. Pontos Importantes para a Prova

- **Ruído térmico** está sempre presente.
- **Fibra óptica** tem maior banda e menor interferência.
- **CSMA/CD** é usado em Ethernet.
- **Token Ring** e **Token Bus** são livres de colisão.
- **Enquadramento por bit** usa flag e bit stuffing.
- **CRC** é um método robusto de detecção de erro.
- **ALOHA** tem baixo desempenho (18% de eficiência).
- **Banda passante** limita a taxa de transmissão.

---

## 🧠 Dica Final

Revise os **protocolos de acesso ao meio** (ALOHA, CSMA, Token) e as **técnicas de enquadramento**. Entenda bem a diferença entre **meios guiados e não guiados** e as **vantagens/desvantagens** de cada um.

---


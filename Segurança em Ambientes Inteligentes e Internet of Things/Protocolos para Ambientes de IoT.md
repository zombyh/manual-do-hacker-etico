
# 🧠 Resumo: Protocolos para Ambientes de IoT

## 1. Introdução à IoT
- Conceito: Interconexão de dispositivos físicos à internet para coleta e troca de dados sem intervenção humana.
- Origem: Termo cunhado por Kevin Ashton (1999) a partir de aplicações com RFID.
- Aplicações: Smart homes, saúde, agricultura, cidades inteligentes, indústria.

---

## 2. Arquitetura de Redes IoT

### Topologias Comuns:
- **Malha (Mesh)**: Alta redundância e confiabilidade. Ideal para ambientes críticos (ex.: hospitais, indústria).
- **Estrela (Star)**: Centralizada em um gateway. Fácil configuração, mas vulnerável a falhas no ponto central.
- **Ponto a Ponto (P2P)**: Conexão direta entre dispositivos. Simples, mas sem redundância.

### Modelo de 7 Camadas IoT:
| Camada | Função |
|--------|--------|
| 1. Coisas | Sensores e dispositivos |
| 2. Conectividade | Protocolos como Bluetooth, Zigbee |
| 3. Infraestrutura | Conexão à internet (LPWAN, celular) |
| 4. Ingestão de Dados | Armazenamento (Data Lakes, bancos) |
| 5. Análise de Dados | Processamento e insights (edge/cloud) |
| 6. Aplicativos | Interface do usuário (apps, assistentes) |
| 7. Pessoas e Processos | Estratégia de negócios |

---

## 3. Protocolos de Camada de Rede

### IPv6
- Solução para escassez de endereços IPv4.
- Suporte a segurança nativa (autenticação e criptografia).

### 6LoWPAN
- Adaptação do IPv6 para redes de baixa potência e perda de pacotes.
- Padrão RFC 4944.
- Uso em sensores com recursos limitados.

### Roteamento IoT: RPL
- Protocolo para redes de baixa potência e alta perda (LLN).
- Usa **ETX** (Expected Transmission Count) para medir qualidade do link.
- Alternativa a OSPF e BGP, que são inviáveis em larga escala IoT.

---

## 4. Protocolos de Camada de Transporte

### Confiáveis:
- **TCP**: Conexão full-duplex, controle de congestionamento, confiabilidade.
- **CoAP**: Versão leve do HTTP para dispositivos restritos. Suporta multicast.

### Não Confiáveis:
- **UDP**: Baixa latência, sem garantia de entrega. Ideal para tempo real.
- **MQTT**: Baseado em pub/sub, com níveis de QoS:
  - QoS 0: Não confiável
  - QoS 1: Pelo menos uma vez
  - QoS 2: Exatamente uma vez

---

## 5. Protocolos de Camada de Aplicação

### M2M (Machine-to-Machine):
- **MQTT**: Leve, assíncrono, ideal para dispositivos com restrições.
- **AMQP**: Robusto, seguro, com filas e suporte a transações.

### Sensores:
- **LoRaWAN**: Longo alcance, baixo consumo, ideal para monitoramento urbano.
- **Zigbee**: Baixa latência, redes mesh, comum em automação residencial.

---

## 6. Aspectos de Segurança em IoT

### Principais Riscos:
- Dispositivos expostos publicamente.
- Ataques via medidores inteligentes, câmeras, sensores.
- Invasão via gateway central.

### Medidas de Segurança:
- Uso de **IPv6** com autenticação e criptografia.
- **WPA2/WPA3** em redes Wi-Fi.
- **MQTT com QoS 2** para entrega garantida.
- **AMQP** com criptografia e autenticação.
- **Zigbee** com segurança integrada (criptografia).

### Caso de Uso: Fazenda Inteligente
- Sensores com **6LoWPAN** e **RPL** para roteamento eficiente e seguro.
- Dados trafegam com autenticação IPv6.

---

## 7. Conclusão e Recomendações

### Tópicos-Chave para Segurança:
- Escolha de protocolos conforme criticidade e restrições.
- Uso de redes mesh para redundância.
- Autenticação e criptografia em todas as camadas.
- Monitoramento de tráfego e detecção de intrusões.

### Leituras Recomendadas:
- *IoT Inc* – Bruce Sinclair
- *Building Arduino Projects for the Internet of Things* – Adeel Javed

---

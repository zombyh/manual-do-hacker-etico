
# Resumo: Segurança em Wireless e VPN

## 📡 Redes Wireless

### Definição e Conceitos
- Comunicação sem fio que utiliza **radiofrequência** ou **infravermelho** como meio de transmissão.
- Substitui cabos de cobre, coaxiais ou ópticos.
- **Transeptores de rádio** são componentes essenciais.

### Classificação das Redes Wireless
| Tipo | Descrição | Exemplo |
|------|------------|---------|
| **WPAN** | Rede pessoal para dispositivos próximos (até 10m). | Bluetooth |
| **WLAN** | Rede local sem fio, baseada em ondas de rádio. | Wi-Fi (IEEE 802.11) |
| **WMAN** | Rede metropolitana sem fio, de longo alcance. | WiMAX (IEEE 802.16) |

### Padrões de Comunicação
- **IrDA**: Infravermelho, baixa velocidade, linha de vista.
- **Bluetooth**: Mestre-escravo, 2.4 GHz, até 7 dispositivos ativos.
- **Wi-Fi**: 2.4 GHz ou 5 GHz, segurança via WPA/WPA2, WEP.
- **WiMAX**: Longo alcance (até 50 km), alta velocidade, subcamada de segurança.

---

## 🛡️ Segurança em Redes Wireless

### Riscos e Ameaças
- Sinal transmitido pelo ar → facilidade de interceptação.
- Dispositivos móveis são alvos preferenciais.
- Ataques exploram vulnerabilidades em SO, navegadores e falta de conhecimento do usuário.

### Medidas de Segurança em Wi-Fi
- **SSID**: Nome da rede. Pode ser ocultado para dificultar acesso.
- **Canais**: Usar canais 1, 6 ou 11 para evitar sobreposição.
- **Autenticação e Criptografia**:
  - **WEP**: Fraco, evitado.
  - **WPA**: Melhor que WEP, usa TKIP.
  - **WPA2**: Usa AES, mais seguro.
  - **WPA3**: Mais recente, ainda mais robusto.

### Protocolos e Mecanismos de Segurança
- **RADIUS**: Autenticação centralizada (AAA).
- **EAP**: Protocolo extensível para autenticação.
- **TKIP**: Gera chaves dinâmicas, substitui WEP.
- **AES**: Criptografia forte, usado no WPA2.
- **RSN**: Rede robusta com controle de acesso 802.1X e AES.

### Filtro MAC
- Lista de endereços MAC permitidos.
- Camada adicional de segurança, mas não inviolável.

---

## 🔐 VPN (Rede Privada Virtual)

### O que é uma VPN?
- Método de comunicação seguro que cria um **túnel criptografado** entre dois pontos.
- Usada para:
  - Acesso remoto seguro a redes corporativas.
  - Interconexão de redes.
  - Proteção de dados em trânsito.

### Vantagens
- Dados criptografados → mesmo interceptados, são ilegíveis.
- Mascara IP e localização.
- Acesso a conteúdos restritos geograficamente.

### Riscos de VPNs Gratuitas
- Podem coletar e vender dados.
- Sem garantia de privacidade.
- Recomenda-se usar **VPNs pagas e confiáveis**.

### Protocolos de VPN
| Protocolo | Descrição |
|-----------|-----------|
| **IPSec** | Extensão do IP, oferece autenticação, integridade e confidencialidade. |
| **L2TP** | Encapsulamento, mas depende do IPSec para criptografia. |
| **PPTP** | Evolução do PPP, criptografia simples. |
| **L2F** | Desenvolvido pela Cisco, sem criptografia nativa. |
| **SSL/TLS VPN** | Funciona via navegador, sem software adicional. Usa TLS. |

---

## ✅ Pontos de Atenção
- **Wi-Fi**: Use WPA2 ou WPA3, evite WEP.
- **SSID**: Oculte e altere o nome padrão.
- **Canais**: Prefira 1, 6 ou 11 em 2.4 GHz.
- **VPN**: Prefira serviços pagos e confiáveis.
- **Autenticação**: Use métodos fortes como EAP com RADIUS em ambientes corporativos.

---

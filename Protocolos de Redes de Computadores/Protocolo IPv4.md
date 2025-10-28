## 📘 Resumo:  Protocolo IPv4

## 1. Introdução ao IPv4
- **O que é**: IPv4 é a quarta versão do Protocolo de Internet, desenvolvida originalmente pela ARPANET.
- **Função**: Permite a comunicação entre dispositivos em redes usando endereços de 32 bits.
- **Camada do Modelo OSI**: Camada de Rede.

---

## 2. Estrutura do Datagrama IPv4
### Cabeçalho IPv4 (20 a 60 bytes)
| Campo | Tamanho | Função |
|--------|-----------|--------|
| Versão | 4 bits | Identifica a versão do IP (4 para IPv4) |
| Tamanho do Cabeçalho | 4 bits | Número de bytes do cabeçalho (normalmente 20) |
| Serviços Diferenciados | 1 byte | Priorização de pacotes (QoS) |
| Tamanho Total | 2 bytes | Tamanho total do pacote (cabeçalho + dados) |
| Identificação, Flag, Fragmento | 4 bytes | Controle de fragmentação de pacotes |
| TTL | 1 byte | Número máximo de saltos (evita loops) |
| Protocolo | 1 byte | Identifica o protocolo da camada superior (ex: TCP=6, UDP=17) |
| Checksum | 2 bytes | Verificação de integridade do cabeçalho |
| Endereço de Origem | 4 bytes | IP do remetente |
| Endereço de Destino | 4 bytes | IP do destinatário |
| Opções | Variável | Informações extras (segurança, roteamento) |

---

## 3. Endereçamento IPv4
### Formato do Endereço
- 32 bits, divididos em 4 octetos (ex: `192.168.1.1`).
- Representação decimal para facilitar a leitura humana.

### Partes do Endereço
- **Endereço de Rede**: Identifica a rede.
- **Endereço de Host**: Identifica o dispositivo dentro da rede.

### Máscara de Sub-rede
- Define a divisão entre rede e host.
- Exemplos:
  - `255.255.255.0` → /24 → 254 hosts
  - `255.255.255.128` → /25 → 126 hosts

### Endereços Especiais
- **Endereço de Rede**: Primeiro IP da rede (não usável).
- **Endereço de Broadcast**: Último IP da rede (não usável).
- **Endereços de Host**: IPs utilizáveis entre o de rede e o de broadcast.

### Cálculo de Hosts
- Fórmula:  
  \[
  Nº\ de\ hosts = 2^{(32 - N)} - 2
  \]
  onde \(N\) = número de bits da máscara.

---

## 4. Classes de Endereços IPv4
| Classe | Primeiro Octeto | Máscara Padrão | Uso |
|--------|------------------|----------------|-----|
| A | 1–126 | 255.0.0.0 | Grandes redes |
| B | 128–191 | 255.255.0.0 | Redes médias |
| C | 192–223 | 255.255.255.0 | Pequenas redes |
| D | 224–239 | - | Multicast |
| E | 240–255 | - | Experimental |

---

## 5. Sub-redes e CIDR/VLSM
### CIDR (Classless Inter-Domain Routing)
- Permite máscaras de tamanho variável.
- Notação: `/24`, `/25`, etc.

### VLSM (Variable Length Subnet Mask)
- Permite criar sub-redes de tamanhos diferentes a partir de uma rede maior.
- Exemplo: Dividir `192.168.1.0/24` em sub-redes `/25`, `/26`, etc.

---

## 6. Esgotamento do IPv4 e Soluções
### Problema
- Limite de ~4,3 bilhões de endereços.
- Crescimento de dispositivos conectados (IoT, smartphones).

### Soluções
1. **IPv6**: 128 bits, praticamente ilimitado.
2. **NAT (Network Address Translation)**:
   - **NAT Estático**: Mapeamento fixo entre IP privado e público.
   - **NAT Dinâmico / PAT**: Múltiplos IPs privados usam um IP público com portas diferentes.
3. **CGNAT**: NAT em nível de provedor (ISP).
4. **DHCP**: Alocação dinâmica e temporária de IPs.

### Endereços Privados (RFC 1918)
- `10.0.0.0/8`
- `172.16.0.0/12`
- `192.168.0.0/16`

---

## 7. Protocolos Auxiliares
### ARP (Address Resolution Protocol)
- Associa IP a endereço MAC.
- Comando: `arp -a`

### ICMP (Internet Control Message Protocol)
- Usado para diagnóstico e erro.
- Mensagens comuns:
  - **Echo Request/Reply** (ping)
  - **Destination Unreachable**
  - **Time Exceeded**

---

## 8. Ferramentas de Troubleshooting
### Ping
- Testa conectividade com ICMP.
- Exemplo: `ping 8.8.8.8`

### Traceroute (tracert)
- Mostra o caminho até um destino.
- Usa TTL e mensagens ICMP Time Exceeded.

### Wireshark
- Analisador de pacotes.
- Filtros comuns: `icmp`, `ip.addr == x.x.x.x`

---

## 9. Projetos de Rede com IPv4
### Planejamento
- Calcular máscara com base no número de hosts.
- Exemplo: Para 120 hosts → `/25` (126 hosts úteis).

### Subdivisão de Redes
- Exemplo: Dividir `172.16.1.0/24` em 4 sub-redes `/26` (62 hosts cada).

### Redes Heterogêneas
- Usar VLSM para atender a diferentes necessidades de hosts em uma mesma rede.

---

## 10. Conclusão
- IPv4 é a base das redes atuais, mas esbarra na limitação de endereços.
- Técnicas como NAT, sub-redes e CIDR prolongaram sua vida útil.
- IPv6 é a solução definitiva para a escassez.
- Ferramentas como ping, traceroute e Wireshark são essenciais para administração e troubleshooting.

---

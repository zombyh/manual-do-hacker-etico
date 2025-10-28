## 🌐 Resumo: Protocolo IPv6

## 1. Introdução ao IPv6
- **O que é**: IPv6 é a sexta versão do Protocolo de Internet, criada para substituir o IPv4.
- **Motivação**: Escassez de endereços IPv4 (4,3 bilhões) vs. capacidade quase ilimitada do IPv6 (3,4 × 10³⁸ endereços).
- **Padronização**: RFC 2460 (1998).
- **Camada do Modelo OSI**: Camada de Rede.

---

## 2. Cabeçalho IPv6
### Estrutura Simplificada (40 bytes fixos)
| Campo | Tamanho | Função |
|--------|-----------|--------|
| Versão | 4 bits | Valor 6 para IPv6 |
| Classe de Tráfego | 8 bits | QoS (Qualidade de Serviço) |
| Identificador de Fluxo | 20 bits | Identifica fluxos de dados |
| Tamanho dos Dados | 16 bits | Tamanho do payload (dados) |
| Próximo Cabeçalho | 8 bits | Indica o protocolo superior ou cabeçalho de extensão |
| Limite de Encaminhamento | 8 bits | Substitui o TTL do IPv4 |
| End. de Origem | 128 bits | Endereço de origem |
| End. de Destino | 128 bits | Endereço de destino |

### Diferenças em relação ao IPv4
- **Sem fragmentação** no caminho: só na origem.
- **Sem checksum** no cabeçalho.
- **Cabeçalhos de extensão** substituem o campo "Opções".

### Cabeçalhos de Extensão
| Nome | Valor | Função |
|------|-------|--------|
| Hop-by-Hop | 0 | Processado por todos os roteadores |
| Routing | 43 | Roteamento de origem |
| Fragment | 44 | Fragmentação |
| AH | 51 | Autenticação (IPSec) |
| ESP | 52 | Criptografia (IPSec) |
| Destination Options | 60 | Opções de destino |

---

## 3. Endereçamento IPv6
### Representação
- 128 bits = 8 grupos de 16 bits (hextetos).
- Notação hexadecimal.
- Exemplo: `2001:0DB8:ACAD:0001:0000:0000:0000:0001`

### Regras de Abreviação
1. **Omitir zeros à esquerda** em cada hexteto.
2. **Substituir sequências de zeros por "::"** (apenas uma vez).

Exemplo:  
`2001:0DB8:0000:1111:0000:0000:0000:0200` → `2001:DB8:0:1111::200`

### Tipos de Endereços
| Tipo | Descrição | Exemplo |
|------|------------|---------|
| Unicast | Comunicação 1 para 1 | `2001:DB8::1` |
| Anycast | Entrega ao mais próximo | - |
| Multicast | Entrega a um grupo | `FF02::1` (todos os nós) |
| **Sem Broadcast** | Substituído por multicast | - |

### Endereços Unicast Especiais
| Tipo | Prefixo | Uso |
|------|---------|-----|
| Global | `2000::/3` | Endereços públicos |
| Link-Local | `FE80::/64` | Comunicação local |
| Unique Local | `FC00::/7` | Similar a redes privadas |
| Loopback | `::1` | Localhost |
| Não Especificado | `::` | Ausência de endereço |

### Formação do Endereço Link-Local
- Prefixo: `FE80::/64`
- Identificador de interface: IEEE EUI-64 (MAC + `FFFE` + bit invertido)

---

## 4. Estrutura Hierárquica do Endereço Global
| Parte | Bits | Exemplo |
|-------|------|---------|
| Prefixo Global | 48 bits | `2001:DB8:ACAD` |
| Sub-rede | 16 bits | `:0001` |
| Identificador de Interface | 64 bits | `::1` |

Exemplo completo:  
`2001:DB8:ACAD:0001::1/64`

---

## 5. Projeto de Redes IPv6
### Cálculo de Capacidade
\[
\text{Hosts} = 2^{(128 - N)}
\]
Onde \(N\) = comprimento do prefixo.

Exemplo: Rede `/64` → \(2^{64}\) hosts.

### Projeto com Sub-redes
- **Prefixo típico**: `/64` (suporta EUI-64).
- **Alocação comum**: `/48` para organizações → 65.536 sub-redes `/64`.

### Exemplo de Projeto
- Rede: `2001:AB34:3001::/48`
- Sub-redes:
  - `2001:AB34:3001:0000::/64`
  - `2001:AB34:3001:0001::/64`
  - ...

---

## 6. Configuração de Redes IPv6
### No Roteador Cisco
```bash
R1(config)# ipv6 unicast-routing
R1(config)# interface gigabitethernet 0/0
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
R1(config-if)# no shutdown
```

### Autoconfiguração (Stateless)
- Roteador anuncia prefixo via **Router Advertisement (RA)**.
- Dispositivo forma endereço com **EUI-64**.

---

## 7. Transição e Coexistência com IPv4
### Técnicas Principais
| Técnica | Descrição |
|---------|-----------|
| **Pilha Dupla** | Dispositivo suporta IPv4 e IPv6 |
| **Tunelamento** | Transporta IPv6 sobre IPv4 |
| **Tradução** | Converte IPv6 ↔ IPv4 |

### Tunelamento
- **6to4**: Prefixo `2002::/16` + IPv4 em hex.
- **ISATAP**: Túneis automáticos em redes IPv4.
- **GRE**: Túnel genérico (configuração manual).

### Tradução
- **NAT64**: Prefixo `64:FF9B::/96` + IPv4.
- **SIIT**: Tradução stateless de cabeçalhos.
- **BIS/BIA**: Tradução em camada de aplicação.

---

## 8. ICMPv6 e Funcionalidades Avançadas
### Novas Funcionalidades
- **NDP (Neighbor Discovery Protocol)**: Substitui ARP.
- **MLD (Multicast Listener Discovery)**: Gerencia grupos multicast.
- **Path MTU Discovery**: Descobre MTU do caminho.
- **Autoconfiguração Stateless**: Configuração sem servidor.
- **Mobilidade IPv6**: Mantém conectividade em movimento.

### Mensagens ICMPv6 Principais
| Tipo | Nome | Uso |
|------|------|-----|
| 133 | Router Solicitation (RS) | Solicita anúncio de roteador |
| 134 | Router Advertisement (RA) | Anuncia roteador e prefixo |
| 135 | Neighbor Solicitation (NS) | Descobre MAC do vizinho |
| 136 | Neighbor Advertisement (NA) | Responde com MAC |
| 137 | Redirect | Redireciona pacotes |

---

## 9. DHCPv6 e Autoconfiguração
### Modos de Configuração
| Flag M | Flag O | Modo |
|--------|--------|------|
| 0 | 0 | Stateless (padrão) |
| 0 | 1 | Stateless + DHCPv6 (DNS) |
| 1 | X | Stateful (tudo via DHCPv6) |

### Configuração no Roteador
```bash
R1(config)# ipv6 dhcp pool NOME
R1(config-dhcpv6)# dns-server 2001::1
R1(config-dhcpv6)# domain-name cisco.com
R1(config-dhcpv6)# address prefix 2001:AAAA::/64
```

---

## 10. Conclusão
- IPv6 resolve a escassez de endereços e introduz melhorias.
- Cabeçalho mais simples e eficiente.
- Funcionalidades avançadas: autoconfiguração, mobilidade, segurança.
- Transição gradual com técnicas de coexistência.
- Ferramentas como NDP, MLD e DHCPv6 facilitam a administração.

---

## Resumo: Segurança com Roteadores

## 📌 Visão Geral
Os roteadores, embora projetados para rotear tráfego entre segmentos de rede, podem ser configurados para atuar como elementos de segurança, implementando funcionalidades similares a firewalls por meio de **listas de acesso (ACLs)** e módulos de software/hardware adicionais.

---

## 🔍 O que é um Roteador?
- Dispositivo que encaminha pacotes entre **domínios de broadcast diferentes**.
- Examina o **cabeçalho IP** de cada pacote para determinar o destino com base em sua **tabela de roteamento**.
- Funcionalidades automáticas:
  - Preenchimento e manutenção de tabelas de roteamento.
  - Execução de protocolos de roteamento dinâmico (RIP, OSPF, BGP).
  - Atribuição de métricas de roteamento.
  - Aceitação de rotas estáticas.

---

## 🛡️ Campos do Cabeçalho IP Relevantes para Segurança
| Campo | Função |
|--------|---------|
| **Endereço IP de origem/destino** | Identifica origem e destino do pacote. |
| **Protocolo** | Indica o tipo de payload (ex: TCP=6, UDP=17, ICMP=1). |
| **Tipo de Serviço (ToS)** | Usado para QoS e priorização. |
| **TTL** | Tempo de vida do pacote; evita loops. |
| **Flags (MF, DF)** | Controle de fragmentação de pacotes. |

---

## 🔐 Roteador com ACL (Access Control List)
### O que é uma ACL?
- Lista sequencial de regras de **permitir** ou **negar** tráfego com base em:
  - Endereço IP de origem/destino.
  - Protocolo (TCP, UDP, etc.).
  - Portas (sockets).

### Tipos de ACL:
- **ACL Padrão (Standard)**: Filtra apenas pelo IP de origem.
- **ACL Estendida (Extended)**: Filtra por IP de origem/destino, protocolo, porta, etc.

### Aplicação de ACLs:
- **Inbound**: Aplicada na entrada da interface.
- **Outbound**: Aplicada na saída da interface.

### Fluxo com ACL:
1. Pacote chega à interface.
2. Roteador verifica a tabela de roteamento.
3. Se houver rota, verifica se há ACL na interface.
4. Se houver ACL, aplica as regras na ordem.
5. Pacote é permitido ou negado.

> ⚠️ Pacotes gerados pelo próprio roteador (ex: atualizações de rota) não são afetados por ACLs **outbound**.

---

## 🧩 Identificação de ACLs (Exemplo Cisco)
| Tipo de ACL | Faixa Numérica |
|-------------|----------------|
| IP Standard | 1–99 |
| IP Extended | 100–199 |
| IPX Standard | 800–899 |
| AppleTalk | 600–699 |

> Versões mais recentes do Cisco IOS permitem usar **nomes** em vez de números.

---

## 🔧 Software de Firewall em Roteadores
### Exemplo: Cisco IOS Firewall
- Funcionalidade **stateful**: inspeciona pacotes com base no estado da conexão.
- Usa o algoritmo **ASA (Adaptive Security Algorithm)**.
- Regras padrão:
  - Permite tráfego de dentro para fora.
  - Bloqueia tentativas de conexão externa não autorizadas.
  - Controla tráfego ICMP.

### Vantagens:
- Amplia as funções de segurança sem hardware adicional.
- Ideal para filiais e PMEs.

### Pré-requisitos para implantação:
- Memória flash e RAM suficientes.
- Versão compatível do IOS.
- Capacidade de processamento.

---

## 💾 Módulo de Hardware de Firewall
- Exemplo: **Cisco ASA Service Module (ASA SM)**.
- Placa dedicada que executa software de firewall.
- Comunica-se com o roteador via barramento interno.
- Alta performance, baixa latência.

---

## 📡 Firewall em Roteadores Wi-Fi
- Roteadores SOHO (Small Office/Home Office) incluem funcionalidades básicas de firewall.
- Recursos comuns:
  - **Firewall SPI** (Stateful Packet Inspection).
  - Filtro por IP/MAC.
  - Proteção contra DoS.
  - Controle de domínios.

### Exemplo: TP-Link Archer C2
- Oferece:
  - Proteção DoS.
  - Filtro de IP/MAC.
  - Vínculo IP-MAC.

---

## ✅ Resumo de Benefícios
- **Controle de tráfego** entre segmentos.
- **Segurança de perímetro** com ACLs e firewalls.
- **Flexibilidade** com software e hardware adicionais.
- **Custo-benefício** para ambientes menores.

---

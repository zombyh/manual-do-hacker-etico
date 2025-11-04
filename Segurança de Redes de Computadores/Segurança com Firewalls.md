
# Resumo: Segurança com Firewalls

## 🎯 Objetivos da Aula
- Definir firewall convencional e de camada 7.
- Explicar o funcionamento do firewall no Linux.
- Classificar iptables, hardening, virtualização de firewall e firewall de aplicação.

---

## 🔥 O que é um Firewall?
- Dispositivo ou software que **filtra tráfego** com base em regras predefinidas.
- Pode ser:
  - **Hardware dedicado**
  - **Software** em servidores ou PCs
- Cria **zonas de segurança**:
  - **Internet** (externa)
  - **Intranet** (LAN interna)
  - **DMZ** (Zona Desmilitarizada)

---

## 🧱 Tipos de Firewalls

### Por Geração
| Tipo | Camada | Características |
|------|--------|------------------|
| Filtro de Pacotes | 3 e 4 | Filtra por IP/porta |
| Com Estado | 3 e 4 | Monitora estado da conexão |
| Proxy | 7 | Intermedia conexões |
| NGFW (Next-Generation) | 7 + 3/4 | Inspeciona aplicação + pacotes |

### Por Localização
- **Firewall de Endpoint**: Instalado no SO da estação.
- **Firewall de Perímetro**: Entre a rede interna e a Internet.

---

## 🐧 Firewall no Linux: **iptables**
- Ferramenta de interface para o módulo **netfilter** no kernel.
- Atua no nível de **pacote**.
- Toma decisões com base em:
  - Porta/origem/destino
  - Estado da conexão
  - Protocolo (TCP, UDP, ICMP)

### Comandos Comuns do iptables
| Ação | Comando Exemplo |
|------|------------------|
| Bloquear IP | `iptables -A INPUT -s 192.168.1.10 -j DROP` |
| Liberar SSH | `iptables -A INPUT -p tcp --dport 22 -j ACCEPT` |
| Redirecionar porta | `iptables -t nat -A PREROUTING -p tcp --dport 422 -j REDIRECT --to-port 22` |
| Limitar ataques DDoS | `iptables -A INPUT -p tcp --dport 80 -m limit --limit 25/minute -j ACCEPT` |

### Funcionalidades do iptables
- SNAT / DNAT
- Masquerading
- Balanceamento de carga
- Controle de tráfego (QoS)
- Logs via Syslog

---

## 🛡️ Hardening de Sistema Operacional
- Conjunto de ações para **reduzir vulnerabilidades**.
- Medidas comuns:
  - Remover usuários e serviços desnecessários
  - Atualizar sistemas e aplicações
  - Reforçar políticas de senha
  - Implementar autenticação AAA
  - Auditar permissões de arquivos

### Exemplo: **Bastille Linux**
- Ferramenta de hardening para Linux.
- Modos:
  - **Interativo**: Pergunta e configura com base nas respostas.
  - **Avaliação**: Gera relatório de segurança.

---

## ☁️ Virtualização de Firewall
- Firewall executado como **máquina virtual**.
- Vantagens:
  - Melhor aproveitamento de hardware
  - Isolamento lógico
  - Redução de custos
- Faz parte da **NFV** (Network Functions Virtualization).
- Exemplos de funções virtualizadas:
  - Firewall
  - Antivírede rede
  - IPS/IDS
  - Mitigação de DDoS

---

## 🧩 Firewall de Aplicação (Camada 7 / NGFW)
- Inspeciona tráfego no nível da **aplicação**.
- Identifica aplicativos (ex.: YouTube, Spotify, Dropbox) mesmo que usem a mesma porta.
- Vantagens:
  - Controle granular de uso de aplicações
  - Bloqueio de apps indesejados (ex.: Torrent)
  - Melhor visibilidade e segurança

### Requisitos:
- Atualizações constantes para reconhecer novas apps.
- Reconhecimento de padrões de comportamento.

---

## 📚 Referências
- KUROSE, ROSS. *Redes de Computadores e a Internet*.
- STALLINGS. *Criptografia e Segurança de Redes*.
- MUNIZ, Vinicius. *O que é iptables?*

---


## 📘 Resumo: Hardening – Ameaças, Web Proxy e Kernel Tuning

### 🎯 **Objetivo Geral**
Capacitar profissionais de segurança a:
- Gerenciar vulnerabilidades e ameaças
- Configurar e proteger servidores **Squid Web Proxy**
- Implementar firewalls com **Iptables**
- Realizar **tuning de kernel** em sistemas Linux para segurança e desempenho

---

## 🔍 1. Gerenciamento de Ameaças e Vulnerabilidades

### O que são?
- **Vulnerabilidade**: Ponto fraco em um ativo que pode ser explorado
- **Ameaça**: Agente que explora uma vulnerabilidade
- **Hardening**: Processo de reduzir vulnerabilidades e fortalecer sistemas

### Processos de Segurança
- **Análise de Vulnerabilidades**: Identifica, enumera e classifica vulnerabilidades
- **Pentest (Teste de Invasão)**: Simula ataques reais para validar segurança

### Diferenças entre Análise de Vulnerabilidades e Pentest
| Análise de Vulnerabilidades | Pentest |
|------------------------------|---------|
| Identifica fragilidades conhecidas | Explora ativamente os pontos fracos |
| Menos intrusiva | Mais intrusivo e realista |
| Gera relatórios de riscos | Mostra impacto de uma invasão real |

### Ferramentas de Varredura
- **Nessus**: Scanner de vulnerabilidades
- **Nmap**: Varredura de redes e hosts
  - Exemplo: `nmap -sS -A --script=vuln 192.168.1.1`
- **Fontes de Consulta**:
  - CVE (Common Vulnerabilities and Exposures)
  - NVD (National Vulnerability Database)
  - Exploit Database

---

## 🌐 2. Squid Web Proxy

### O que é?
- Servidor proxy de cache para HTTP, HTTPS, FTP
- Melhora desempenho e controla acesso à web

### Funcionalidades
- **Cache**: Armazena conteúdos frequentemente acessados
- **Controle de Acesso via ACLs** (Access Control Lists)
- **Proxy Reverso**
- **Balanceamento de Carga**

### Configuração Básica
Arquivo: `/etc/squid/squid.conf`

#### Exemplo de ACLs:
```squid
acl rede_interna src 192.168.1.0/24
acl horario_comercial time M T W H F 09:00-18:00
http_access allow rede_interna horario_comercial
http_access deny all
```

### Hardening do Squid
- Bloquear portas desconhecidas
- Restringir acesso ao gerenciador de cache apenas ao localhost
- Monitorar logs com ferramentas como **Calamaris** e **Squidtaild**

---

## 🔥 3. Firewall com Iptables

### O que é Iptables?
- Ferramenta para configurar regras de firewall no kernel Linux
- Utiliza o framework **Netfilter**

### Tabelas e Chains
| Tabela | Chains | Função |
|--------|--------|---------|
| `filter` | INPUT, OUTPUT, FORWARD | Filtragem comum de pacotes |
| `nat` | PREROUTING, POSTROUTING | Tradução de endereços (NAT) |
| `mangle` | Várias | Modificação de pacotes (QoS, etc.) |

### Comandos Básicos
```bash
iptables -A INPUT -p tcp --dport 22 -j ACCEPT   # Permitir SSH
iptables -P INPUT DROP                          # Política padrão: DROP
iptables -L                                     # Listar regras
iptables-save > /etc/iptables/rules.v4         # Salvar regras
```

### Exemplo de Configuração
```bash
# Limpar regras
iptables -F

# Política padrão: DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

# Permitir loopback e SSH
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

### NAT e Masquerading
```bash
# SNAT (IP Fixo)
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 11.22.33.44

# Masquerading (IP Dinâmico)
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

---

## ⚙️ 4. Tuning de Kernel Linux

### O que é?
- Ajuste de parâmetros do kernel para melhorar **desempenho** e **segurança**

### Ferramentas
- **sysctl**: Interface para modificar parâmetros em tempo de execução
- **/proc/sys**: Sistema de arquivos virtual com configurações do kernel
- **tuned**: Daemon para ajustes automáticos baseados em perfis

### Exemplos de Ajustes de Segurança
```bash
# Desativar IP Forwarding
net.ipv4.ip_forward = 0

# Ignorar broadcasts ICMP (proteção contra flood)
net.ipv4.icmp_echo_ignore_broadcasts = 1

# Ativar proteção contra SYN Flood
net.ipv4.tcp_syncookies = 1

# Desativar source routing
net.ipv4.conf.all.accept_source_route = 0

# Ativar ASLR (Address Space Layout Randomization)
kernel.randomize_va_space = 2
```

### Ajustes de Desempenho de Rede
```bash
# Aumentar buffers TCP
net.core.rmem_max = 8388608
net.core.wmem_max = 8388608

# Ajustar janela TCP
net.ipv4.tcp_rmem = 4096 87380 8388608
net.ipv4.tcp_wmem = 4096 87380 8388608

# Habilitar window scaling
net.ipv4.tcp_window_scaling = 1
```

### Configuração Persistente
Editar ou criar arquivo em `/etc/sysctl.d/`:
```bash
echo "net.ipv4.ip_forward=0" >> /etc/sysctl.d/99-hardening.conf
sysctl -p /etc/sysctl.d/99-hardening.conf
```

---

## 📈 5. Diagnóstico e Monitoramento

### Comandos Úteis
- `dmesg`: Buffer de mensagens do kernel
- `systemctl`: Gerenciar serviços systemd
- `ulimit`: Limites de recursos por usuário
- `tuned-adm list`: Listar perfis de tuning

### Boas Práticas
- Use **CLI** em servidores (menos recursos que GUI)
- Desative serviços desnecessários
- Monitore logs regularmente
- Teste alterações em ambiente controlado

---

## ✅ Checklist de Hardening

- [ ] Realizar análise de vulnerabilidades com ferramentas como Nessus ou Nmap
- [ ] Configurar Squid com ACLs restritivas
- [ ] Implementar firewall com Iptables (política DROP por padrão)
- [ ] Aplicar tuning de kernel para segurança (ex: SYN cookies, ASLR)
- [ ] Ajustar parâmetros de rede para desempenho
- [ ] Desativar serviços e interfaces desnecessários
- [ ] Monitorar logs e usar ferramentas como tuned para otimização contínua

---

## 📚 Fontes Recomendadas

- [NVD](https://nvd.nist.gov)
- [CVE](https://cve.mitre.org)
- [Linux Kernel Documentation](https://www.kernel.org/doc/)
- [DigitalOcean: Systemd Tutorials](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)

---

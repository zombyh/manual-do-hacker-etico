## O que é o Nmap?
O Nmap (Network Mapper) é uma ferramenta de código aberto para exploração de rede e auditoria de segurança. É usado para descobrir hosts, serviços, sistemas operacionais e vulnerabilidades em redes.

## Sintaxe Básica
```bash
nmap [tipo de scan] [opções] [alvo]
```

## Tipos de Scans Principais

### 1. **Scan de Portas TCP**
```bash
# TCP SYN Scan (stealth scan) - Padrão
nmap -sS 192.168.1.1

# TCP Connect Scan
nmap -sT 192.168.1.1

# TCP ACK Scan
nmap -sA 192.168.1.1

# TCP Window Scan
nmap -sW 192.168.1.1

# TCP Maimon Scan
nmap -sM 192.168.1.1
```

### 2. **Scan de Portas UDP**
```bash
nmap -sU 192.168.1.1
```

### 3. **Scans Especiais**
```bash
# NULL Scan (sem flags)
nmap -sN 192.168.1.1

# FIN Scan (apenas flag FIN)
nmap -sF 192.168.1.1

# Xmas Scan (flags FIN, PSH, URG)
nmap -sX 192.168.1.1
```

## Opções de Alvo

### Especificação de Alvos
```bash
# IP único
nmap 192.168.1.1

# Range de IPs
nmap 192.168.1.1-100

# Sub-rede
nmap 192.168.1.0/24

# Múltiplos alvos
nmap 192.168.1.1 192.168.1.50 192.168.2.1

# Lista de hosts de arquivo
nmap -iL hosts.txt

# Excluir hosts
nmap 192.168.1.0/24 --exclude 192.168.1.50
```

## Opções de Portas

### Especificação de Portas
```bash
# Portas específicas
nmap -p 22,80,443 192.168.1.1

# Range de portas
nmap -p 1-1000 192.168.1.1

# Todas as portas
nmap -p- 192.168.1.1

# Portas mais comuns (top ports)
nmap --top-ports 100 192.168.1.1

# Portas por nome de serviço
nmap -p http,https,ssh 192.168.1.1
```

## Detecção de Serviços e Versões

### Detecção de Serviços
```bash
# Detecção de versão de serviços
nmap -sV 192.168.1.1

# Detecção intensiva de versão
nmap -sV --version-intensity 9 192.168.1.1

# Detecção leve de versão
nmap -sV --version-intensity 1 192.168.1.1

# Detecção de versão com trace
nmap -sV --version-trace 192.168.1.1
```

## Detecção de Sistema Operacional

### OS Fingerprinting
```bash
# Detecção de SO
nmap -O 192.168.1.1

# Detecção agressiva de SO
nmap -O --osscan-guess 192.168.1.1

# Detecção limitada de SO
nmap -O --osscan-limit 192.168.1.1
```

## Scripts NSE (Nmap Scripting Engine)

### Uso de Scripts
```bash
# Scan com scripts padrão
nmap -sC 192.168.1.1

# Scripts específicos
nmap --script=http-title 192.168.1.1
nmap --script=ssl-cert 192.168.1.1

# Múltiplos scripts
nmap --script=http-title,ssl-cert,ssh-auth-methods 192.168.1.1

# Categorias de scripts
nmap --script=safe 192.168.1.1
nmap --script=vuln 192.168.1.1
nmap --script=exploit 192.168.1.1
nmap --script=auth 192.168.1.1

# Todos os scripts de uma categoria
nmap --script="default or safe" 192.168.1.1
```

## Opções de Timing e Desempenho

### Controle de Velocidade
```bash
# Timing templates (T0 a T5)
nmap -T0 192.168.1.1  # Paranoid (muito lento)
nmap -T1 192.168.1.1  # Sneaky
nmap -T2 192.168.1.1  # Polite
nmap -T3 192.168.1.1  # Normal (padrão)
nmap -T4 192.168.1.1  # Aggressive
nmap -T5 192.168.1.1  # Insane (muito rápido)

# Controle manual
nmap --min-rate 100 192.168.1.1
nmap --max-rate 1000 192.168.1.1
```

## Opções de Evasão e Furtividade

### Técnicas de Evasão
```bash
# Fragmentação de pacotes
nmap -f 192.168.1.1

# MTU personalizado
nmap --mtu 24 192.168.1.1

# IP spoofing
nmap -S 192.168.1.100 192.168.1.1

# Porta fonte específica
nmap --source-port 53 192.168.1.1

# Decoy scans
nmap -D 192.168.1.100,192.168.1.200,ME 192.168.1.1
```

## Opções de Saída

### Formatos de Output
```bash
# Saída normal
nmap -oN resultado.txt 192.168.1.1

# Saída XML
nmap -oX resultado.xml 192.168.1.1

# Saída grepable
nmap -oG resultado.grep 192.168.1.1

# Todos os formatos
nmap -oA resultado 192.168.1.1

# Saída em tempo real
nmap --reason 192.168.1.1

# Verbose
nmap -v 192.168.1.1
nmap -vv 192.168.1.1  # Mais verbose
```

## Scans Avançados

### Host Discovery
```bash
# Apenas descobrir hosts (sem scan de portas)
nmap -sn 192.168.1.0/24

# Desabilitar descoberta de hosts (scan todas as portas)
nmap -Pn 192.168.1.1

# Ping scan com diferentes métodos
nmap -PS 192.168.1.1  # SYN ping
nmap -PA 192.168.1.1  # ACK ping
nmap -PU 192.168.1.1  # UDP ping
```

### Scans Específicos
```bash
# Scan de firewall/IDS evasion
nmap -f -D 192.168.1.100 --data-length 100 192.168.1.1

# Scan com payload personalizado
nmap --data-string "TEST" 192.168.1.1

# Scan IPv6
nmap -6 2001:db8::1
```

## Exemplos Práticos Comuns

### Scan Básico de Rede
```bash
nmap -sS -sV -O 192.168.1.0/24
```

### Scan Completo de Servidor Web
```bash
nmap -p 80,443,8080,8443 -sV --script=http-* 192.168.1.1
```

### Scan de Segurança
```bash
nmap -sS -sV -sC -O -A -T4 192.168.1.1
```

### Scan Furtivo
```bash
nmap -sS -T2 -f -D 192.168.1.100 --source-port 53 192.168.1.1
```

### Scan de Vulnerabilidades
```bash
nmap -sV --script=vuln 192.168.1.1
```

## Considerações Importantes

### Boas Práticas
- Comece com scans menos intrusivos
- Use timing apropriado para não sobrecarregar a rede
- Documente seus resultados
- Entenda as limitações de cada tipo de scan

### Dicas de Performance
- Use `-T4` para scans internos
- Use `-T2` ou `-T3` para scans externos
- Limite o número de portas quando possível
- Use `--min-rate` e `--max-rate` para controle preciso

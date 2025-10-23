## O que é o Netdiscover?
O `netdiscover` é uma ferramenta de descoberta de rede ativa/passiva para redes LAN, utilizada principalmente para descobrir hosts em uma rede local.

## Sintaxe Básica
```bash
netdiscover [opções]
```

## Modos de Operação

### 1. Modo Ativo (Padrão)
- Envia requisições ARP ativamente
- Mais rápido mas mais "barulhento"
```bash
netdiscover -i eth0
```

### 2. Modo Passivo
- Apenas escuta o tráfego ARP existente
- Mais lento mas stealth
```bash
netdiscover -p -i eth0
```

### 3. Modo Scan de Intervalo
- Escaneia um range específico de IPs
```bash
netdiscover -r 192.168.1.0/24
```

## Parâmetros Principais

### Interface de Rede
```bash
-i <interface>      # Especifica a interface de rede
# Exemplo:
netdiscover -i eth0
netdiscover -i wlan0
```

### Range de IPs
```bash
-r <range>          # Range de IPs (CIDR ou intervalo)
-l <arquivo>        # Lista de IPs/ranges de arquivo
# Exemplos:
netdiscover -r 192.168.1.0/24
netdiscover -r 192.168.1.1-192.168.1.100
netdiscover -l ips.txt
```

### Modo de Operação
```bash
-p                 # Modo passivo (apenas escuta)
-f                 # Modo fast (scan mais rápido)
-s                 # Modo sleep (intervalo entre requisições)
# Exemplo:
netdiscover -p -i eth0        # Passivo
netdiscover -f -i eth0        # Fast mode
```

### Filtros e Opções
```bash
-F                 # Filtro por fabricante (vendor)
-P                 # Imprime resultados em formato legível
-c <count>         # Número de vezes para executar
# Exemplos:
netdiscover -P -i eth0        # Saída formatada
netdiscover -c 5 -i eth0      # Executa 5 vezes
```

## Exemplos Práticos

### 1. Scan Básico da Rede Local
```bash
netdiscover -i eth0
```

### 2. Scan de Subnet Específica
```bash
netdiscover -r 10.0.0.0/24 -i eth0
```

### 3. Modo Passivo para Discovery Silencioso
```bash
netdiscover -p -i wlan0
```

### 4. Scan com Intervalo Personalizado
```bash
netdiscover -r 192.168.1.50-192.168.1.150 -i eth0
```

### 5. Scan Rápido com Saída Formatada
```bash
netdiscover -f -P -i eth0
```

## Saída Típica
```
 Currently scanning: 192.168.1.0/24   |   Screen View: Unique Hosts                                                                                
                                                                                                                                                   
 4 Captured ARP Req/Rep packets, from 4 hosts.   Total size: 240                                                                                   
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 192.168.1.1     00:11:22:33:44:55      1      60  Cisco Systems
 192.168.1.10    aa:bb:cc:dd:ee:ff      1      60  Samsung Electronics
 192.168.1.15    11:22:33:44:55:66      1      60  Apple, Inc.
```

## Opções Avançadas

### Timeout e Intervalos
```bash
-t <timeout>       # Timeout em ms (padrão: 500)
-s <time>          # Tempo entre requisições (padrão: 0)
```

### Arquivos de Configuração
```bash
-f <arquivo>       # Arquivo com ranges de IP
-L                 # Carrega arquivo OUI (vendor database)
```

## Dicas de Uso

### 1. Para Pentesting
```bash
# Discovery silencioso
netdiscover -p -i eth0

# Scan rápido para mapeamento inicial
netdiscover -f -r 192.168.1.0/24
```

### 2. Para Administração de Rede
```bash
# Verificar hosts ativos na rede
netdiscover -P -i eth0

# Monitorar rede continuamente
netdiscover -p -c 0 -i eth0
```

### 3. Para Troubleshooting
```bash
# Verificar conflitos de IP
netdiscover -p -i eth0 | grep -i "duplicate"

# Identificar dispositivos não autorizados
netdiscover -P -i eth0 | grep -v "KNOWN_VENDOR"
```

### Performance
- Modo ativo é mais rápido mas gera mais tráfego
- Modo passivo é mais lento mas menos detectável
- Em redes grandes, use ranges específicos para evitar timeouts

### Limitações
- Funciona apenas em redes locais (LAN)
- Não atravessa routers sem configurações especiais
- Pode ser detectado por sistemas de segurança modernos

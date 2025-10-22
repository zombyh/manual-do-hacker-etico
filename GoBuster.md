## Visão Geral
GoBuster é uma ferramenta de brute-force escrita em Go, utilizada para descobrir diretórios, arquivos, subdomínios e S3 buckets em servidores web.

## Sintaxe Básica
```bash
gobuster [modo] [opções]
```

## Modos Principais

### 1. Modo DIR (Diretórios/Arquivos)
```bash
# Busca básica por diretórios
gobuster dir -u http://alvo.com -w wordlist.txt

# Busca com extensões específicas
gobuster dir -u http://alvo.com -w wordlist.txt -x php,html,txt

# Busca recursiva
gobuster dir -u http://alvo.com -w wordlist.txt -r

# Com autenticação
gobuster dir -u http://alvo.com -w wordlist.txt -U admin -P senha
```

### 2. Modo DNS (Subdomínios)
```bash
# Busca básica por subdomínios
gobuster dns -d alvo.com -w wordlist.txt

# Com servidor DNS específico
gobuster dns -d alvo.com -w wordlist.txt -r 8.8.8.8

# Mostrar todos os IPs
gobuster dns -d alvo.com -w wordlist.txt -i
```

### 3. Modo S3 (Buckets AWS)
```bash
# Busca por buckets S3
gobuster s3 -w wordlist.txt

# Verificar permissões do bucket
gobuster s3 -w wordlist.txt -s
```

## Opções Comuns

### Opções Gerais
```bash
-h, --help                  Ajuda
-v, --verbose              Modo verboso
-q, --quiet                Modo silencioso
-t, --threads int          Threads (padrão: 10)
--delay duration           Delay entre requisições
--random-agent             User-Agent aleatório
--timeout duration         Timeout (padrão: 10s)
```

### Opções Específicas do Modo DIR
```bash
-u, --url string           URL alvo
-w, --wordlist string      Wordlist
-x, --extensions string    Extensões (ex: php,html)
-r, --follow-redirect      Seguir redirecionamentos
-s, --status-codes string  Códigos de status (ex: 200,204,301,302)
--exclude-length int       Excluir por tamanho de conteúdo
-c, --cookies string       Cookies
-H, --headers stringArray  Headers customizados
-U, --username string      Usuário para autenticação
-P, --password string      Senha para autenticação
```

### Opções Específicas do Modo DNS
```bash
-d, --domain string        Domínio alvo
-r, --resolver string      Servidor DNS
-c, --show-ips             Mostrar IPs
-i, --show-cname           Mostrar CNAME
```

## Exemplos Práticos

### Exemplo 1: Enumeração Básica de Diretórios
```bash
gobuster dir -u http://10.10.10.10 -w /usr/share/wordlists/dirb/common.txt -x php,txt,html -t 50
```

### Exemplo 2: Busca por Subdomínios
```bash
gobuster dns -d example.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -t 100
```

### Exemplo 3: Com Headers Customizados
```bash
gobuster dir -u http://alvo.com -w wordlist.txt -H "X-Forwarded-For: 127.0.0.1" -H "User-Agent: Mozilla"
```

### Exemplo 4: Filtrando por Códigos de Status
```bash
gobuster dir -u http://alvo.com -w wordlist.txt -s 200,204,301,302,307,403
```

### Exemplo 5: Excluindo por Tamanho
```bash
gobuster dir -u http://alvo.com -w wordlist.txt --exclude-length 1234
```

## Wordlists Recomendadas

### Diretórios/Arquivos
```bash
/usr/share/wordlists/dirb/common.txt
/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
/usr/share/wordlists/seclists/Discovery/Web-Content/common.txt
```

### Subdomínios
```bash
/usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt
/usr/share/wordlists/seclists/Discovery/DNS/namelist.txt
```

## Dicas de Uso

1. **Ajuste de Threads**: Use mais threads para redes rápidas, menos para redes lentas
2. **Filtros**: Use `--exclude-length` para remover falsos positivos
3. **Extensões**: Sempre teste múltiplas extensões de arquivo
4. **Verbosidade**: Use `-v` para debugging quando necessário
5. **Rate Limiting**: Use `--delay` em ambientes sensíveis

## Exemplo Completo de Pentest
```bash
# Fase 1: Enumeração de subdomínios
gobuster dns -d empresa.com -w subdomains.txt -t 100 -o subdomains_results.txt

# Fase 2: Enumeração de diretórios em cada subdomínio
for sub in $(cat subdomains_results.txt); do
    echo "Scanning $sub"
    gobuster dir -u "http://$sub" -w common.txt -x php,html -t 50 >> dir_results.txt
done
```

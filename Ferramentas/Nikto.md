## O que é o Nikto?
**Nikto** é um scanner de segurança web de código aberto que realiza testes abrangentes em servidores web, identificando arquivos e programas perigosos, verifica versões desatualizadas de servidores e problemas específicos de versão.

## Sintaxe Básica
```bash
nikto [opções] -h <host>
```

## Comandos Principais

### 1. Escaneamento Básico
```bash
# Escaneamento simples
nikto -h http://exemplo.com

# Escaneamento com porta específica
nikto -h 192.168.1.1 -p 8080

# Usando HTTPS
nikto -h https://exemplo.com
```

### 2. Opções de Host e Porta
```bash
# Múltiplos hosts
nikto -h arquivo_hosts.txt

# Range de portas
nikto -h exemplo.com -p 80,443,8080

# Porta não padrão
nikto -h exemplo.com -p 8443
```

### 3. Opções de Saída e Relatórios
```bash
# Salvar em formato texto
nikto -h exemplo.com -o resultado.txt

# Formato CSV
nikto -h exemplo.com -o resultado.csv -F csv

# Formato XML
nikto -h exemplo.com -o resultado.xml -F xml

# Formato HTML
nikto -h exemplo.com -o resultado.html -F htm

# Múltiplos formatos
nikto -h exemplo.com -o resultado.txt -F txt -o resultado.xml -F xml
```

### 4. Autenticação e Cookies
```bash
# Autenticação Básica
nikto -h exemplo.com -id usuario:senha

# Cookie específico
nikto -h exemplo.com -C cookie=valor

# Header personalizado
nikto -h exemplo.com -H "User-Agent: Mozilla/5.0"
```

### 5. Configurações de Escaneamento
```bash
# Escaneamento evasivo (mais lento)
nikto -h exemplo.com -evasion 1

# Não verificar certificado SSL
nikto -h https://exemplo.com -nossl

# Ignorar códigos HTTP específicos
nikto -h exemplo.com -ignore-code 404,403

# Usar proxy
nikto -h exemplo.com -useproxy http://proxy:8080
```

### 6. Otimização e Performance
```bash
# Timeout personalizado
nikto -h exemplo.com -timeout 10

# Número máximo de requisições
nikto -h exemplo.com -maxtime 1h

# Pausa entre requisições
nikto -h exemplo.com -pause 2
```

### 7. Plugins e Testes Específicos
```bash
# Listar plugins disponíveis
nikto -list-plugins

# Executar plugin específico
nikto -h exemplo.com -Plugins "apache_expect_xss"

# Atualizar banco de dados
nikto -update

# Mostrar informações do banco
nikto -dbinfo
```

### 8. Opções Avançadas
```bash
# Escanear diretório específico
nikto -h exemplo.com -c /cgi-bin/

# Modo tunel (para proxies)
nikto -h exemplo.com -tunnel

# Forçar modo SSL mesmo na porta 80
nikto -h exemplo.com -ssl
```

## Exemplos Práticos

### Exemplo 1: Escaneamento Completo
```bash
nikto -h exemplo.com -p 80,443 -o scan_completo.html -F htm -Tuning 123bde -timeout 3
```

### Exemplo 2: Escaneamento com Autenticação
```bash
nikto -h intranet.local -id admin:senha123 -C "sessionid=abc123" -o auth_scan.txt
```

### Exemplo 3: Escaneamento com Proxy
```bash
nikto -h exemplo.com -useproxy http://127.0.0.1:8080 -evasion 1 -pause 1
```

### Exemplo 4: Scan com Tuning Options
```bash
# Tuning options disponíveis:
# 1 - Testar arquivos e diretórios
# 2 - Testar métodos HTTP perigosos
# 3 - Testar múltiplos index files
# 4 - Testar informações do servidor
# 5 - Testar SSL
# 6 - Testar apenas testes de baixo "ruído"
# 7 - Testar apenas testes de intrusão
# 8 - Testar configurações do servidor
# 9 - Testar arquivos de log
# 0 - Testar detecção de WAF
# a - Testar detecção de aplicações
# b - Testar detecção de backend
# c - Testar detecção de CMS
# d - Testar detecção de DB
# e - Testar detecção de SO
# x - Testar detecção de reverse proxy

nikto -h exemplo.com -Tuning 1234567890abcde
```

## Opções de Tuning Explicadas

### Tuning Básico (1-9)
- **1**: Testes de arquivos (robots.txt, sitemap.xml)
- **2**: Métodos HTTP (PUT, DELETE, OPTIONS)
- **3**: Páginas de índice múltiplas
- **4**: Banner grabbing e informações
- **5**: Problemas relacionados a SSL/TLS
- **6**: Testes silenciosos (menos detecção)
- **7**: Testes intrusivos
- **8**: Configurações do servidor
- **9**: Arquivos de log

### Tuning Avançado (0,a-e,x)
- **0**: Detecção de WAF (Web Application Firewall)
- **a**: Detecção de aplicações web
- **b**: Detecção de backend
- **c**: Detecção de CMS (WordPress, Joomla, etc.)
- **d**: Detecção de banco de dados
- **e**: Detecção de sistema operacional
- **x**: Detecção de proxy reverso

## Docker Usage
```bash
# Escaneamento básico com Docker
docker run --rm sullo/nikto -h http://exemplo.com

# Com saída em arquivo
docker run --rm -v $(pwd):/tmp sullo/nikto -h http://exemplo.com -o /tmp/resultado.txt
```

## Dicas Importantes

### 1. Otimização
```bash
# Para evitar detecção
nikto -h exemplo.com -evasion 1 -Tuning 6 -pause 2

# Para escaneamento rápido
nikto -h exemplo.com -Tuning 0 -maxtime 30m
```

### 2. Interpretação de Resultados
- Verifique falsos positivos
- Priorize vulnerabilidades críticas
- Considere o contexto da aplicação
- Documente todos os achados

## O que é o DIRB?
**DIRB** é um scanner de conteúdo web que busca por diretórios e arquivos ocultos em servidores web. É uma ferramenta essencial para testes de penetração e auditorias de segurança.

## Sintaxe Básica
```bash
dirb [opções] <URL> [<wordlist>] [opções]
```

## Parâmetros Principais

### 1. Parâmetros Básicos
```bash
dirb http://exemplo.com/                    # Scan básico
dirb https://exemplo.com/ wordlist.txt      # Com wordlist personalizada
dirb http://exemplo.com/ -o resultado.txt   # Salvar resultados em arquivo
```

### 2. Opções de Wordlists
```bash
dirb http://exemplo.com/ /usr/share/dirb/wordlists/common.txt
dirb http://exemplo.com/ -w /caminho/para/wordlist.txt
```

### 3. Opções de Saída
```bash
-o resultado.txt          # Salvar output em arquivo
-N 404                    # Ignorar código 404
-v                        # Modo verboso
-S                        # Modo silencioso
```

## Wordlists Comuns Incluídas

```bash
/usr/share/dirb/wordlists/common.txt        # Mais comum
/usr/share/dirb/wordlists/big.txt           # Mais extensa
/usr/share/dirb/wordlists/small.txt         # Mais rápida
/usr/share/dirb/wordlists/catala.txt        # Catalão
/usr/share/dirb/wordlists/extensions_common.txt # Extensões comuns
```

## Opções Detalhadas

### Opções de Scanner
```bash
-a "User-Agent Customizado"    # Customizar User-Agent
-c "cookie=valor"              # Enviar cookies
-H "Header: Valor"             # Adicionar headers personalizados
-p http://proxy:porta          # Usar proxy
-P usuario:senha               # Autenticação proxy
-z milisegundos                # Atraso entre requisições
```

### Opções de Autenticação
```bash
-u usuario:senha               # Autenticação HTTP básica
-u "usuario:senha" -X .php     # Combinar com extensão específica
```

### Opções de Filtragem
```bash
-X .php,.html,.txt            # Procurar por extensões específicas
-x extensoes.txt              # Lista de extensões em arquivo
-N 404,403                    # Ignorar códigos específicos
-w                            # Não parar em códigos de warning
```

### Opções de Método HTTP
```bash
-M GET,POST,HEAD              # Métodos HTTP a usar
-i                            # Usar método HEAD (mais rápido)
-f                            # Fine-tuning do modo HEAD
-r                            # Não buscar recursivamente
-R                            # Buscar recursivamente
-l                            # Incluir caminhos não existentes no output
```

## Exemplos Práticos

### 1. Scan Básico
```bash
dirb http://exemplo.com/
```

### 2. Scan com Wordlist Personalizada
```bash
dirb http://exemplo.com/ /usr/share/dirb/wordlists/big.txt
```

### 3. Scan com Extensões Específicas
```bash
dirb http://exemplo.com/ -X .php,.html,.txt
```

### 4. Scan com Autenticação
```bash
dirb http://exemplo.com/ -u admin:senha123
```

### 5. Scan com Proxy
```bash
dirb http://exemplo.com/ -p http://127.0.0.1:8080
```

### 6. Scan com Delay
```bash
dirb http://exemplo.com/ -z 1000  # 1 segundo entre requisições
```

### 7. Scan com Headers Personalizados
```bash
dirb http://exemplo.com/ -H "X-Forwarded-For: 127.0.0.1"
```

### 8. Scan Salvando Resultados
```bash
dirb http://exemplo.com/ -o resultado_scan.txt
```

### 9. Scan Ignorando Código 404
```bash
dirb http://exemplo.com/ -N 404
```

### 10. Scan com Cookies
```bash
dirb http://exemplo.com/ -c "sessionid=12345"
```

## Exemplo de Output Típico

```
DIRB v2.22    
By The Dark Raver

START_TIME: Mon Jan 1 12:00:00 2024
URL_BASE: http://exemplo.com/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

---- Scanning URL: http://exemplo.com/ ----
+ http://exemplo.com/admin (CODE:200|SIZE:1234)
+ http://exemplo.com/backup (CODE:200|SIZE:5678)
+ http://exemplo.com/config (CODE:403|SIZE:291)
+ http://exemplo.com/phpinfo.php (CODE:200|SIZE:43210)

END_TIME: Mon Jan 1 12:05:00 2024
DOWNLOADED: 4614 - FOUND: 4
```

## Dicas de Uso

### 1. Para Testes de Segurança
```bash
# Scan completo com múltiplas wordlists
dirb https://alvo.com/ /usr/share/dirb/wordlists/common.txt -X .php,.bak,.old -o scan_completo.txt
```

### 2. Para Evitar Detecção
```bash
# Com delay e User-Agent personalizado
dirb http://alvo.com/ -z 2000 -a "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
```

### 3. Para Aplicações Web Específicas
```bash
# Para WordPress
dirb http://alvo.com/ /usr/share/dirb/wordlists/common.txt -X .php -u admin:password
```


## Alternativas e Ferramentas Similares

- **Gobuster** - Mais rápido e moderno
- **Dirsearch** - Python-based
- **FFuF** - Extremamente versátil
- **Wfuzz** - Com fuzzing capabilities

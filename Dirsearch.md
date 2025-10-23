## O que é o Dirsearch?
**Dirsearch** é uma ferramenta de brute force de diretórios e arquivos em servidores web, escrita em Python. É amplamente utilizada em testes de penetração e auditorias de segurança.

## Sintaxe Básica

```bash
python3 dirsearch.py -u <URL> [opções]
```

## Comandos Principais

### 1. Alvo
```bash
# URL básica
-u, --url <URL>

# Exemplos:
python3 dirsearch.py -u http://exemplo.com
python3 dirsearch.py -u https://192.168.1.1
```

### 2. Wordlists
```bash
# Wordlist personalizada
-w, --wordlist <arquivo>

# Wordlists padrão incluídas:
-w /usr/share/dirsearch/db/dicc.txt
-w /usr/share/wordlists/dirb/common.txt

# Exemplo:
python3 dirsearch.py -u http://exemplo.com -w /path/to/wordlist.txt
```

### 3. Extensões
```bash
# Extensões específicas
-e, --extensions <extensões>

# Exemplos:
-e php,html,js
-e txt,log,bak
-e all (todas as extensões disponíveis)

# Extensões com wordlist
--extensions-list <arquivo>
```

### 4. Métodos HTTP
```bash
# Método HTTP específico
-m, --http-method <método>

# Exemplos:
-m GET
-m POST
-m HEAD
-m PUT
```

### 5. Configurações de Requisição

#### Headers Personalizados
```bash
# Header único
-H, --header <header>

# Múltiplos headers
--header-list <arquivo>

# Exemplos:
-H "User-Agent: CustomAgent"
-H "Authorization: Bearer token123"
--header-list headers.txt
```

#### Cookies
```bash
# Cookie
--cookie <cookie>

# Exemplo:
--cookie "session=abc123; user=admin"
```

#### User-Agent
```bash
# User-Agent personalizado
--user-agent <agent>

# Exemplo:
--user-agent "Mozilla/5.0 (Custom)"
```

### 6. Filtros e Configurações de Resposta

#### Códigos de Status
```bash
# Incluir códigos específicos
--include-status <códigos>

# Excluir códigos específicos
--exclude-status <códigos>

# Exemplos:
--include-status 200,301,302
--exclude-status 404,500
```

#### Tamanho das Respostas
```bash
# Excluir por tamanho
--exclude-sizes <tamanhos>

# Exemplo:
--exclude-sizes 0,1234
```

#### Filtro por Texto
```bash
# Filtrar por conteúdo
--filter-text <texto>

# Exemplo:
--filter-text "Not Found"
```

### 7. Configurações de Performance

#### Threads
```bash
# Número de threads (padrão: 25)
-t, --threads <número>

# Exemplo:
-t 50
```

#### Timeout
```bash
# Timeout das requisições (segundos)
--timeout <segundos>

# Exemplo:
--timeout 10
```

#### Delay
```bash
# Delay entre requisições
--delay <segundos>

# Exemplo:
--delay 0.5
```

### 8. Recursividade
```bash
# Escaneamento recursivo
-r, --recursive

# Profundidade máxima da recursão
--max-recursion-depth <nível>

# Exemplo:
-r --max-recursion-depth 2
```

### 9. Saída e Relatórios
```bash
# Formato de saída
--format <formato>

# Formatos disponíveis:
--format plain
--format json
--format xml
--format html

# Arquivo de saída
-o, --output <arquivo>

# Exemplo:
-o resultados.txt --format json
```

### 10. Configurações Avançadas

#### Proxy
```bash
# Usar proxy
--proxy <proxy>

# Exemplos:
--proxy http://127.0.0.1:8080
--proxy socks5://127.0.0.1:9050
```

#### Follow Redirects
```bash
# Seguir redirecionamentos
--follow-redirects
```

#### Force Extension
```bash
# Forçar extensão em todas as requisições
--force-extensions
```

#### Prefix/Suffix
```bash
# Prefixo para todas as palavras
--prefix <prefixo>

# Sufixo para todas as palavras
--suffix <sufixo>

# Exemplo:
--prefix "api/v1/" --suffix ".php"
```

## Exemplos Práticos

### Scan Básico
```bash
python3 dirsearch.py -u http://exemplo.com -e php,html,js -t 30
```

### Scan com Headers Personalizados
```bash
python3 dirsearch.py -u http://exemplo.com \
  -H "Authorization: Bearer token" \
  -H "X-Forwarded-For: 127.0.0.1" \
  -e php \
  -t 50
```

### Scan Recursivo com Filtros
```bash
python3 dirsearch.py -u http://exemplo.com \
  -r \
  --max-recursion-depth 2 \
  --exclude-status 404,500 \
  --exclude-sizes 0,1234
```

### Scan com Proxy (Burp Suite)
```bash
python3 dirsearch.py -u http://exemplo.com \
  --proxy http://127.0.0.1:8080 \
  -e php,html,txt
```

### Scan com Wordlist Personalizada
```bash
python3 dirsearch.py -u http://exemplo.com \
  -w /path/to/custom_wordlist.txt \
  -e all \
  -t 20 \
  -o resultados_scan.txt
```

## Dicas Importantes

1. **Rate Limiting**: Use `--delay` para evitar bloqueios
2. **Stealth**: Configure headers realistas para evitar detecção
3. **Performance**: Ajuste threads conforme a capacidade do servidor
4. **Filtros**: Use filtros para reduzir falsos positivos
5. **Wordlists**: Escolha wordlists apropriadas para o alvo

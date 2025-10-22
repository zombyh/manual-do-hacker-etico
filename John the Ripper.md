# John the Ripper - Guia de Comandos e Uso

## Visão Geral
John the Ripper é uma ferramenta de auditoria de senhas de código aberto, utilizada para testar a força de senhas através de diferentes métodos de cracking.

### Versões Principais
- **John the Ripper Community Edition**: Versão gratuita
- **John the Ripper Pro**: Versão comercial com mais recursos

## Comandos Básicos

### 1. Modo de Ataque Simples (Single Crack)
```bash
john --single arquivo_de_senhas
john --single --format=raw-md5 hash.txt
```

### 2. Modo Wordlist (Dictionary Attack)
```bash
john --wordlist=rockyou.txt arquivo_de_senhas
john --wordlist=wordlist.txt --rules arquivo_de_senhas
```

### 3. Modo Incremental (Força Bruta)
```bash
john --incremental arquivo_de_senhas
john --incremental=Alpha hash.txt
```

### 4. Mostrar Senhas Quebradas
```bash
john --show arquivo_de_senhas
john --show --format=nt hashfile.txt
```

## Formatos de Hash Suportados

### Listar Formatos Disponíveis
```bash
john --list=formats
```

### Formatos Comuns
```bash
# MD5
john --format=raw-md5 hash.txt

# SHA1
john --format=raw-sha1 hash.txt

# NTLM
john --format=nt hash.txt

# LM Hashes
john --format=lm hash.txt

# Unix crypt
john --format=crypt hash.txt

# WordPress
john --format=phpass hash.txt
```

## Opções Avançadas

### Regras de Mangling
```bash
# Usar regras específicas
john --wordlist=wordlist.txt --rules=Jumbo hash.txt

# Listar regras disponíveis
john --list=rules
```

### Sessões e Restauração
```bash
# Iniciar com sessão nomeada
john --session=minhasessao hash.txt

# Restaurar sessão
john --restore=minhasessao

# Listar sessões
john --list=session
```

### Otimização de Performance
```bash
# Especificar número de processos
john --fork=4 hash.txt

# Usar GPU (se disponível)
john --format=raw-md5 --device=1,2 hash.txt
```

## Casos de Uso Específicos

### Quebrar Senhas do Linux
```bash
# Extrair hashes do /etc/shadow
unshadow /etc/passwd /etc/shadow > hashes.txt

# Quebrar hashes
john hashes.txt
```

### Quebrar Senhas do Windows
```bash
# SAM files
john --format=nt samfile.txt

# Usar pwdump output
john --format=lm pwdump.txt
```

### Arquivos ZIP Protegidos
```bash
# Extrair hash
zip2john arquivo.zip > hash.zip

# Quebrar hash
john hash.zip
```

### Arquivos PDF Protegidos
```bash
pdf2john arquivo.pdf > hash.pdf
john hash.pdf
```

### Arquivos RAR
```bash
rar2john arquivo.rar > hash.rar
john hash.rar
```

## Opções de Saída e Monitoramento

### Status e Progresso
```bash
# Mostrar status atual
john --status

# Mostrar senhas quebradas
john --show hash.txt

# Mostrar estatísticas
john --show --count
```

### Salvar Resultados
```bash
# Salvar em arquivo específico
john --stdout --wordlist=wordlist.txt | tee resultados.txt
```

## Configuração Personalizada

### Arquivo de Configuração
```bash
# Editar configuração
nano ~/.john/john.conf

# Usar configuração personalizada
john --config=minhaconfig.conf hash.txt
```

### Exemplo de Regra Personalizada
```
# Adicionar no john.conf
[List.Rules:MinhasRegras]
c
$1$2$3
^[0-9]
```

## Comandos Úteis para Pentesting

### Benchmark de Performance
```bash
john --test
john --test --format=nt
```

### Gerar Wordlists
```bash
# Usar crunch com john
crunch 6 8 abc123 | john --stdin hash.txt
```

### Ataques Combinados
```bash
# Wordlist + regras + incremental
john --wordlist=wordlist.txt --rules --incremental hash.txt
```

## Dicas de Otimização

1. **Ordenar Wordlists**: Ordenar por frequência de uso
2. **Usar Regras**: Aplicar transformações inteligentes
3. **Parallel Processing**: Utilizar múltiplos cores
4. **GPU Acceleration**: Para formatos suportados
5. **Session Management**: Para pausar/retomar trabalhos longos

## Exemplo de Fluxo Completo

```bash
# 1. Extrair hashes
unshadow /etc/passwd /etc/shadow > hashes.txt

# 2. Ataque inicial com wordlist
john --wordlist=rockyou.txt hashes.txt

# 3. Ataque com regras
john --wordlist=rockyou.txt --rules hashes.txt

# 4. Força bruta para senhas restantes
john --incremental hashes.txt

# 5. Mostrar resultados
john --show hashes.txt
```

## Considerações Éticas

- Use apenas em sistemas que você possui ou tem autorização para testar
- Respeite os termos de serviço
- Obtenha autorização por escrito antes de realizar testes
- Use em ambientes controlados para aprendizado
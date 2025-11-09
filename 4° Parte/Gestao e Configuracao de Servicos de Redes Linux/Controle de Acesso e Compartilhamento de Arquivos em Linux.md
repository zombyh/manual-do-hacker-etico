## 🧠 Resumo: Controle de Acesso e Compartilhamento de Arquivos em Linux

### 📌 Visão Geral
Este conteúdo aborda três pilares fundamentais para infraestrutura de TI em Linux:
1. **OpenLDAP**: autenticação centralizada e serviço de diretório.
2. **NFS**: compartilhamento de arquivos em ambientes homogêneos (Linux/Linux).
3. **Samba**: compartilhamento de arquivos em ambientes heterogêneos (Linux/Windows).

---

## 📂 Módulo 1: OpenLDAP – Serviço de Diretório

### 🎯 Conceitos
- **LDAP**: protocolo aberto para autenticação e consulta a serviços de diretório.
- **OpenLDAP**: implementação livre e amplamente utilizada.
- **Vantagem**: otimizado para leitura, ideal para autenticação.
- **Estrutura**: 
  - **DN**: Nome Distinto (identificador único).
  - **RDN**: Nome Distinto Relativo.
  - **DIT**: Árvore de Informações do Diretório.

### 🔧 Instalação e Configuração
- Pacotes: `slapd`, `ldap-utils`
- Comando de instalação:  
  ```bash
  apt install slapd ldap-utils
  ```
- Reconfiguração:  
  ```bash
  dpkg-reconfigure slapd
  ```
- Backend recomendado: **MDB** (Lightning Memory-Mapped Database)

### 🛠 Comandos Básicos
- Consulta:
  ```bash
  ldapsearch -x -LLL -H ldap:/// -b dc=exemplo,dc=org dn
  ```
- Autenticação:
  ```bash
  ldapwhoami -x -D cn=admin,dc=exemplo,dc=org -W
  ```
- Adição de entradas:
  ```bash
  ldapadd -x -D cn=admin,dc=exemplo,dc=org -W -f arquivo.ldif
  ```
- Modificação:
  ```bash
  ldapmodify -x -D cn=admin,dc=exemplo,dc=org -W -f arquivo.ldif
  ```

### 🔐 Boas Práticas de Segurança
- **Senhas**:
  - Nunca armazenar em texto claro.
  - Usar **hash + salt** (ex: MD5, SHA).
  - Evitar **Rainbow Tables**.
- **Conexão**:
  - Usar **TLS/SSL** para criptografar tráfego.
  - Certificado autoassinado ou de CA confiável.

### 💾 Backup e Restauração
- Parar serviço:
  ```bash
  systemctl stop slapd
  ```
- Backup:
  ```bash
  slapcat -b cn=config > config.ldif
  slapcat -b dc=exemplo,dc=org > dados.ldif
  ```
- Restaurar:
  ```bash
  slapadd -F /etc/ldap/slapd.d -b cn=config -i config.ldif
  ```

---

## 📂 Módulo 2: NFS – Network File System

### 🎯 Conceitos
- Protocolo para compartilhamento de arquivos em rede.
- Cliente-servidor.
- Versão atual: **NFSv4**.

### 🔧 Instalação e Configuração
- Servidor:
  ```bash
  apt install nfs-kernel-server
  ```
- Cliente:
  ```bash
  apt install nfs-common
  ```
- Exportar pasta: editar `/etc/exports`
  ```
  /mnt/sharedfolder 192.168.1.100(rw,sync,no_subtree_check)
  ```
- Aplicar exportações:
  ```bash
  exportfs -a
  systemctl restart nfs-kernel-server
  ```

### 🔐 Segurança no NFS
- **Problema**: NFS presume clientes confiáveis.
- **Controle de acesso**:
  - Por IP/hostname.
  - Por UID/GID (AUTH_SYS) – pouco seguro.
  - Recomendado: **AUTH_GSS** com Kerberos (RPCSEC_GSS).

### 🔄 Alternativa: SSHFS
- Montagem de sistema de arquivos via SSH.
- Criptografia nativa.
- Comando:
  ```bash
  sshfs usuario@servidor:/pasta/remota /pasta/local
  ```

---

## 📂 Módulo 3: Samba – Compartilhamento com Windows

### 🎯 Conceitos
- Implementação open source do protocolo **SMB/CIFS**.
- Permite integração com domínios Windows (Active Directory).
- Serviços principais:
  - **smbd**: compartilhamento de arquivos e impressão.
  - **nmbd**: resolução de nomes NetBIOS.

### 🔧 Instalação e Configuração
- Instalação:
  ```bash
  apt install samba samba-common
  ```
- Arquivo de configuração: `/etc/samba/smb.conf`

### 🔓 Compartilhamento Inseguro (Público)
- Permite acesso anônimo.
- Exemplo de diretiva:
  ```ini
  [Anonymous]
    path = /mnt/samba/inseguro
    browsable = yes
    writable = yes
    guest ok = yes
    force user = nobody
  ```

### 🔐 Compartilhamento Seguro
- Autenticação por usuário Linux + senha Samba.
- Criar grupo e usuários:
  ```bash
  addgroup gruposal
  usermod usuario -aG gruposal
  smbpasswd -a usuario
  ```
- Diretiva segura:
  ```ini
  [Seguro]
    path = /mnt/samba/seguro
    valid users = @gruposal
    guest ok = no
    writable = yes
  ```

---

## 🧩 Tópicos de Segurança da Informação

### ✅ Autenticação Centralizada
- OpenLDAP como base única para usuários.
- Reduz dispersão de credenciais.

### ✅ Criptografia
- LDAP com TLS.
- SSHFS como alternativa segura ao NFS.
- Samba com autenticação por usuário.

### ✅ Controle de Acesso
- NFS: restrição por IP e uso de Kerberos.
- Samba: grupos e permissões POSIX.

### ✅ Armazenamento de Senhas
- Hash + salt.
- Uso de schemas como `inetOrgPerson`.

### ✅ Logon Único (SSO)
- Diferente de "mesmo logon" (LDAP apenas).
- SSO permite acesso a múltiplos sistemas com uma única autenticação.

---

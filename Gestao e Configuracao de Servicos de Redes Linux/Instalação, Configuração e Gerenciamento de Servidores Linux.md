## 🐧 Resumo: Instalação, Configuração e Gerenciamento de Servidores Linux

## 1. Servidor Web Apache

### 1.1. Introdução
- **Apache HTTP Server**: servidor web de código aberto, modular e amplamente utilizado.
- Surgiu em 1995 como uma evolução do **NCSA HTTPd**.
- Nome inspirado na tribo Apache e no termo “a patchy server”.

### 1.2. Estrutura Modular
- **Núcleo principal** + **módulos** que podem ser habilitados/desabilitados.
- Exemplos de módulos:
  - `mod_rewrite`: reescrita de URLs
  - `mod_ssl`: suporte a HTTPS
  - `mod_security`: WAF (Web Application Firewall)

### 1.3. Diretórios Principais (Debian/Ubuntu)
- `/etc/apache2/`
  - `apache2.conf`: arquivo principal de configuração
  - `ports.conf`: define portas de escuta
  - `sites-available/` e `sites-enabled/`: hosts virtuais
  - `mods-available/` e `mods-enabled/`: módulos
  - `conf-available/` e `conf-enabled/`: configurações adicionais

### 1.4. Comandos de Gerenciamento
```bash
sudo systemctl start|stop|restart|status apache2
sudo systemctl enable|disable apache2
sudo a2enmod|a2dismod <módulo>
sudo a2ensite|a2dissite <site>
sudo apache2ctl configtest
```

### 1.5. Logs e Monitoramento
- Localização: `/var/log/apache2/`
  - `access.log`: requisições recebidas
  - `error.log`: erros do servidor
- Comandos úteis:
  ```bash
  tail -f /var/log/apache2/access.log
  grep "404" access.log
  awk '{print $1}' access.log  # extrai IPs
  ```

### 1.6. Virtual Hosts
- Permite hospedar múltiplos sites no mesmo servidor.
- Configuração em `/etc/apache2/sites-available/`
- Uso do arquivo `/etc/hosts` para testes locais.

---

## 2. Servidor DNS BIND

### 2.1. Introdução ao DNS
- **DNS (Domain Name System)**: converte nomes em IPs.
- **BIND (Berkeley Internet Name Domain)**: implementação mais usada.
- **Servidores Raiz**: 13 servidores globais (A a M), essenciais para a resolução.

### 2.2. Componentes do BIND
- `named`: daemon principal
- `rndc`: controle remoto
- `dig`: ferramenta de consulta
- Arquivos de zona: definem domínios e registros

### 2.3. Arquivos de Configuração
- `named.conf`: configuração principal
- `named.conf.options`: opções globais
- `named.conf.local`: zonas locais
- Arquivos de zona: `db.exemplo.com`, `db.192.168.1`

### 2.4. Tipos de Zonas
- **Zona Direta (Primária)**: mapeia nome → IP
- **Zona Reversa**: mapeia IP → nome
- **Zona Secundária**: cópia de uma zona primária para redundância

### 2.5. Comandos de Gerenciamento
```bash
sudo systemctl start|stop|restart|status bind9
sudo named-checkconf
sudo named-checkzone <zona> <arquivo>
dig @localhost exemplo.com
nslookup exemplo.com localhost
```

### 2.6. Configuração como Forwarder
- Encaminha consultas para outro servidor DNS (ex.: 8.8.8.8).
- Melhora desempenho com cache e permite políticas de segurança.

---

## 3. Aspectos de Segurança da Informação

### 3.1. Apache
- Use `mod_security` para proteger contra ataques web.
- Habilite `mod_ssl` e certifique-se de usar TLS atualizado.
- Restrinja permissões de diretórios com `<Directory>`.
- Monitore logs com ferramentas como `fail2ban`.

### 3.2. BIND
- Use **DNSSEC** para garantir autenticidade e integridade.
- Restrinja transferências de zona com `allow-transfer`.
- Configure `rndc` com chaves seguras.
- Mantenha o BIND atualizado contra vulnerabilidades.

### 3.3. Boas Práticas Gerais
- Atualize o sistema regularmente: `sudo apt update && sudo apt upgrade`
- Use firewall (`ufw`) para abrir apenas portas necessárias.
- Isolar serviços em containers ou VMs quando possível.
- Backup de configurações e zonas DNS.

---

## 4. Referências Úteis
- [Documentação Oficial do Apache](https://httpd.apache.org/docs/)
- [Manual do BIND 9](https://www.isc.org/bind/)
- Livros:
  - *DNS e BIND* (Albitz & Liu)
  - *Pro DNS e BIND 10* (Aitchison)
  - *Apache: Guia do Administrador* (Costa)

---

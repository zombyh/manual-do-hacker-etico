
# Resumo: Hardening de Servidores Web

## 1. Introdução ao Hardening

- **Hardening**: Processo de fortalecimento de sistemas para reduzir vulnerabilidades e aumentar a resistência a ataques.
- **Objetivo**: Garantir a **Confidencialidade, Integridade e Disponibilidade (CID)** dos dados e serviços.
- **Benefícios**:
  - Melhoria da segurança e resistência a ataques.
  - Aumento do desempenho e estabilidade do sistema.
  - Redução da superfície de ataque.

---

## 2. Conceito e Importância do Hardening

- Surgiu como resposta ao aumento de ataques cibernéticos.
- Envolve:
  - Identificação de vulnerabilidades.
  - Aplicação de patches e atualizações.
  - Configuração segura de serviços e permissões.
  - Remoção de serviços desnecessários.
- **Exemplo prático**: Servidor com hardening resiste a ataques de força bruta; servidor sem hardening é comprometido.

---

## 3. Hardening no IIS (Internet Information Services)

### Sobre o IIS:
- Servidor web da Microsoft.
- Integrado com tecnologias Microsoft (ex: ASP.NET).
- Arquitetura modular.
- Suporte a HTTP, HTTPS, FTP, SMTP.

### Boas Práticas no IIS:

#### Antes da Instalação:
- Isolar o servidor (não instalar outros serviços no mesmo host).
- Criar partição separada para o site (ex: disco D:).

#### Durante a Configuração:
- Usar **pools de aplicativos** separados para cada site.
- Desabilitar protocolos inseguros (SSLv2, SSLv3) – usar **TLS 1.2+**.
- Restringir verbos HTTP: permitir apenas **GET** e **POST**; negar **OPTIONS** e **CONNECT**.
- Configurar **cabeçalhos de segurança**:
  - `X-Frame-Options`
  - `X-XSS-Protection`
  - `Content-Security-Policy`
- Habilitar **Restrição de IP Dinâmico** para bloquear ataques de força bruta.
- Ativar **logs detalhados** para monitoramento e auditoria.
- Executar o serviço com o **mínimo de privilégios** necessários.

---

## 4. Hardening no Apache HTTP Server

### Sobre o Apache:
- Servidor web de código aberto.
- Modular, extensível e amplamente utilizado.
- Suporte a múltiplas linguagens (PHP, Python, etc.).

### Boas Práticas no Apache:

#### Sistema Operacional (Linux):
- Atualizar sistema e pacotes regularmente.
- Desativar serviços desnecessários.
- Configurar firewall (ex: `ufw` ou `iptables`) para liberar apenas portas 80 e 443.

#### Configurações do Apache:
- Ocultar versão do servidor:
  ```apache
  ServerTokens Prod
  ServerSignature Off
  ```
- Habilitar módulos de segurança:
  - `mod_reqtimeout`: proteção contra DoS.
  - `mod_ssl`: suporte a HTTPS.
  - `mod_log_config`: registro de logs.
- Usar **HTTPS** com certificados válidos (ex: Let's Encrypt).
- Limitar permissões de arquivos e diretórios.
- Criar usuários e grupos específicos para o serviço.
- Monitorar logs de acesso e erro regularmente.

---

## 5. Configurações Comuns de Hardening

### Redução da Superfície de Ataque:
- Fechar portas desnecessárias.
- Desabilitar serviços e módulos não utilizados.

### Autenticação e Acesso:
- Usar princípio do **menor privilégio**.
- Restringir acesso remoto por IP.
- Evitar contas compartilhadas.

### Criptografia:
- Usar **TLS 1.2+**.
- Redirecionar HTTP para HTTPS.

### Logs e Monitoramento:
- Ativar logs de acesso, erro e segurança.
- Revisar logs periodicamente para detectar atividades suspeitas.

---

## 6. Casos Reais com Falta de Hardening

- **Equifax (2017)**: Vulnerabilidade não corrigida no Apache Struts → vazamento de dados.
- **MyFitnessPal (2018)**: Falha de segurança explorada → 150 milhões de usuários afetados.
- **Lição**: Aplicar patches rapidamente e manter sistemas atualizados.

---

## 7. Materiais de Aprofundamento

- **NIST SP 800**: Publicações sobre segurança computacional.
- **OWASP Top 10**: Guia de segurança para aplicações web.
- **CERT.br**: Orientações de segurança cibernética no Brasil.

---

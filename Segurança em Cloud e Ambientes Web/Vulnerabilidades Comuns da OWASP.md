
# 🎯 Vulnerabilidades Comuns da OWASP – Resumo Estruturado

## 📌 Introdução
- O **OWASP Top 10** é uma lista das vulnerabilidades mais críticas em aplicações web.
- Conhecer essas vulnerabilidades é essencial para desenvolvedores e profissionais de segurança.
- Muitos problemas surgem por **falta de conhecimento** sobre como os ataques são realizados.

---

## 🧩 Módulo 1: Injeção, Quebra de Controle de Acesso e Falhas Criptográficas

### 1. Injeção (Injection)
- Ocorre quando dados não confiáveis são enviados a um interpretador como parte de um comando.
- Exemplos comuns:
  - **SQL Injection**: Inserção de código SQL malicioso em campos de entrada.
  - **Command Injection**: Execução de comandos do sistema operacional.

#### Exemplo de SQL Injection:
- Comando original:
  ```sql
  SELECT * FROM users WHERE name="tom" AND password="123456"
  ```
- Injeção no campo senha: `' OR 1='1`
- Comando resultante:
  ```sql
  SELECT * FROM users WHERE name="tom" AND password="' OR 1='1'"
  ```
- Resultado: Acesso concedido sem senha correta.

#### Exemplo de Command Injection:
- Aplicação executa: `ping <IP>`
- Injeção: `127.0.0.1; cat /etc/passwd`
- Resultado: Executa `ping` e depois exibe o arquivo de senhas.

---

### 2. Quebra de Controle de Acesso (Broken Access Control)
- Ocorre quando usuários podem acessar funcionalidades ou dados sem autorização.
- Exemplo: Acesso à página de administração sem credenciais administrativas.

#### Ataque de Força Bruta:
- Uso de scripts (ex: Python) para testar senhas comuns.
- Ferramentas como **Burp Suite** ajudam a interceptar e modificar requisições.

#### Mitigações:
- Autenticação multifator (MFA)
- Limite de tentativas de login
- Senhas fortes e políticas de rotação

---

### 3. Falhas Criptográficas (Cryptographic Failures)
- Exposição de dados sensíveis devido à falta de criptografia ou uso inadequado.
- Exemplos:
  - Senhas armazenadas em texto claro
  - Uso de algoritmos fracos (ex: MD5)
  - Falta de "salt" em hashes

#### Rainbow Tables:
- Tabelas pré-computadas com hashes de senhas comuns.
- Uso de "salt" aleatório torna inviável o uso de rainbow tables.

---

## 🧩 Módulo 2: Projeto Inseguro, Configurações Incorretas e Componentes Vulneráveis

### 1. Projeto Inseguro (Insecure Design)
- Vulnerabilidades na arquitetura ou no design da aplicação.
- Exemplos:
  - Falta de limites para entradas
  - Uso de APIs inseguras
  - Privilégios excessivos

#### Prevenção:
- Ciclo de vida de desenvolvimento seguro (SDLC)
- Uso de componentes seguros
- Validação em todas as camadas

---

### 2. Configurações de Segurança Incorretas (Security Misconfiguration)
- Configurações padrão, serviços desnecessários, páginas de erro detalhadas.
- Exemplo:
  - Listagem de diretórios ativa
  - Mensagens de erro que revelam versões de software

#### Ferramentas de Varredura:
- **Nikto**: Identifica versões desatualizadas e diretórios expostos.
- **Nessus**, **OpenVAS**: Varreduras mais profundas.

---

### 3. Componentes Vulneráveis e Desatualizados
- Uso de bibliotecas, frameworks ou plugins com vulnerabilidades conhecidas.
- Exemplo: Plugins do WordPress sem atualização.

#### Prevenção:
- Inventário de componentes
- Atualizações regulares
- Fontes confiáveis
- Monitoramento de CVEs

---

## 🧩 Módulo 3: Falhas de Identificação, Autenticação, Integridade e Software

### 1. Falhas de Identificação e Autenticação
- Autenticação "quebrada" permite assumir identidades de usuários.
- Cenários:
  - Força bruta com listas de senhas comuns
  - Ausência de MFA

#### Autenticação Multifator (MFA):
- Fatores:
  - Algo que você sabe (senha)
  - Algo que você tem (token)
  - Algo que você é (biometria)

---

### 2. Falhas de Integridade de Dados e Software
- Dados ou software são adulterados sem verificação.
- Exemplo: **Desserialização Insegura**

#### Desserialização Insegura:
- Objetos serializados são manipulados para alterar comportamentos.
- Exemplo em PHP:
  - Objeto serializado: `O:4:"User":3:{s:8:"username";s:6:"carlos";s:6:"logged";b:0;s:5:"admin";b:0;}`
  - Alterado para: `...s:5:"admin";b:1;}` → usuário vira admin.

#### Prevenção:
- Assinatura digital de componentes
- Verificação de origem confiável
- Criptografia e integridade de dados serializados

---

## 🧩 Módulo 4: Falha de Registro e Monitoração, e Falsificação de Requisição

### 1. Falhas de Registro e Monitoração (Logging and Monitoring Failures)
- Falta de logs adequados ou monitoramento contínuo.
- Cenários:
  - Ataques não detectados
  - Logs apagados por invasores

#### Ferramentas de Monitoramento:
- **Nagios**, **Splunk**, **OSSEC**, **Tripwire**

#### Boas Práticas:
- Backup de logs
- Alertas para atividades suspeitas
- Análise forense possibilitada

---

### 2. Falsificação de Requisição do Lado do Servidor (SSRF)
- Ataque que engana o servidor para fazer requisições a sistemas internos.
- Exemplo: URL maliciosa que altera a senha do usuário autenticado.

#### Prevenção:
- Validação de origem das requisições
- Confirmação do usuário para ações críticas
- Uso de tokens anti-CSRF

---

## ✅ Conclusão
- O **OWASP Top 10** é uma referência essencial para segurança de aplicações web.
- Desenvolvedores e analistas de segurança devem:
  - Conhecer as vulnerabilidades
  - Implementar mitigações
  - Manter-se atualizados com novas ameaças

---

### 🔧 Ferramentas Mencionadas:
- Burp Suite
- Nikto
- SQLMap
- OWASP BWA (Broken Web Applications)
- Nessus, OpenVAS
- Nagios, Splunk, OSSEC

---

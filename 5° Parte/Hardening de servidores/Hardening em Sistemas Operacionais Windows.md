## 📘 Resumo: Hardening em Sistemas Operacionais Windows

### 🎯 **Objetivo Geral**
Capacitar profissionais de TI a implementar práticas de segurança, auditoria e hardening em ambientes Windows, com foco em:
- Registro do Windows
- Gerenciamento de serviços
- PowerShell
- Active Directory

---

## 🔐 1. Hardening no Windows

### O que é Hardening?
- Processo de **redução da superfície de ataque** por meio de:
  - Remoção de aplicativos e serviços desnecessários
  - Aplicação de configurações seguras
  - Atualizações e patches
  - Implementação de políticas de segurança

### Base de Referência (Baseline)
- Utilização de **baselines de segurança** como ponto de partida
- Exemplos de referências:
  - **CIS Benchmarks**
  - **NIST**
  - **Microsoft Security Baselines**

---

## 🛠️ 2. Ferramentas e Utilitários do Windows

### Prompt de Comando (CMD)
- Interpretador de linha de comando
- Comandos básicos (ex.: `dir`, `cd`, `tasklist`, `netstat`, `sc`)
- Uso de **redirecionadores** (`>`, `>>`, `|`) para automação

### PowerShell
- Shell baseado em **.NET**
- Trabalha com **objetos**, não apenas texto
- Cmdlets no formato **Verbo-Substantivo** (ex.: `Get-Service`)
- Permite automação avançada, mas também é alvo de ataques

### Comandos Úteis para Auditoria
| Comando | Função |
|---------|--------|
| `whoami` | Exibe usuário atual |
| `systeminfo` | Informações do sistema |
| `netstat -an` | Portas abertas e conexões |
| `tasklist` | Processos em execução |
| `net user` | Gerenciamento de usuários |
| `schtasks` | Tarefas agendadas |
| `attrib` | Atributos de arquivos |
| `icacls` | Permissões de acesso |

---

## 🧩 3. Registro do Windows (Registry)

### Estrutura
- Banco de dados **hierárquico** com configurações do sistema e aplicações
- Principais chaves:
  - `HKEY_LOCAL_MACHINE (HKLM)`
  - `HKEY_CURRENT_USER (HKCU)`
  - `HKEY_CLASSES_ROOT (HKCR)`
  - `HKEY_USERS (HKU)`
  - `HKEY_CURRENT_CONFIG (HKCC)`

### Tipos de Valores
- `REG_SZ`, `REG_DWORD`, `REG_BINARY`, `REG_MULTI_SZ`, etc.

### Comando `reg`
- Exemplo:  
  ```cmd
  reg add HKLM\Software\Policies\Microsoft\Windows\WindowsUpdate\AU /v NoAutoRebootWithLoggedOnUsers /t REG_DWORD /d 1 /f
  ```

---

## ⚙️ 4. Gerenciamento de Serviços

### Service Control Manager (SCM)
- Gerencia serviços e drivers
- Comando: `sc.exe`
- Exemplos:
  - `sc query type= service`
  - `sc sidtype MyService restricted`

### Serviços Desnecessários
- Desativar serviços não essenciais para **reduzir superfície de ataque**

---

## 🔒 5. Segurança com PowerShell

### Vantagens
- Automação de tarefas administrativas
- Acesso a provedores (Registry, Certificados, etc.)
- Pipeline de objetos

### Riscos
- Pode ser usado para **malware em memória**
- **Scripts maliciosos** podem ser executados sem tocar em disco

### Boas Práticas
- Use a **versão mais recente**
- Habilite **logging**
- Use **Just Enough Administration (JEA)**
- Aplique **políticas de execução** restritivas

---

## 🏢 6. Active Directory (AD)

### O que é?
- Serviço de diretório para **gerenciamento centralizado** de usuários, computadores e políticas

### Componentes
- **Esquema**: define classes e atributos
- **Catálogo Global**: índice de todos os objetos
- **Replicação**: sincronização entre controladores de domínio

### Protocolos
- **LDAP**
- **Kerberos**
- **DNS**

---

## 🧪 7. Microsoft Defender for Endpoint

- Antigo **Microsoft Defender ATP**
- Plataforma unificada para:
  - Prevenção
  - Detecção
  - Investigação
  - Resposta a ameaças

---

## ✅ 8. Checklist de Hardening

- [ ] Aplicar baseline de segurança (CIS, NIST, Microsoft)
- [ ] Remover serviços e aplicativos desnecessários
- [ ] Atualizar sistema e aplicações
- [ ] Configurar firewall e políticas de rede
- [ ] Auditar permissões de arquivos e registros
- [ ] Monitorar logs e eventos
- [ ] Implementar controles de acesso (ex.: JEA)
- [ ] Usar PowerShell com logging habilitado
- [ ] Proteger o Active Directory
- [ ] Utilizar Microsoft Defender for Endpoint

---

## 📚 Fontes Recomendadas

- [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks/)
- [NIST](http://www.nist.org)
- [Microsoft Learn](https://learn.microsoft.com)
- [SANS](https://www.sans.org)

---

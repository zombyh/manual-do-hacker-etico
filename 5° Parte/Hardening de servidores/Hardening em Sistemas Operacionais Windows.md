## 📌 **1. Introdução e Propósito**

### **Contexto**
- **Foco**: Segurança da informação em ambientes Microsoft Windows.
- **Público-alvo**: Profissionais de TI, administradores de sistemas, auditores de segurança.
- **Objetivo**: Capacitar para **garantir integridade, confiabilidade e segurança** de sistemas Windows.

### **Tópicos Principais**
1. **Hardening**: Reforço de segurança.
2. **Auditoria**: Monitoramento e detecção de riscos.
3. **Registro do Windows**: Configurações do sistema.
4. **PowerShell**: Automação e administração avançada.
5. **Active Directory**: Gestão de identidades e acessos.

### **Importância**
- Windows é o sistema mais atacado globalmente.
- Necessidade de **gestão proativa** e **controles contínuos**.

---

## 🛡️ **2. Hardening em Sistemas Operacionais Windows – Parte 1**

### **O que é Hardening?**
- **Processo de fortalecimento** de sistemas para reduzir vulnerabilidades.
- **Base normativa**: ISO/IEC 27000-27002.
- **Objetivo**: Minimizar a **superfície de ataque**.

### **Baselines de Segurança**
- **Definição**: Conjunto mínimo de configurações e boas práticas.
- **Fontes recomendadas**:
  - **CIS Benchmarks** (Center for Internet Security)
  - **NIST** (National Institute of Standards and Technology)
  - **Microsoft Security Baselines**

### **Por que o Windows é visado?**
- **Popularidade** e vasta base de instalação.
- **Compatibilidade** com hardwares e softwares diversos.
- **Uso de softwares de terceiros** aumenta riscos.

### **Microsoft Defender for Endpoint**
- **Plataforma unificada** de proteção.
- **Funcionalidades**:
  - Prevenção, detecção, investigação e resposta.
  - Proteção contra malware, trojans, ransomware.
- Substitui o **Microsoft Defender ATP**.

---

## 💻 **3. Prompt de Comando e Comandos Básicos**

### **cmd.exe vs PowerShell**
- **cmd.exe**: Interpretador de comandos tradicional.
- **PowerShell**: Shell avançado baseado em **.NET CLR**, com manipulação de objetos.

### **Comandos Essenciais para Auditoria**
| Comando | Função |
|---------|---------|
| `dir /a` | Lista arquivos ocultos e de sistema |
| `tree /f` | Mostra estrutura de diretórios e arquivos |
| `tasklist` | Lista processos em execução |
| `netstat -an` | Mostra portas abertas e conexões |
| `systeminfo` | Informações do sistema e hotfixes |
| `whoami` | Exibe usuário atual e domínio |
| `driverquery` | Drivers instalados |
| `attrib` | Atributos de arquivos (oculto, sistema, etc.) |
| `icacls` | Permissões de arquivos e diretórios |

### **Operadores de Redirecionamento**
- `>`: Saída para arquivo (sobrescreve).
- `>>`: Saída para arquivo (anexa).
- `|`: Pipe – passa saída para outro comando.
- `>&` e `<&`: Redirecionamento de identificadores.

---

## 🛠️ **4. Utilitários Administrativos do Windows**

### **Agendamento de Tarefas**
- **schtasks.exe**: Agendar comandos local ou remotamente.
- **Exemplo malicioso**: Agendar backdoor (`schtasks /create /tn "backdoor" /tr "C:\backdoor.exe" /sc onstart`).

### **Gerenciamento de Processos**
- **tasklist**: Lista processos com filtros (memória, usuário, PID).
- **taskkill**: Finaliza processos por PID ou nome.

### **Gerenciamento de Usuários**
- **net user**: Adiciona, remove, modifica usuários.
- **net localgroup**: Gerencia grupos locais.
- **Exemplo**: `net user aluno 123456 /add` + `net localgroup "Remote Desktop Users" aluno /add`.

### **Gerenciamento de Rede**
- **netsh**: Configura interfaces, firewall, IP, DNS.
- **Exemplo**: `netsh interface ip set address "Ethernet 1" static 192.168.10.23 255.255.255.0 192.168.10.1 1`

### **Firewall**
- **netsh advfirewall**: Gerencia regras de firewall.
- **Comandos**:
  - `set allprofile state off` → Desativa firewall.
  - `set currentprofile state on` → Ativa perfil atual.

### **WMIC (Windows Management Instrumentation)**
- **Coleta de dados** do sistema.
- **Exemplos**:
  - `wmic product get name,version` → Lista softwares.
  - `wmic product where name="Programa" call uninstall` → Desinstala.

---

## 🗃️ **5. Registro do Windows (Registry)**

### **O que é?**
- Banco de dados hierárquico com configurações do sistema, hardware, software e usuários.

### **Principais Chaves**
| Chave | Descrição |
|-------|-----------|
| **HKLM** (HKEY_LOCAL_MACHINE) | Configurações do hardware e sistema |
| **HKCU** (HKEY_CURRENT_USER) | Configurações do usuário logado |
| **HKCR** (HKEY_CLASSES_ROOT) | Associações de arquivos e COM |
| **HKU** (HKEY_USERS) | Configurações de todos os usuários |
| **HKCC** (HKEY_CURRENT_CONFIG) | Perfil de hardware atual |

### **Tipos de Valores**
- REG_SZ → String de texto.
- REG_DWORD → Valor inteiro 32-bit.
- REG_BINARY → Dados binários.
- REG_MULTI_SZ → Múltiplas strings.
- REG_EXPAND_SZ → String com variáveis de ambiente.

### **Comando `reg`**
- Exemplos:
  ```cmd
  reg add HKLM\Software\Teste /v Valor /t REG_DWORD /d 1 /f
  reg delete HKLM\Software\Teste /f
  reg save HKLM\Software\Teste backup.hiv
  ```

### **Segurança do Registro**
- **Restringir acesso** anônimo e remoto.
- **Auditar alterações** em chaves sensíveis.
- **Backup regular** do registro.

---

## ⚙️ **6. Service Control Manager (SCM)**

### **O que é?**
- Utilitário para gerenciar serviços do Windows.
- **sc.exe**: Versão em linha de comando.

### **Comandos Úteis**
```cmd
sc query type= service          # Lista serviços
sc query wuauserv              # Informações de um serviço
sc config Serviço start= disabled  # Desativa serviço
sc sidtype Serviço restricted  # Restringe SID do serviço
```

### **Segurança de Serviços**
- **Reduzir privilégios** dos serviços.
- **Usar SIDs específicos** para serviços.
- **Monitorar** serviços não autorizados.

---

## 🚀 **7. Windows PowerShell**

### **Conceito**
- Shell e linguagem de script baseada em **.NET**.
- Trabalha com **objetos**, não texto.

### **Cmdlets**
- **Verbo-Substantivo**: `Get-Service`, `Stop-Process`, `New-User`.
- **Pipeline**: Encadeamento de comandos (`Get-Service | Where Status -eq "Running"`).

### **Exemplos de Uso**
```powershell
# Download de arquivo
(New-Object Net.WebClient).DownloadFile('http://exemplo.com/arquivo.exe', 'C:\arquivo.exe')

# Scan de portas
$ports = (21,80,443); $ip = "192.168.1.1"
foreach ($port in $ports) { Test-NetConnection -ComputerName $ip -Port $port }
```

### **Riscos de Segurança**
- PowerShell pode ser usado em **ataques fileless**.
- **Download e execução direto da memória**.
- **Bypass de execução** com `-ExecutionPolicy Bypass`.

### **Boas Práticas**
- Usar **versão mais recente**.
- Habilitar **logging extensivo** (Eventos do PowerShell).
- **Restringir execução** com AppLocker ou Windows Defender Application Control.
- **Validar parâmetros** em scripts.

---

## 🌐 **8. Active Directory (AD)**

### **O que é?**
- Serviço de diretório para redes Windows.
- **Centraliza autenticação** e gerenciamento de recursos.

### **Componentes Principais**
- **Domínio**: Unidade administrativa.
- **Controlador de Domínio (DC)**: Servidor que autentica usuários.
- **Árvore e Floresta**: Estruturas hierárquicas.
- **Catálogo Global**: Index de objetos do diretório.

### **Protocolos Envolvidos**
- **LDAP**: Consulta ao diretório.
- **Kerberos**: Autenticação.
- **DNS**: Resolução de nomes e localização de DCs.

### **Funcionalidades de Segurança**
- **Políticas de Grupo (GPO)**: Aplicação centralizada de configurações.
- **Delegação de Controle**: Permissões granulares.
- **Replicação**: Sincronização entre DCs.

### **Comandos Úteis**
```cmd
whoami /user          # Exibe SID do usuário
net user /domain      # Lista usuários do domínio
gpupdate /force       # Atualiza políticas de grupo
```

---

## ✅ **9. Hardening em Sistemas Operacionais Windows – Parte 2**

### **Camadas de Proteção do Windows**
1. **Virtualização segura** (VMs blindadas).
2. **Controle de aplicativos** (Windows Defender Application Control).
3. **Proteção de credenciais** (Credential Guard).
4. **Detecção e resposta** (Microsoft Advanced Threat Analytics).
5. **Firewall de datacenter**.

### **Itens de Configuração para Hardening**
- ✅ Desativar serviços desnecessários.
- ✅ Configurar NTP (sincronização de tempo).
- ✅ Aplicar patches regularmente.
- ✅ Restringir acesso remoto (RDP, WinRM).
- ✅ Criptografia de disco (BitLocker).
- ✅ Monitoramento contínuo de logs.

---

## 📚 **10. Conclusão e Referências**

### **Conclusões**
- **Hardening é contínuo**, não apenas uma etapa.
- **Automação é essencial** (PowerShell, scripts).
- **Monitoramento proativo** previne incidentes.
- **AD é central** para segurança corporativa.

### **Fontes Recomendadas**
- **Microsoft Learn**: Documentação oficial.
- **CIS Benchmarks**: Baselines gratuitas.
- **SANS Institute**: Artigos e treinamentos.
- **Windows Command Line Blog**: Dicas de cmd e PowerShell.

---

## 📌 **Resumo Final**

| Área | Conceito-Chave | Ferramentas | Boas Práticas |
|------|---------------|-------------|---------------|
| **Hardening** | Reduzir superfície de ataque | CIS Benchmarks, NIST | Baselines, updates, serviços mínimos |
| **CLI** | Automação e auditoria | cmd, PowerShell, netsh | Logging, redirecionamento, scripts |
| **Registro** | Configuração centralizada | reg.exe, regedit | Backup, controle de acesso, auditoria |
| **Serviços** | Gerenciamento de processos | sc.exe, tasklist | Privilégios mínimos, SID restrito |
| **AD** | Gestão de identidades | GPO, Kerberos, LDAP | Políticas fortes, replicação segura |
| **PowerShell** | Automação avançada | cmdlets, módulos | Logging, ExecutionPolicy restrito |

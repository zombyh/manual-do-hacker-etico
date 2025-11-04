
## 🧠 Resumo Detalhado: Administração Avançada do Windows Server

### 1. Gestão em Lote de Objetos do AD via PowerShell
- **Objetivo**: Realizar alterações massivas em objetos do AD de forma rápida e precisa.
- **Ferramentas**: Cmdlets do PowerShell (`Get-ADUser`, `Set-ADUser`, `Disable-ADAccount`, etc.).
- **Operações comuns**:
  - Criar usuários a partir de planilhas.
  - Desabilitar contas inativas.
  - Alterar atributos em massa (ex.: departamento).
- **Exemplo de comando**:
  ```powershell
  Get-ADUser -Filter {LastLogonDate -lt "2020-01-01"} | Disable-ADAccount
  ```
- **Benefícios para segurança**:
  - Automação de desativação de contas inativas.
  - Aplicação de políticas de senha e acesso em lote.

---

### 2. Active Directory em Nuvem (Azure AD)
- **Conceito**: Serviço de identidade baseado em nuvem para autenticação e autorização.
- **Licenças**:
  - **Gratuita**: Gerenciamento básico de usuários e grupos.
  - **Premium P1**: Acesso híbrido, grupos dinâmicos, redefinição de senha.
  - **Premium P2**: Identity Protection, Privileged Identity Management.
- **Métodos de autenticação**:
  - Somente em nuvem.
  - Sincronização de diretório com senha.
  - SSO com AD FS.
- **Diferenças entre Azure AD e AD DS**:
  - Azure AD: HTTP/HTTPS, SAML, OAuth, multitenant.
  - AD DS: LDAP, Kerberos, estrutura hierárquica com OUs e GPOs.
- **Ferramenta de sincronização**: **Azure AD Connect**.
- **Aplicação em segurança**:
  - Autenticação multifator.
  - Acesso condicional.
  - Proteção de identidade.

---

### 3. Análise de Logs e Gerenciamento de Rede
- **Ferramentas nativas**:
  - **Gerenciador de Tarefas**: Monitoramento em tempo real de processos e recursos.
  - **Visualizador de Eventos**: Logs de aplicação, segurança, sistema, etc.
  - **Server Manager**: Dashboard centralizado com alertas visuais (vermelho = crítico).
  - **Windows Admin Center**: Console web para gerenciamento remoto.
  - **Performance Monitor**: Contadores de desempenho (CPU, memória, disco, rede).
- **Contadores de desempenho relevantes**:
  - `% Processor Time` > 85% → CPU sobrecarregada.
  - `Pages/sec` alto → Pouca memória.
  - `% Disk Time` > 85% → Disco saturado.
- **Uso em segurança**:
  - Detecção de atividades suspeitas via logs.
  - Identificação de gargalos que podem indicar ataques (ex.: alto uso de rede).

---

### 4. Serviço DHCP
- **Função**: Atribuição automática de endereços IP e configurações de rede.
- **Processo em 4 etapas**:
  1. Discover
  2. Offer
  3. Request
  4. Ack
- **Benefícios**:
  - Redução de esforço manual.
  - Centralização do gerenciamento de IP.
- **Configurações de segurança**:
  - **Reservas de IP** para dispositivos críticos.
  - **Exclusões de IP** para servidores e impressoras.
  - **Escopos com tempo de concessão ajustável**.
- **Gerenciamento via PowerShell**:
  ```powershell
  Add-DhcpServerv4Scope -Name "Escopo-Rede" -StartRange 192.168.1.1 -EndRange 192.168.1.100 -SubnetMask 255.255.255.0
  ```

---

### 5. Conclusão e Aplicações em Segurança
- **PowerShell**: Automação de políticas de acesso e senha.
- **Azure AD**: Controle de identidade híbrida e proteção contra vazamento de credenciais.
- **Monitoramento**: Detecção proativa de falhas e comportamentos anômalos.
- **DHCP**: Controle de rede e prevenção de conflitos de IP.

---

### 🔗 Links Úteis (Explore +)
- [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/) – ISO do Windows Server para testes.
- [Azure – Guia do Windows Server](https://azure.microsoft.com/pt-br/services/virtual-machines/windows-server/)

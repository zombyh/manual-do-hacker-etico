## 🧠 Resumo Detalhado: Configurações Essenciais do Windows Server

### 1. Instalação e Configuração do Controlador de Domínio (AD DS)
- **Função**: **Active Directory Domain Services (AD DS)**
- **Objetivo**: Centralizar autenticação, gerenciar usuários, computadores, grupos e políticas de segurança.
- **Componentes do AD**:
  - **Floresta**: Conjunto de árvores de domínio.
  - **Árvore**: Conjunto de domínios.
  - **Domínio**: Unidade administrativa básica.
  - **Unidade Organizacional (UO)**: Container para organizar objetos.
- **Etapas de instalação**:
  - Via **Gerenciador do Servidor** → Adicionar Funções → AD DS.
  - Promover o servidor a controlador de domínio.
  - Definir nome do domínio (ex: `empresa.com`).
  - Escolher nível funcional da floresta e domínio.
  - Instalar **DNS** e **Catálogo Global (GC)**.
- **Serviços Relacionados**:
  - **AD CS**: Certificados digitais e criptografia.
  - **AD FS**: Federação de identidade entre domínios.
  - **AD LDS**: Serviço de diretório leve.
  - **AD RMS**: Proteção de informações.

---

### 2. Unidades Organizacionais (UOs)
- **Função**: Organizar objetos (usuários, computadores) de forma lógica e hierárquica.
- **Critérios de Planejamento**:
  - Localização geográfica
  - Estrutura organizacional
  - Funções de negócio
  - Modelo híbrido
- **Boas Práticas**:
  - Criar UOs para **Funcionários**, **Terceirizados**, **Computadores**, **Contas Desabilitadas**.
  - Aplicar **Políticas de Grupo (GPOs)** apenas em UOs (não em containers padrão).
  - Proteger UOs contra exclusão acidental.
- **Uso em Segurança**:
  - Isolar contas de terceiros.
  - Aplicar políticas específicas por departamento.
  - Movimentar contas inativas para UO de contas desabilitadas.

---

### 3. Gerenciamento de Usuários e Grupos
- **Contas de Usuário**:
  - Criadas em UOs específicas.
  - Atributos: nome, login, senha, políticas de senha.
  - Opções: "Alterar senha no próximo logon", "Senha nunca expira", "Conta desabilitada".
- **Grupos de Segurança**:
  - **Escopos**:
    - **Domínio Local**: Permissões apenas no domínio local.
    - **Global**: Visível em todo o domínio.
    - **Universal**: Visível em toda a floresta.
  - **Tipos**:
    - **Segurança**: Para aplicar permissões.
    - **Distribuição**: Para e-mails e listas.
- **Contas de Computador**:
  - Registrar computadores e servidores em UOs específicas.
  - Aplicar políticas de segurança por UO.

---

### 4. PowerShell para Administração
- **Características**:
  - Linguagem de script baseada em **.NET**.
  - Multiplataforma: Windows, Linux, macOS.
  - Orientada a objetos.
- **Estrutura de Cmdlets**: `Verbo-Substantivo`
  - Exemplos:
    - `Get-Service`: Lista serviços.
    - `New-ADUser`: Cria usuário.
    - `Set-ADUser`: Modifica usuário.
    - `Remove-ADComputer`: Remove computador.
- **Ferramentas**:
  - **Console do PowerShell**
  - **PowerShell ISE**: Edição com IntelliSense.
- **Módulos**:
  - Ex: `ActiveDirectory`, `DNS`, `DHCP`
  - Carregamento automático ou via `Import-Module`
- **Uso em Segurança**:
  - Automação de criação de usuários.
  - Desabilitação em massa de contas.
  - Aplicação de políticas via script.

---

### 5. Aplicações em Segurança da Informação
- **Autenticação Centralizada**: Controle de acesso via AD.
- **Políticas de Grupo (GPOs)**: Aplicadas via UOs para reforçar segurança.
- **Controle de Acesso Baseado em Grupo**: Permissões granulares.
- **Auditoria e Logs**: Monitoramento de logins e acessos.
- **Scripts de Automação**: Resposta a incidentes, desabilitação de contas, configuração de segurança.
- **Segurança de Contas**:
  - Senhas com expiração.
  - Bloqueio após tentativas.
  - Contas desabilitadas movidas para UO específica.

---

### 🔗 Links Úteis (Explore +)
- [Gerenciamento Remoto do Windows por GPO – Gabriel Luiz Cunha de Oliveira](https://www.example.com)
- [Novidades do Windows Server 2019 – Eduardo Costa](https://www.hsbs.com.br)

---

### 📚 Referências
- DAUTI, M. *Windows Server 2019 Administration Fundamentals*. Packt, 2019.
- KRAUSE, J. *Mastering Windows Server 2019*. Packt, 2021.
- THOMAS, O. *Windows Server 2019 Inside Out*. Microsoft Press, 2020.

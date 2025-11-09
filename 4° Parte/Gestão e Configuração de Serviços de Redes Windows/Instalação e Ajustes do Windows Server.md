## 🖥️ Instalação e Ajustes do Windows Server


### 🛠️ 1. Instalação do Windows Server

### 🔹 Pré-requisitos e Preparação
- **Sistema**: Windows Server 2019 Standard
- **Licença**: Disponível via Azure Dev Tools for Teaching ou Windows Evaluation Center (180 dias)
- **Ambiente**: Máquina virtual (VirtualBox, VMware, Hyper-V) ou física
- **Recursos Mínimos**:
  - **Sem GUI**: 512 MB RAM
  - **Com GUI**: 2 GB RAM
  - **Disco**: 32 GB (mínimo) – recomendado 50 GB

### 🔹 Escolhas Durante a Instalação
- **Edição**:
  - **Standard**: Para pequenas/médias empresas
  - **Datacenter**: Para virtualização ilimitada
- **Tipo de Instalação**:
  - **Com GUI (Experiência Desktop)**: Interface gráfica completa
  - **Sem GUI (Server Core)**: Linha de comando – **menor superfície de ataque**

> ✅ **Recomendação de segurança**: Use **Server Core** para reduzir a superfície de ataque.

### 🔹 Partições Criadas na Instalação
| Partição | Função |
|----------|--------|
| **Recuperação** | Restauração do sistema |
| **Sistema** | Arquivos de boot e BitLocker |
| **MSR** | Reserva para sistemas UEFI (128 MB) |
| **Primária** | Instalação do SO com NTFS |

---

## ⚙️ 2. Ajustes Pós-Instalação

### 🔸 Configurações Básicas de Segurança
- **Renomear o computador** e definir domínio/grupo de trabalho
- **Ativar Windows Update** para correções de segurança
- **Desabilitar Configuração de Segurança Aprimorada do IE** (apenas para administradores)
- **Habilitar Windows Defender Firewall** – liberar apenas portas necessárias

### 🔸 Configurações de Rede
- **Agrupamento de NIC**:
  - Agrega múltiplas interfaces
  - Aumenta throughput e fornece redundância

### 🔸 Ativação do Windows
- Período de avaliação: 180 dias
- Após expiração: desligamentos automáticos

---

## 🐧 3. Windows Subsystem for Linux (WSL)

### 🔹 O que é o WSL?
- Permite executar distribuições Linux diretamente no Windows
- Evita dual boot ou máquinas virtuais separadas

### 🔹 Instalação e Configuração
- Instalar via **Gerenciador do Servidor** → **Adicionar Funções e Recursos**
- Escolher **Subsistema do Windows para Linux**
- Reiniciar o servidor
- Baixar distribuição (ex: Ubuntu 20.04) e instalar via arquivo `.appx`
- Configurar usuário e senha

### 🔹 Arquivo de Configuração: `/etc/wsl.conf`
- Define montagem automática, rede e outros comportamentos
- Exemplo:
  ```ini
  [automount]
  enabled = true
  root = /mnt/
  ```

---

## 🛡️ 4. Diretivas de Grupo (GPO)

### 🔸 Conceito
- Ferramenta para gerenciar configurações de usuários e computadores de forma centralizada
- Aplicável via **Active Directory** ou **localmente**

### 🔸 Tipos de GPO
| Tipo | Escopo | Uso |
|------|--------|-----|
| **Política Local** | Máquina local | Estações sem AD |
| **Política de AD** | Domínio | Centralizada, aplicada a usuários/computadores |

### 🔸 Instalação do Gerenciamento de Políticas de Grupo
- Via **Gerenciador do Servidor** → **Adicionar Funções e Recursos**
- Selecionar: **Gerenciamento de Política de Grupo**

### 🔸 Exemplos de Aplicação
- Restringir acesso ao Painel de Controle
- Bloquear instalação de dispositivos USB
- Ocultar unidades de rede
- Aplicar políticas de senha

> ✅ **Boas Práticas**:
> - Planejar políticas com todas as áreas da empresa
> - Testar em ambiente controlado antes de aplicar em produção
> - Documentar todas as políticas aplicadas

---

## ✅ Conclusão

### 🧩 Pontos-Chave para Segurança da Informação:
1. Use **Server Core** sempre que possível para reduzir a superfície de ataque.
2. Mantenha o sistema **atualizado** com Windows Update.
3. Use **GPOs** para aplicar políticas de segurança de forma centralizada.
4. **WSL** é uma alternativa segura e integrada para execução de ferramentas Linux.
5. **Firewall** deve ser habilitado e configurado com regras restritivas.
6. **Renomeie o servidor** e defina um domínio adequado.

---

### 📌 Recomendações Práticas:
- Use **VirtualBox** ou **Hyper-V** para ambientes de teste
- Habilite **agrupamento de NIC** para redundância e performance
- Crie e teste **GPOs** em um OU (Unidade Organizacional) de teste antes do rollout
- Use o WSL para scripts e automação, mantendo o ambiente Windows Server limpo

---

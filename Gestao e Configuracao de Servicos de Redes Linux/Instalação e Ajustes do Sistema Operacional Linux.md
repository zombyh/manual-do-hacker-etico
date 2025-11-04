
# 🐧 Resumo: Instalação e Ajustes do Sistema Operacional Linux

## 1. Introdução ao Linux e Distribuições

### 1.1. O que é o Linux?
- Sistema operacional moderno, gratuito, baseado no UNIX.
- Desenvolvido por **Linus Torvalds** em 1991.
- Multitarefa e multiusuário.
- **Kernel**: núcleo do sistema com rotinas essenciais.

### 1.2. Distribuições Linux
- Pacotes que incluem Kernel + aplicativos.
- Exemplos: Slackware, RedHat, Fedora, CentOS, **Debian**.
- Debian: software livre, licença GNU, três ramos:
  - **Instável**: pacotes novos, podem conter bugs.
  - **Teste**: pacotes em fase de estabilização.
  - **Estável**: versão suportada por anos, com atualizações de segurança.

---

## 2. Preparação do Ambiente de Estudo

### 2.1. Recursos Utilizados
- SO: Windows 10 Pro
- Imagem do instalador: **Debian 10 'Buster'** (amd64)
- Softwares de virtualização:
  - **VirtualBox** (cross-platform)
  - **Hyper-V** (Windows)

### 2.2. Obtenção do Debian
- Download da imagem `.iso` pelo site oficial.
- Escolha da arquitetura conforme o hardware (ex.: amd64 para processadores Intel/AMD de 64 bits).

---

## 3. Criação de Máquinas Virtuais

### 3.1. No VirtualBox
1. Baixar e instalar o VirtualBox.
2. Criar nova VM:
   - Nome, tipo: Linux, versão: Debian (64-bit)
   - Ajustar memória RAM (balancear entre host e guest)
   - Criar disco virtual (VDI, alocação dinâmica, ex.: 8 GB)
3. Iniciar VM e selecionar imagem `.iso` para boot.

### 3.2. No Hyper-V
1. Habilitar Hyper-V no Windows:
   - Painel de Controle → Programas e Recursos → Ativar ou desativar recursos do Windows → Marcar Hyper-V → Reiniciar.
2. Criar VM via **Hyper-V Quick Create**.
3. Configurar hardware e rede.
4. Iniciar e instalar o SO.

### 3.3. Boas Práticas
- Criar **snapshots** ou **pontos de verificação** para reversão em caso de falha.
- Desligar a VM corretamente (comando `shutdown` ou via interface).

---

## 4. Instalação do Debian

### 4.1. Passos da Instalação (Modo Texto)
1. **Boot** e seleção de idioma (Português do Brasil).
2. Configuração de teclado (ex.: Português Brasileiro).
3. **Hostname**: nome do servidor na rede (ex.: `servidor1`).
4. **Domínio**: (ex.: `teste.com`).
5. **Senha de root**: senha forte (letras, números, pontuação).
6. Criação de usuário:
   - Nome real (ex.: Administrador)
   - Nome de usuário (ex.: `administrador`)
   - Senha forte
7. Configuração de fuso horário.
8. **Particionamento de disco**:
   - Assistido – usar disco inteiro
   - Todos os arquivos em uma partição (para iniciantes)
9. Seleção de **mirror** (repositório) – ex.: Brasil.
10. Instalação de pacotes:
    - Servidor mínimo: **SSH server** + **standard system utilities**
    - Para estudo: incluir **ambiente de área de trabalho do Debian** (GNOME)

### 4.2. Boas Práticas de Segurança na Instalação
- Senhas fortes para root e usuários.
- Evitar usar `admin` como nome de usuário.
- Instalar apenas o necessário (ex.: evitar GUI em servidores).

---

## 5. Locais de Instalação do Linux

### 5.1. On-Premise
- Instalação direta em hardware físico.
- Uso de máquinas virtuais (VirtualBox, Hyper-V, KVM).
- Controle total sobre o ambiente.

### 5.2. Nuvem (Cloud)
- Modelos de serviço:
  - **IaaS** (Infraestrutura como Serviço): ex.: AWS EC2, Azure VMs
  - **PaaS** (Plataforma como Serviço): ex.: Google App Engine
  - **SaaS** (Software como Serviço): ex.: Google Workspace
- Provedores: AWS, Azure, Google Cloud, Oracle, DigitalOcean.
- Vantagens: escalabilidade, redundância, custo variável.
- Cuidado: leia termos, SLA e políticas de cobrança.

---

## 6. Ajustes Iniciais Pós-Instalação

### 6.1. Acesso e Interface
- Login via terminal (modo texto) ou GUI (GNOME).
- Terminal: iniciar com `Activities` → `terminal`.
- **Não usar GUI em servidores**: consome recursos e aumenta superfície de ataque.

### 6.2. Comandos Básicos e Privilegiados
- `$`: usuário comum
- `#`: root
- `su`: alternar para root
- `sudo <comando>`: executar comando como root
- `exit`: sair do modo root
- `passwd`: alterar senha

### 6.3. Configuração de Rede
- Arquivo: `/etc/network/interfaces`
- Exemplo de configuração IPv4 estático:
  ```bash
  auto ens33
  iface ens33 inet static
  address 192.168.0.100
  netmask 255.255.255.0
  gateway 192.168.0.1
  ```
- Reiniciar rede: `systemctl restart networking`

### 6.4. Arquivos Importantes
- `/etc/hosts`: mapeamento local de nomes para IPs
- `/etc/hostname`: nome do host
- `/etc/resolv.conf`: servidores DNS
- `/etc/apt/sources.list`: repositórios de pacotes
- `~/.bashrc`: configurações do shell do usuário

### 6.5. Instalação de Pacotes e Ferramentas
- Atualizar sistema:
  ```bash
  sudo apt-get update && sudo apt-get upgrade
  ```
- Instalar ferramentas de rede:
  ```bash
  sudo apt-get install net-tools -y
  ```
- Instalar servidor SSH:
  ```bash
  sudo apt-get install openssh-server -y
  ```
- Instalar compilador GCC:
  ```bash
  sudo apt install build-essential
  ```

---

## 7. Segurança da Informação – Destaques

### 7.1. Hardening Básico
- Senhas fortes e únicas para root e usuários.
- Uso de `sudo` em vez de login direto como root.
- Desabilitar serviços desnecessários.
- Não instalar GUI em servidores.

### 7.2. Rede
- Configurar IP estático conforme necessidade.
- Usar firewall (ex.: `ufw`).
- Restringir acesso SSH:
  - Alterar porta padrão
  - Usar chaves SSH em vez de senhas

### 7.3. Atualizações
- Manter sistema e pacotes atualizados:
  ```bash
  sudo apt update && sudo apt upgrade
  ```

### 7.4. Monitoramento e Logs
- Verificar logs do sistema (`/var/log/`).
- Usar `journalctl` para logs do systemd.
- Instalar e configurar ferramentas de monitoramento (ex.: `fail2ban`).

---

## 8. Referências e Links Úteis

- [Documentação do Debian](https://www.debian.org/doc/)
- [Microsoft Azure](https://azure.microsoft.com/)
- [OpenSSH](https://www.openssh.com/)
- [GNU Compiler Collection](https://gcc.gnu.org/)

---

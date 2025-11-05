### 📘 Resumo: Administração e Configurações Avançadas de Sistemas Linux

### 🎯 **Propósito**
Compreender conceitos avançados de administração Linux, essenciais para profissionais de infraestrutura de TI, considerando a relevância do Linux em ambientes corporativos e em nuvem.

---

## 📂 Módulo 1: Armazenamento, Partições, RAID e LVM

### 🧩 **Conceitos Fundamentais**
- **Discos Rígidos (HD)**: Responsáveis por armazenar e recuperar dados.
- **Sistemas de Arquivos**: Estrutura que organiza dados em blocos (ex: `ext3`, `ext4`, `NTFS`, `FAT32`).
- **Fragmentação**: Blocos não contíguos que podem impactar performance e redimensionamento.

### 🗂️ **Partições**
- **Tabela de Partições**: Mapeamento lógico das partições no disco.
- **Tipos**:
  - **Primárias**: Máximo de 4 por disco.
  - **Estendidas**: Contêm partições lógicas, sem limite fixo (recomenda-se até 12).
- **Nomenclatura no Linux**:
  - Exemplo: `/dev/sda1` → Primeira partição do primeiro disco SCSI.

### 🔁 **RAID (Redundant Array of Independent Disks)**
- **RAID 0 (Striping)**: Performance, sem redundância.
- **RAID 1 (Mirroring)**: Espelhamento, alta confiabilidade.
- **RAID 5**: Striping com paridade distribuída, tolerante a 1 falha.
- **RAID 6**: Similar ao RAID 5, mas com dupla paridade, tolerante a 2 falhas.
- **RAID 10**: Combinação de RAID 1 + RAID 0 (espelhamento + striping).

> ⚠️ **RAID não é backup!**

### 💽 **LVM (Logical Volume Manager)**
- **Conceito**: Camada de abstração entre o SO e o armazenamento físico.
- **Componentes**:
  - **PV (Physical Volume)**: Disco físico ou RAID.
  - **VG (Volume Group)**: Agrupamento de PVs.
  - **LV (Logical Volume)**: "Partição" lógica redimensionável.
- **Vantagens**:
  - Flexibilidade no redimensionamento.
  - Snapshots para backup sem interrupção.
- **Estratégias de Mapeamento**:
  - Linear
  - Striped (para performance)

---

## 💾 Módulo 2: Backup no Linux

### 📦 **Tipos de Backup**
- **Completo**: Cópia total dos dados.
- **Incremental**: Apenas alterações desde o último backup (completo ou incremental).
- **Diferencial**: Alterações desde o último backup completo.
- **Delta**: Inclui hardlinks para arquivos não alterados.

### 🛠️ **Ferramentas de Backup**
- **fwbackups**: Interface gráfica, agendamento, suporte a remoto.
- **Bacula**: Framework completo com componentes:
  - Director, Console, File, Storage, Catalog, Monitor.
- **Rsync**: Sincronização local/remota, eficiente com `--delete`, `-z` (compressão), `-P` (progresso).

---

## 📄 Módulo 3: Análise de Logs e Gerenciamento de Rede

### 📁 **Logs no Linux**
- **Localização**: `/var/log`
- **Arquivos comuns**:
  - `auth.log` / `secure`: Autenticações (SSH, login).
  - `syslog` / `messages`: Logs gerais do sistema.
  - `kern.log`: Logs do kernel.
  - `cron`: Tarefas agendadas.
- **Formato**: `Timestamp, Hostname, Application, Priority, Message`
- **Rotação**: Gerenciada pelo `logrotate`

### 🔍 **Ferramentas de Análise de Logs**
- `grep`: Busca por texto ou regex.
- `awk`: Processamento e extração de campos.
- `sed`: Edição de fluxo de texto.
- `tail -f`: Monitoramento em tempo real.
- `cut`: Extração de colunas por delimitador.
- `wc -l`: Contagem de linhas/eventos.

### 🌐 **Gerenciamento de Rede**
- **Portas Comuns**:
  - 22 (SSH), 80 (HTTP), 443 (HTTPS), 53 (DNS), 25 (SMTP)
- **Ferramentas**:
  - `nmap`: Varredura de portas e serviços.
  - `netstat`: Conexões ativas e portas abertas.

---

## 🌐 Módulo 4: Servidor DHCP

### 🔄 **Conceitos do DHCP**
- **Função**: Atribuir IP, gateway, DNS automaticamente.
- **Fases (DORA)**:
  1. Descoberta (Discover)
  2. Oferta (Offer)
  3. Solicitação (Request)
  4. Confirmação (Acknowledgment)
- **Alocação**:
  - Dinâmica
  - Automática
  - Manual (por MAC)

### ⚙️ **Configuração no Linux**
- **Pacote**: `isc-dhcp-server`
- **Arquivo de Configuração**: `/etc/dhcp/dhcpd.conf`
- **Exemplo de Configuração**:
  ```conf
  subnet 10.0.0.0 netmask 255.255.255.0 {
    range 10.0.0.50 10.0.0.99;
    option routers 10.0.0.1;
    option domain-name-servers 8.8.8.8;
    host impressora {
      hardware ethernet 00:aa:bb:01:01:01;
      fixed-address 10.0.0.30;
    }
  }
  ```

---

## 🧠 **Pontos Relevantes para Segurança da Informação**
- **Logs de Autenticação**: Monitorar `auth.log` para tentativas de acesso SSH.
- **RAID 1/5/6**: Garantia de disponidade e tolerância a falhas.
- **LVM Snapshots**: Backup consistente sem downtime.
- **Bacula Catalog**: Auditoria completa de backups.
- **Nmap e Netstat**: Identificação de serviços expostos e portas abertas.
- **DHCP com IP Fixo**: Controle de dispositivos críticos por MAC.

---

## 🧩 Resumo Estruturado: Instalação e Configuração de Servidores Windows Server

### 🔍 1. DNS no Windows Server

#### 📌 Conceito Básico
- **DNS (Domain Name System)**: converte nomes de computadores em endereços IP.
- **FQDN (Fully Qualified Domain Name)**: nome completo do dispositivo na rede (ex: `rh01.contoso.local`).

#### 🗂️ Zonas DNS
- **Zona de Pesquisa Direta**: mapeia nome → IP.
- **Zona de Pesquisa Reversa**: mapeia IP → nome.
- **Zona Primária**: permite criar, editar e excluir registros.
- **Zona Secundária**: cópia da primária, somente leitura.

#### 📝 Tipos de Registros DNS
| Tipo | Descrição |
|------|-----------|
| A | Nome → IPv4 |
| AAAA | Nome → IPv6 |
| CNAME | Apelido para outro nome |
| MX | Servidor de e-mail |
| PTR | IP → Nome (reverso) |
| SRV | Localização de serviços |

#### ⚙️ Configuração e Segurança
- **TTL (Time To Live)**: tempo de cache do registro.
- **Atualizações Dinâmicas Seguras**: só clientes autorizados atualizam registros.
- **Zonas Integradas ao AD DS**: replicação automática entre controladores de domínio.

#### 🛠️ Comandos PowerShell Úteis
```powershell
Add-DnsServerPrimaryZone
Add-DnsServerResourceRecordA
Get-DnsServerZone
Remove-DnsServerZone
```

---

### 🌐 2. Servidor Web IIS (Internet Information Services)

#### 📌 Introdução
- Serviço web da Microsoft para hospedagem de sites e aplicações.
- Protocolos: HTTP (porta 80) e HTTPS (porta 443).

#### 🧩 Módulos do IIS
| Categoria | Exemplos |
|-----------|----------|
| HTTP | CustomErrorModule, HttpRedirectionModule |
| Segurança | AnonymousAuthentication, WindowsAuthentication |
| Conteúdo | StaticFileModule, DefaultDocumentModule |
| Cache | FileCacheModule, HTTPCacheModule |
| Log | HttpLoggingModule, FailedRequestsTracingModule |

#### 🔒 Segurança no IIS
- Instalar apenas módulos necessários.
- Habilitar autenticação conforme necessário (ex: Windows Auth).
- Restringir IPs com `IpRestrictionModule`.

#### 🖥️ IIS no Nano Server
- Versão minimalista do Windows Server sem interface gráfica.
- Menor superfície de ataque.
- Instalação via PowerShell:
```powershell
New-NanoServerImage -Package Microsoft-NanoServer-IIS-Package
```

---

### 🖧 3. Acesso Remoto no Windows Server

#### 📌 Conceitos
- **RDS (Remote Desktop Services)**: acesso remoto a desktops e aplicações.
- **Virtualização baseada em sessão**: múltiplos usuários acessam o mesmo servidor.
- **VDI (Virtual Desktop Infrastructure)**: desktop virtualizado com Hyper-V.

#### 🔐 Autenticação e Segurança
- **NLA (Network Level Authentication)**: autenticação antes da conexão RDP.
- Porta padrão: **TCP 3389**.
- Certificados SSL para acesso web (RD Web Access).

#### 🧱 Componentes do RDS
- **Session Host**: hospeda sessões de usuários.
- **License Server**: gerencia licenças RDS.
- **Gateway**: acesso externo seguro.
- **Web Access**: acesso via navegador.

#### 🛠️ Administração via PowerShell
```powershell
Enter-PSSession -ComputerName Server01
```
- Acesso remoto a Windows, Linux e macOS.

---

### ✅ Considerações de Segurança

#### 🛡️ DNS
- Use zonas integradas ao AD para replicação segura.
- Configure TTL adequado para balancear desempenho e atualização.
- Limite atualizações dinâmicas a clientes autorizados.

#### 🛡️ IIS
- Remova módulos não utilizados.
- Use HTTPS e certificados SSL.
- Habilite logs e monitoramento de falhas.

#### 🛡️ Acesso Remoto
- Use NLA para autenticação prévia.
- Restrinja acesso por IP/grupo.
- Use certificados válidos para RD Gateway.

---

### 📚 Referências
- Microsoft (2021). *IIS no Nano Server*
- Microsoft (2020). *IIS Modules Overview*
- Microsoft (2021). *Implementar o DNS do Windows Server*

---

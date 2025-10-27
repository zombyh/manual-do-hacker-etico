
### **Resumo para Estudo: Automação de Tarefas de Segurança com PowerShell, Python e Shell Script**

A automação é a espinha dorsal da segurança operacional moderna (SecOps). Ela permite escalar processos, reduzir erros humanos, responder a incidentes com velocidade e manter uma postura de segurança proativa.

#### **1. Por que Automação na Segurança da Informação?**

*   **Escale:** Execute tarefas em centenas ou milhares de sistemas simultaneamente.
*   **Velocidade de Resposta:** Reaja a ameaças em minutos ou segundos, não em horas ou dias (ex: conter um malware automaticamente).
*   **Consistência e Redução de Erros:** Um script executa a mesma tarefa, da mesma forma, toda vez.
*   **Monitoramento Contínuo:** Scripts podem ficar rodando 24/7, coletando dados e alertando sobre anomalias.
*   **Liberação de Time:** Permite que analistas focam em atividades estratégicas e de caça a ameaças, em vez de tarefas repetitivas.

#### **2. Principais Ferramentas de Automação**

Cada linguagem/Shell tem seu forte e é comum ver ambientes que utilizam todas elas em conjunto.

| Ferramenta | Ambiente Principal | Força na Segurança | Exemplo de Uso |
| :--- | :--- | :--- | :--- |
| **PowerShell** | Windows / Microsoft 365 / Azure | **Nativa no Windows**, profundamente integrada ao SO e aos serviços Microsoft. Objetos, não texto. | Gerenciamento de Active Directory, análise de logs do Windows (Event Viewer), automação do Microsoft Defender, gestão de Azure. |
| **Shell Script (Bash)** | Linux / Unix / macOS | **Nativa em Linux/macOS**, ideal para automatizar comandos do sistema, administração de servidores. | Parsing de logs (auth.log, syslog), hardening de sistemas, monitoramento de arquivos de sistema, integração com ferramentas CLI. |
| **Python** | Multiplataforma (Windows, Linux, macOS) | **Versatilidade e Ecossistema**. vasta quantidade de bibliotecas para segurança, rede, APIs, IA. | Desenvolver ferramentas complexas, interagir com APIs de segurança (SIEM, Firewalls), análise de malware, automação de testes de penetração. |

#### **3. Exemplos Práticos de Automação em Segurança**

**a) Monitoramento e Análise de Logs:**
*   **Problema:** Verificar manualmente os logs de autenticação (ex: `/var/log/auth.log` no Linux ou `Security.evtx` no Windows) para tentativas de login falhadas é demorado.
*   **Solução (Shell Script - Bash):**
    ```bash
    #!/bin/bash
    # Monitora tentativas de login SSH falhas no Linux
    LOG_FILE="/var/log/auth.log"
    LIMITE=5

    # Conta os failures por IP e alerta se passar do limite
    echo "Monitorando tentativas de login SSH falhas..."
    grep "Failed password" $LOG_FILE | awk '{print $11}' | sort | uniq -c | while read COUNT IP; do
        if [ "$COUNT" -gt "$LIMITE" ]; then
            echo "[ALERTA] Possível ataque de força bruta do IP $IP ($COUNT tentativas) - $(date)"
            # Comando opcional para bloquear o IP automaticamente:
            # iptables -A INPUT -s $IP -j DROP
        fi
    done
    ```
    *   **Este script pode ser colocado no `cron` para rodar a cada 5 minutos.**

*   **Solução (PowerShell):**
    ```powershell
    # Analisa logs do Windows Event Viewer para eventos de login falho (ID 4625)
    $FailedLogons = Get-WinEvent -FilterHashtable @{
        LogName='Security'
        ID=4625
        StartTime=(Get-Date).AddHours(-1)  # Última hora
    }

    $FailedLogons | Group-Object -Property @{Expression={$_.Properties[5].Value}} | ForEach-Object {
        if ($_.Count -gt 5) {
            Write-Host "[ALERTA] IP $($_.Name) falhou $($_.Count) logins nas últimas horas."
        }
    }
    ```

**b) Resposta a Incidentes e Contenção:**
*   **Problema:** Um malware foi detectado em um endpoint. É preciso isolar a máquina da rede rapidamente.
*   **Solução (PowerShell):** Um script pode ser disparado pelo SIEM ou EDR para conter a ameaça.
    ```powershell
    # Script de Contenção de Endpoint (Windows)
    $ComputerName = "WORKSTATION01"

    # 1. Desabilita a placa de rede
    Disable-NetAdapter -Name "*" -Confirm:$false

    # 2. Para serviços suspeitos comuns
    Stop-Service -Name "suspicious_svc" -Force

    # 3. Cria uma regra de firewall para bloquear todo o tráfego
    New-NetFirewallRule -DisplayName "QUARANTINE_BLOCK_ALL" -Direction Outbound -Action Block -Enabled True

    # 4. Envia um alerta para a equipe de SOC
    Write-EventLog -LogName "Application" -Source "SOC_Script" -EntryType Warning -EventId 1001 -Message "O computador $env:COMPUTERNAME foi colocado em quarentena."
    ```

**c) Hardening e Configuração Segura:**
*   **Problema:** Aplicar consistentemente políticas de segurança (ex: desativar protocolos inseguros) em uma frota de servidores Linux.
*   **Solução (Shell Script):**
    ```bash
    # Script de Hardening Básico para SSH
    SSH_CONFIG="/etc/ssh/sshd_config"

    # Faz um backup
    cp $SSH_CONFIG "$SSH_CONFIG.backup_$(date +%Y%m%d)"

    # Ajusta as configurações para maior segurança
    sed -i 's/^#PermitRootLogin yes/PermitRootLogin no/' $SSH_CONFIG
    sed -i 's/^#PasswordAuthentication yes/PasswordAuthentication no/' $SSH_CONFIG
    sed -i 's/^#Protocol 2/Protocol 2/' $SSH_CONFIG

    # Reinicia o serviço SSH
    systemctl restart sshd

    echo "Hardening do SSH aplicado. Root login e autenticação por senha desabilitados."
    ```

**d) Integração com APIs (Python):**
*   **Problema:** Consultar automaticamente uma inteligência de ameaças (Threat Intelligence) para verificar se um IP é malicioso.
*   **Solução (Python):**
    ```python
    import requests

    def check_ip_virustotal(ip_address, api_key):
        url = f'https://www.virustotal.com/api/v3/ip_addresses/{ip_address}'
        headers = {'x-apikey': api_key}
        
        response = requests.get(url, headers=headers)
        if response.status_code == 200:
            data = response.json()
            stats = data['data']['attributes']['last_analysis_stats']
            if stats['malicious'] > 0:
                print(f"[ALERTA] IP {ip_address} é malicioso para {stats['malicious']} engines.")
            else:
                print(f"IP {ip_address} parece limpo.")
        else:
            print("Erro ao consultar API.")

    # Uso da função
    API_KEY = "SUA_CHAVE_AQUI"
    check_ip_virustotal("192.168.1.100", API_KEY)
    ```

#### **4. Boas Práticas na Automação de Segurança**

*   **Princípio do Menor Privilégio:** Scripts devem rodar com as permissões mínimas necessárias para executar sua tarefa. Nunca como root/administrador sem necessidade.
*   **Registro em Log (Logging):** Seu script deve gerar logs próprios, detalhando o que fez, se teve sucesso ou falha, e por quê.
*   **Tratamento de Erros:** Previna falhas. Seu script deve se comportar gracefulmente se um comando falhar ou um arquivo não for encontrado.
*   **Segurança do Código:** Cuidado com credenciais. **NUNCA** armazene senhas ou API Keys hardcoded no script. Use variáveis de ambiente, cofres de senhas (Azure Key Vault, AWS Secrets Manager) ou arquivos de configuração com permissões restritas.
*   **Teste em Ambiente Controlado:** Sempre teste exaustivamente em um ambiente de laboratório antes de rodar em produção. Um script de automação poderoso pode causar uma pane generalizada se tiver um bug.

---

### **Dica para a Prova da Procergs:**

Entenda o **contexto de uso** de cada ferramenta:
*   **PowerShell:** É a chave para ambientes **Microsoft** (Windows Server, Active Directory, Azure).
*   **Shell Script:** É a base para administração e segurança de servidores **Linux**.
*   **Python:** É a ferramenta para **desenvolver soluções customizadas** e integrar diferentes sistemas via APIs.

Pense em como a automação apoia os **princípios de segurança**: confidencialidade (criptografando dados), integridade (verificando hashes de arquivos) e disponibilidade (monitorando a saúde dos sistemas).
## 📘 Resumo: Resumo para Estudo: Redes e Protocolos Seguros

#### **1. Fundamentos: Pilha TCP/IP e seus Riscos**

A pilha TCP/IP é o conjunto de protocolos que permite a comunicação em redes modernas, incluindo a internet. Entender suas camadas é crucial para entender as ameaças e as defesas.

*   **Camadas e Protocolos Principais:**
    *   **Aplicação (HTTP, HTTPS, FTP, DNS, SMTP):** Interface com o usuário e aplicações. **Maior superfície de ataque.**
    *   **Transporte (TCP, UDP):** Controla a comunicação fim-a-fim (confiabilidade TCP vs. velocidade UDP).
    *   **Rede (IP, ICMP):** Responsável pelo roteamento e endereçamento lógico (endereços IP).
    *   **Enlace/Física (Ethernet, Wi-Fi):** Controla o acesso ao meio físico (cabos, ondas de rádio).

*   **Ameaças Inerentes ao TCP/IP:**
    *   **Sniffing:** Interceptação passiva de dados trafegados na rede (especialmente em redes não criptografadas como Wi-Fi aberto). **Fere a Confidencialidade.**
    *   **Spoofing:** Falsificação de endereços IP ou MAC para se passar por um host confiável.
    *   **Hijacking de Sessão:** Sequestro de uma sessão de comunicação já autenticada.
    *   **Ataques de Negação de Serviço (DoS/DDoS):** Sobrecarregar um servidor ou recurso de rede com tráfego, tornando-o indisponível. **Fere a Disponibilidade.**

---

#### **2. Criptografia na Rede: SSL/TLS**

O **SSL (Secure Sockets Layer)** e seu sucessor, o **TLS (Transport Layer Security)**, são protocolos criptográficos projetados para fornecer segurança de comunicação sobre uma rede.

*   **O que é e onde é usado?** É o que garante o "S" em **HTTPS**. Protege a comunicação entre um navegador web e um servidor, mas também é usado em e-mails (SMTPS), VPNs, etc.
*   **Quais princípios do CIA ele garante?**
    *   **Confidencialidade:** Criptografa os dados trafegados.
    *   **Integridade:** Usa MAC (Message Authentication Code) para detectar se os dados foram alterados em trânsito.
    *   **Autenticação:** Opcionalmente, usa certificados digitais para o servidor (e às vezes para o cliente) provar sua identidade.

*   **Como funciona (Handshake simplificado):**
    1.  **Client Hello:** O cliente se conecta e oferece suíte de criptografias suportadas.
    2.  **Server Hello:** O servidor escolhe a criptografia e envia seu **certificado digital**.
    3.  **Verificação do Certificado:** O cliente verifica se o certificado é válido e confiável (emitido por uma Autoridade Certificadora - CA confiável).
    4.  **Chave de Sessão:** O cliente gera uma chave de sessão (simétrica), criptografa-a com a chave pública do servidor (do certificado) e a envia.
    5.  **Comunicação Segura:** Ambas as partes usam a chave de sessão simétrica para criptografar e descriptografar os dados daquela sessão.

---

#### **3. Mecanismos de Defesa de Rede**

*   **Firewall**
    *   **O que é:** Um sistema (hardware, software ou ambos) que atua como uma **barreira** entre uma rede confiável (ex: rede interna da empresa) e uma rede não confiável (ex: internet), controlando o tráfego com base em um conjunto de regras de segurança predefinidas.
    *   **Como funciona:** Analisa os pacotes de dados e decide se permite (allow) ou bloqueia (deny) a passagem com base em:
        *   **Endereço IP de origem/destino**
        *   **Porta (ex: bloquear a porta 23 - Telnet)**
        *   **Protocolo (ex: permitir apenas TCP na porta 443 - HTTPS)**
        *   **Estado da conexão (Firewalls Stateful):** São mais inteligentes, lembrando o estado das conexões. Ex: Se um pacote de resposta chega, ele é permitido porque uma solicitação saiu antes.
    *   **Tipos Comuns:**
        *   **Firewall de Rede:** Protege o perímetro da rede.
        *   **Firewall de Host:** Software instalado em um servidor ou estação de trabalho específica.

*   **IDS (Sistema de Detecção de Intrusão)**
    *   **O que é:** Um sistema de **monitoramento** passivo. Ele "cheira" o tráfego da rede (Network-based IDS - NIDS) ou analisa logs de um sistema (Host-based IDS - HIDS) em busca de atividades maliciosas ou violações de política.
    *   **Como funciona:** Compara a atividade com uma **assinatura** de ataques conhecidos (como um antivírus) ou com um **baseline** de comportamento normal (detecção de anomalias).
    *   **Ação:** Quando detecta algo, gera um **alarme** para um administrador. **Ele não age por conta própria.**

*   **IPS (Sistema de Prevenção de Intrusão)**
    *   **O que é:** Um sistema **ativo** que evoluiu do IDS. Além de detectar, ele pode **tomar ações automaticamente** para bloquear a ameaça.
    *   **Como funciona:** Opera em linha com o tráfego de rede (ou seja, o tráfego passa por ele), permitindo que bloqueie pacotes maliciosos em tempo real antes que atinjam o alvo.
    *   **Ação:** Pode descartar pacotes, resetar conexões ou reconfigurar firewalls para bloquear o IP atacante.

| Característica | **Firewall** | **IDS** | **IPS** |
| :--- | :--- | :--- | :--- |
| **Foco** | Controle de Acesso (Permitir/Negar) | **Detecção** e Alerta | **Detecção e Prevenção** |
| **Ação** | Ativa (bloqueia com base em regras) | Passiva (apenas alerta) | Ativa (bloqueia automaticamente) |
| **Posicionamento** | No perímetro (Gateway) | Fora da linha principal (espelho) | **Em linha** com o tráfego |

---

#### **4. Proteção Aplicada a Sistemas e Servidores**

A segurança de rede é inútil se os sistemas finais estiverem vulneráveis.

*   **Hardening (Fortificação de Sistemas):** Processo de **reduzir a superfície de ataque** de um sistema.
    *   **Remover software/services desnecessários:** Cada serviço running (ex: FTP, Telnet) é uma porta potencial para um invasor.
    *   **Aplicar as políticas de senha fortes:** Mínimo de caracteres, complexidade, troca periódica.
    *   **Aplicar o Princípio do Privilégio Mínimo:** Usuários e serviços devem ter apenas as permissões estritamente necessárias para funcionar.
    *   **Manter sistemas atualizados (Patch Management):** Aplicar patches de segurança regularmente é uma das medidas de proteção **mais críticas** contra vulnerabilidades exploradas.

*   **Criptografia de Dados:**
    *   **Em Repouso (At Rest):** Criptografar discos (ex: BitLocker, LUKS) e bancos de dados. Protege os dados se o hardware for roubado ou acessado fisicamente.
    *   **Em Trânsito (In Transit):** Usar SSL/TLS, VPNs. Protege os dados trafegando na rede.
    *   **Em Uso (In Use):** Área emergente que lida com criptografia mesmo durante o processamento na memória RAM.

*   **Gestão de Logs e Auditoria:**
    *   Manter **logs** centralizados de todos os sistemas e servidores críticos.
    *   **Monitorar e auditar** os logs regularmente para detectar atividades suspeitas (ex: múltiplas tentativas de login falhas, acesso a arquivos sensíveis fora do horário comercial).
    *   É crucial para **detecção de incidentes** e **investigação forense** pós-incidente.

---

### **Dicas:**

1.  **Entenda a Diferença IDS vs IPS:** Esta é uma questão clássica. Lembre-se: IDS é o alarme, IPS é o alarme que também tranca a porta.
2.  **SSL/TLS é Chave:** Saiba que ele atua entre as camadas de Transporte e Aplicação e fornece Confidencialidade, Integridade e Autenticação. Entenda o papel do certificado digital.
3.  **Firewall Stateful:** Dê ênfase a este tipo, pois é o mais comum e eficaz. Ele entende o contexto da conexão.
4.  **Pensar em Camadas:** A prova pode dar um cenário e perguntar qual mecanismo é mais adequado. A resposta correta geralmente é "uma combinação de todos" (ex: Firewall + IPS + SSL).
5.  **Hardening:** Lembre-se que é um processo contínuo e básico para a segurança de qualquer servidor. "Servidor travado é servidor seguro".

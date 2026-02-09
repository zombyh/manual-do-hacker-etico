## 🎯 **Objetivos do Hardening**
- **Compreender** os principais conceitos de hardening e sua relação com normas ISO/IEC 27000.
- **Analisar** o impacto do controle de acesso físico e a gestão de privilégios em sistemas Linux.
- **Identificar** vulnerabilidades relacionadas a permissões e vetores de ataque.
- **Implementar** estratégias de defesa em camadas para reduzir a superfície de ataque.

---

## 🔐 **Conceitos Fundamentais**
1. **Hardening**: Processo de fortalecimento de sistemas por meio de configurações, remoção de componentes desnecessários e aplicação de controles de segurança.
2. **Segurança em Camadas**: Estratégia que combina proteção física, lógica, de rede, aplicação e usuário.
3. **Superfície de Ataque**: Conjunto de pontos vulneráveis que podem ser explorados.
4. **Vetor de Ataque**: Meio utilizado para explorar uma vulnerabilidade.
5. **Princípio do Menor Privilégio**: Conceder apenas as permissões necessárias para cada usuário ou processo.

---

## 📂 **Tipos de Hardening**
- **Hardening de Redes**: Firewalls, controle de protocolos, criptografia.
- **Hardening de Servidores**: Controle físico, instalação minimalista, segregação.
- **Hardening de Aplicações**: Remoção de funções desnecessárias, controle de acesso.
- **Hardening de Bancos de Dados**: Criptografia, controle de acesso, senhas seguras.
- **Hardening de Sistemas Operacionais**: Instalação minimalista, controle de usuários, auditoria.

---

## 🛡️ **Controles Essenciais de Segurança**
### 1. **Controle de Acesso Físico**
- Acesso físico não controlado permite redefinição de senhas (via GRUB, LILO, modo single-user).
- Exemplo: Stuxnet infectou sistemas não conectados à internet via dispositivo físico.
- Recomendações: Criptografia de disco, senhas no bootloader, controle de acesso físico rigoroso.

### 2. **Gestão de Usuários e Permissões**
- Arquivo `/etc/passwd` e `/etc/shadow` são críticos.
- Permissões especiais:
  - **SUID**: Executa com permissões do proprietário.
  - **SGID**: Executa com permissões do grupo.
  - **Sticky-bit**: Restringe exclusão/renomeação a proprietários.
- **Linux Capabilities**: Permite conceder privilégios específicos sem dar acesso total ao root.

### 3. **Controles de Sistema**
- **SELinux**: Controle de acesso obrigatório (MAC) para maior segurança.
- **sudo**: Permite execução de comandos com privilégios sem compartilhar senha do root.
- **Ambiente de Shell Restrito (rbash)**: Limita ações do usuário, mas pode ser contornado (ex: via Vim, find, man).

---

## ⚙️ **Ferramentas e Comandos Úteis**
- **find**: Localiza arquivos com permissões especiais (ex: `find / -type f -perm -4000`).
- **chattr**: Define atributos de arquivo (ex: imutável `+i`).
- **getcap / setcap**: Gerencia Linux Capabilities.
- **sysctl**: Ajusta parâmetros do kernel.
- **fuser / lsof**: Identifica processos usando arquivos ou portas.

---

## 📊 **Processo de Hardening Recomendado**
1. **Mapeamento de ameaças** e análise de riscos.
2. **Instalação minimalista**: Instalar apenas o necessário.
3. **Aplicação de baselines**: CIS Benchmarks, STIGs, normas ISO.
4. **Configuração de firewall**: Permitir apenas tráfego essencial.
5. **Atualização contínua** de software.
6. **Monitoramento e auditoria** de logs.
7. **Varredura regular de vulnerabilidades** (ex: OpenSCAP).
8. **Revisão periódica** de permissões e configurações.

---

## 🧠 **Princípios Chave**
- **Defesa em Camadas**: Nenhum controle único é suficiente.
- **Princípio do Menor Privilégio**: Conceder apenas o necessário.
- **Segurança Física é Fundamental**: Sem ela, controles lógicos podem ser inúteis.
- **Hardening é um Processo Contínuo**: Requer revisão e atualização constantes.

---

## 📚 **Referências e Próximos Passos**
- **Normas ISO/IEC 27000**: Base teórica para gestão de segurança.
- **CIS Benchmarks** e **STIGs**: Guias práticos para configuração.
- **Ferramentas**: OpenSCAP, ferramentas de auditoria nativas do Linux.
- **Leitura Recomendada**: *Securing Debian Manual*, manuais de `capabilities` e `rbash`.

---

## ✅ **Conclusão**
O hardening de servidores é um processo essencial para proteger infraestruturas contra ameaças cibernéticas. Requer uma abordagem estruturada, combinando controles físicos e lógicos, gestão rigorosa de permissões e monitoramento contínuo. A segurança deve ser vista como um conjunto de camadas interdependentes, onde a falha em uma pode comprometer todo o sistema.

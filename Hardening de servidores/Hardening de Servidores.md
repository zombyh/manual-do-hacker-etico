
## 🛡️ Resumo: Hardening de Servidores

### 📌 Definição de Hardening
- **Hardening** é o processo de fortalecimento de sistemas computacionais por meio de configurações, remoção de componentes desnecessários e aplicação de controles de segurança.
- Objetivo: **reduzir a superfície de ataque**, mitigar vulnerabilidades e aumentar a resiliência contra tentativas de invasão.
- É um processo **contínuo**, preventivo e corretivo, alinhado a normas como a família **ISO/IEC 27000**.

---

## 🎯 Conceitos Fundamentais
- **Ameaça**: causa potencial de um incidente indesejado.
- **Vulnerabilidade**: fragilidade que pode ser explorada por uma ameaça.
- **Risco**: probabilidade de uma ameaça se concretizar e suas consequências.
- **Ativo**: qualquer recurso de valor para a organização (hardware, software, dados, pessoas).
- **Superfície de Ataque**: nível de exposição do sistema a possíveis ataques.

---

## 🧩 Tipos de Hardening
| Tipo | Foco |
|------|------|
| **Rede** | Firewall, controle de portas, criptografia de tráfego |
| **Servidor** | Controles físicos e lógicos, instalação minimalista |
| **Aplicação** | Remoção de funções desnecessárias, controle de acesso |
| **Banco de Dados** | Criptografia, controle de acesso, senhas seguras |
| **Sistema Operacional** | Controle de usuários, auditoria, serviços essenciais |

---

## 🛠️ Controles Essenciais de Hardening

### 1. **Acesso Físico**
- Controle rigoroso ao datacenter e servidores.
- Exemplo: sem controle físico, é possível redefinir senha do **root** via GRUB ou mídia externa.

### 2. **Permissões e Atributos de Arquivos**
- **SUID** e **SGID**: permitem execução com permissões do proprietário/grupo.
- **Sticky-bit**: só o dono pode excluir/renomear.
- **Atributos avançados**: `chattr +i` (imutável), `chattr +a` (apenas append).

### 3. **Política de Mínimo Privilégio**
- Usar `sudo` para comandos privilegiados.
- Auditar e revisar permissões especiais com `find / -type f -perm -4000`.

### 4. **Linux Capabilities**
- Permitem conceder privilégios específicos sem dar acesso total ao root.
- Exemplo: `CAP_DAC_OVERRIDE` ignora verificações de permissão.
- Comandos: `getcap`, `setcap`.

### 5. **Restricted Shell (rbash)**
- Shell com restrições para usuários comuns.
- Pode ser contornado com comandos como `vim`, `find`, `man`, que permitem executar shells alternativos.

### 6. **Configurações do Kernel**
- Parâmetros ajustáveis via `sysctl`.
- Exemplo: alterar TTL com `sysctl -w net.ipv4.ip_default_ttl=255`.

### 7. **Criptografia e Senhas**
- Criptografia de dados em repouso e em trânsito.
- Políticas de senhas fortes.

---

## 📋 Checklist Básico para Hardening de Servidores
- [ ] Instalação minimalista do SO
- [ ] Configuração de firewall (apenas portas necessárias)
- [ ] Atualização de software
- [ ] Remoção de serviços desnecessários
- [ ] Controle de usuários e grupos
- [ ] Política de senhas
- [ ] Logs e monitoramento
- [ ] Criptografia de dados
- [ ] Uso de baselines (ex: CIS, STIG, Microsoft)

---

## 🔍 Ferramentas e Normas
- **ISO/IEC 27002**: boas práticas para controles de segurança.
- **CIS Benchmark**: guias gratuitos para hardening.
- **STIG**: implementações técnicas de segurança (DISA).
- **OpenSCAP**: auditoria de conformidade.
- **Comandos úteis**:
  - `find / -perm -4000` → arquivos SUID
  - `lsattr` → atributos de arquivos
  - `getcap` → capacidades do Linux
  - `fuser`, `lsof` → processos e arquivos abertos

---

## ⚠️ Riscos e Mitigações
- **Acesso físico**: usar senha no GRUB, criptografia de disco.
- **SUID/SGID**: revisar periodicamente, remover quando não essencial.
- **Shell restrito**: auditar comandos que permitem escape (vim, find, man).
- **Varreduras de vulnerabilidade**: executar regularmente, tratar falsos positivos.

---

## 🧠 Conclusão
- Hardening é uma **jornada contínua**.
- Deve seguir uma **abordagem em camadas** (física, lógica, rede, aplicação).
- Requer alinhamento com **políticas de segurança** e **normas internacionais**.
- Objetivo final: **reduzir riscos** e **proteger ativos** com base no princípio do menor privilégio.

---

## 🔗 Explore +
- Leitura: **ISO/IEC 27001, 27002, 27003**
- Manual prático: **Securing Debian Manual**
- Comandos no Linux: `man capabilities`, `man rbash`

---


### **Resumo para Estudo: Testes de Penetração, Engenharia Social e Phishing**

#### **1. Testes de Penetração (PenTest)**

**Conceito:** É uma simulação autorizada de um ciberataque contra um sistema, rede ou aplicação, com o objetivo de identificar e explorar vulnerabilidades **antes que um atacante real o faça**.

*   **Objetivo Final:** Não é quebrar o sistema, mas **melhorar a segurança** através da descoberta de falhas e da entrega de um relatório detalhado com recomendações de correção.
*   **Diferença para um Ataque Real:**
    *   **Autorizado:** Possui escopo, regras de engajamento (RoE) e autorização formal por escrito.
    *   **Ético:** Foca na melhoria, não no dano ou lucro.
    *   **Controlado:** Busca minimizar impactos no ambiente.
    *   **Documentado:** Gera um relatório completo para o cliente.

**Tipos de Teste:**
*   **Caixa Preta (Black Box):** O testador não possui nenhuma informação inicial sobre o alvo. Simula um atacante externo.
*   **Caixa Branca (White Box):** O testador possui total conhecimento e acesso à infraestrutura do alvo (documentação, código-fonte, etc.). É mais profundo e abrangente.
*   **Caixa Cinza (Grey Box):** Um meio-termo. O testador possui algum conhecimento limitado (ex: credenciais de um usuário padrão).

**Fases de um PenTest (Metodologia):**
Seguem uma abordagem estruturada, como a **MITRE ATT&CK Framework** ou **OWASP Testing Guide**.

1.  **Reconhecimento (Reconnaissance):** Coleta de informações públicas (OSINT) sobre o alvo (domínios, e-mails, redes sociais, tecnologias usadas).
2.  **Varredura (Scanning):** Uso de ferramentas (Nmap) para identificar portas abertas, serviços rodando e vulnerabilidades potenciais.
3.  **Ganho de Acesso (Exploitation):** Exploração das vulnerabilidades encontradas para obter acesso inicial ao sistema (usando ferramentas como Metasploit).
4.  **Manutenção de Acesso (Persistence):** Garantir que o acesso permaneça mesmo se o sistema for reiniciado (criando backdoors, usuários).
5.  **Análise de Pós-Exploração (Lateral Movement/Privilege Escalation):** Explorar o sistema internamente para roubar dados, mover-se lateralmente para outras máquinas e elevar privilégios (de usuário para admin).
6.  **Relatório (Reporting):** A fase **MAIS IMPORTANTE**. Documenta todas as descobertas, riscos, provas (screenshots, logs) e fornece recomendações claras e acionáveis para remediar as falhas.

---

#### **2. Engenharia Social**

**Conceito:** É a arte de **manipular pessoas** para que divulguem informações confidenciais ou realizem ações que comprometam a segurança. Explora a **confiança**, a **ingenuidade** ou a **autoridade**, não falhas técnicas.

*   **É o elo mais fraco da cadeia de segurança.** Nenhum firewall protege contra um funcionário que, enganado, revela sua senha.

**Princípios Psicológicos (Por que funciona?):**
*   **Reciprocidade:** Sentir-se obrigado a retribuir um favor.
*   **Compromisso e Consistência:** Tendência a manter uma posição após se comprometer com ela.
*   **Prova Social:** Tendência a fazer o que os outros estão fazendo.
*   **Afinidade/Gostar:** Estamos mais propensos a confiar em pessoas de quem gostamos.
*   **Autoridade:** Obedecer a figuras de autoridade (chefe, policial, suporte técnico).
*   **Escassez:** A percepção de que algo é raro ou limitado ("oferta por tempo limitado").

---

#### **3. Phishing (A principal técnica de Engenharia Social)**

**Conceito:** Tentativa fraudulenta de obter informações sensíveis (credenciais, dados bancários) se passando por uma comunicação legítima e confiável, principalmente por e-mail.

**Tipos de Phishing:**

*   **Phishing de Âncora (Spear Phishing):** Altamente personalizado contra um **alvo específico** (ex: um CFO, um administrador de sistema). Usa informações colhidas do LinkedIn, Facebook, etc., para parecer extremamente verídico. **É a técnica mais perigosa e comum em ataques direcionados.**
*   **Whaling:** Um spear phishing direcionado a "baleias" – executivos de alto nível (CEO, CFO).
*   **Vishing (Voice Phishing):** Phishing realizado por telefone. Ex.: "Olá, aqui é do suporte técnico, precisamos confirmar sua senha".
*   **Smishing (SMS Phishing):** Phishing via mensagens de texto (SMS).
*   **QRishing (Phishing por QR Code):** Uso de QR codes maliciosos que redirecionam para sites falsos.

**Indicadores (IOCs) de um E-mail de Phishing:**
*   **Sensação de Urgência:** "Sua conta será bloqueada em 24h!"
*   **Remetente Suspeito:** E-mail similar, mas não igual, ao oficial (ex: `suporte@procergs.com.br` vs `suporte@procergs.org`).
*   **Saudação Genérica:** "Prezado cliente" em vez do seu nome.
*   **Links Maliciosos:** Passar o mouse sobre o link (sem clicar) revela um endereço diferente.
*   **Anexos Inesperados:** Arquivos `.zip`, `.exe`, `.pdf.exe`.
*   **Erros de Gramática e Ortografia:** Comuns em campanhas amplas, mas raros em spear phishing.

---

#### **4. Ferramentas Essenciais**

**Kali Linux:**
*   **O que é:** Uma distribuição Linux **especializada e pré-configurada** para testes de segurança e penetration testing. Contém centenas de ferramentas de segurança instaladas.
*   **Não é:** Uma ferramenta de hacking para ser usada sem conhecimento. É uma plataforma para profissionais de segurança.
*   **Principais Categorias de Ferramentas Incluídas:**
    *   Coleta de Informação (OSINT)
    *   Varredura de Rede e Vulnerabilidades
    *   Exploração de Vulnerabilidades (Metasploit)
    *   Testes de Senha (Ferramentas de quebra de hash)
    *   Análise de Wireless
    *   Ferramentas de Engenharia Social (ex: SET)

**Metasploit Framework:**
*   **O que é:** A ferramenta de **exploitation** mais famosa e usada no mundo. É um projeto de código aberto que fornece uma infraestrutura para desenvolver, testar e executar exploits.
*   **Como funciona:** Possui um banco de dados de exploits (códigos que exploram falhas) e payloads (códigos que são executados no alvo após a exploração, como um shell reverso).
*   **Componentes Principais:**
    *   `msfconsole`: A interface principal de linha de comando.
    *   **Exploit:** O módulo que aproveita uma vulnerabilidade.
    *   **Payload:** O código que é executado no sistema-alvo após uma exploração bem-sucedida (ex: `meterpreter`).
    *   **Auxiliary:** Módulos para outras funções (varredura, enumeração, DoS).
*   **Fluxo Básico:**
    1.  Selecionar um exploit (`use exploit/windows/smb/ms17_010_eternalblue`)
    2.  Configurar o exploit (definir o RHOSTS - IP alvo)
    3.  Selecionar um payload (`set payload windows/x64/meterpreter/reverse_tcp`)
    4.  Configurar o payload (definir o LHOST - seu IP)
    5.  Executar (`exploit`)

**Social-Engineer Toolkit (SET):**
*   **O que é:** Uma ferramenta específica, muitas vezes incluída no Kali, projetada para **simular ataques de engenharia social**.
*   **Funcionalidades:** Cria clones de sites de login (Gmail, Facebook), campanhas de e-mail malicioso e ataques via mídia removível.

---

#### **5. Defesas e Mitigações (O que a Procergs pode fazer)**

*   **Contra Engenharia Social e Phishing:**
    *   **Treinamento de Conscientização Contínuo:** É a defesa **número um**. Simulações de phishing para ensinar os usuários.
    *   **Políticas de Segurança Claras:** Ex: "O departamento de TI nunca pedirá sua senha por e-mail ou telefone".
    *   **Filtros Anti-Spam/Anti-Phishing:** Em gateways de e-mail e provedores.
    *   **Autenticação Multifator (MFA):** Mitiga drasticamente o roubo de credenciais via phishing. Mesmo que a senha seja roubada, o atacante não terá o segundo fator.
    *   **Análise de DNS:** Bloquear domínios maliciosos ou recém-criados que imitam o domínio da empresa.

*   **Contra Testes de Penetração (A perspectiva defensiva):**
    *   **Realizar Pentests Regularmente:** Identificar falhas proativamente.
    *   **Gerenciamento de Vulnerabilidades:** Ciclo contínuo de varredura, priorização e correção de vulnerabilidades.
    *   **Hardening de Sistemas:** Seguir benchmarks de segurança (CIS).
    *   **Monitoramento e Resposta (SOC/SIEM):** Detectar atividades anômalas (tentativas de exploração, movimentação lateral).
    *   **Segmentação de Rede:** Dificultar o movimento lateral de um possível invasor.

**Bons estudos!** Foque em entender os **conceitos** por trás das ferramentas e as **mitigações**, que são tão importantes quanto os ataques para uma prova de segurança.

### **Resumo para Estudo: Gestão de Acessos e Identidades (IAM - Identity and Access Management)**

#### **1. Conceito Central: O Princípio do Menor Privilégio (Least Privilege)**

Este é o pilar de toda a gestão de acessos. Ele determina que qualquer usuário, sistema ou processo deve ter **apenas as permissões mínimas necessárias** para realizar sua função específica, e nada mais.

*   **Por que é importante?**
    *   **Reduz a superfície de ataque:** Se uma conta for comprometida, o estrago que o invasor pode fazer é limitado.
    *   **Minimiza erros internos:** Impede que usuários modifiquem ou excluam acidentalmente dados ou configurações críticas.
    *   **É um requisito fundamental de normas** como ISO 27001 e LGPD.

---

#### **2. Os Quatro Pilares da Gestão de Identidade (AAAA)**

Um ciclo de vida completo de gestão de identidades segue estes quatro processos, conhecidos como "AAAA":

1.  **Autenticação (Authentication):** **"Você é quem diz ser?"** É o processo de **verificar a identidade** de um usuário ou sistema. Envolve a apresentação de credenciais.
    *   **Exemplos:** Login e senha, biometria, token físico ou de software.

2.  **Autorização (Authorization):** **"O que você tem permissão para fazer?"** É o processo de **determinar quais recursos** um usuário autenticado **pode acessar** e **quais ações** pode realizar.
    *   **Exemplos:** Ter permissão para ler um arquivo, mas não para editá-lo. Ter acesso à pasta "Financeiro", mas não à pasta "RH".

3.  **Administração (Administration):** É a gestão do ciclo de vida completo das identidades e seus acessos. Inclui:
    *   **Provisionamento:** Criar a conta e conceder acessos quando um usuário entra na empresa (onboarding).
    *   **Revisão de Acessos (Access Review):** Auditorias periódicas para confirmar se os acessos ainda são necessários.
    *   **Desprovisionamento:** Remover todos os acessos imediatamente quando o usuário sai da empresa ou muda de função (offboarding). **Este é um ponto crítico de segurança.**

4.  **Auditoria (Auditing):** **Registro e análise** de todas as atividades relacionadas ao acesso. Responde à pergunta **"Quem fez o quê, e quando?"**
    *   **Exemplos:** Logs de tentativas de login (sucesso e falha), logs de acesso a arquivos sensíveis, logs de alteração de permissões.
    *   **É crucial** para investigação de incidentes, detecção de comportamentos maliciosos e conformidade (LGPD, ISO 27001).

---

#### **3. Métodos de Autenticação (Fatores)**

A autenticação pode ser baseada em algo que o usuário **sabe**, **tem** ou **é**.

*   **Fator 1: Algo que você SABE (Knowledge)**
    *   *Exemplos:* Senha, PIN, resposta a uma pergunta de segurança.
    *   *Vantagem:* Simples e barato.
    *   *Desvantagem:* Pode ser roubado, adivinhado ou vazado.

*   **Fator 2: Algo que você TEM (Possession)**
    *   *Exemplos:* Token físico (RSA SecurID), aplicativo de autenticação no celular (Google Authenticator, Microsoft Authenticator), cartão inteligente, SMS/email com código.
    *   *Vantagem:* Mais seguro que apenas senha. Mesmo que a senha seja roubada, o invasor precisa do token.
    *   *Desvantagem:* Pode ser inconveniente; o token pode ser perdido ou roubado.

*   **Fator 3: Algo que você É (Inherence)**
    *   *Exemplos:* Impressão digital, reconhecimento facial, scanner de retina, reconhecimento de voz.
    *   *Vantagem:* Muito difícil de forjar ou transferir. Alta conveniência para o usuário.
    *   *Desvantagem:* Pode ser mais caro; preocupações com privacidade e viés algorítmico.

---

#### **4. Autenticação Multifator (MFA) ou 2FA**

*   **O que é:** O uso de **dois ou mais fatores** diferentes dos listados acima para autenticar um usuário.
*   **Por que é crucial?** Ele **mitiga drasticamente** o risco de contas comprometidas. Um invasor pode ter sua senha (Fator 1), mas é extremamente improvável que também tenha seu celular (Fator 2) ou sua digital (Fator 3).
*   **Exemplo Comum (2FA):** Digitar a senha (Fator 1) e, em seguida, inserir um código temporário gerado por um app no celular (Fator 2).

---

#### **5. Controle de Acesso Baseado em Funções (RBAC - Role-Based Access Control)**

*   **O que é:** Uma metodologia de autorização onde os acessos são concedidos **não diretamente aos usuários**, mas a **funções (roles)**. Os usuários são então atribuídos a uma ou mais funções.
*   **Como funciona:**
    1.  **Criação de Funções:** São definidas funções de acordo com as necessidades da organização (ex: "AnalistaFinanceiro", "GerenteDeTI", "EstagiarioRH").
    2.  **Atribuição de Permissões:** Cada função recebe um conjunto específico de permissões necessárias para desempenhar aquela função.
    3.  **Atribuição de Usuários:** Os usuários são associados às funções. Seu acesso é derivado automaticamente das permissões da(s) sua(s) função(ões).
*   **Vantagens:**
    *   **Gestão Simplificada:** Em vez de gerenciar permissões para 1000 usuários, você gerencia para 20 funções.
    *   **Redução de Erros:** Menos chance de dar permissões erradas a um usuário.
    *   **Conformidade e Auditoria:** É muito mais fácil auditar e comprovar quem deveria ter acesso a quê.
    *   **Ciclo de Vida:** Quando um usuário muda de função, basta removê-lo de uma role e adicioná-lo a outra. Quando deixa a empresa, basta desativar sua conta – todos os acessos são revogados de uma vez.

---

#### **6. IAM (Gerenciamento de Identidades e Acessos)**

*   **O que é:** É um **framework** ou conjunto de tecnologias que automatiza e gerencia todo o ciclo de vida dos AAAA (Administração, Autenticação, Autorização e Auditoria).
*   **Componentes comuns de um sistema IAM:**
    *   **Repositório de Identidades:** Um banco de dados seguro (como um Directory Service, ex: **Microsoft Active Directory** ou **OpenLDAP**) que armazena todas as identidades e suas atribuições a grupos/roles.
    *   **Sistema de Provisionamento:** Automatiza a criação, modificação e desativação de contas.
    *   **Sistema de SSO (Single Sign-On):** Permite que um usuário se autentique uma única vez e ganhe acesso a múltiplos sistemas e aplicações sem precisar se logar novamente. Melhora a experiência do usuário e a segurança (menos senhas para gerenciar).
    *   **Ferramentas de Governança:** Facilitam as revisões de acesso e a auditoria.

---

### **Dicas para a Prova da Procergs:**

1.  **Foque no Princípio do Menor Privilégio:** É a base de tudo. Muitas questões de prova giram em torno dessa ideia.
2.  **Domine a Diferença entre Autenticação e Autorização:** Esta é uma distinção fundamental. **Autenticação** prova a identidade. **Autorização** concede permissões.
3.  **MFA é Obrigatório:** Entenda que MFA não é mais "legal ter", é "preciso ter". Saiba os diferentes fatores e por que a MFA é tão eficaz.
4.  **RBAC é Eficiência e Segurança:** Saiba explicar como o RBAC simplifica a gestão e reforça a segurança através de roles, em vez de permissões individuais.
5.  **Pense no Ciclo de Vida (Provisionamento/Desprovisionamento):** A prova pode ter uma questão sobre o maior risco de segurança quando um funcionário é demitido. A resposta certa sempre envolve o **desprovisionamento imediato dos acessos**.

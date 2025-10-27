
### **Resumo para Estudo: Fundamentos de Segurança da Informação**

#### **1. Conceito Central: A Tríade CIA**

A base de toda a segurança da informação repousa sobre três princípios fundamentais, conhecidos como **Tríade CIA**:

*   **C - Confidencialidade:** Garantir que a informação seja acessível **apenas por pessoas autorizadas**. Impedir a divulgação ou acesso não autorizado.
    *   **Exemplos práticos:** Criptografia de dados, uso de senhas, controles de acesso físico e lógico, acordos de confidencialidade (NDA).
    *   **Ameaças:** Vazamento de dados, espionagem, phishing, eavesdropping (escuta não autorizada).

*   **I - Integridade:** Garantir que a informação **não seja alterada** de forma não autorizada, preservando sua exatidão e completude durante todo o seu ciclo de vida.
    *   **Exemplos práticos:** Assinaturas digitais, hashes criptográficos (ex: SHA-256), controles de versão, logs de auditoria.
    *   **Ameaças:** Alteração maliciosa de arquivos, corrupção de dados durante transmissão, erro de software.

*   **D - Disponibilidade:** Garantir que a informação e os sistemas necessários para acessá-la **estejam acessíveis e utilizáveis** sempre que forem necessários pelos usuários autorizados.
    *   **Exemplos práticos:** Sistemas de redundância (RAID, servidores em cluster), backups, planos de recuperação de desastre (DRP), proteção contra ataques de negação de serviço (DDoS).
    *   **Ameaças:** Ataques DDoS, falhas de hardware/software, desastres naturais, erros humanos que causam indisponibilidade.

**Importante:** Muitas vezes, é necessário fazer um **balanceamento** entre esses princípios. Por exemplo, aumentar excessivamente a segurança para confidencialidade (muitas camadas de autenticação) pode impactar negativamente a disponibilidade.

---

#### **2. Normas e Frameworks Internacionais (ISO/IEC)**

Estas normas fornecem um framework reconhecido globalmente para implementar e manter um Sistema de Gestão de Segurança da Informação (SGSI).

*   **ISO/IEC 27001:**
    *   **O que é:** A norma **certificável** que especifica os **requisitos** para estabelecer, implementar, manter e melhorar continuamente um SGSI.
    *   **Foco:** É sobre a **gestão do processo** de segurança. Ela segue o ciclo PDCA (Plan-Do-Check-Act) e exige que a organização defina seu contexto, avalie riscos e estabelece objetivos de segurança.
    *   **Palavra-chave:** **Requisitos**.

*   **ISO/IEC 27002:**
    *   **O que é:** Um código de **práticas** ou um catálogo de **controles de segurança**.
    *   **Foco:** Fornece diretrizes e melhores práticas para implementar os controles de segurança listados no Anexo A da ISO 27001. É uma orientação, **não é certificável**.
    *   **Exemplo:** A ISO 27002 detalha *como* implementar um controle de política de senhas, enquanto a 27001 exige que você *tenha* uma política de controle de acesso.
    *   **Palavra-chave:** **Melhores Práticas**.

*   **ISO/IEC 27005:**
    *   **O que é:** A norma que fornece diretrizes para o **processo de gestão de riscos** de segurança da informação.
    *   **Foco:** Explica como realizar uma avaliação de riscos de forma estruturada, dentro do contexto de um SGSI baseado na ISO 27001. Ela cobre as fases de:
        1.  **Identificação de ativos, ameaças e vulnerabilidades.**
        2.  **Avaliação** da probabilidade e impacto dos riscos.
        3.  **Tratamento** do risco (aceitar, mitigar, transferir ou evitar).
        4.  **Monitoramento** e revisão contínua dos riscos.
    *   **Palavra-chave:** **Gestão de Riscos**.

**Relação entre elas:** A **ISO 27001** é o coração do SGSI, definindo "o que" fazer. A **ISO 27002** sugere "como" fazer, detalhando os controles. A **ISO 27005** dá o suporte para a principal atividade ("como") que alimenta o SGSI: a gestão de riscos.

---

#### **3. Legislação Nacional: LGPD (Lei Geral de Proteção de Dados - Lei nº 13.709/2018)**

A LGPD é a principal legislação brasileira sobre privacidade e proteção de dados pessoais. Ela impacta diretamente os princípios de segurança, especialmente a **Confidencialidade** e a **Integridade**.

*   **Principais Pilares:**
    *   **Finalidade:** Coletar dados apenas para um propósito legítimo, específico e explícito.
    *   **Consentimento:** O titular dos dados deve consentir com o tratamento de suas informações (com algumas exceções legais).
    *   **Necessidade:** Coletar apenas os dados estritamente necessários para a finalidade declarada (minimização de dados).
    *   **Segurança:** O **Controlador** (quem decide sobre o tratamento dos dados) deve adotar **medidas de segurança** técnicas e administrativas para proteger os dados pessoais. É aqui que a segurança da informação se conecta diretamente com a LGPD.

*   **Direitos do Titular:** Acesso aos dados, correção, eliminação, portabilidade, revogação do consentimento.
*   **Autoridade Nacional:** A ANPD (Autoridade Nacional de Proteção de Dados) é o órgão responsável por fiscalizar e aplicar sanções.
*   **Sanções:** Multas de até 2% do faturamento (com limite de R$ 50 milhões por infração), publicização da infração e bloqueio/eliminação dos dados.

**Conexão com a Segurança:** Implementar um SGSI baseado na ISO 27001 é uma das melhores formas de demonstrar conformidade com o princípio de segurança da LGPD.

---

#### **4. Gestão de Riscos e Conformidade**

*   **Gestão de Riscos (conforme ISO 27005):**
    *   **Objetivo:** Identificar, analisar e tratar os riscos que podem impactar a confidencialidade, integridade e disponibilidade dos ativos de informação de uma organização.
    *   **Processo:**
        1.  **Identificação de Ativos:** O que precisa ser protegido? (dados, hardware, software, pessoas, reputação).
        2.  **Identificação de Ameaças e Vulnerabilidades:** O que pode explorar uma fraqueza no ativo?
        3.  **Avaliação de Riscos:** Calcular o risco (`Risco = Probabilidade x Impacto`). Classificar os riscos (alto, médio, baixo).
        4.  **Tratamento de Riscos:**
            *   **Mitigar:** Implementar um controle de segurança (ex: firewall, backup).
            *   **Aceitar:** Conscientemente decidir não agir, pois o risco é baixo ou o custo do tratamento é muito alto.
            *   **Transferir:** Terceirizar o risco (ex: contratar um seguro cibernético).
            *   **Evitar:** Descontinuar a atividade que gera o risco.
    *   **Importante:** A gestão de riscos é um **processo contínuo**, não um projeto único.

*   **Conformidade (Compliance):**
    *   **O que é:** O ato de estar em conformidade com leis, regulamentos, normas e políticas aplicáveis à organização.
    *   **Exemplos:** Estar em conformidade com a LGPD, com a ISO 27001 (se certificada), com políticas internas de segurança.
    *   **Como alcançar:** Através de **auditorias** (internas e externas), **avaliações contínuas**, **documentação** e implementação de **controles**.
    *   **Motivação:** Evitar multas e sanções, proteger a reputação da organização, ganhar vantagem competitiva e melhorar a maturidade em segurança.

---

### **Dicas para a Prova da Procergs:**

1.  **CIA é Fundamental:** Tenha claro na mente a definição e exemplos de Confidencialidade, Integridade e Disponibilidade. Provavelmente, haverá questões que testarão seu entendimento sobre qual princípio está sendo violado em um cenário hipotético.
2.  **Diferencie as ISOs:** Foque em entender a diferença principal entre a 27001 (requisitos para o SGSI) e a 27002 (guias de implementação de controles). Saiba que a 27005 é focada no processo de gestão de riscos.
3.  **LGPD e Segurança:** Relacione a LGPD ao princípio de segurança. Lembre-se que a lei exige medidas de segurança para proteger dados pessoais, o que se alinha perfeitamente com um SGSI.
4.  **Risco é Chave:** Entenda as etapas do processo de gestão de riscos e as quatro opções de tratamento (mitigar, aceitar, transferir, evitar). Uma questão pode pedir para você identificar a melhor opção em um caso.
5.  **Terminologia:** Use os termos técnicos corretos (ex: "mitigar um risco", "controle de segurança", "titular de dados", "SGSI").

Bons estudos! Este resumo cobre os pilares essenciais para a sua prova.
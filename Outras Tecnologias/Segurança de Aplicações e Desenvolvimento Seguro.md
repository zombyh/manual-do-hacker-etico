## 📘 Resumo: Segurança de Aplicações e Desenvolvimento Seguro

#### **1. Introdução: A Importância da Segurança no SDLC**
A segurança de aplicações não pode ser uma reflexão tardia. Ela deve ser integrada em **todas as fases do Ciclo de Vida de Desenvolvimento de Software (SDLC - Software Development Life Cycle)**. O objetivo é identificar e mitigar vulnerabilidades o mais cedo possível, reduzindo drasticamente o custo e o esforço para corrigi-las, em comparação com a descoberta em produção.

---

#### **2. OWASP Top 10: As 10 Principais Vulnerabilidades de Aplicações Web**
O OWASP (Open Web Application Security Project) é uma referência mundial em segurança de aplicações. O "Top 10" é um documento que cataloga as falhas de segurança mais críticas. **É essencial memorizar e entender cada uma delas.**

**A01:2021 – Quebra de Controle de Acesso**
*   **O que é:** Falhas que permitem a um usuário acessar funcionalidades ou dados beyond their permissions (ex: acessar dados de outro usuário alterando um ID na URL).
*   **Prevenção:** Implementar mecanismos sólidos de autorização, negar por padrão, e auditar regularmente os controles.

**A02:2021 – Falhas Criptográficas**
*   **O que é:** Exposição de dados sensíveis (senhas, números de cartão, dados pessoais) devido à criptografia fraca, ausência de criptografia ou má gestão de chaves.
*   **Prevenção:** Usar algoritmos modernos e fortes (ex: AES, SHA-256), gerenciar chaves de forma segura, usar HTTPS em toda a aplicação.

**A03:2021 – Injeção**
*   **O que é:** O clássico. Ocorre quando dados não confiáveis são enviados a um interpretador como parte de um comando (ex: SQL, OS, LDAP). A injeção de SQL é a mais famosa.
*   **Prevenção:** Usar **consultas parametrizadas/prepared statements**, ORMs, validar e sanitizar todas as entradas.

**A04:2021 – Design Insecure**
*   **O que é:** Novidade no Top 10. Falhas que surgem de uma arquitetura ou design flawed, antes mesmo da codificação (ex: fluxo de autenticação mal concebido).
*   **Prevenção:** Integrar a segurança na fase de design, usar padrões de segurança estabelecidos e modelagem de ameaças.

**A05:2021 – Configuração Incorreta de Segurança**
*   **O que é:** Configurações padrão inseguras, servidores desatualizados, serviços desnecessários habilitados, mensagens de erro detalhadas expostas.
*   **Prevenção:** Ter um processo de hardening para todos os ambientes, remover funcionalidades não usadas, automatizar o deployment para garantir configurações seguras.

**A06:2021 – Componentes Vulneráveis e Desatualizados**
*   **O que é:** Usar bibliotecas, frameworks e outros componentes de software com vulnerabilidades conhecidas.
*   **Prevenção:** Gerenciar um inventário de componentes (SBOM - Software Bill of Materials), assinar e verificar componentes, monitorar e atualizar proativamente usando ferramentas como SCA (Software Composition Analysis).

**A07:2021 – Identificação e Autenticação Quebradas**
*   **O que é:** Falhas em mecanismos de login, como permitir ataques de força bruta, credenciais padrão, recuperação fraca de senhas e armazenamento inadequado de credenciais.
*   **Prevenção:** Implementar autenticação multifator (MFA), proteger contra ataques de força bruta, usar senhas fortes e armazená-las com salt e hashing robusto (ex: bcrypt).

**A08:2021 – Falhas na Integridade de Software e Dados**
*   **O que é:** Falhas em assumir que software ou dados do cliente não foram modificados (ex: atualizações de aplicativos sem verificação de integridade, desserialização insegura de dados).
*   **Prevenção:** Usar assinaturas digitais para verificar a integridade do código e dados, não aceitar objetos serializados de fontes não confiáveis.

**A09:2021 – Falhas no Controle de Acesso a Registros de Segurança (Logging) e Monitoramento**
*   **O que é:** Falha em detectar, escalar e alertar sobre violações ativas. Sem logs adequados, monitoramento e resposta a incidentes, os ataques passam despercebidos.
*   **Prevenção:** Garantir que todos os eventos de login, falhas de controle de acesso e transações de alto valor sejam registrados (logados) e monitorados.

**A10:2021 – Falsificação de Solicitação do Lado do Servidor (SSRF)**
*   **O que é:** Ocorre quando um aplicativo busca um recurso remoto sem validar a URL fornecida pelo usuário, permitindo que um atacante faça com que o aplicativo envie requests a sistemas internos não destinados à exposição.
*   **Prevenção:** Implementar whitelists de DNS e endereços IP, não enviar respostas brutas do cliente, desvincular e validar todas as entradas do usuário.

---

#### **3. Testes de Segurança: SAST e DAST**
São metodologias de teste essenciais para encontrar vulnerabilidades em diferentes fases do SDLC.

*   **SAST (Static Application Security Testing) - Teste Estático**
    *   **O que é:** Analisa o **código-fonte** da aplicação em repouso, sem executá-la ("white-box testing"). É usado nas fases iniciais de desenvolvimento.
    *   **Vantagens:** Encontra bugs no início (Shift Left), cobre grande parte do código, ideal para integrar no CI/CD.
    *   **Exemplos de Ferramentas:** SonarQube, Checkmarx, Veracode, Snyk Code.

*   **DAST (Dynamic Application Security Testing) - Teste Dinâmico**
    *   **O que é:** Testa a aplicação **em execução** ("black-box testing"). Simula ataques de um hacker externo contra uma aplicação web funcionando.
    *   **Vantagens:** Encontra vulnerabilidades runtime e de configuração, não depende da linguagem de programação.
    *   **Exemplos de Ferramentas:** OWASP ZAP (gratuito), Burp Suite (professional), Nessus.

| Característica | SAST | DAST |
| :--- | :--- | :--- |
| **Tipo de Análise** | Estática (código) | Dinâmica (aplicação running) |
| **Fase do SDLC** | Desenvolvimento | Testes / Pré-produção |
| **Abordagem** | White-Box | Black-Box |
| **Encontra** | Bugs de código | Vulnerabilidades runtime |
| **Custo de Correção** | Baixo (é cedo) | Alto (já está quase pronto) |

**Importante:** SAST e DAST são **complementares**, não excludentes. Um programa robusto usa ambos.

---

#### **4. Metodologias para Proteção no Ciclo de Desenvolvimento (SDLC Seguro)**
Integrar segurança em todas as etapas é conhecido como **DevSecOps** (Development + Security + Operations).

1.  **Requisitos e Design (Fase Inicial):**
    *   **Modelagem de Ameaças (Threat Modeling):** Identificar ameaças em potencial e definir controles de segurança antes da codificação. (Ex: Framework STRIDE).
    *   **Definir Requisitos de Segurança:** Estabelecer padrões de codificação segura e políticas de segurança.

2.  **Desenvolvimento (Codificação):**
    *   **Treinamento:** Desenvolvedores treinados em segurança (ex: OWASP Top 10).
    *   **Práticas de Codificação Segura:** Seguir guias como OWASP Secure Coding Practices.
    *   **SAST:** Ferramentas de análise estática integradas na IDE ou no repositório de código (ex: em um pull request).

3.  **Testes:**
    *   **SAST (novamente):** Análise automatizada no pipeline de integração (CI).
    *   **DAST:** Testes automatizados na build de teste.
    *   **SCA (Software Composition Analysis):** Escanear dependências em busca de vulnerabilidades conhecidas.
    *   **Testes de Penetração:** Testes manuais especializados para simular um ataque real.

4.  **Deploy/Implantação:**
    *   **Hardening do Ambiente:** Configuração segura de servidores, containers e redes.
    *   **Scanners de Vulnerabilidades em Containers/Imagens:** (Ex: Trivy, Clair).

5.  **Operação e Manutenção:**
    *   **Monitoramento Contínuo:** Usar SIEM, WAF (Web Application Firewall) para detectar e bloquear ataques em tempo real.
    *   **Gerenciamento de Vulnerabilidades:** Ter um processo para corrigir vulnerabilidades descobertas em produção (ex: via patch).
    *   **Resposta a Incidentes:** Plano para agir em caso de violação.

**Conceito-Chave: Shift Left**
Significa "deslocar a segurança para a esquerda" no ciclo, ou seja, para o início do processo de desenvolvimento. É muito mais barato e fácil consertar uma vulnerabilidade durante a codificação do que após o deploy.

---

### **Dicas:**
*   **Foque no OWASP Top 10:** Entenda a essência de cada item, seu impacto e a principal forma de prevenção. Especialmente **Injeção, Quebra de Controle de Acesso e Componentes Desatualizados**.
*   **Diferencie SAST e DAST:** Tenha claro o momento, a abordagem e o objetivo de cada um.
*   **Use os termos técnicos corretos:** SDLC, DevSecOps, Shift Left, Threat Modeling, CI/CD, WAF.

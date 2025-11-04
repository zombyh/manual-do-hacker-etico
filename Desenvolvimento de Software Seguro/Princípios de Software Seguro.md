
# Resumo: Princípios de Software Seguro

## 1. Introdução aos Princípios de Segurança e Software Seguro

- **Dados são valiosos** e devem ser protegidos contra acessos não autorizados, modificações ou indisponibilidade.
- **Software seguro**: sistema projetado e desenvolvido para garantir proteção contra ameaças e ataques.
- **Princípios de segurança** são a base para identificar ameaças e vulnerabilidades e projetar medidas de proteção.

### Princípios Fundamentais da Segurança da Informação:
- **Confidencialidade**: apenas pessoas autorizadas acessam os dados.
- **Integridade**: dados não são modificados de forma não autorizada.
- **Disponibilidade**: sistemas e dados estão acessíveis quando necessário.
- **Autenticação**: verificação da identidade do usuário.
- **Autorização**: permissões de acesso concedidas conforme o perfil do usuário.

---

## 2. Princípios de Design Seguro de Software

Conjunto de diretrizes para reduzir vulnerabilidades desde a concepção do sistema.

### Princípios de Design Seguro:
- **Privilégio Mínimo**: usuários têm apenas os acessos necessários.
- **Defesa em Profundidade**: múltiplas camadas de segurança (rede, servidor, aplicação, dados).
- **Padrões à Prova de Falhas**: configurações seguras por padrão.
- **Separação de Funções**: divisão de responsabilidades para reduzir riscos.
- **Security by Design**: segurança integrada em todas as fases do ciclo de vida.
- **Economia de Mecanismo**: simplicidade para reduzir erros.
- **Design Aberto**: transparência para revisão por outros profissionais.
- **Tratamento de Erros**: exceções tratradas explicitamente, sem expor detalhes ao usuário.

---

## 3. Cadeia de Suprimentos de Software

- **Software seguro depende de componentes de terceiros** (bibliotecas, ferramentas, hardware).
- **Vulnerabilidades conhecidas** em componentes podem comprometer todo o sistema.
- Exemplos:
  - **Heartbleed** (OpenSSL)
  - **Spectre e Meltdown** (processadores)
  - **Violação da Equifax** (Apache Struts)
  - **Spyware Pegasus** (NSO Group)

### Boas Práticas para a Cadeia de Suprimentos:
- Usar fontes oficiais e confiáveis.
- Manter componentes atualizados.
- Consultar bases de vulnerabilidades como:
  - **OWASP Top Ten**
  - **National Vulnerability Database (NVD)**

---

## 4. Vulnerabilidades Comuns em Componentes de Software

- **Componentes desatualizados**
- **Configuração inadequada**
- **Injeção de código (ex.: SQL Injection)**
- **Falhas de autenticação**
- **Quebra de autorização**
- **Fragilidade de criptografia**
- **Falta de validação de entrada**

### Medidas para Reduzir Vulnerabilidades:
- Práticas seguras durante o desenvolvimento.
- Testes regulares de segurança.
- Configurações seguras.
- Atualizações frequentes.

---

## 5. Avaliação e Gerenciamento de Riscos

Processo estruturado para identificar, analisar e mitigar riscos.

### Etapas do Gerenciamento de Riscos:
1. **Identificação de riscos**
2. **Análise de risco** (probabilidade e impacto)
3. **Priorização de riscos**
4. **Mitigação de riscos** (controles de acesso, contramedidas)
5. **Monitoramento e revisão contínuos**

---

## 6. Práticas de Codificação Segura

- **Validação de entrada**
- **Tratamento explícito de erros**
- **Autenticação segura** (senhas fortes, MFA)
- **Controle de acesso baseado em perfis**
- **Comunicação segura** (criptografia)
- **Armazenamento seguro** (dados criptografados)
- **Uso de funções especializadas e documentadas**
- **Atualizações regulares**

---

## 7. Testes de Vulnerabilidades

- **Teste Estático**: análise do código-fonte.
- **Teste Dinâmico**: execução do software e análise do comportamento.
- **Teste Interativo**: combinação de estático e dinâmico.
- **Teste de Penetração**: simulação de ataques reais.
- **Teste Fuzzing**: envio de entradas aleatórias para identificar falhas.

---

## 8. Conclusão

- Segurança deve estar presente **desde a concepção** do software.
- É essencial **manter-se atualizado** com vulnerabilidades conhecidas.
- **Ferramentas e processos** devem ser apoiados por **conscientização e formação ética**.
- Fontes recomendadas:
  - Microsoft: *Visão geral do desenvolvimento e das operações de segurança*
  - OWASP Top Ten
  - National Vulnerability Database (NVD)

---

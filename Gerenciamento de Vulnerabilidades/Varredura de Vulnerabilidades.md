## 📘 Resumo: Varredura de Vulnerabilidades

### 1. **Tipos de Escaneamento**
- **Discovery Scan**: Foco em inventariar dispositivos na rede.
- **Assessment Scan**: Avaliação de dispositivos para identificar vulnerabilidades.

---

### 2. **Preparação para a Varredura**
- **Ferramentas**: Devem ser compatíveis com a infraestrutura e atualizadas.
- **Pentest**: Complementa o escaneamento automático, especialmente em ambientes PCI-DSS.
- **Atividades Pré-escaneamento**:
  - Inventário de ativos
  - Classificação de dados
  - Definição de escopo
  - Periodicidade dos testes

---

### 3. **Periodicidade do Escaneamento**
- Deve ser definida com base na criticidade dos ativos e na frequência de atualizações.
- Exemplo: PCI-DSS recomenda escaneamentos trimestrais.
- Escaneamentos eventuais podem ser necessários para vulnerabilidades críticas.

---

### 4. **Restrições Técnicas**
- **Incompatibilidade**: Ferramenta vs. sistema
- **Sobrecarga**: Servidores no limite podem falhar durante o escaneamento
- **Atualizações**: Plugins e bancos de vulnerabilidades devem estar sempre atualizados (ex.: OpenVAS/GVM)

---

### 5. **Agentes de Escaneamento**
- **Agente Passivo**: Coleta informações e as disponibiliza para o servidor central.
- **Agente Ativo**: Envia informações automaticamente em intervalos programados.
- Podem exigir elevação de privilégios para maior detalhamento.

---

### 6. **Permissões e Acessos**
- Antivírus, firewalls e outras ferramentas de segurança podem bloquear o escaneamento.
- É necessário configurar exceções e garantir comunicação entre agente e servidor.

---

### 7. **Nível de Sensibilidade do Escaneamento**
- Define a profundidade do acesso aos recursos durante a varredura.
- Deve respeitar a política de proteção de dados.
- Exemplo: OpenVAS oferece perfis como “Full and fast”, “Full and very deep”, etc.

---

## 🛠️ **Ferramentas Práticas**

### OpenVAS / GVM (Greenbone Vulnerability Management)
- **Instalação**: Via Kali Linux (`apt-get install gvm` ou `openvas-setup`)
- **Configuração**: Acesso via `https://127.0.0.1:9392`
- **Uso**: Definir target → Criar task → Executar escaneamento → Analisar resultados

### OWASP ZAP
- Focado em aplicações web (OWASP Top 10)
- **Uso**: Inserir URL → Iniciar ataque → Analisar alertas

---

### 8. **Análise e Classificação dos Resultados**
- **Consolidação**: Reunir resultados de ferramentas automáticas e testes manuais.
- **Validação**:
  - Descarte de falsos positivos
  - Correlação com logs
  - Pesquisa de alertas de fabricantes
  - Prova de conceito (PoC)
- **Classificação de Risco**:
  - Uso do CVSS (Common Vulnerability Scoring System)
  - Ajuste com base no contexto organizacional

---

### 9. **Priorização**
- Baseada em:
  - Criticidade do ativo
  - Classificação de dados
  - Tempo para correção
  - Nível de risco (CVSS)

---

## 🧠 **Conclusões Chave**
- Varredura não é só executar ferramentas: requer planejamento, permissões, atualizações e validação.
- Resultados automatizados devem ser consolidados e contextualizados.
- A fase de análise é crucial para a priorização e remediação efetivas.

---

## 🔍 **Explore Mais**
- Ferramentas: **Nexpose**, **OpenVAS**, **OWASP ZAP**
- Normas: **PCI-DSS**, **CVSS**
- Prática: **Metasploitable** para ambientes de teste

---

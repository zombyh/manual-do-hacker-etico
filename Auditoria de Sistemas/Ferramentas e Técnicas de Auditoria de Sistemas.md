## 🛠️ Resumo: Ferramentas e Técnicas de Auditoria de Sistemas

### 1. Fases de uma Auditoria de Sistemas
- **Sistemas em desenvolvimento**: foco nos **controles planejados**.
- **Sistemas em operação**: verificação e **teste dos controles implementados**.
- O auditor utiliza três tipos de programas:
  1. **Softwares generalistas**
  2. **Softwares especializados**
  3. **Softwares utilitários**

---

### 2. Tipos de Programas de Auditoria

#### 2.1 Softwares Generalistas
- Conjunto de programas em **ambiente batch** (processamento offline).
- Funções: extração de amostras, testes, estatísticas, detecção de duplicidades, etc.
- **Vantagens**:
  - Processa vários arquivos e formatos
  - Integração com diferentes softwares/hardwares
  - Não exige conhecimento técnico profundo
- **Desvantagens**:
  - Não permite aplicações online
  - Não oferece cálculos específicos para sistemas especializados

#### 2.2 Softwares Especializados
- Desenvolvidos sob demanda para sistemas com características únicas (ex.: leasing, câmbio).
- **Vantagens**:
  - Incluem testes de controles internos específicos
  - Permitem **hash total** (soma de campos sem sentido funcional para verificar integridade)
  - Usam **header label** (primeiro registro) e **trailer label** (último registro) para controle
- **Desvantagens**:
  - Exigem conhecimento em desenvolvimento
  - Custos de desenvolvimento

#### 2.3 Softwares Utilitários
- Programas básicos para funções como soma, classificação e listagem.
- **Vantagens**:
  - Fáceis de aprender e usar
- **Desvantagens**:
  - Limitados a funções padrão

---

### 3. Programa de Computador para Auditoria
- Correlacionam dados, tabulam e imprimem conteúdos.
- Funções comuns:
  - **Tabulação de campos**: somatórios, hash total, controle de lote
  - **Contagem de registros**: totais por tipo
  - **Análise de conteúdo**: verificação de coerência e validade
  - **Correlação de arquivos**: confronto entre registros
  - **Estatísticas**: média, desvio-padrão, moda

---

### 4. Técnicas de Auditoria

#### 4.1 Questionários
- Um questionário para cada **ponto de controle**.
- Inclui:
  - Perguntas relevantes
  - Espaço para observações
  - Referência a papéis de trabalho
- **Temas comuns**:
  - Segurança de rede
  - Segurança do centro de computação
  - Eficiência no uso de recursos
  - Eficácia de sistemas aplicativos
- Devem ser usados em conjunto com **entrevistas** e **visita in loco**.

#### 4.2 Visita In Loco
- Presença do auditor no local para verificação física.
- **Objetivos**:
  - Verificar ativos computacionais
  - Checar inventários (fitas, suprimentos)
  - Acompanhar rotinas de backup
  - Verificar controle de acesso
- Deve ser **marcada formalmente** e documentada.

#### 4.3 Entrevistas
- Podem ser: **pessoais, por telefone ou vídeo**.
- **Tipos**:
  - **Estruturada**: com formulário
  - **Não estruturada**: sem formulário
- Devem seguir um **roteiro prévio** e uma **sequência lógica**.
- Úteis quando o auditor tem **conhecimento limitado** do processo.

---

### 7. Referências
- **Auditoria de Sistemas de Informação** – Joshua Onome Imoniana (Cap. 5)
- **Auditoria de Computadores** – Antonio de Loureiro Gil (Cap. 3)

---

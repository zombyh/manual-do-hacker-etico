## 🧪 Resumo: Mais Técnicas de Auditoria de Sistemas

## 🎯 Objetivos da Aula
- Conhecer novas técnicas de teste de auditoria.
- Aprender a fazer **simulação paralela**.
- Compreender a **lógica de auditoria embutida** nos sistemas.
- Aprender a fazer **rastreamento e mapeamento**.
- Conhecer a técnica de **análise de log/accounting**.
- Compreender a importância da **análise do programa fonte**.

---

## 1. Tipos de Testes de Auditoria

### 1.1 Teste de Observância
- Verifica se os **procedimentos internos** estão sendo **cumpridos** pelos colaboradores.
- Objetivo: avaliar a **credibilidade dos controles**, não a exatidão dos registros.
- Comum em **auditorias operacionais**.
- Aplicado de forma **discreta** para evitar alteração no comportamento dos auditados.

### 1.2 Teste Substantivo
- Busca **evidências suficientes e convincentes** sobre as transações.
- Objetivos:
  - **Existência real**: transações realmente ocorreram.
  - **Integridade**: nada foi omitido ou alterado.
  - **Parte interessada**: informações foram recebidas integralmente.
  - **Avaliação e aferição**: itens foram avaliados corretamente.
  - **Divulgação**: transações foram divulgadas adequadamente.
- Essencial para fundamentar a **opinião do auditor**.

---

## 2. Técnicas de Auditoria

### 2.1 Dados de Teste (Test Data / Test Deck)
- Aplicado em **ambiente batch**.
- Auditor cria uma **massa de dados** com transações corretas e incorretas.
- Objetivo: testar **controles programados** e do sistema.
- Exemplos de situações simuladas:
  - Campos incorretos
  - Valores no limite
  - Transações incompletas, duplicadas ou incompatíveis
- Etapas:
  1. Compreensão do módulo
  2. Simulação dos dados
  3. Elaboração de formulários de controle
  4. Transcrição para meio computacional
  5. Preparação do ambiente
  6. Processamento
  7. Avaliação dos resultados
  8. Emissão de opinião

### 2.2 Facilidade de Teste Integrado (ITF – Integrated Test Facility)
- Usado em **ambiente online e real-time**.
- Dados de teste são **integrados ao ambiente real**.
- Utiliza **entidades fictícias** (ex.: funcionário fantasma).
- Resultados são comparados com o esperado.
- **Não altera** as bases reais, mas cria arquivos de resultado separados.

### 2.3 Simulação Paralela
- Auditor **cria um programa** que simula a lógica do sistema auditado.
- Utiliza **dados reais de produção** como entrada.
- Compara resultados do sistema real com o programa simulado.
- Estrutura de aplicação:
  1. Identificação da rotina e arquivos
  2. Desenvolvimento e teste do programa simulado
  3. Preparação do ambiente

### 2.4 Lógica de Auditoria Embutida
- Inclusão de **rotinas de auditoria** durante o desenvolvimento do sistema.
- Gera **relatórios periódicos** para revisão.
- Exemplo: **arquivos de log** de acesso e **relatórios de exceção** (ex.: comportamento incomum de cliente em sistema de cartão).

### 2.5 Mapeamento Estatístico (Mapping)
- Identifica:
  - Rotinas não utilizadas
  - Frequência de uso de cada rotina
- Revela:
  - Rotinas obsoletas
  - Rotinas fraudulentas
  - Rotinas de controle
- Requer software auxiliar ou rotinas no sistema operacional.
- Pode **degradar o desempenho** do sistema.

### 2.6 Rastreamento (Tracing)
- Acompanha o **caminho de uma transação** durante o processamento.
- Lista a **sequência de instruções executadas**.
- Identifica **inadequações e ineficiências**.
- Permite detectar **rotinas fraudulentas**.
- Exige que o auditor **conheça programação**.
- Permite verificar:
  - Padronização de código
  - Qualidade da estrutura
  - Vícios de programação

### 2.7 Análise do Log/Accounting
- Arquivo gerado pelo **sistema operacional** com registros de uso de hardware e software.
- Permite verificar:
  - Intensidade de uso de dispositivos
  - Uso de software aplicativo
- Fonte valiosa para **detecção de fraudes**.

---

## 🔍 Dica Importante
- Para garantir que está testando a **versão correta do programa em produção**, o auditor pode:
  1. Solicitar a recompilação do fonte na biblioteca de origem.
  2. Comparar o código objeto gerado com o que está em produção.
  3. Verificar eventuais divergências.

---


# Resumo: Ciclo de Relatórios em Gerenciamento de Vulnerabilidades

## 📌 Objetivo da Aula
- Descrever o processo de **criação de grupos de ativos**.
- Definir as **métricas** utilizadas no gerenciamento de vulnerabilidades.

---

## 🧩 Gestão de Ativos

### Por que é importante?
- A gestão de ativos é a base para relatórios eficazes e para a **tomada de decisão** pela alta administração.
- Está prevista na **ABNT NBR ISO/IEC 27002** como um dos controles essenciais de segurança da informação.
- Integra-se ao **gerenciamento de vulnerabilidades**, influenciando priorização, varredura e remediação.

### Componentes da Gestão de Ativos:

#### 1. Inventário de Bens
- Identificação de **todos os ativos** relevantes para o negócio.
- Deve incluir informações que permitam a **recuperação em caso de desastre**.
- Quanto mais completo, melhor o **mapeamento e a priorização**.

#### 2. Classificação dos Dados
- Define o **nível de proteção** com base na sensibilidade da informação.
- Ativos com classificação alta devem ser **escaneados primeiro**.

#### 3. Mapeamento de Grupos de Ativos
- Agrupa ativos por categorias para facilitar o gerenciamento e a aplicação de políticas de segurança.
- Categorias comuns:
  - **Ativos de informação**: BD, contratos, manuais, etc.
  - **Ativos de software**: aplicações, sistemas, utilitários.
  - **Ativos físicos**: equipamentos, mídias, infraestrutura.
  - **Serviços**: computação, energia, refrigeração.
  - **Intangíveis**: reputação, imagem.

#### 4. Ciclo de Vida dos Ativos
- Acompanhamento contínuo para **substituição, renovação ou mitigação**.
- Evita que ativos obsoletos ou com licenças expiradas permaneçam em uso.

#### 5. Integração das Informações
- Centralizar dados dos ativos em um **local único** facilita a correlação e a tomada de decisão.

#### 6. Alertas Automatizados
- Notificações automáticas sobre **vencimentos, falhas ou mudanças** nos ativos.
- Reduz a dependência de ações manuais e aumenta a eficiência.

---

## 📊 Métricas de Controle para Segurança da Informação

### Objetivo:
- Quantificar atividades para **melhorar a prevenção** e a **resiliência cibernética**.
- Apoiar a **tomada de decisão** com base em dados.

### Métricas Principais:

#### 1. Cobertura de Código de Software
- Mede a % do código realmente utilizado.
- Áreas inoperantes podem indicar **ineficácia ou alterações suspeitas**.

#### 2. Gap de Detecção de Novas Vulnerabilidades
- Tempo entre a **publicação de um CVE** e sua **detecção na organização**.
- Quanto menor o gap, maior a agilidade na correção.

#### 3. Ciclo de Vida de Vulnerabilidades Existentes
- Tempo desde que a vulnerabilidade **passou a existir** até sua **correção ou mitigação**.
- Vulnerabilidades antigas aumentam o risco de exploração.

#### 4. Tempo Médio para Remediação
- Período entre a **detecção** e a **correção**.
- Indicador de **eficiência do processo** de gerenciamento.

#### 5. Quantidade de Vulnerabilidades por Período
- Número total de vulnerabilidades identificadas em um intervalo.
- Deve ser analisado em conjunto com outras métricas para evitar distorções.

#### 6. Índice de Patches Aplicados
- Número de **correções aplicadas** em um período.
- Reflete a **capacidade de resposta** da equipe.

#### 7. Tempo Médio para Detectar um Incidente
- Tempo desde o **início do incidente** até sua **detecção**.
- Estudos mostram que a detecção pode levar **mais de 200 dias**.

#### 8. Tempo Médio Entre Incidentes
- Frequência com que incidentes ocorrem.
- Espera-se que **diminua** com a maturidade do gerenciamento de vulnerabilidades.

---

## ✅ Conclusão
- A gestão de ativos é **fundamental** para um gerenciamento de vulnerabilidades eficaz.
- Métricas **quantificam e orientam** a melhoria contínua do processo.
- Relatórios devem ser **atualizados constantemente** e alinhados aos **objetivos do negócio**.

---

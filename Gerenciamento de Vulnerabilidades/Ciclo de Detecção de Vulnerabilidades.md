
# Resumo: Ciclo de Detecção de Vulnerabilidades

## 📌 Objetivo da Aula
- Definir o **escopo** de um teste de vulnerabilidades.
- Descrever as **principais ferramentas** de verificação de vulnerabilidades.

---

## 🧭 Definição do Escopo

### Pré-requisitos Essenciais:
1. **Classificação dos Dados**  
   - Define o nível de sensibilidade das informações.
   - Categorias:
     - **Pública**: Sem risco (ex.: número de funcionários).
     - **Classificada**: Acesso restrito (ex.: sanção disciplinar).
     - **Confidencial**: Acesso autorizado (ex.: mapa de rede).
     - **Secreta**: Impacto grave (ex.: vazamento de dados de clientes).
     - **Top Secret**: Altamente restrita (ex.: projeto de produto).

2. **Inventário de Ativos**  
   - Levantamento de todos os ativos (hardware, software, dados, serviços).
   - Base para definir **o que será escaneado**.
   - Considerado a **melhor prática #1** pelo CIS Controls (2020).

### Ações para Definição do Escopo:
- Identificar a **capacidade da ferramenta** e da equipe.
- Integrar **inventário** e **classificação de dados**.
- Definir **ativos prioritários** com base na criticidade.

---

## 🔍 Métodos de Verificação de Vulnerabilidades

- **Ferramentas Automatizadas**: Varreduras em rede/sistemas.
- **Teste de Invasão (Pentest)**: Simulação de ataques.
- **Análise Crítica de Código**: Revisão de código-fonte.

> ⚠️ **Atenção**: Nem todas as vulnerabilidades detectadas são reais (**falsos positivos**). É essencial validar os resultados no contexto do ambiente.

---

## 🛠️ Ferramentas de Escaneamento

### 1. **OpenVAS**
- **Tipo**: Open Source
- **Plataforma**: Linux (mas escaneia multiplataforma)
- **Características**:
  - Banco de vulnerabilidades extenso e atualizado.
  - Suporte a varreduras **autenticadas** e **não autenticadas**.
  - Relatórios detalhados com sugestões de correção.
  - Suporte a protocolos industriais.
  - Atualizações via **NVT (Network Vulnerability Tests)**.

### 2. **OWASP ZAP**
- **Tipo**: Open Source
- **Foco**: Aplicações Web
- **Plataforma**: Multiplataforma (Linux, Windows, OSX)
- **Características**:
  - Fácil de usar, mesmo para não especialistas.
  - Suporte a testes autenticados e não autenticados.
  - Gera relatórios em HTML, XML, texto.
  - Utiliza plugins para extensibilidade.

### 3. **Nessus**
- **Tipo**: Proprietário (versão free limitada)
- **Plataforma**: Multiplataforma
- **Características**:
  - Banco de vulnerabilidades muito extenso.
  - Integração com NMAP para varredura de portas.
  - Baixa taxa de falsos positivos.
  - Plugins personalizáveis (NASL).
  - Relatórios em vários formatos (inclusive LaTeX).

---

## 🔗 Protocolo SCAP
- Padroniza a comunicação sobre vulnerabilidades.
- Componentes principais:
  - **CVE**: Identifica vulnerabilidades.
  - **CPE**: Identifica plataformas.
  - **CCE**: Melhores práticas de configuração.
  - **OVAL**, **XCCDF**, **CVSS**: Padrões de avaliação e pontuação.

---

## 📋 Conclusão
- A definição do **escopo** é fundamental e depende da **classificação de dados** e **inventário de ativos**.
- Ferramentas como **OpenVAS**, **OWASP ZAP** e **Nessus** são essenciais para a detecção automatizada.
- A **validação** dos resultados e a **documentação** são etapas críticas para evitar retrabalho.

---

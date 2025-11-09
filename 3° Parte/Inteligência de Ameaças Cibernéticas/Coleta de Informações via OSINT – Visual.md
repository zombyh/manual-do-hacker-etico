## 📘 Resumo: Coleta de Informações via OSINT – Visual

## 📌 Visão Geral da Aula
- **Tema**: Inteligência de Ameaças Cibernéticas
- **Foco**: Uso de ferramentas visuais para coleta de OSINT (Open Source Intelligence)
- **Objetivos**:
  - Explicar Indicadores de Compromisso (IOCs)
  - Descrever tipos de relatórios de inteligência
  - Aplicar ferramentas visuais como o Maltego na criação de relatórios

---

## 🔍 O que é OSINT?
- **OSINT**: Inteligência de Fontes Abertas
- Coleta passiva de informações disponíveis publicamente na internet
- Não envolve varreduras ativas ou invasivas
- Deve atender aos requisitos definidos no ciclo de vida do CTI (Cyber Threat Intelligence)

---

## 🛠️ Ferramentas de OSINT Visual

### Maltego
- Ferramenta de **análise de links** desenvolvida pela Paterva
- Versão gratuita disponível (com limitações)
- Funciona com **Transforms**: plug-ins que automatizam a coleta de dados

### Tipos de Transforms
1. **Pagos**: Oferecidos por empresas de segurança
2. **Gratuitos**: Requerem cadastro para token de acesso
3. **Próprios**: Desenvolvidos pelo usuário (ex.: com Python ou Perl)

---

## 🧩 Casos de Uso do Maltego

### 1. Mapeamento de Domínios e IPs
- Identificação de subdomínios
- Busca de endereços IP e blocos de rede
- Exemplo: Análise do domínio `oglobo.com.br` e seus subdomínios

### 2. Uso do Shodan via Transform
- Identificação de serviços e portas abertas
- Exemplo: Detecção de servidor Microsoft IIS na porta 443

### 3. Verificação de E-mails Comprometidos
- Identificação de vazamentos de dados (ex.: Adobe, LinkedIn, Dropbox)
- Tipos de dados vazados: senhas, e-mails, telefones, cartões de crédito, etc.

### 4. Busca por IOCs (Indicadores de Compromisso)
- Uso de hashes de arquivos maliciosos no VirusTotal
- Verificação de IPs suspeitos e associação a malwares (ex.: Emotet)

### 5. Mapeamento de Infraestrutura com Machines
- **Machines**: Conjuntos de tarefas automatizadas no Maltego
- Exemplos:
  - **Footprint L1**: Busca básica de infraestrutura
  - **Footprint L2**: Inclui servidores de e-mail e domínio
  - **Footprint L3**: Inclui histórico de DNS e reversos

---

## 📱 OSINT em Mídias Sociais (SOCMINT)
- **SOCMINT**: Social Media Intelligence
- Caso de uso: Identificar seguidores em comum entre contas no Twitter
- Exemplo: Banda Calypso e Baile da Gaiola

---

## ❓ Perguntas de Revisão (Com Respostas)

1. **O que o Maltego visualiza?**  
   → Informações coletadas por transforms OSINT

2. **O que a imagem de subdomínios do Linux.com representa?**  
   → **b) Lista dos subdomínios associados ao domínio Linux.com**

3. **Sequência de passos para chegar ao resultado com IP e portas:**  
   → **c) Subdomínio, Website, Lista de IP, Portas**

4. **O que significa "443: < unknown >" no Shodan?**  
   → **a) Porta aberta, mas servidor não identificado**

5. **Como o Maltego automatiza tarefas?**  
   → Por meio de **Machines**

---

## 📚 Referências e Exploração Adicional
- **Site da Paterva**: [https://www.paterva.com](https://www.paterva.com)
- **Artigos sugeridos**:
  - *A Beginner’s Guide to OSINT Investigation with Maltego*
  - *Nine must-have OSINT tools*
  - *How to Use Maltego to do Network Reconnaissance*

---

## 🧠 Conceitos Importantes para Revisão
- **IOC**: Indicador de Compromisso
- **OSINT**: Inteligência de Fontes Abertas
- **SOCMINT**: Inteligência em Mídias Sociais
- **Transform**: Plug-in do Maltego
- **Machine**: Conjunto de transforms automatizados

---

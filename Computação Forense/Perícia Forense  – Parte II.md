## Resumo: Perícia Forense Computacional – Parte II

## 🔎 Procedimentos Básicos da Perícia Forense
De acordo com Freitas (2007), a perícia forense computacional segue quatro etapas principais:

1. **Identificação**
2. **Preservação**
3. **Análise**
4. **Apresentação**

> ⚠️ Nem todas as etapas são obrigatórias em todos os casos. A aplicação depende do tipo de crime e das evidências disponíveis.

---

## 🧠 Princípio de Locard na Computação
> *"Quaisquer que sejam os passos, quaisquer objetos tocados por ele, o que quer que ele deixe, mesmo que inconscientemente, servirá como uma testemunha silenciosa contra ele."* – Paul Leland Kirk

- Vestígios digitais são análogos aos vestígios físicos.
- Tanto o contato físico (hardware) quanto o lógico (dados) deixam rastros.

---

## 🧩 Contextos de Análise Forense

### Contexto Físico
- Parte tangível do sistema: circuitos, processadores, mídias de armazenamento.
- Exemplo: HD, pendrive, DVD.

### Contexto Lógico
- Parte intangível: dados, arquivos, instruções binárias.
- Exemplo: fotos, documentos, logs.

> 🔁 Um item lógico pode estar relacionado a um ou mais itens físicos (ex.: RAID).

---

## 🛡️ Etapas Detalhadas da Investigação Forense

### 1. Identificação
- Atentar ao tipo de crime.
- Buscar logs, conexões, alterações em arquivos.
- Usar todos os meios disponíveis para elucidação.

### 2. Isolamento
- Evitar contaminação da cena.
- Dividido em:
  - **Isolamento físico**: preservar a área do crime.
  - **Isolamento lógico**: proteger dados em meio digital.

### 3. Coleta
- Trabalhar com cópias (imagens bit-a-bit).
- Preservar atributos de tempo (MAC Times):
  - `mtime` (modificação)
  - `atime` (acesso)
  - `ctime` (criação)
- Coletar dados voláteis (RAM, conexões de rede, processos).

### 4. Preservação
- Uso de **cadeia de custódia** para garantir integridade.
- Uso de bloqueadores de escrita e duplicadores forenses.

### 5. Análise
- Fase mais demorada e técnica.
- Correlacionar evidências para reconstruir eventos.
- Uso de ferramentas como FTK, Encase, IPED.

### 6. Apresentação
- Elaboração de laudo pericial.
- Incluir todas as evidências, documentos e comprovação da cadeia de custódia.

---

## 📋 Cadeia de Custódia
- Registro detalhado de todas as pessoas que tiveram posse da evidência.
- Elementos essenciais:
  - Identificação do equipamento (fabricante, modelo, nº de série)
  - Detalhes da imagem (data, hash, método de cópia)
  - Registro de trânsito e guarda da evidência

> ❌ Ausência da cadeia de custódia pode invalidar a evidência no tribunal.

---

## 🛠️ Ferramentas e Técnicas

### Técnicas de Imagem e Espelhamento
- Cópias idênticas (bit-a-bit) para análise.
- Uso de duplicadores forenses (ex.: AXIOM, Tableau).

### Recuperação de Arquivos (Data Carving)
- Recuperação por assinaturas de arquivo.
- Técnicas para quebra de senhas:
  - Engenharia reversa
  - Engenharia social
  - Ataque de força bruta

### Indexação de Dados
- Acelera buscas em grandes volumes de dados.
- Ferramentas: FTK, Encase, IPED.

---

## 👨‍💼 Perito Criminal vs. Perito Nomeado

### Perito Oficial
- Servidor público concursado.
- Formação superior específica.
- Atua preferencialmente na esfera criminal.

### Perito Nomeado
- Não é servidor público.
- Atua principalmente na esfera cível.
- Nomeado pelo juiz na falta de perito oficial.

---

## 📚 Referências Principais
- FREITAS (2007)  
- ELEUTÉRIO e MACHADO (2010)  
- BRASIL, Lei nº 12.030/2009  
- CARVALHO (2020)  
- NBR 27037:2012 (Diretrizes para evidência digital)

---

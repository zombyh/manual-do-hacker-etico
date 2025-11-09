
## 📘 Resumo: Técnicas Antiforense – Parte I

### 🎯 Objetivos da Aula
- Abordar conceitos gerais sobre **antiforense**.
- Descrever técnicas antiforense comuns.
- Identificar e traçar **procedimentos antiforense**.

---

### 🔍 O que é Antiforense?

- **Definição**: Conjunto de técnicas e procedimentos aplicados para **dificultar, subverter ou inviabilizar** a coleta, análise ou utilidade de vestígios digitais em uma investigação forense.
- **Objetivo principal**: Impedir que evidências de crimes sejam **detectadas, coletadas ou utilizadas** em processos judiciais.
- **Contexto**: Surge como contrapartida ao desenvolvimento da perícia computacional.

> “Antiforense é qualquer tentativa de comprometer a disponibilidade ou utilidade das evidências para o processo forense.”

---

### 🧩 Técnicas Antiforense Comuns

#### 1. **Destruição ou Sobrescrita de Dados**
- Uso de ferramentas como **Wipe, Eraser, PGP Wipe**.
- **Método**: Sobrescrever dados repetidamente para impedir recuperação.
- **Ponto fraco**: Pode deixar **vestígios de limpeza**, indicando ação intencional.

#### 2. **Ocultação de Dados**
- **Realocação**: Mover dados para locais menos óbvios ou para dispositivos externos.
- **Invisibilidade**:
  - **Esteganografia**: Ocultar dados dentro de imagens, áudios ou vídeos.
  - **Streaming de arquivos**: Associar múltiplos arquivos a uma única entrada na tabela de arquivos.
- **Alteração de extensões**: Mudar a extensão do arquivo para enganar investigadores.

#### 3. **Ofuscação de Trilhas (Falsificação)**
- **Desfragmentação**: Reorganiza o disco, **sobrescrevendo espaços alocados** e destruindo dados residuais.
- **Modificação de metadados**:
  - Alterar carimbos de data/hora (**valores MACE**).
  - Ferramentas: **Metasploit Timestomp**, **File Touch**.
  - Pode ser detectada por **análise de consistência temporal**.

#### 4. **Criptografia de Volume**
- Criptografar arquivos, pastas ou discos inteiros.
- **Ferramentas comuns**: BitLocker, TrueCrypt, VeraCrypt.
- **Dificuldade**: Sem a chave, o acesso aos dados é praticamente impossível.
- **Estratégia contra criptografia**:
  - Coleta **"live"** da memória RAM (dump de memória).
  - Uso de ferramentas como **Volatility** para extrair chaves da RAM.

---

### ⚔️ Ataques a Ferramentas e Processos Forenses

#### 1. **Ataques de Negação de Serviço (DoS)**
- **Zip da Morte (Zip Bomb)**:
  - Arquivo compactado pequeno que, ao ser descompactado, consome terabytes.
  - Exemplo: `42.zip` → 4,5 PB ao descompactar.
- **ReDoS (Regular Expression DoS)**:
  - Uso de expressões regulares maliciosas para travar ferramentas.

#### 2. **Ataques às Fases do Processo Forense**
- **Identificação**: Ocultar o incidente ou a relação do dispositivo com o crime.
- **Preservação**: Quebrar a cadeia de custódia ou questionar a integridade das evidências.
- **Coleta**: Limitar a integridade dos dados coletados.
- **Exame**: Questionar a validade científica das ferramentas.
- **Análise**: Atacar a interpretação das evidências.
- **Apresentação**: Questionar a credibilidade do perito ou do relatório.

---

### 🧪 Exemplos de Casos

- **Caso de suicídio fraudulento**: Nota de suicídio com data de criação posterior à morte – metadados inconsistentes.
- **Uso de desfragmentação frequente**: Indício de tentativa de destruir evidências.

---

### 🛡️ Como se Proteger ou Contornar Técnicas Antiforense

- **Análise de assinatura de arquivos**: Verificar se a extensão corresponde ao tipo real.
- **Análise de consistência temporal**: Cruzar metadados com logs do sistema.
- **Coleta de memória RAM** em sistemas ligados.
- **Uso de ferramentas especializadas**:
  - **EDD (Encrypted Disk Detector)**: Identifica volumes criptografados.
  - **Volatility**: Análise de memória RAM.
  - **Autopsy + TSK**: Análise de discos e recuperação de arquivos.

---

### ✅ Resumo das Técnicas

| Técnica | Objetivo | Exemplo |
|---------|----------|---------|
| Limpeza de dados | Impedir recuperação | Eraser, Wipe |
| Esteganografia | Ocultar dados em arquivos | Ocultar texto em imagem |
| Alteração de metadados | Confundir linha do tempo | Timestomp |
| Criptografia | Impedir acesso | TrueCrypt, BitLocker |
| Zip Bomb | Travar ferramentas | 42.zip |
| Desfragmentação | Destruir dados residuais | Desfragmentador do Windows |

---

### 📚 Referências
- ELEUTÉRIO, Pedro. *Desvendando a Computação Forense*.
- VELHO, Jesus Antonio. *Tratado de Computação Forense*.
- MITRE ATT&CK: [https://attack.mitre.org/](https://attack.mitre.org/)

---

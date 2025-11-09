
## 📘 Resumo: Preservação de Evidências em Computação Forense

### 🎯 Objetivos da Aula
- Descrever procedimentos de preservação de evidências **durante a coleta e análise**.
- Identificar **softwares e dispositivos** utilizados na coleta de dados.

---

### 🔍 Procedimentos Durante Busca e Apreensão

#### 1. Identificação do Local
- Identificar todos os equipamentos de informática: computadores, laptops, switches, redes Wi-Fi, etc.

#### 2. Preservação dos Vestígios Digitais
- Impedir que pessoas não autorizadas manuseiem os equipamentos.
- **Não ligar** equipamentos que estejam desligados.

#### 3. Interrupção das Conexões de Rede
- Desconectar redes para evitar transmissão ou exclusão remota de dados.
- Desligar a fonte de energia, **evitando o desligamento pelo SO**.

---

### 🧠 Cuidados Especiais com Evidências Voláteis

#### Memória RAM
- Dados voláteis são perdidos ao desligar.
- Em computadores ligados, pode ser necessário fazer uma **cópia da memória RAM** antes de desligar.

#### Evitar Alterações
- Não usar dispositivos locais para verificar dados.
- Somente **peritos treinados** devem manusear equipamentos.
- Usar **softwares e hardwares forenses** para evitar alterações.

---

### 📦 Coleta e Acondicionamento

#### Coleta
- Coletar equipamentos que possam conter evidências.
- **Não desligar pelo SO**: preferir retirar a fonte de energia para evitar execução de scripts maliciosos.

#### Acondicionamento
- Proteger contra:
  - **Choques mecânicos**: usar caixas especiais e plástico-bolha.
  - **Temperatura inadequada**: evitar calor, frio extremo e luz solar.
  - **Umidade excessiva**: usar sílica gel e ambientes climatizados.
  - **Campos magnéticos e elétricos**: evitar imãs, motores e usar materiais antiestáticos.

---

### 💾 Duplicação de Dados de Forma Forense

#### Técnicas
- Criar **imagens ou espelhos** bit-a-bit do dispositivo original.
- Usar equipamentos com **bloqueio de escrita** (ex: Tableau TD3, ICS Solo IV).
- Em software: usar `dd`, `dc3dd`, `dcfldd` em distribuições Linux forenses (ex: SIFT, CAINE).

#### Formatos de Imagem
- **Raw/dd**
- **E01** (EnCase)

---

### 🛠️ Ferramentas de Análise Forense

#### Comerciais
- **EnCase**: completo, interface gráfica, suporte a múltiplas mídias.
- **FTK (AccessData)**: fácil uso, compatível com várias imagens forenses.

#### Livres e Open Source
- **The Sleuth Kit (TSK)**: linha de comando, foco em análise de discos.
- **Autopsy**: interface gráfica sobre o TSK.
- **IPED**: desenvolvido pela Polícia Federal do Brasil.

---

### ✅ Princípios Fundamentais

1. **Tratar toda informação como prova judicial**.
2. **Coletar o máximo de material possível**, seguindo a ordem de volatilidade.
3. **Autenticar, catalogar e preservar** cada item.
4. **Manter a cadeia de custódia**.
5. **Analisar apenas cópias**, nunca os originais.

---

### 📌 Dicas Práticas

- **Dispositivos móveis**: colocar em **modo avião** ou remover o chip.
- **Senhas**: solicitar ao usuário, se possível.
- **Laboratório**: deve ter controle de acesso, ambiente controlado e equipamentos especializados.

---

### 📚 Referências
- COSTA, M.A.S.L. *Computação Forense*
- ELEUTÉRIO; MACHADO. *Desvendando a Computação Forense*
- LAWRENCE, K.R. *Tools for Computer Forensics*
- RODRIGUES; FOLTRAN JR. *Análise de Ferramentas Forenses*

---

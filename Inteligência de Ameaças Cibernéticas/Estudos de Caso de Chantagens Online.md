
## 📘 Resumo: Aula 10 – Estudos de Caso de Chantagens Online

### 🎯 Objetivos da Aula
- Analisar dois casos reais de chantagem por e-mail.
- Aplicar ferramentas de análise de ameaças (Maltego, OSINT).
- Utilizar inteligência para orientar decisões em outras áreas da empresa.

---

## 🔍 Caso 1: Sextortion (Chantagem Sexual)

### 📌 Descrição
- E-mail que alega que o atacante invadiu o dispositivo da vítima e registrou seu comportamento em sites adultos.
- Ameaça: divulgar imagens ou vídeos para contatos da vítima se não for pago um resgate em Bitcoin.
- Pode ser **real** (com acesso real ao sistema) ou **falso** (usando dados vazados e engenharia social).

### ✉️ Exemplo de E-mail (Traduzido)
- Inclui:
  - Senha real da vítima (obtida de vazamentos).
  - Alegação de acesso via malware no roteador.
  - Prazo de 48 horas para pagamento em Bitcoin.
  - Ameaça de bloqueio do dispositivo e envio de "provas" para contatos.

### 🧠 Análise de Inteligência (CTI)
- **E-mail da vítima**: Verificado em bases vazadas (Have I Been Pwned).
  - Senhas reais aparecem em vazamentos (ex.: Adobe, LinkedIn).
  - Indica reutilização de senhas.
- **Carteira Bitcoin**:
  - Múltiplas transações (entrada e saída).
  - Não é única por vítima → impossível vincar pagamento a uma pessoa.
  - Indica golpe em massa.

### ✅ Conclusão do Caso 1
- E-mail é **fraudulento**.
- Recomenda-se:
  - Não pagar.
  - Alterar senhas.
  - Usar autenticação de dois fatores.
  - Verificar vazamentos com ferramentas como Have I Been Pwned.

---

## 🛡️ Caso 2: Ameaça de DDoS – Armada Collective

### 📌 Descrição
- E-mail ameaçando realizar um ataque de DDoS se não for pago 10 BTC.
- Grupo se passa pelo “Armada Collective”, conhecido por extorsão.
- Inclui link para dar credibilidade à ameaça.

### 🧠 Análise de Inteligência (CTI)
- **Pesquisa no Threat Connect**:
  - Grupo real, mas ameaças recentes são de **imitadores**.
- **Relatório GovCERT.ch**:
  - Nova onda de e-mails é de “copycat”.
  - Recomendação oficial: **não pagar**.
- **Artigo da Cloudflare**:
  - Nenhum ataque real foi registrado.
  - Mesmo endereço Bitcoin usado para várias vítimas → campanha genérica.

### ✅ Conclusão do Caso 2
- Ameaça de **baixa credibilidade**.
- Recomenda-se:
  - Monitorar tráfego de rede.
  - Preparar defesas contra DDoS (portas UDP 123, 1900, SYN Flood).
  - Manter equipe de rede alerta.

---

## 🛠️ Ferramentas e Técnicas Utilizadas
- **Maltego**:
  - Transform “Have I Been Pwned” para verificar vazamentos de e-mail.
  - Transforms de Blockchain para analisar transações Bitcoin.
- **Blockchain.com**:
  - Visualizar transações e saldo de carteiras BTC.
- **Threat Connect (TIP)**:
  - Pesquisar grupos de ameaças e relacionar indicadores.
- **OSINT**:
  - Consultar relatórios de CERTs, blogs de segurança (Cloudflare), notícias.

---

## 📚 Lições Chave
- **Sextortion**:
  - Use senhas únicas para cada serviço.
  - Desconfie de e-mails com senhas reais – podem vir de vazamentos.
- **Ameaças de DDoS**:
  - Verifique a credibilidade da ameaça com fontes confiáveis.
  - Nem toda ameaça se concretiza.
- **Bitcoin em Golpes**:
  - Carteiras com múltiplas transações indicam golpe em massa.
  - Pagamento não garante silêncio ou solução.

---

## ❓ Perguntas de Revisão (Respostas)
1. **a) Verdadeiro** – Sextortion pode ser real ou falso.
2. **b) Sim** – Reutilizar senhas expõe a vítima a novos ataques.
3. **b) As transações associadas àquele endereço Bitcoin.**
4. **e) Opções A e C** – Revela se o e-mail foi vazado e em qual base.
5. **b) Sim** – A equipe de rede pode tratar tráfego TCP na porta 53 de forma especial.

---

## 📌 Palavras-Chave para Obsidian
```
#Sextortion #DDoS #Bitcoin #OSINT #Maltego #CTI #HaveIBeenPwned #Blockchain #ThreatIntelligence #Segurança #EngenhariaSocial #VazamentoDeDados #ArmadaCollective #GovCERT #Cloudflare
```

---

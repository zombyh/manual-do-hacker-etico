## 📘 Resumo:  Coleta de Informações via OSINT

## 📌 Visão Geral da Aula
- **Disciplina**: Inteligência de Ameaças Cibernéticas  
- **Aula 4**: Coleta de informações via OSINT  
- **Objetivos**:
  - Definir OSINT (Open Source Intelligence)
  - Descrever ferramentas de coleta de informações
  - Aplicar técnicas e ferramentas em um caso real

---

## 🔎 O que é OSINT?
- **OSINT**: Inteligência de Fontes Abertas  
- Informações publicamente disponíveis na internet  
- Passa pelo ciclo de vida do CTI: coleta, análise e disseminação  
- Fontes: portais de notícias, blogs, GitHub, Pastebin, Shodan, etc.

---

## 🛠️ Como o OSINT é Utilizado?
- Depende dos requisitos definidos no planejamento do CTI  
- Atende a diferentes áreas da organização  
- Exemplos de aplicação:
  1. **Exposição de dados da organização**
  2. **Exploits para vulnerabilidades recentes**
  3. **Informações desconhecidas sobre o estado da rede**

---

## 📂 Casos de Uso e Ferramentas

### 1. Exposição de Dados da Organização
- **Cenário**: Código-fonte ou documentação exposta no GitHub  
- **Ferramenta**: `gitformant.py`  
  - Busca por palavras-chave em repositórios públicos  
  - Exemplo: `python gitformant.py "empresa.br"` → 500 resultados

### 2. Vazamentos em Pastebin
- **Pastebin**: Site para compartilhamento rápido de texto  
- Usado para vazamentos de dados, códigos, cartões, etc.  
- **Ferramentas**:
  - **Pastehunter**: Coleta automática com regras YARA  
  - **Stumbler**: Interface web para buscas e armazenamento

#### Exemplo de Regra YARA para E-mails:
```yara
rule email_filter {
    strings:
        $email_add = /\b[\w-]+(\.[\w-]+)*@[\w-]+(\.[\w-]+)*\.[a-zA-Z-]+[\w-]\b/
    condition:
        #email_add > 20
}
```

### 3. Estado da Rede Exposta
- **Cenário**: Servidores de teste esquecidos online  
- **Ferramenta**: **Shodan**  
  - Scanner passivo de dispositivos conectados à internet  
  - Exemplo: Rede `186.192.80.0/20` da Globo  
    - 340 hosts  
    - Portas abertas: 80, 443, 5060 (SIP), 53 (DNS)  
    - Servidor mais comum: Nginx

#### Exemplo de Banner Shodan (SIP):
```
SIP/2.0 200 OK
User-Agent: Yealink VC400 30.23.0.20
```

---

## 🔧 Ferramentas de OSINT Utilizadas
- **nslookup**: Resolução de DNS  
- **whois**: Consulta de blocos de IP e ASN  
- **Shodan**: Busca por serviços e dispositivos expostos  
- **Gitformant**: Busca no GitHub por dados sensíveis  
- **Pastehunter**: Monitoramento de vazamentos no Pastebin

---

## ✅ Perguntas de Revisão (Com Respostas)

1. **OSINT representa informações que podem ser adquiridas livremente na internet.**  
   → **a) Verdadeiro**

2. **O que podemos encontrar com OSINT?**  
   → **e) Todas as alternativas estão corretas**

3. **Pastebin permite postagens anônimas com tempo de vida variável.**  
   → **a) Certo**

4. **nslookup e whois são ferramentas de OSINT.**  
   → **a) Certo**

5. **gitformant.py busca informações no:**  
   → **c) Github**

---

## 📚 Referências e Exploração
- **GitHub**: Netflix-Skunkworks/Scumbir, kevtheermit/PasteHunter  
- **Shodan**: https://www.shodan.io  
- **YARA**: https://virustotal.github.io/yara/  
- **Leituras sugeridas**:
  - *YARA in a nutshell*
  - *YARA: Simple and Effective Way to Dissecting Malware*

---

## 🧠 Conceitos-Chave
- **OSINT**: Inteligência de fontes abertas  
- **YARA**: Linguagem para criação de regras de identificação  
- **Shodan**: Motor de busca para dispositivos conectados  
- **Pastebin**: Plataforma de compartilhamento de texto  
- **GitHub**: Repositório de código-fonte

---

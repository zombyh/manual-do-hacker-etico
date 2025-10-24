
# 📘 Resumo para Estudo: Ameaças e Vulnerabilidades em Segurança da Informação

## 1. Conceitos Fundamentais

### ✅ Ativos
- **Tangíveis**: Podem ser medidos (ex.: servidores, dados, colaboradores).
  - **Lógicos**: Informações, softwares, algoritmos.
  - **Físicos**: Equipamentos, infraestrutura.
  - **Humanos**: Colaboradores, prestadores de serviço.
- **Intangíveis**: Difíceis de medir (ex.: imagem da empresa, marca).

### ✅ Ameaça
- Qualquer evento ou ação que possa causar dano a um ativo.
- Ex.: incêndio, hacker, enchente, phishing.

### ✅ Vulnerabilidade
- Fraqueza em um ativo ou controle que pode ser explorada por uma ameaça.
- Ex.: senha fraca, sistema desatualizado, falta de backup.

### ✅ Controle (Medida de Proteção)
- Ferramentas, processos ou metodologias usadas para proteger ativos.
- Ex.: firewalls, criptografia, treinamento, backups.

---

## 2. Classificação das Ameaças

### 🔹 Por Tipo de Ativo Afetado
- **Confidencialidade**: Acesso não autorizado.
- **Integridade**: Alteração indevida de dados.
- **Disponibilidade**: Interrupção do serviço.

### 🔹 Por Vetor de Ataque
- **Física**: Enchente, incêndio, furto.
- **Lógica**: Ataque de negação de serviço, vírus.
- **Humana**: Phishing, erro de colaborador.
- **Não Humana**: Desastres naturais, falha de infraestrutura.

### 🔹 Por Origem (Subclassificação das Não Humanas)
- **Desastres Naturais**: Enchentes, tempestades.
- **Problemas de Infraestrutura**: Falha elétrica, superaquecimento.

---

## 3. Técnicas de Ataques Cibernéticos

### 🚨 Ataques de Negação de Serviço (DoS/DDoS)
- Objetivo: Tornar um serviço indisponível.
- Exemplos:
  - **Ping of Death**: Pacotes ICMP grandes.
  - **SYN Flood**: Explora handshake TCP.
  - **UDP Flood**: Envio massivo de pacotes UDP.

### 🚨 Engenharia Social
- Explora a psicologia humana para obter informações.
- Exemplos:
  - **Phishing**: E-mails falsos.
  - **Chupa-cabra**: Clonagem de cartões.
  - **Trashing/Dumpster Diving**: Busca no lixo por informações.

### 🚨 Defacement (Pichação de Sites)
- Alteração não autorizada de sites.
- Motivação: exibicionismo, protesto.

### 🚨 Botnets
- Redes de dispositivos infectados (zumbis) controlados por um hacker.
- Usadas para: DDoS, envio de spam, mineração de criptomoedas.

### 🚨 Outras Técnicas
- **IP Spoofing**: Falsificação de endereço IP.
- **Pharming/DNS Poisoning**: Redirecionamento para sites falsos.
- **Session Hijacking**: Sequestro de sessão de usuário.
- **Quebra de Senhas**: Força bruta, rainbow tables.

---

## 4. Malwares (Softwares Maliciosos)

| Tipo               | Descrição                                                                 |
|--------------------|---------------------------------------------------------------------------|
| **Vírus**          | Precisam de um hospedeiro para se propagar.                               |
| **Worm**           | Auto-replicante, propaga-se pela rede.                                   |
| **Trojan**         | Disfarça-se como software legítimo.                                       |
| **Spyware**        | Monitora atividades do usuário (ex.: keylogger).                         |
| **Adware**         | Exibe propagandas indesejadas.                                           |
| **Ransomware**     | Criptografa dados e exige resgate (ex.: WannaCry).                       |
| **Sniffers**       | Capturam tráfego de rede.                                                |
| **Port Scanners**  | Varrem portas abertas em sistemas.                                       |

---

## 5. Controles e Mitigações

### 🔒 Controles Gerais
- **Senhas fortes** e autenticação multifatorial.
- **Criptografia** de dados em trânsito e em repouso.
- **Backups** regulares e testes de recuperação.
- **Firewalls**, IDS/IPS.
- **Treinamento** de usuários contra engenharia social.
- **Redundância** de sistemas e links.

### 🔒 Controles Específicos
- **Anti-DDoS**: Serviços de mitigação.
- **Antivírus/Antimalware**.
- **Atualizações** e patches de sistemas.
- **Políticas de descarte** seguro de informações.

---

## 6. Exemplos Clássicos Citados

- **Apple e Steve Jobs**: Exemplo de ativo humano e impacto no valor de mercado.
- **11 de Setembro**: Ameaça física, humana, terrorista e de infraestrutura.
- **Zone-h.org**: Site que lista ataques de defacement (hall da fama de hackers).
- **WannaCry**: Ransomware que afetou sistemas globais.

---

## 7. Legislação e Normas Referenciadas

- **ISO/IEC 27002**: Código de prática para controles de segurança.
- **NIST SHS (Secure Hash Standards)**: Padrões de funções hash.

---

## 📌 Dicas para a Prova (Procergs)

- Foque em: **classificações de ameaças**, **tipos de malware**, **técnicas de engenharia social** e **controles de mitigação**.
- Entenda bem os conceitos de **confidencialidade, integridade e disponibilidade** (Tríade CIA).
- Revise casos reais como **WannaCry**, ** phishing**, **DDoS**.
- Pratique com questões de concursos anteriores sobre segurança da informação.

---

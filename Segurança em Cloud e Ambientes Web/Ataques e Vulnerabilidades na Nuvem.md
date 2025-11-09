## Resumo: Ataques e Vulnerabilidades na Nuvem

## 1. Introdução à Segurança na Nuvem

- A computação em nuvem oferece benefícios como elasticidade, provisionamento rápido e acesso amplo, mas também introduz riscos específicos de segurança.
- A segurança na nuvem depende do **modelo de serviço** (IaaS, PaaS, SaaS) e do **modelo de implantação** (pública, privada, híbrida).

---

## 2. Modelo de Responsabilidade Compartilhada

- Conceito fundamental que define a divisão de responsabilidades entre **provedor de nuvem (CSP)** e **cliente**.
- A divisão varia conforme o modelo de serviço:

| Modelo | Responsabilidade do Cliente | Responsabilidade do Provedor |
|--------|-----------------------------|-------------------------------|
| **IaaS** | Aplicações, dados, SO, rede | Infraestrutura física |
| **PaaS** | Aplicações e dados | Plataforma, SO, infraestrutura |
| **SaaS** | Dados e acesso | Tudo (software, infraestrutura, plataforma) |

---

## 3. Riscos por Modelo de Serviço

### IaaS (Infrastructure as a Service)
- **Perda de controle** sobre hardware.
- **Ameaças internas** e **externas**.
- **Falta de habilidades técnicas** da equipe.
- **Custos operacionais** variáveis conforme o uso.
- **Conformidade** sob responsabilidade do cliente.

### PaaS (Platform as a Service)
- **Dependência da segurança do provedor**.
- **Risco de violação de dados**.
- **Problemas de interoperabilidade**.
- **Backdoors persistentes** em aplicações.
- **Compartilhamento de recursos** pode levar a vazamentos.

### SaaS (Software as a Service)
- **Transferência de controle** para o provedor.
- **Dependência total do provedor**.
- **Risco de acesso não autorizado** por ameaças internas.
- **Formatos proprietários** dificultam migração.
- **Vulnerabilidades em aplicações web e APIs**.

---

## 4. Superfície de Ataque na Nuvem

- Refere-se aos **pontos de entrada** e **vulnerabilidades** que podem ser explorados.
- Inclui:
  - Credenciais de usuário
  - Configurações inadequadas
  - APIs expostas
  - Falhas de software

### Superfície por Modelo:
- **IaaS**: Maior controle do cliente → maior responsabilidade na configuração.
- **PaaS**: Foco em desenvolvimento seguro e configuração da plataforma.
- **SaaS**: Menor controle → dependência da segurança do provedor.

---

## 5. Principais Vulnerabilidades na Nuvem

### Técnicas:
- **Vulnerabilidades de dia zero**: Falhas sem correção disponível.
- **Falta de patches**: Sistemas desatualizados.
- **Configurações inadequadas**: Exposição de recursos.
- **Credenciais fracas**: Senhas padrão ou fáceis.

### Gestão de Identidade e Acesso:
- **Contas privilegiadas** mal gerenciadas.
- **Falta de princípio do menor privilégio**.

### Interfaces e APIs:
- **APIs mal configuradas** são vetores comuns de ataque.
- Exemplos: endpoints sem autenticação, permissões excessivas.

### Desenvolvimento Inseguro:
- Falta de **Security Shift Left**.
- Uso de **recursos de terceiros** inseguros (código aberto, APIs externas).

### Serverless e Containers:
- **Configurações incorretas** em contêineres.
- **Compartilhamento de recursos** temporários pode vazar dados.

---

## 6. Atores de Ameaças

### Internos (Insiders):
- Funcionários, ex-funcionários, administradores.
- Motivações: roubo, vingança, vantagem competitiva, extorsão.
- Ações: vazamento, sabotagem, facilitar ataques externos.

### Externos:
- **For-profit attackers**: Buscam lucro (ransomware, fraude, venda de dados).
- **Nation state actors**: Espionagem, ataques a infraestrutura crítica.
- **Corporações concorrentes**: Espionagem industrial, sabotagem.
- **Script kiddies**: Baixo conhecimento técnico, motivação por curiosidade ou diversão.

---

## 7. Cyber Kill Chain na Nuvem

Modelo de 7 etapas para entender o ciclo de vida de um ataque:

1. **Reconhecimento**: Coleta de informações sobre o alvo.
2. **Armar**: Preparação de ferramentas e payloads.
3. **Entregar**: Entrega do ataque (phishing, watering hole).
4. **Explorar**: Exploração de vulnerabilidades.
5. **Instalar**: Instalação de malware ou backdoor.
6. **Comando e Controle (C2)**: Estabelecimento de comunicação com o atacante.
7. **Ações sob Objetivos**: Execução do objetivo final (roubo, destruição, persistência).

### Adaptação para Nuvem:
- Uso de serviços de nuvem para hospedar payloads.
- Exploração de APIs públicas e configurações inadequadas.
- Persistência em ambientes dinâmicos e escaláveis.

---

## 8. Conclusão e Recomendações

### Principais Aprendizados:
- Compreensão dos **modelos de serviço** e **responsabilidade compartilhada**.
- Identificação de **vulnerabilidades técnicas e humanas**.
- Reconhecimento de **atores de ameaças** e suas motivações.
- Aplicação do modelo **Cyber Kill Chain** para prevenção e resposta.

### Materiais de Aprofundamento:
- **MITRE ATT&CK® Cloud Matrix**
- **OWASP Cloud-Native Application Security Top 10**
- Referências: ENISA, CSA, NIST, Lockheed Martin.

---

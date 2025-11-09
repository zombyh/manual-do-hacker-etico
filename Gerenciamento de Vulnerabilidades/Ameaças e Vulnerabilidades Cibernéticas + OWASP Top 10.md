
## 📘 Resumo: Ameaças e Vulnerabilidades Cibernéticas + OWASP Top 10

### 1. **Ameaças Cibernéticas**
- **Definição**: Agentes ou condições que exploram vulnerabilidades para causar danos a sistemas ou organizações.
- **Classificação**:
  - **Humanas**:
    - Intencionais (ex.: hacker, funcionário mal-intencionado)
    - Não intencionais (ex.: erro humano, descuido)
  - **Não humanas/naturais** (ex.: raios, enchentes, furacões)

---

### 2. **Principais Ameaças Cibernéticas**
| Ameaça | Descrição | Exemplo |
|--------|-----------|---------|
| **Scan** | Varredura de rede para identificar portas e serviços abertos | Escaneamento de IP com Nmap |
| **Exploits** | Código que explora vulnerabilidades específicas (CVEs) | Exploit para Apache |
| **Sniffers** | Interceptação de tráfego de rede | Captura de emails não criptografados |
| **APT** | Ameaça persistente avançada para espionagem | Roubo de dados de produto não lançado |
| **DDoS** | Ataque de negação de serviço distribuído | Botnet sobrecarrega servidor |
| **Ataques a IoT** | Exploração de dispositivos com segurança fraca | Câmera com senha padrão vira zumbi |
| **Documentos Maliciosos** | Arquivos com código malicioso | PDF com malware enviado por email |
| **Engenharia Social** | Manipulação psicológica para obter informações ou acesso | Impersonação de auditor |
| **Ransomware** | Criptografia de arquivos seguida de resgate | WannaCry |
| **Man-in-the-Middle** | Interceptação e alteração de tráfego | Alteração de boleto bancário |
| **Phishing** | Email falso para roubo de credenciais | Falso email bancário |

---

### 3. **Estatísticas e Tendências (2020)**
- Ransomware: prejuízo de US$ 6 trilhões/ano (projeção 2021)
- Ameaças a aplicações web: crescimento de 52% em 2019
- Ataques sem malware: aumento de 40% para 51% (2018–2019)
- Phishing e engenharia social: maior sofisticação

---

## 🔐 OWASP Top 10 – Vulnerabilidades em Aplicações Web

### 1. **Injection (Injeção)**
- **Descrição**: Entrada maliciosa em formulários (ex.: SQL)
- **Exemplo**: `' OR 1=1 --` em campo de login

### 2. **Broken Authentication (Quebra de Autenticação)**
- **Descrição**: Falhas em sessões, senhas fracas, força bruta
- **Exemplo**: Uso de Hydra para quebra de senha

### 3. **Sensitive Data Exposure (Exposição de Dados Sensíveis)**
- **Descrição**: Dados trafegados ou armazenados sem criptografia
- **Exemplo**: Cartão de crédito em HTTP

### 4. **XXE (Entidades Externas XML)**
- **Descrição**: Processador XML mal configurado permite acesso a arquivos locais
- **Exemplo**: Inclusão de `file:///etc/passwd` em XML

### 5. **Broken Access Control (Quebra de Controle de Acesso)**
- **Descrição**: Acesso não autorizado a funcionalidades restritas
- **Exemplo**: Manipulação de URL para acessar nota fiscal de outro usuário

### 6. **Security Misconfiguration (Configurações Incorretas)**
- **Descrição**: Configurações padrão, contas default, versões expostas
- **Exemplo**: Servidor com banner mostrando versão do software

### 7. **XSS (Cross-Site Scripting)**
- **Descrição**: Script malicioso executado no navegador do usuário
- **Tipos**: Refletido (via URL) e Armazenado (no servidor)
- **Exemplo**: `<script>alert('Ataque XSS')</script>` na URL

### 8. **Insecure Deserialization (Desserialização Insegura)**
- **Descrição**: Manipulação de objetos serializados para elevar privilégios
- **Exemplo**: Alterar objeto de `"user"` para `"admin"`

### 9. **Using Components with Known Vulnerabilities**
- **Descrição**: Uso de bibliotecas/ferramentas com CVEs conhecidos
- **Exemplo**: CVE-2019-16222 (XSS em componente)

### 10. **Insufficient Logging & Monitoring**
- **Descrição**: Falta de registros ou demora na detecção de incidentes
- **Exemplo**: APT não detectado por meses

---

## 🧠 Conclusões Chave
- Ameaças evoluem rapidamente; prevenção > reação
- Conhecer vulnerabilidades comuns (OWASP) reduz superfície de ataque
- Equipes devem acompanhar relatórios de ameaças e atualizações de CVEs
- Segurança deve ser proativa, contínua e baseada em melhores práticas

---

## 🔍 Explore Mais
- **OWASP Top 10** (em português)
- Relatórios anuais de ameaças (CrowdStrike, SonicWall)
- Ferramentas: OWASP ZAP, Hydra, John the Ripper

---

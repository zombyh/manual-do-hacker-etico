
# 📘 Resumo: Boas Práticas em Segurança da Informação

## 1. Conceitos Fundamentais

### ✅ Segurança da Informação
- Conjunto de medidas para garantir a **confidencialidade**, **integridade** e **disponibilidade** das informações.
- Envolve pessoas, processos e tecnologia.

### ✅ Boas Práticas
- Ações preventivas e corretivas para minimizar riscos e proteger ativos informacionais.
- Baseadas em normas como a **ISO/IEC 27002**.

---

## 2. Gerenciamento de Senhas

### 🔐 Recomendações para Senhas Fortes
- Mínimo de **8 caracteres**.
- Uso de **letras maiúsculas, minúsculas, números e caracteres especiais** (@, #, $, etc.).
- **Não usar** nomes, números de matrícula, sequências óbvias ou informações pessoais.
- **Nunca compartilhar** senhas ou anotá-las em locais inseguros.
- **Alterar periodicamente** e não reutilizar senhas antigas.
- Usar **senhas diferentes** para diferentes serviços.

### ❌ Exemplos de Senhas Inválidas
- `K03Y0@` → Muito curta.
- `RTGE1598` → Apenas letras e números.
- `Jose_6523` → Contém nome do usuário.

### ✅ Exemplo de Senha Válida
- `Kut@4896` → Atende aos critérios.

---

## 3. Treinamento e Conscientização

### 🎯 Objetivo
- Capacitar colaboradores para identificar e evitar ameaças.
- Criar uma **cultura de segurança** na organização.

### 📌 Recomendações da ISO/IEC 27002
- Envolvimento da **diretoria** e de **todos os setores**.
- Desenvolvimento de **conteúdo contextualizado** (ex.: phishing, malware).
- **Diversidade de métodos**: treinamentos presenciais, online, simulados, quizzes.
- **Simulações de ataques** (ex.: phishing) para testar a eficácia.
- **Periodicidade**: treinamentos contínuos, não apenas na admissão.

### 📉 Exemplo de Ameaça: Phishing
- E-mails falsos que simulam instituições confiáveis.
- Objetivo: roubo de dados sensíveis (senhas, cartões).
- Prevenção: desconfiar de links e anexos suspeitos, verificar remetente.

---

## 4. Mecanismos de Proteção

### 🛡️ Princípios de Projeto Seguro
1. **Economia de mecanismo**: sistemas simples e fáceis de auditar.
2. **Padrão à prova de falhas**: acesso negado por padrão; permissões concedidas explicitamente.
3. **Mediação completa**: todos os acessos devem ser validados.
4. **Projeto aberto**: segurança não deve depender do segredo do design.
5. **Separação de privilégios**: exigir múltiplas chaves ou autorizações.
6. **Privilégio mínimo**: conceder apenas permissões necessárias.
7. **Compartilhamento mínimo**: reduzir interdependências entre sistemas.
8. **Aceitação psicológica**: interface amigável para incentivar o uso correto.

---

## 5. Controle de Acesso

### 🔒 Tipos de Controle de Acesso
- **DAC (Discricionário)**: dono do recurso define permissões.
- **MAC (Obrigatório)**: políticas centralizadas baseadas em rótulos.
- **RBAC (Baseado em Função)**: permissões atribuídas a funções, não a usuários.

### 🖥️ Recursos a Proteger
- Aplicativos
- Arquivos de dados
- Utilitários e sistema operacional
- Arquivos de senha
- Arquivos de log

### 📋 Procedimentos de Logon Seguro
- Limitar tentativas de acesso.
- Não revelar qual dado está incorreto (usuário ou senha).
- Registrar tentativas falhas.
- Exibir data/hora do último acesso válido.
- Encerrar sessões ociosas.

---

## 6. Política contra Vírus

### 🦠 Tipos Comuns de Malware
- Vírus de arquivo, boot, macro, mutante, polimórfico, Cavalo de Troia, etc.
- **Ransomware**: criptografa dados e exige resgate.

### 🛡️ Medidas de Proteção
- Antivírus instalado e **atualizado** em todos os dispositivos.
- Verificação de arquivos recebidos externamente.
- Escaneamento de dispositivos USB antes do uso.
- Não inicializar sistemas a partir de mídias externas.
- Uso de software de proteção em tempo real.

---

## 7. Sistemas de Backup

### 💾 Tipos de Backup
- **Completo**: copia todos os dados.
- **Incremental**: copia apenas alterações desde o último backup.
- **Diferencial**: copia alterações desde o último backup completo.

### ✅ Boas Práticas
- Definir **política de backup**: frequência, responsáveis, local de armazenamento.
- Testar **restauração** regularmente.
- Considerar **Disaster Recovery** para continuidade do negócio.

---

## 8. Criptografia e Certificado Digital

### 🔐 Tipos de Criptografia
- **Simétrica**: mesma chave para cifrar e decifrar (ex.: AES, DES).
- **Assimétrica**: par de chaves pública/privada (ex.: RSA).
- **Função Hash**: irreversível, para integridade (ex.: SHA, MD5).

### 📜 Certificado Digital
- Documento eletrônico que autentica identidades.
- Garante **autenticidade**, **integridade** e **não repúdio**.
- Emitido por **Autoridade Certificadora (AC)**.
- Contém: nome, chave pública, número de série, data de validade, assinatura da AC.

### 🇧🇷 ICP-Brasil
- Infraestrutura de Chaves Públicas Brasileira.
- Base legal: Medida Provisória 2.200-2/2001.
- Usado em: nota fiscal eletrônica, processos judiciais, compras governamentais, etc.

---

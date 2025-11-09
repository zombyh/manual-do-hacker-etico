## 🛡️ Controle de Acesso e Compartilhamento de Arquivos no Windows Server

## 📚 Visão Geral
Este material aborda a gestão de armazenamento, sistemas de arquivos, permissões de acesso e implementação de servidores de arquivos no **Windows Server 2019**, com ênfase em segurança e controle de acesso.

---

## 🗂️ 1. Gerenciamento de Discos

### 🔹 Tipos de Tabela de Partição
- **MBR (Master Boot Record)**:
  - Até 4 partições primárias.
  - Limite de 2 TB por partição.
  - Compatível com sistemas legados.

- **GPT (GUID Partition Table)**:
  - Até 128 partições.
  - Suporte a volumes acima de 2 TB (até 18 EB).
  - Exige suporte de BIOS UEFI.

> ✅ **Recomendação de segurança**: Use GPT para discos grandes e modernos.

---

### 🔹 Tipos de Discos
- **Disco Básico**:
  - Compatível com todas as versões do Windows.
  - Partições primárias e estendidas.

- **Disco Dinâmico**:
  - Permite volumes que abrangem múltiplos discos.
  - Suporte a recursos de tolerância a falhas (espelhamento, RAID-5).

> ⚠️ A conversão de dinâmico para básico **apaga todos os dados**.

---

### 🔹 Sistemas de Arquivos

| Sistema | Segurança | Tamanho Máximo | Uso Recomendado |
|---------|-----------|----------------|------------------|
| **FAT/FAT32** | ❌ Sem segurança | 2 TB | Mídias externas |
| **exFAT** | ❌ Sem segurança | > 2 TB | Dispositivos multimídia |
| **NTFS** | ✅ Com ACLs, criptografia, auditoria | 256 TB | Volume de sistema, AD DS, VSS |
| **ReFS** | ✅ Integridade, resiliência, correção de erros | 1 YB | Hiper-V, arquivamento, grandes volumes |

> 🚫 **Nunca use FAT/FAT32 em servidores**.

---

### 🔹 Tamanho do Setor (Unidade de Alocação)
- Ajuste o tamanho do cluster conforme o tipo de arquivo.
- Exemplo: Banco de dados com registros de 8 KB → use unidade de 8 KB.
- Reduz fragmentação e melhora desempenho.

---

## 🔐 2. Permissões em Pastas e Arquivos

### 🔸 Permissões NTFS vs. Compartilhamento
- **NTFS**: Controla acesso local e remoto.
- **Compartilhamento**: Controla acesso via rede.
- A permissão **mais restritiva** prevalece.

> 🛡️ Use **NTFS** para segurança granular.

---

### 🔸 Permissões Básicas NTFS
| Permissão | Pasta | Arquivo |
|-----------|-------|---------|
| **Controle Total** | Todas as ações | Todas as ações |
| **Modificar** | Excluir pasta | Modificar/excluir arquivo |
| **Ler e Executar** | Navegar + ler | Ler + executar |
| **Listar Conteúdo** | Ver nomes de arquivos | - |
| **Ler** | Ver conteúdo | Ler arquivo |
| **Escrever** | Criar arquivos/pastas | Sobrescrever arquivo |

---

### 🔸 Permissões Avançadas NTFS (14 no total)
- Incluem:
  - `Traverse Folder / Execute File`
  - `List Folder / Read Data`
  - `Create Files / Write Data`
  - `Delete Subfolders and Files`
  - `Take Ownership`
  - `Change Permissions`
  - Entre outras.

> 🧩 Use permissões avançadas para controle granular (ex.: impedir exclusão, mas permitir escrita).

---

## 📡 3. Servidor de Arquivos e SMB

### 🔹 Protocolo SMB (Server Message Block)
- Versões:
  - **SMB 1.0**: Vulnerável ❌ – desative se possível.
  - **SMB 3.1.1**: Suporte a AES-128, SHA-512, pré-autenticação ✅.

#### Recursos do SMB 3.x:
- Criptografia de ponta a ponta
- Transparent Failover
- SMB Multichannel
- SMB Direct (RDMA)
- Leasing de diretório

---

### 🔹 Perfis de Compartilhamento SMB

| Perfil | Enumeração por Acesso | Cache | Criptografia | Cotas | Uso |
|--------|------------------------|-------|--------------|-------|-----|
| **Rápido** | Sim | Sim | Sim | Não | Geral |
| **Avançado** | Sim | Sim | Sim | Sim | Com recursos extras |
| **Aplicativos** | Não | Não | Sim | Não | Hyper-V, Bancos de Dados |

> ✅ Para Hyper-V: use perfil **Aplicativos**.

---

### 🔹 Gerenciamento via PowerShell
- Módulo: `SmbShare`
- Comandos úteis:
  - `Get-SmbShare`
  - `New-SmbShare`
  - `Get-SmbSession`
  - `Set-SmbBandwidthLimit`
  - `Get-Command -Module SmbShare`

---

## ✅ Conclusão

### 🧩 Pontos-Chave para Segurança da Informação:
1. Use **NTFS ou ReFS** para controle de acesso e auditoria.
2. Evite **SMB 1.0**.
3. Combine **permissões de compartilhamento e NTFS** – a mais restritiva vale.
4. Use **GPT** para discos modernos e grandes.
5. Ajuste o **tamanho do setor** conforme a aplicação.
6. Prefira **ReFS** para cargas de trabalho críticas e grandes volumes.
7. Monitore sessões e arquivos abertos via `Get-SmbSession` e `Get-SmbOpenFile`.

---

### 📌 Recomendações Práticas:
- Implemente **espelhamento (RAID-1)** ou **RAID-5** para tolerância a falhas.
- Use **criptografia SMB** em redes não confiáveis.
- Habilite **enumeração baseada em acesso** para ocultar pastas não autorizadas.
- Documente e revise permissões regularmente.

---

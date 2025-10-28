## 📘 Resumo: Sistema de Arquivos no Linux

## 📌 Visão Geral
- **Sistema de Arquivos**: Estrutura lógica que organiza e gerencia dados em dispositivos de armazenamento.
- **Propósito**: Garantir persistência de dados, permitir acesso concorrente e organizar arquivos e diretórios.
- **Foco no Linux**: Estudo da implementação, ferramentas e gerenciamento no SO Linux.

---

## 🧠 Módulo 1: Implementação de Sistemas de Arquivos

### [[Arquivos]]
- Unidade lógica de informação.
- Tipos:
  - **Regulares**: Dados do usuário (texto ou binário).
  - **Diretórios**: Estrutura do sistema.
  - **Especiais**: Dispositivos (bloco ou caractere).
- Estruturas possíveis:
  - Sequência de bytes desestruturada (Linux e Windows).
  - Sequência de registros (tamanho fixo ou variável).

### [[Diretórios]]
- Organizam arquivos logicamente.
- Estruturas:
  - **Nível único** (não usado mais).
  - **Dois níveis** (diretório mestre + por usuário).
  - **Hierárquico em árvore** (adotado atualmente).
- Caminhos: absolutos e relativos.

### [[Métodos de Acesso]]
- **Sequencial**: Em ordem.
- **Aleatório/Direto**: Acesso direto a qualquer registro.
- **Indexado**: Usa índice para localização.

### [[Implementação em Disco]]
- **Partições**: Divisões lógicas do disco.
- **Superbloco**: Contém parâmetros do sistema de arquivos.
- **i-nodes**: Metadados do arquivo (localização, permissões, etc.).
- **Mapas de bits**: Controle de blocos livres.

### [[Alocação de Espaço]]
- **Contígua**: Arquivos em blocos sequenciais → fragmentação.
- **Lista Encadeada**: Blocos ligados por ponteiros → fragmentação de arquivos.
- **Lista Encadeada com Índice (FAT)**: Tabela de alocação em memória.
- **i-nodes (Indexada)**: Tabela por arquivo; eficiente para muitos arquivos abertos.

### [[Cache]]
- Objetivo: Reduzir acesso ao disco.
- Estratégias:
  - **Write-through**: Grava imediatamente no disco.
  - **Write-back**: Grava posteriormente (mais rápido, mas arriscado).

---

## 🐧 Módulo 2: Sistema de Arquivos do Linux

### [[Virtual File System (VFS)]]
- Camada que unifica diferentes sistemas de arquivos.
- Objetos principais:
  - `i-node`, `arquivo`, `superbloco`, `dentry`.

### [[Ext2]]
- Layout:
  - Bloco de inicialização → Grupos de blocos → Superbloco → Descritor → Mapas de bits → i-nodes → Dados.
- i-node: Armazena metadados e endereços dos blocos.

### [[Journaling (Ext3)]]
- Registra transações em diário antes de aplicar ao disco.
- Vantagem: Recuperação rápida após falhas.

### [[Partições e Dispositivos]]
- Identificação: `/dev/sda1`, `/dev/hdb`, etc.
- **Particionamento**: Divisão do disco em seções.
- **Formatação**: Criação da estrutura do sistema de arquivos.
- **Montagem**: Integração à árvore de diretórios.

### [[Comandos de Gerenciamento]]
- `fsck`: Verifica e corrige sistemas de arquivos.
- `df`: Exibe espaço em disco.
- `lsblk`: Lista dispositivos de bloco.

---

## 💻 Módulo 3: Ferramentas de Gerenciamento no Linux

### [[Comandos de Diretório]]
- `ls`: Lista conteúdo.
- `pwd`: Mostra diretório atual.
- `cd`: Altera diretório.
- `mkdir`: Cria diretórios.
- `rmdir`: Remove diretórios vazios.

### [[Comandos de Arquivo]]
- `rm`: Remove arquivos/diretórios.
- `cp`: Copia arquivos/diretórios.
- `mv`: Move ou renomeia.
- `cat`: Exibe conteúdo.
- `find`: Busca arquivos.

### [[Links]]
- **Simbólicos**: Atalhos para caminhos.
- **Hardlinks**: Entradas adicionais para o mesmo i-node.

---

## 📝 Módulo 4: Editores de Texto no Linux

### [[Editores vs. Processadores]]
- **Editores**: Texto puro (ASCII).
- **Processadores**: Formatação rica (ex: LibreOffice Writer).

### [[Vim]]
- **Modal**: Comando e edição.
- Comandos úteis:
  - `i` (inserir), `Esc` (voltar), `:wq` (salvar e sair), `dd` (apagar linha).

### [[Nano]]
- **Simples**: Sem modos; comandos visíveis.
- Exemplo: `Ctrl+O` (salvar), `Ctrl+X` (sair).

### [[Gedit]]
- **Grágico**: Editor do GNOME.
- Ideal para uso com interface gráfica.

---

## ✅ Conclusão
- Sistemas de arquivos são essenciais para organização e persistência de dados.
- Linux oferece flexibilidade com suporte a múltiplos sistemas de arquivos via VFS.
- Ferramentas de linha de comando e editores são vitais para administração.

---

## 🔗 Explore +
- **LVM** (Gerenciador de Volumes Lógicos)
- **Listas de Controle de Acesso (ACL)**
- **Distrowatch** e **LibreOffice**

---

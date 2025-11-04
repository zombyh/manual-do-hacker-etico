
## 📘 **Resumo: Administração e Configurações Essenciais do Linux**

### **Módulo 1: Gerenciamento de Arquivos e Diretórios**

#### 📁 Estrutura do Sistema de Arquivos
- Hierarquia única, iniciando em `/` (diretório raiz).
- Caminhos absolutos (começam com `/`) e relativos (baseados no diretório atual).
- Exemplo: `/etc/network/interfaces` (absoluto) vs `network/interfaces` (relativo a `/etc`).

#### 🗂️ Principais Diretórios (FHS)
| Diretório | Função |
|-----------|--------|
| `/bin` | Executáveis essenciais |
| `/etc` | Arquivos de configuração |
| `/home` | Diretórios dos usuários |
| `/var` | Logs e bancos de dados |
| `/tmp` | Arquivos temporários |
| `/proc` | Informações do sistema e processos |

#### 📄 Tipos de Arquivos
- **Regular**: Dados comuns
- **Diretório**: Lista de arquivos
- **Link simbólico**: Atalho para outro arquivo
- **Dispositivo**: Representa hardware

#### 🛠️ Comandos Básicos
| Comando | Função |
|---------|--------|
| `ls` | Lista arquivos |
| `cd` | Muda diretório |
| `mkdir` | Cria diretório |
| `rm` | Remove arquivos/diretórios |
| `cp` | Copia arquivos |
| `mv` | Move/renomeia arquivos |
| `find` | Busca arquivos |

#### 🔗 Links
- **Hardlink**: Várias entradas para o mesmo i-node (mesmo dispositivo).
- **Link simbólico**: Atalho que referencia o caminho do arquivo.

---

### **Módulo 2: Processos e Gerenciamento de Pacotes**

#### ⚙️ Processos
- **PID**: Identificador único do processo.
- **PPID**: PID do processo pai.
- Estados: Executando, dormindo, parado, zumbi.

#### 🎛️ Comandos de Processos
| Comando | Função |
|---------|--------|
| `ps` | Lista processos |
| `top` | Monitora processos em tempo real |
| `kill` | Envia sinal a processo |
| `pstree` | Mostra árvore de processos |

#### 🧩 Gerenciamento de Pacotes (Debian)
- **dpkg**: Ferramenta base para instalação de pacotes `.deb`.
- **APT**: Resolve dependências automaticamente.

| Comando | Função |
|---------|--------|
| `apt update` | Atualiza lista de pacotes |
| `apt upgrade` | Atualiza pacotes instalados |
| `apt install` | Instala pacote |
| `apt remove` | Remove pacote |

---

### **Módulo 3: Usuários, Grupos e Permissões**

#### 👥 Arquivos de Controle
| Arquivo | Função |
|---------|--------|
| `/etc/passwd` | Dados públicos dos usuários |
| `/etc/shadow` | Senhas criptografadas |
| `/etc/group` | Grupos do sistema |
| `/etc/gshadow` | Senhas de grupos |

#### 👤 Comandos de Usuários e Grupos
| Comando | Função |
|---------|--------|
| `adduser` | Adiciona usuário |
| `passwd` | Altera senha |
| `usermod` | Modifica usuário |
| `chown` | Muda dono do arquivo |
| `chmod` | Altera permissões |

#### 🔐 Permissões
- **Tipos**: Leitura (r), Gravação (w), Execução (x).
- **Agrupamentos**: Dono, Grupo, Outros.
- **Modo Octal**:  
  - Exemplo: `chmod 755 arquivo` → Dono: rwx, Grupo: r-x, Outros: r-x.

---

### **Módulo 4: Editores de Texto**

#### ✏️ Vim (Modal)
- **Modo Comando**: Para executar ações.
- **Modo Inserção**: Para digitar texto.
- Comandos úteis:
  - `i` → Entra no modo de inserção.
  - `Esc` → Volta ao modo de comando.
  - `:wq` → Salva e sai.
  - `:q!` → Sai sem salvar.

#### ✏️ Nano (Simples)
- Interface intuitiva, sem modos.
- Atalhos exibidos na tela:
  - `Ctrl + O` → Salvar
  - `Ctrl + X` → Sair
  - `Ctrl + G` → Ajuda

#### ✏️ Gedit (Graphical)
- Editor gráfico do GNOME.
- Ideal para uso com interface gráfica.

---

### ✅ **Conceitos-Chave para Revisão**
- Sistema de arquivos único a partir de `/`.
- Processos são identificados por PID e podem ser controlados com sinais.
- Pacotes no Debian usam `dpkg` e `APT`.
- Permissões usam modelo: Dono-Grupo-Outros (ex: rwxr-xr--).
- Vim é modal; Nano é mais simples; Gedit é gráfico.

---

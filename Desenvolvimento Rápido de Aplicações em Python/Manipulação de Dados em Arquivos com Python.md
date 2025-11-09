## 📘 Resumo: Manipulação de Dados em Arquivos com Python

### 1. Introdução
- A manipulação de arquivos é essencial em aplicações modernas.
- Envolve operações como abrir, fechar, ler, escrever e tratar exceções.
- Objetivos:
  - Identificar funções de manipulação de arquivos e strings.
  - Descrever exceções comuns e seu tratamento.

---

### 2. Funções de Manipulação de Arquivos

#### 🔹 Abrindo Arquivos
- Função: `open(caminho, modo)`
- Modos principais:
  - `r`: leitura (padrão)
  - `w`: escrita (sobrescreve)
  - `a`: append (adiciona ao final)
  - `b`: binário (ex: `rb`, `wb`)
  - `+`: leitura e escrita (ex: `r+`)

#### 🔹 Caminhos
- **Absoluto**: caminho completo (ex: `C:/pasta/arquivo.txt`)
- **Relativo**: caminho a partir do diretório atual (ex: `arquivo.txt`)

#### 🔹 Atributos do Objeto Arquivo
- `name`: nome do arquivo
- `mode`: modo de acesso
- `closed`: indica se o arquivo está fechado

#### 🔹 Fechando Arquivos
- Método: `arquivo.close()`
- Boa prática: usar `with open(...) as arquivo:` para fechamento automático.

#### 🔹 Lendo Conteúdo
- `read()`: retorna todo o conteúdo como string
- `readline()`: retorna uma linha por vez
- `readlines()`: retorna lista de linhas
- Iteração direta: `for linha in arquivo:`

#### 🔹 Escrevendo Conteúdo
- `write(texto)`: escreve uma string
- `writelines(lista)`: escreve uma lista de strings
- Modo `w`: sobrescreve o arquivo
- Modo `a`: adiciona ao final

---

### 3. Manipulação de Strings

#### 🔹 Métodos Comuns
- `strip()`: remove espaços e quebras de linha
- `split(separador)`: quebra string em lista
- `join(iterável)`: junta lista em string com conector
- `count(palavra)`: conta ocorrências de uma substring

#### 🔹 Formatação com f-strings
- Sintaxe: `f"Texto {expressão}"`
- Exemplo:
  ```python
  nome = "Maria"
  f"Olá, {nome.upper()}!"
  ```
- Formatação de números e datas:
  - `f"{valor:.2f}"` → 2 casas decimais
  - `f"{data:%d/%m/%Y}"` → data formatada

#### 🔹 Codificação com ZENIT POLAR
- Cifra de substituição simples: Z ↔ P, E ↔ O, N ↔ L, I ↔ A, T ↔ R
- Uso de `replace()` para codificação/decodificação

---

### 4. Tratamento de Exceções

#### 🔹 Bloco `try/except`
- Sintaxe:
  ```python
  try:
      # código crítico
  except FileNotFoundError:
      # tratamento específico
  except Exception as e:
      # tratamento genérico
  ```

#### 🔹 Exceções Comuns com Arquivos
- `FileNotFoundError`: arquivo não existe
- `PermissionError`: sem permissão de acesso
- `FileExistsError`: arquivo já existe
- `IsADirectoryError`: tentativa de remover diretório com `remove()`

---

### 5. Operações com Diretórios

#### 🔹 Criar e Remover
- `os.mkdir(caminho)`: cria diretório
- `os.rmdir(caminho)`: remove diretório vazio

#### 🔹 Listar Conteúdo
- `os.scandir(caminho)`: retorna iterável com `DirEntry`
- Atributos/métodos úteis:
  - `name`, `path`, `is_dir()`, `is_file()`, `stat()`

#### 🔹 Mover e Renomear
- `os.rename(origem, destino)`: renomeia ou move
- `shutil.move(origem, destino)`: move entre diretórios

---

### 6. Exemplos Práticos

#### 🔹 Processamento de Texto
- Ler → transformar (ex: maiúsculas) → sobrescrever

#### 🔹 Organização por Extensão
- Mover arquivos para pastas como `pdf/`, `txt/`, `img/`

#### 🔹 Codificação de Imagens com PIL
- Converter imagem para binário → manipular bytes → reconstruir imagem

---

### 7. Boas Práticas
- Sempre usar `with open()` para garantir fechamento.
- Tratar exceções específicas.
- Usar `os.path.join()` para caminhos multiplataforma.
- Preferir `f-strings` para formatação.

---

### 8. Módulos Úteis
- `os`: operações de sistema
- `shutil`: operações de alto nível (mover, copiar)
- `PIL` (Pillow): manipulação de imagens
- `gzip`: arquivos comprimidos

---

### 9. Referências
- Documentação oficial do Python
- Módulos: `os`, `shutil`, `PIL`, `gzip`

---

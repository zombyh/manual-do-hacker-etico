## O que é o SearchSploit?

SearchSploit é uma ferramenta de linha de comando para o Exploit Database (Exploit-DB) que permite pesquisar exploits localmente em seu sistema. Quando instalado via snap no Ubuntu, ele fornece uma maneira conveniente de acessar o banco de dados de exploits.

## Estrutura Básica de Comandos

```bash
searchsploit [opções] <termo_de_pesquisa>
```

## Comandos Principais

### 1. Pesquisa Básica
```bash
# Pesquisa por palavra-chave
searchsploit apache 2.4

# Pesquisa exata (entre aspas)
searchsploit "windows 10"

# Pesquisa com operador OR
searchsploit apache | grep -i local
```

### 2. Opções de Pesquisa

#### `-t` ou `--title` - Pesquisa apenas nos títulos
```bash
searchsploit -t apache
```

#### `-j` ou `--json` - Saída em formato JSON
```bash
searchsploit -j apache
```

#### `-o` ou `--overflow` - Quebra de linha para textos longos
```bash
searchsploit -o windows
```

#### `-c` ou `--case` - Pesquisa case-sensitive
```bash
searchsploit -c Linux
```

#### `-e` ou `--exact` - Pesquisa exata
```bash
searchsploit -e "Apache 2.4.49"
```

### 3. Filtros por Tipo

#### `-w` ou `--www` - Mostra URLs do Exploit-DB
```bash
searchsploit -w apache
```

#### `-p` ou `--path` - Mostra o caminho local do exploit
```bash
searchsploit -p 12345
```

#### Filtrar por plataforma
```bash
searchsploit windows remote
searchsploit linux local
searchsploit php webapps
```

### 4. Gerenciamento do Banco de Dados

#### `-u` ou `--update` - Atualiza o banco de dados
```bash
searchsploit -u
```

#### Verificar versão
```bash
searchsploit --version
```

#### Mostrar estatísticas
```bash
searchsploit --stats
```

#### Mostrar ajuda completa
```bash
searchsploit --help
```

### 5. Operações com Arquivos

#### Copiar exploit para diretório atual
```bash
searchsploit -m 12345
```

#### Copiar exploit para diretório específico
```bash
searchsploit -m 12345 /caminho/destino/
```

#### Ver conteúdo do exploit (sem copiar)
```bash
searchsploit -x 12345
```

### 6. Pesquisas Avançadas

#### Pesquisa com múltiplos termos
```bash
searchsploit linux kernel 3.2
```

#### Pesquisa por tipo de exploit
```bash
searchsploit dos windows
searchsploit shellcode linux
```

#### Pesquisa por autor
```bash
searchsploit -a "John Doe"
```

#### Pesquisa por data
```bash
searchsploit --date 2023
searchsploit --date "2023-01"
```

## Exemplos Práticos

### Exemplo 1: Pesquisa para servidor web específico
```bash
searchsploit -t apache 2.4.49
searchsploit -w --exact "Apache 2.4.49"
```

### Exemplo 2: Pesquisa para sistema operacional
```bash
searchsploit windows 10 local
searchsploit linux kernel 5.0 privilege
```

### Exemplo 3: Trabalhando com resultados
```bash
# Buscar e copiar exploit específico
searchsploit -m 49757

# Buscar e examinar sem copiar
searchsploit -x 12345

# Buscar e obter URL para download
searchsploit -w 12345
```

### Exemplo 4: Pipeline com outras ferramentas
```bash
# Filtrar resultados com grep
searchsploit apache | grep -i "remote"

# Contar resultados
searchsploit linux | wc -l

# Salvar resultados em arquivo
searchsploit windows > exploits_windows.txt
```

## Estrutura de Diretórios (quando instalado via snap)

Os exploits são geralmente armazenados em:
```
/snap/exploitdb/current/opt/exploitdb/
```

Principais subdiretórios:
- `exploits/` - Exploits organizados por plataforma
- `shellcodes/` - Códigos de shell
- `papers/` - Documentos e artigos
- `files/` - Arquivos relacionados

## Dicas Importantes

1. **Sempre atualize** o banco de dados antes de pesquisas importantes:
   ```bash
   searchsploit -u
   ```

2. **Use filtros específicos** para refinar resultados:
   ```bash
   searchsploit -t "wordpress plugin" --exact
   ```

3. **Examine o código** antes de usar:
   ```bash
   searchsploit -x <id_do_exploit>
   ```

4. **Use com responsabilidade** - apenas em ambientes autorizados para teste.

5. **Combine com outras ferramentas** para pentesting completo.

## 📘 Resumo: Automatizando Tarefas no Linux

## 1. Introdução à Automação
- **Objetivo**: Automatizar tarefas rotineiras em servidores e estações Linux
- **Ferramentas principais**:
  - **CRON**: para agendamento de tarefas
  - **Shell Script**: para criação de scripts automatizados
- **Vantagens**: eficiência, redução de erros, execução independente de usuários

---

## 2. CRON - Agendamento de Tarefas
### Conceitos Básicos
- **CRON**: serviço para execução automática de comandos em horários específicos
- **Multiusuário**: cada usuário possui configuração independente (crontab)
- **Comando para editar**: `crontab -e`

### Formato do Crontab
```
minuto hora dia_mês mês dia_semana comando
```
- **Minuto**: 0-59
- **Hora**: 0-23  
- **Dia do mês**: 1-31
- **Mês**: 1-12 (ou jan, feb, mar...)
- **Dia da semana**: 0-7 (0 e 7 = domingo)

### Caracteres Especiais
- `*`: qualquer valor
- `,`: múltiplos valores (ex: `1,15,30`)
- `-`: intervalo (ex: `1-5`)
- `/`: passo (ex: `*/2` = a cada 2 unidades)

### Exemplos Práticos
```bash
# Todos os dias às 17:30
30 17 * * * /bin/comando

# Dia 10 de cada mês às 17:30
30 17 10 * * /bin/comando

# Sextas-feiras às 17:30
30 17 * * 5 /bin/comando

# A cada 2 horas
0 */2 * * * /bin/comando
```

### CRON do Sistema
- Arquivo: `/etc/crontab`
- Diretórios organizados:
  - `/etc/cron.hourly`
  - `/etc/cron.daily` 
  - `/etc/cron.weekly`
  - `/etc/cron.monthly`

### Atenção Importante
- ❌ **Não usar `sudo` no crontab** (é interativo)
- ✅ Configurar diretamente no crontab do root se necessário privilégios

---

## 3. Shell Script - Fundamentos
### Estrutura Básica
```bash
#!/bin/bash
# Comentários são ignorados
comando1
comando2
```

### Primeiro Script
```bash
#!/bin/bash
date
```
- **Permissão de execução**: `chmod u+x script1`
- **Executar**: `./script1`

### Comandos Úteis
- `echo`: exibe texto
- `sleep`: pausa a execução
- `read`: aguarda entrada do usuário
- `clear`: limpa o terminal
- `exit`: termina o script com código de retorno

### Exemplo com Saída Formatada
```bash
#!/bin/bash
echo -e "Data: $(date +%d/%m/%Y)\nHora: $(date +%H:%M)"
```

---

## 4. Variáveis e Estruturas de Decisão
### Variáveis
```bash
VAR="valor"
echo "$VAR"
```

### Parâmetros
- `$0`: nome do script
- `$1`, `$2`, ...: parâmetros passados
- `${10}`, `${11}`: parâmetros acima de 9

### Operador IF
```bash
if [[ condição ]]
then
    # comandos
else
    # outros comandos
fi
```

### Comparadores Numéricos
- `-eq`: igual
- `-ne`: diferente  
- `-gt`: maior que
- `-lt`: menor que
- `-ge`: maior ou igual
- `-le`: menor ou igual

### Comparadores de Texto
- `=`: igual
- `!=`: diferente
- `-z`: vazio (zero caracteres)
- `-n`: não vazio

### Exemplo com Validação
```bash
#!/bin/bash
if [[ -z "$1" ]]
then
    echo "Parâmetro necessário"
    exit 1
fi
```

---

## 5. Operações Aritméticas
### Cálculos Básicos
```bash
(( resultado = A + B ))
echo $(( A + B ))
```

### Incremento
```bash
(( i++ ))
```

### Ponto Flutuante com `bc`
```bash
media=$(echo "scale=2; ($A+$B+$C)/3" | bc)
```

---

## 6. Estruturas de Repetição
### WHILE
```bash
i=1
while [[ $i -le 10 ]]
do
    echo "Contando... $i"
    (( i++ ))
done
```

### FOR
```bash
# Com lista fixa
for numero in 10 11 15 20
do
    echo "Número: $numero"
done

# Com arquivos
for arquivo in *
do
    echo "Arquivo: $arquivo"
done
```

### Controle de Loops
- `break`: interrompe o loop
- `continue`: pula para próxima iteração

---

## 7. Boas Práticas para Scripts no CRON
### Entrada de Dados
- ❌ Não depender de interação do usuário
- ✅ Usar arquivos ou parâmetros para dados variáveis

### Saída de Dados
- ✅ Salvar em arquivos de log
- ✅ Redirecionar saída no crontab:
```bash
30 19 * * 0 /home/user/script.sh >> /home/user/script.log
```

### Validação com Expressões Regulares
```bash
if [[ $numero =~ ^[0-9]{3}$ ]]
then
    echo "Número válido"
fi
```

---

## 8. Exemplo Prático Completo
### Script de Backup Automatizado
```bash
#!/bin/bash
# Backup diário às 20:00
0 20 * * * tar -czf /tmp/backup_$(date +%Y%m%d).tar.gz /home/user
```

### Script Interativo com Validação
```bash
#!/bin/bash
echo -n "Digite um número: "
read numero

if [[ $numero =~ ^[0-9]+$ ]]
then
    echo "Número válido: $numero"
else
    echo "Por favor, digite apenas números"
    exit 1
fi
```

---

## 9. Referências e Melhores Práticas
- **Documentação**: `man cron`, `man bash`
- **Expressões regulares**: para validações complexas
- **Arquivos de configuração**: separar dados do código
- **Logs**: sempre registrar execuções automáticas

---

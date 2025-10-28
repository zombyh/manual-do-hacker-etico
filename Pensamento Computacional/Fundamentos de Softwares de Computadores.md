## 📘 Resumo: Fundamentos de Softwares de Computadores

## 1. Introdução aos Softwares
- **Software**: Conjunto de instruções que determinam as ações executadas por um computador ou dispositivo eletrônico.
- **Função**: Transformar ações humanas em comandos executáveis pela máquina.
- **Exemplos**: Sistemas operacionais, navegadores, aplicativos, firmware.

---

## 2. Conceitos Básicos

### O que é Software?
- Conjunto de funções programadas que se materializam virtualmente.
- Não é físico, mas depende de hardware para execução.

### Como o Software é Executado?
- **CPU (Unidade Central de Processamento)**: Executa instruções de código de máquina (binário: 0 e 1).
- **Código de Máquina**: Linguagem de baixo nível, específica para cada família de CPUs (ex: Intel x86).
- **Memória RAM**: Armazena instruções do programa enquanto ele está em execução.

### Instruções de Alto e Baixo Nível
- **Baixo nível**: Código de máquina (ex: somar dois números).
- **Alto nível**: Linguagem próxima à humana (ex: `pixel.setRed(255)` em JavaScript).
- **Compilação**: Tradução de código de alto nível para código de máquina.

---

## 3. Programa e Execução

### O que é um Programa?
- Sequência de instruções de máquina armazenadas na RAM.
- Exemplo: Firefox.exe é um arquivo com milhões de instruções.

### Ciclo de Execução
1. **Carregamento**: Cópia do programa do disco (HD/SSD) para a RAM.
2. **Busca-Execução (Fetch Execute Cycle)**: CPU busca e executa uma instrução por vez, em sequência.
3. **Velocidade**: CPUs modernas executam bilhões de instruções por segundo (ex: 4 GHz).

### Controle de Fluxo
- **Instrução `goto`**: Altera a ordem de execução (ex: loops, condicionais `if`).
- **Estruturas de repetição e condicionais**: Implementadas com desvios na sequência de instruções.

---

## 4. Softwares Funcionais

### Sistema Operacional (SO)
- **Função**: Gerenciar hardware e software, intermediar interações do usuário.
- **Exemplos**: Windows, Linux, macOS, Android, iOS.
- **Multitarefa**: Permite execução simultânea de programas, cada um em sua própria área de memória (“área restrita”).

### Firmware
- **Função**: Programa inicial gravado no hardware, responsável pelo **boot**.
- **Exemplo**: BIOS em PCs.
- **Processo de Boot**:
  1. Teste de hardware (POST).
  2. Busca pelo SO no disco.
  3. Carregamento do SO na RAM.

---

## 5. Tipos de Linguagens de Programação

### Linguagens Compiladas
- **Processo**: Código-fonte → Compilador → Código de máquina (executável).
- **Vantagem**: Alta performance.
- **Exemplos**: C, C++.
- **Uso**: Uma vez compilado, o programa pode ser distribuído e executado diretamente.

### Linguagens Interpretadas (Dinâmicas)
- **Processo**: Código-fonte → Interpretador → Execução linha a linha.
- **Vantagem**: Desenvolvimento mais ágil.
- **Exemplos**: JavaScript, Python, Java.
- **Uso comum**: Scripts em navegadores.

### Tendências e JIT (Just-In-Time Compiler)
- **Tendência**: Uso de linguagens interpretadas para ganho de produtividade.
- **JIT**: Combina vantagens de compilação e interpretação – compila trechos frequentes em tempo de execução.
- **Exemplo**: Navegadores modernos usam JIT para JavaScript.

---

## 6. Código Aberto vs. Código Fechado

### Código Aberto
- Código-fonte disponível.
- Liberdade para modificar e redistribuir.
- Exemplo: Linux, Firefox.

### Código Fechado
- Código-fonte restrito ao fabricante.
- Dependência do fornecedor para correções e melhorias.
- Exemplo: Windows, iOS.

---

## 7. Conclusão
- Softwares são essenciais para a funcionalidade de dispositivos eletrônicos.
- Compreender sua lógica, execução e tipos de linguagem é fundamental para o pensamento computacional.
- A evolução das linguagens tende a priorizar a produtividade do programador, com uso de ferramentas como JIT.

---

## Referências Sugeridas
- CARVALHO, A.; LORENA, A. *Introdução à Computação*
- DALE, N.; LEWIS, J. *Ciência da Computação*
- FLANAGEN, D. *Javascript: o guia definitivo*
- Artigos e livros sobre software livre, mercado de TI e educação.

---

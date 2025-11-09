# Resumo: Coleta de Dados em Computação Forense

## 📌 Conceitos Introdutórios
- **Computação Forense**: Área da segurança da informação com rigor legal, cujo objetivo é produzir provas para o Fórum.
- **Investigação Digital**: Processo de desenvolver e testar hipóteses sobre ocorrências digitais.

## 🎯 Objetivos da Aula
- Descrever materiais a serem examinados e garantir a **cadeia de custódia**.
- Identificar tipos de materiais periciáveis.

## 💾 Evidência Digital
- Pode ser de qualquer tamanho (ex.: 1 byte, endereço IP).
- Pode residir em:
  - **Memória volátil**: RAM.
  - **Memória não volátil**: HDs, SSDs, pendrives, cartões de memória, etc.

## 🖥️ Dispositivos e Mídias
| Tipo de Dispositivo | Exemplos |
|----------------------|----------|
| **Portáteis** | Laptop, notebook, tablet, smartphone, wearable |
| **Desktops/Servidores** | Torre, servidor em rack, mainframe, all-in-one |
| **Armazenamento** | HD interno/externo, storage, pendrive, CD/DVD, cartão de memória |
| **Disfarçados** | Caneta espiã, relógio, canivete com memória |

> 🔍 Em servidores/storages grandes: muitas vezes faz-se a **cópia forense in loco** em vez de apreensão física.

## 🔧 Procedimento de Coleta (Guia PR/2020)
1. Verificar se o computador está desligado. Se não, **desconectar da tomada**.
2. Remover tampa do gabinete.
3. Localizar e identificar HD(s) (anotando portas SATA, etc.).
4. Remover HD com cuidado.
5. Verificar outras mídias no gabinete (CD, cartão, etc.).
6. Preencher formulário de remessa.
7. Identificar HD com etiqueta única.
8. Embalar em plástico bolha e lacrar.

> ❌ **NÃO apreender**: mouses, teclados, caixas de som (a menos que tenham memória embutida).

## ✅ Preservação da Evidência
- Cópia deve ser **bit a bit** (inclui dados apagados e espaços vazios).
- **Sistema preferencial**: Linux (não altera *timestamps*).
- **Ferramentas**: `dd`, `dc3dd`, duplicadores de mídia.
- **Verificação de integridade**: Calcular e comparar **HASH** (ex.: MD5, SHA-256) do original e da cópia.

## 📑 Cadeia de Custódia
- Garante a **integridade e rastreabilidade** da evidência.
- Começa na **notificação da ocorrência**.
- Registra todos os movimentos da prova, desde a coleta até a devolução.

### Formulário de Cadeia de Custódia deve conter:
- Especificação e quantidade do vestígio.
- Identificação numérica única.
- Local, data e responsável pela coleta.
- Assinaturas de quem entrega e recebe.
- Número do processo/UPJ.

## 🚨 Procedimentos em Caso de Crime Digital
### Fase Externa (Local do Crime):
a. Preservação do local  
b. Busca do vestígio  
c. Reconhecimento  
d. Fixação  
e. Coleta  
f. Acondicionamento  
g. Transporte  
h. Recebimento  

### Fase Interna (Laboratório):
a. Recepção e conferência  
b. Classificação e guarda  
c. Análise pericial  
d. Guarda e devolução  
e. Guarda para contraperícia  
f. Registro da cadeia de custódia  

## ⚠️ Cuidados no Manuseio
- Usar **EPI** e materiais específicos.
- Numerar vestígio de forma **inequívoca**.
- **Só o perito** pode abrir o recipiente — e deve registrar cada abertura.
- Guardar o **lacre rompido** dentro do novo recipiente.

## ❌ Erros Comuns
- Tentar “consertar” o computador antes de desligar.
- Usar softwares não homologados.
- Abrir arquivos do vestígio (altera *timestamp* e HASH).
- Usar ferramentas que modifiquem os dados originais.

---

## 📘 Resumo: Técnicas Antiforense – Parte II

### 🎯 Objetivos da Aula
- Abordar conceitos gerais sobre **criptografia**.
- Descrever os conceitos relacionados à **esteganografia**.
- Explanar as particularidades de **sistemas de arquivos (ADS)** e **sanitização de discos**.

---

### 🔐 Criptografia

#### Definição e Objetivos
- Ciência de codificar e decodificar dados para garantir:
  1. **Autenticação**: Comprovação da identidade.
  2. **Privacidade/Confidencialidade**: Apenas o destinatário pode ler.
  3. **Integridade**: Garantia de que a mensagem não foi alterada.
  4. **Não repúdio**: Prova de que o remetente enviou a mensagem.

#### Tipos de Criptografia
- **Criptografia Simétrica (Chave Secreta)**:
  - Mesma chave para criptografar e descriptografar.
  - Rápida, ideal para grandes volumes de dados.
- **Criptografia Assimétrica (Chave Pública)**:
  - Par de chaves: pública e privada.
  - Usada para troca de chaves e autenticação.
- **Funções Hash**:
  - Convertem dados em um valor fixo (hash).
  - Garantem integridade (ex: SHA-256, MD5).

---

### 🕵️ Esteganografia

#### Conceito
- Arte de ocultar mensagens, imagens ou arquivos dentro de outros meios (imagens, áudios, vídeos).
- Do grego: *steganos* (coberto) + *graphia* (escrita).

#### Objetivo
- Comunicar-se de forma **indetectável**, sem levantar suspeitas.
- Diferente da criptografia, que chama atenção por ser óbvia.

#### Aplicações
- **Marca d’água digital**: Proteção de direitos autorais.
- **Impressão digital (fingerprinting)**: Identificação de cópias individuais.
- **Comunicação secreta**: Ocultação de mensagens em arquivos comuns.

#### Como Funciona
- Dados são embutidos em arquivos de mídia (ex: imagem, áudio).
- Apenas remetente e destinatário sabem da existência.
- Ferramentas modernas permitem ocultação em diversos formatos.

---

### 📁 Sistemas de Arquivos: Alternate Data Streams (ADS)

#### O que é ADS?
- Recurso do sistema de arquivos **NTFS** do Windows.
- Permite que um arquivo tenha **múltiplos fluxos de dados**.
- O fluxo padrão é sem nome; fluxos adicionais são nomeados.

#### Uso Inocente vs. Malicioso
- **Inocente**: Armazenar metadados, comentários.
- **Malicioso**: Ocultar **malwares, rootkits, backdoors**.
- Exemplo: Ocultar `malicioso.exe` dentro de `calc.exe:malicioso.exe`.

#### Detecção e Análise
- **Comando `dir /r`** no Windows mostra fluxos alternativos.
- Ferramentas como **Streams** (Sysinternals) identificam ADS.
- **Não é visível** no Explorer ou com comandos comuns.

#### Exemplo Prático
```cmd
# Criar ADS
type malicioso.exe > calc.exe:malicioso.exe

# Executar arquivo oculto
start .\calc.exe:malicioso.exe
```

---

### 🧼 Sanitização de Discos

#### Problema da Exclusão Convencional
- Excluir um arquivo **não remove seus dados** do disco.
- Apenas **remove referências** (metadados) no sistema de arquivos.
- Dados permanecem recuperáveis até serem sobrescritos.

#### Técnicas de Sanitização
1. **Sobrescrita**:
   - Preencher o disco com dados aleatórios ou zeros.
   - Padrões: **DoD 5220.22-M** (EUA), **Gutmann** (35 passes).
2. **Desmagnetização**:
   - Usa campo magnético forte para apagar dados em mídias magnéticas.
3. **Destruição Física**:
   - Trituração, incineração, pulverização.

#### Recomendações
- Para uso doméstico/comercial: **sobrescrita com zeros** é suficiente.
- Para dados ultrassecretos: **destruição física** é recomendada.

---

### 🛡️ Resumo das Técnicas Antiforense (Parte II)

| Técnica | Objetivo | Exemplo |
|---------|----------|---------|
| Criptografia | Impedir leitura dos dados | TrueCrypt, BitLocker |
| Esteganografia | Ocultar existência dos dados | Ocultar texto em imagem |
| ADS (NTFS) | Esconder arquivos em fluxos alternativos | `arquivo.txt:oculto.exe` |
| Sanitização | Impedir recuperação de dados | Sobrescrita, desmagnetização |

---

### 📚 Referências
- ELEUTÉRIO, Pedro. *Desvendando a Computação Forense*.
- VELHO, Jesus Antonio. *Tratado de Computação Forense*.
- RAMALHO JÚNIOR; AMORIM. *Esteganografia: Integridade, confidencialidade e autenticidade*.

---

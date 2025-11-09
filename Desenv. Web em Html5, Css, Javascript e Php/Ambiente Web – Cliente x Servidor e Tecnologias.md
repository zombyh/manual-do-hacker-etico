## 🧱 **Resumo: Ambiente Web – Cliente x Servidor e Tecnologias**

### 1. **Arquitetura Cliente x Servidor**
- **Cliente**: Dispositivo (computador, smartphone, tablet) que solicita serviços via navegador.
- **Servidor**: Máquina robusta que processa requisições e retorna respostas.
- **Ciclo**: Requisição (request) → Processamento no servidor → Resposta (response).
- **Histórico**: Surgiu na Xerox PARC nos anos 1970, substituindo o modelo centralizado (mainframe).

#### Modelos de Camadas:
- **Duas camadas**: Cliente (interface + lógica) + Servidor (dados).
- **Três camadas**: Cliente (navegador) + Servidor Web + Servidor de Aplicação + Servidor de Banco de Dados.
- **Quatro camadas**: Separação ainda mais granular, com maior portabilidade e robustez.

---

### 2. **Comunicação no Ambiente Web**
- **Protocolo principal**: HTTP/HTTPS.
- **Fluxo**:
  1. Cliente envia requisição (ex: `Listar-TV.php`).
  2. Servidor processa e retorna resposta (ex: `Listagem-TV.php`).
- **Métodos de envio**:
  - `GET`: Dados anexados na URL.
  - `POST`: Dados no corpo da mensagem (mais seguro).

---

### 3. **Tecnologias do Lado Cliente (Client-Side)**

#### a) **HTML (HyperText Markup Language)**
- Estrutura páginas web.
- Tags semânticas: `<header>`, `<nav>`, `<main>`, `<footer>`.
- HTML5: Suporte a áudio, vídeo, armazenamento local, melhor semântica.

#### b) **CSS (Cascading Style Sheets)**
- Estilização e layout.
- Formas de inserção:
  - Inline: `style="..."`
  - Interno: `<style>...</style>`
  - Externo: `<link rel="stylesheet" href="estilo.css">`
- Unidades de medida:
  - Fixas: `px`
  - Flexíveis: `%`, `em`, `rem`

#### c) **JavaScript**
- Adiciona interatividade.
- Eventos: `onclick`, `onload`, etc.
- Pode se comunicar com o servidor via `XMLHttpRequest` ou `Fetch API`.

---

### 4. **Tecnologias do Lado Servidor (Server-Side)**

#### **PHP (Hypertext Preprocessor)**
- Linguagem de script open source.
- Executada no servidor → retorna HTML ao cliente.
- Sintaxe:
  - Variáveis: `$nome`
  - Acesso a dados do formulário: `$_POST["campo"]`
  - Saída: `echo "Texto";`
- Integração com bancos de dados e sistemas de arquivos.

#### Exemplo de código PHP:
```php
<html>
<body>
  Olá, <?php echo $_POST["nome"]; ?><br>
  Seja bem-vindo ao curso de <?php echo $_POST["curso"]; ?>
</body>
</html>
```

---

### 5. **Interface do Usuário e Design Responsivo**

#### a) **Interface (UI)**
- Ponte entre usuário e aplicação.
- Deve ser clara, usável e acessível.
- Importância da **Interação Humano-Computador (IHC)**.

#### b) **Design Responsivo**
- Adaptação do layout a diferentes tamanhos de tela.
- Técnicas:
  - Layout fluido (%, em, rem)
  - Media Queries:
    ```css
    @media (max-width: 360px) {
      .menu_lateral { display: none; }
    }
    ```
  - Mobile First: Desenvolver primeiro para mobile e depois para desktop.

#### c) **Design Adaptativo**
- Layouts pré-definidos para tamanhos específicos (ex: 360px, 720px).
- Menos flexível que o responsivo.

---

### 6. **Páginas Dinâmicas x Estáticas**

| Tipo | Características | Exemplo |
|------|-----------------|---------|
| Estática | HTML + CSS + JS fixos | Site institucional |
| Dinâmica | Conteúdo gerado sob demanda | Redes sociais, bankline |

- Páginas dinâmicas usam PHP (ou similar) + banco de dados para personalizar conteúdo.

---

### 7. **Atividades Práticas e Exemplos**

#### Exemplo de Formulário HTML + PHP:
- Frontend (HTML):
  ```html
  <form action="welcome.php" method="post">
    Nome: <input type="text" name="nome">
    E-mail: <input type="text" name="email">
    <input type="submit">
  </form>
  ```
- Backend (PHP – `welcome.php`):
  ```php
  Welcome <?php echo $_POST["nome"]; ?>
  Your email is <?php echo $_POST["email"]; ?>
  ```

---

### 8. **Conceitos-Chave para Revisão**
- **Cliente x Servidor**
- **Requisição e Resposta**
- **HTML, CSS, JavaScript**
- **PHP e Server-Side**
- **Design Responsivo e Mobile First**
- **Páginas Dinâmicas x Estáticas**

---

### 9. **Referências e Links Úteis**
- W3Schools (HTML, CSS, PHP)
- W3C – CSS Units
- Estatísticas de resolução de tela: StatCounter

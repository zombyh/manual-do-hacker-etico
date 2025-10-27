
## 📘 Resumo: **Interface Gráfica com Python + PostgreSQL (Tkinter + psycopg2)**

### 📌 Objetivos do Conteúdo:
- Desenvolver aplicações com interface gráfica (GUI) usando Python e Tkinter.
- Integrar operações CRUD com banco de dados PostgreSQL via psycopg2.
- Criar interfaces interativas e eficientes para manipulação de dados.

---

## 🧩 1. Frameworks e Bibliotecas para GUI em Python

### Principais opções:
- **Tkinter**: Biblioteca padrão do Python, simples e multiplataforma.
- **Flexx**: Usa tecnologia web para renderização (desktop e web).
- **Kivy**: Focado em aplicações multitoque e multiplataforma (mobile inclusive).
- **PyQt**: Rico em funcionalidades, usado em aplicações complexas.
- **wxPython**: Componentes nativos do sistema operacional.
- **PyAutoGUI**: Automação de mouse e teclado.
- **PySimpleGUI**: Camada simplificada sobre Tkinter, PyQt, etc.

> ✅ **Exemplo de código Tkinter:**
```python
import tkinter as tk
janela = tk.Tk()
janela.title("Minha App")
janela.mainloop()
```

---

## 🧱 2. Criação de Aplicação GUI com Tkinter

### Widgets Principais:
- `Button`, `Label`, `Entry`, `Text`, `Checkbutton`, `Radiobutton`, `Scale`, `Scrollbar`, `Message`, `Dialog`, `Combobox`, etc.

### Exemplo com `Label` e `Button`:
```python
import tkinter as tk

def clique():
    print("Botão pressionado!")

janela = tk.Tk()
tk.Label(janela, text="Olá, Tkinter!").pack()
tk.Button(janela, text="Clique", command=clique).pack()
janela.mainloop()
```

---

## 🗃️ 3. Interação com Banco de Dados (PostgreSQL + psycopg2)

### Operações CRUD:
- **C**reate: `INSERT`
- **R**ead: `SELECT`
- **U**pdate: `UPDATE`
- **D**elete: `DELETE`

### Conexão e Execução:
```python
import psycopg2

conn = psycopg2.connect(
    database="postgres",
    user="postgres",
    password="senha123",
    host="127.0.0.1",
    port="5432"
)
cur = conn.cursor()
cur.execute("SELECT * FROM AGENDA")
registros = cur.fetchall()
conn.commit()
conn.close()
```

---

## 🔄 4. Integração: GUI + Banco de Dados

### Exemplo de Aplicação Completa:
- Interface com Tkinter para entrada de dados.
- TreeView para exibição de registros.
- Botões para Inserir, Atualizar, Excluir e Consultar.

### Estrutura Básica:
```python
import tkinter as tk
import psycopg2

class App:
    def __init__(self, root):
        self.root = root
        self.conectar_banco()
        self.criar_widgets()

    def conectar_banco(self):
        self.conn = psycopg2.connect(...)
        self.cur = self.conn.cursor()

    def criar_widgets(self):
        # Labels, Entries, Buttons, Treeview
        pass

    def inserir_dados(self):
        # Lógica de INSERT
        pass

    def carregar_dados(self):
        # Lógica de SELECT e exibição
        pass

root = tk.Tk()
app = App(root)
root.mainloop()
```

---

## ✅ 5. Validação e Tratamento de Erros

### Uso de `try-except`:
```python
try:
    cur.execute("INSERT INTO tabela VALUES (%s)", (valor,))
    conn.commit()
except Exception as e:
    print("Erro ao inserir:", e)
    conn.rollback()
```

---

## 🧪 6. Geração de Dados Aleatórios com Faker

### Exemplo:
```python
from faker import Faker

fake = Faker('pt_BR')
nome = fake.name()
preco = round(fake.random_number(digits=5) / 100, 2)
```

---

## 📚 7. Explore Mais:
- Documentação oficial: [Tkinter](https://docs.python.org/3/library/tkinter.html), [psycopg2](https://www.psycopg.org/)
- Frameworks: Kivy, PyQt, wxPython, etc.
- Bancos: MySQL, SQLite, MongoDB (via PyMongo).

---

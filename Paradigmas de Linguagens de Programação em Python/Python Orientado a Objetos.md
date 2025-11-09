## 📘 Resumo: **Python Orientado a Objetos**

### **Módulo 1: Conceitos Fundamentais de POO**
- **Objetos**: Instâncias de classes que possuem **atributos** (estado) e **métodos** (comportamento).
- **Classes**: Modelos ou "plantillas" para criar objetos. Definem atributos e métodos comuns.
- **Encapsulamento**: Ocultação dos detalhes internos do objeto, expondo apenas uma interface controlada.
- **Herança**: Mecanismo que permite que uma classe herde atributos e métodos de outra.
- **Polimorfismo**: Capacidade de um método se comportar de maneira diferente em classes diferentes.

---

### **Módulo 2: Implementação em Python**
#### **Definição de Classes e Objetos**
- Sintaxe: `class NomeClasse:`
- Construtor: `__init__(self, ...)`
- Referência ao objeto: `self`

#### **Atributos e Métodos**
- Atributos públicos vs. privados (usando `__`).
- Uso de `@property` para controle de acesso.
- Métodos de classe (`@classmethod`) e estáticos (`@staticmethod`).

#### **Associação entre Objetos**
- **Agregação**: Relação "tem-um" onde objetos podem existir independentemente.
- **Composição**: Relação "parte-de" onde o objeto dependente não existe sem o principal.

---

### **Módulo 3: Herança e Polimorfismo em Python**
#### **Herança**
- Simples: `class Filha(Pai):`
- Múltipla: `class Filha(Pai1, Pai2):`
- Sobrescrita de métodos (`override`).

#### **Polimorfismo**
- Um mesmo método pode ter comportamentos diferentes em classes diferentes.
- Exemplo: `mover()` em `Carro` vs. `Avião`.

#### **Classes Abstratas**
- Não podem ser instanciadas.
- Usam `from abc import ABC, abstractmethod`.
- Métodos abstratos devem ser implementados nas subclasses.

#### **Tratamento de Exceções**
- Blocos `try`, `except`, `finally`.
- Criação de exceções personalizadas herdando de `Exception`.

---

### 📚 **Recomendações de Leitura**
- *Fluent Python* – Luciano Ramalho
- *Clean Code in Python* – Mariano Anaya
- *Learning Python Design Patterns* – Giridhar

---

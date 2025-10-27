
# 🚀 Resumo: Aplicando RAD – Desenvolvimento Rápido de Software

## 📌 Introdução à Metodologia RAD
- **RAD** = Desenvolvimento Rápido de Aplicações
- Foca em **prototipagem rápida**, **colaboração contínua** e **iterações**.
- Objetivos:
  - Reduzir tempo de desenvolvimento.
  - Aumentar flexibilidade.
  - Melhorar comunicação entre desenvolvedores e usuários.

---

## 🧩 Fases do RAD (Segundo Martin, 1991)
1. **Planejamento de Requisitos**
2. **Design do Usuário**
3. **Construção** (prototipagem)
4. **Transição** (testes, implantação, treinamento)

---

## 🧠 Engenharia de Requisitos no RAD

### ✅ Atividades (Pressman, 2011):
- **Elicitação**
- **Análise**
- **Documentação**
- **Validação**
- **Gerenciamento**

### 🛠️ Técnicas de Elicitação:
- Entrevistas (abertas/fechadas)
- Casos de uso
- Observação
- Grupos focais
- Brainstorming
- Prototipagem

### 🔁 Especificidades do RAD:
- Requisitos **evoluem** com o projeto.
- Priorização dinâmica a cada iteração.
- Uso de **sessões JAD** (*Joint Application Development*) para colaboração.

---

## 🏢 Modelagem de Negócios
- Objetivo: Mapear processos e interações do negócio.
- Técnica principal: **Diagramas de Casos de Uso (UML)**
- Elementos:
  - **Processos principais**
  - **Processos auxiliares**
  - **Processos de gerenciamento**

### 📌 Exemplo:
- Sistema de embarque em aeroporto:
  - Atores: Passageiro, Guia de turismo
  - Casos de uso: Check-in, Rastreio de segurança

---

## 🗃️ Modelagem de Dados
- Objetivo: Estruturar e organizar os dados do sistema.
- Níveis:
  1. **Conceitual** (entidades, atributos, relacionamentos)
  2. **Lógico** (estrutura, normalização)
  3. **Físico** (implementação no BD)

### 📌 Exemplo:
- Entidade: `Aluno`
- Atributos: nome, nota1, nota2, média, situação
- Relacionamento: “Escola tem vários Alunos”

---

## 🎨 Design de Interface no RAD
- Foco na **experiência do usuário (UX)** e **interface (UI)**
- Prototipagem contínua e iterativa
- Técnicas:
  - **Sketches** (rascunhos)
  - **Wireframes** (estrutura)
  - **Mockups** (design visual)
  - **Protótipos interativos** (funcionais)

### ✅ Princípios de Design:
- Previsibilidade
- Simplicidade
- Organização
- Moderação no uso de cores
- Controles próximos aos objetos
- Feedback ao usuário

---

## 🐍 Aplicação Prática com Python

### Exemplo 1: Sistema de Pedidos para Lanchonete
- **Tecnologias**: Python + Tkinter
- **Funcionalidades**:
  - Listar itens do menu
  - Adicionar itens ao pedido
  - Calcular total
  - Adicionar novos itens ao menu

### Exemplo 2: Sistema de Gestão Escolar
- **Tecnologias**: Python + Tkinter + Pandas + OpenPyXL
- **Funcionalidades**:
  - Cadastrar alunos e notas
  - Calcular média e situação (aprovado, recuperação, reprovado)
  - Salvar e carregar dados do Excel
  - Tela de login com níveis de acesso (aluno/professor)

---

## 🔁 Evolução do Sistema (Exemplo com Login)
- Dicionário de usuários:
  - Professor: acesso total
  - Aluno: apenas visualização das próprias notas
- Funcionalidades restritas por tipo de usuário

---

## 🧪 Testes e Validação
- Protótipos são validados com usuários.
- Feedback contínuo direciona iterações.
- Exemplo: Testar adição de itens, cálculo de totais, login.

---

## 🧰 Ferramentas e Frameworks Sugeridos
- **Python 3.8.5**
- **Spyder** (IDE)
- **Tkinter** (GUI)
- **Pandas** + **OpenPyXL** (manipulação de dados e Excel)

---

## 📚 Referências Principais
- Martin (1991) – *Rapid Application Development*
- Pressman (2011) – *Engenharia de Software*
- Kerr & Hunter (1994) – *Inside RAD*
- Alavi (1984) – Prototipagem em sistemas de informação

---

## 🎧 Conteúdo Complementar
- Podcasts e vídeos interativos sobre RAD
- Sites oficiais: Python, Microsoft (normalização de BD), LGPD

---

## 💡 Pontos-Chave para Revisão
- RAD é **iterativo e colaborativo**.
- Protótipos **evoluem para a versão final**.
- Modelagem de dados e negócios é **essencial**.
- Python é uma ferramenta **eficaz** para prototipagem rápida.
- A validação contínua com o usuário é **fundamental**.

---

## 📘 Resumo: Noções de Programação com Manipulação de Imagens

### 🎯 **Objetivo do Material**
Introduzir conceitos básicos de programação por meio da manipulação de imagens digitais, desenvolvendo habilidades de **pensamento computacional**: abstração, automação, reconhecimento de padrões, análise e decomposição.

---

## 🧱 **Módulo 1: Manipulação de Dados**

### 📌 Conceitos Chave
- **Manipulação singular de dados**: operações em um único dado por vez (ex: um pixel).
- **Pixel**: menor unidade de uma imagem digital.
- **Formato BMP**: formato de imagem bitmap.

### 🛠️ Instruções Básicas em JavaScript (simplificado)
```javascript
img = new SimpleImage("circulo.bmp"); // Carrega a imagem
img.setZoom(20);                      // Aplica zoom (0.5 = afastamento 2x)
print(img);                           // Exibe a imagem
```

### 🎨 Manipulação de Cores (RGB)
- `pixel.setRed(255)`
- `pixel.setGreen(255)`
- `pixel.setBlue(255)`
- Valores entre 0 e 255.

### ✅ Exemplo de Código para Modificar um Pixel
```javascript
img = new SimpleImage("circulo.bmp");
img.setZoom(20);
pixel = img.getPixel(4,4);  // Acessa pixel na posição (4,4)
pixel.setRed(255);          // Muda vermelho para máximo
print(img);
```

---

## 🔁 **Módulo 2: Estrutura de Repetição `for`**

### 📌 Por que Usar `for`?
- Permite manipular milhares de pixels com poucas linhas.
- Evita repetição manual de código.

### 🔁 Exemplo de Loop em Imagem
```javascript
img = new SimpleImage("passaro.jpg");
for (pixel : img) {
  pixel.setRed(0);
  pixel.setGreen(0);
  pixel.setBlue(0);
}
print(img);
```
- Resultado: imagem totalmente preta.

### 🎭 Canais de Cor
- **Canal Vermelho**: remove verde e azul.
- **Canal Verde**: remove vermelho e azul.
- **Canal Azul**: remove vermelho e verde.

---

## 🧮 **Módulo 3: Expressões em Código**

### 📌 O que São Expressões?
- Combinações de valores e operadores que produzem um resultado.
- Ex: `pixel.getRed() * 2`

### 🧩 Funções de Leitura de Cores
- `pixel.getRed()`
- `pixel.getGreen()`
- `pixel.getBlue()`

### ✨ Exemplo: Ajuste de Cor com Expressão
```javascript
pixel.setRed(pixel.getRed() * 0.7); // Reduz vermelho para 70%
```

### 🖼️ Conversão para Escala de Cinza
```javascript
media = (pixel.getRed() + pixel.getGreen() + pixel.getBlue()) / 3;
pixel.setRed(media);
pixel.setGreen(media);
pixel.setBlue(media);
```

---

## 🔀 **Módulo 4: Estrutura Condicional `if`**

### 📌 O que é `if`?
- Executa um bloco de código **apenas se** uma condição for verdadeira.

### 🎯 Exemplo: Pintar Apen Pixels Vermelhos de Cinza
```javascript
if (pixel.getRed() == 255 && pixel.getGreen() == 0 && pixel.getBlue() == 0) {
  pixel.setRed(120);
  pixel.setGreen(120);
  pixel.setBlue(120);
}
```

### 🧠 Exemplo Avançado: Detecção de Amarelo
```javascript
media = (pixel.getRed() + pixel.getGreen() + pixel.getBlue()) / 3;
if (pixel.getRed() > media && pixel.getGreen() > media) {
  // Ajusta para cinza
  pixel.setRed(media);
  pixel.setGreen(media);
  pixel.setBlue(media);
}
```

---

## 🧠 **Pensamento Computacional: Pilares**

1. **Abstração**: Foco no essencial (ex: cor e posição do pixel).
2. **Automação**: Código que executa tarefas automaticamente.
3. **Decomposição**: Quebrar problemas em partes menores.
4. **Reconhecimento de Padrões**: Identificar comportamentos comuns (ex: tons de amarelo).
5. **Análise e Avaliação**: Testar, ajustar e melhorar o código.

---

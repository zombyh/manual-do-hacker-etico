
# Resumo: Representação de Imagens em Computadores

## 1. Fundamentos de Pixels

### O que é um pixel?
- **Pixel** é o menor elemento de uma imagem digital.
- Cada pixel é um **quadrado de uma única cor**.
- Imagens são compostas por milhões de pixels.
- Quanto mais pixels, maior a **resolução** e mais próxima da realidade a imagem parece.

### Habilidades do Pensamento Computacional Usadas:
- **Decomposição**: quebrar a imagem em pixels.
- **Abstração**: focar nas características essenciais (formas, cores, padrões).

> Exemplo:  
> Imagem com 800×600 pixels = 480.000 pixels = 0,48 megapixels.

---

## 2. Grade de Pixels e Coordenadas
- Imagens são representadas como uma **grade bidimensional** de pixels.
- Cada pixel é identificado por coordenadas **(x, y)**:
  - **x**: coluna (a partir de 0)
  - **y**: linha (a partir de 0)
- Exemplo: Pixel (5,0) → coluna 6, linha 1.

---

## 3. Esquema de Cores RGB

### O que é RGB?
- **RGB** = Red (Vermelho), Green (Verde), Blue (Azul).
- Modelo **aditivo**: cores são criadas combinando luz.
- Cada cor (R, G, B) tem intensidade de **0 a 255**.

### Cores Principais no RGB:
- Preto: (0, 0, 0)
- Branco: (255, 255, 255)
- Vermelho: (255, 0, 0)
- Verde: (0, 255, 0)
- Azul: (0, 0, 255)
- Amarelo: (255, 255, 0)  
- Ciano: (0, 255, 255)  
- Magenta: (255, 0, 255)

> 💡 Com 8 bits por canal (R, G, B), temos:  
> \( 2^8 \times 2^8 \times 2^8 = 16,7 \) milhões de cores.

---

## 4. Esquema Grayscale (Escala de Cinza)

### O que é Grayscale?
- Imagens em **tons de cinza**, do preto ao branco.
- Cada pixel tem **apenas um valor de intensidade luminosa** (0 a 255).
- 0 = Preto | 255 = Branco

### Vantagens:
- Menos dados → processamento mais rápido.
- Ideal para:
  - Diagnósticos médicos (raio-X, ressonância)
  - Fotografia artística
  - Processamento de imagem

---

## 5. Comparação: RGB vs. Grayscale

| Característica       | RGB                          | Grayscale                    |
|----------------------|------------------------------|------------------------------|
| Componentes          | 3 (R, G, B)                  | 1 (intensidade)              |
| Valores por pixel    | 3 valores (0–255)            | 1 valor (0–255)              |
| Complexidade         | Alta                         | Baixa                        |
| Uso típico           | Telas, fotos, design         | Medicina, arte, processamento |

---

## 6. Conversão de RGB para Grayscale
- Fórmula comum:  
  \[
  \text{Gray} = \frac{R + G + B}{3}
  \]
- Exemplo:  
  RGB (200, 100, 50) → Gray = (200+100+50)/3 ≈ 117  
  Pixel resultante: (117, 117, 117)

---

## 7. Aplicações Práticas

### RGB:
- Fotografia e vídeo
- Design gráfico
- Interfaces de usuário

### Grayscale:
- Diagnóstico por imagem
- Reconhecimento de padrões
- Fotografia artística

---

## 8. Processamento de Imagens com Pensamento Computacional
- Ajustar brilho: aumentar todos os valores RGB em uma porcentagem.
- Escurecer: diminuir valores RGB.
- Converter para grayscale: simplifica análise e reduz custo computacional.

---

## 9. Exemplo de Código RGB para Cores Comuns

| Cor         | R    | G    | B    |
|-------------|------|------|------|
| Preto       | 0    | 0    | 0    |
| Branco      | 255  | 255  | 255  |
| Cinza       | 128  | 128  | 128  |
| Laranja     | 255  | 165  | 0    |
| Roxo        | 128  | 0    | 128  |
| Rosa        | 255  | 192  | 203  |

---

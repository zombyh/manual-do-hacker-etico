## 📘 Resumo: Fontes de OSINT – Inteligência de Ameaças Cibernéticas

## 📌 Visão Geral
Esta aula aborda **fontes de IOCs (Indicadores de Comprometimento)**, também conhecidas como **feeds de OSINT**, e as ferramentas utilizadas para coletar e analisar essas informações.

---

## 🎯 Objetivos
- Demonstrar como coletar **OSINT** a partir de diferentes feeds.
- Apresentar ferramentas para coleta de IOCs em fontes públicas.

---

## 🔍 O que são IOCs?
IOCs são evidências de atividades maliciosas, como:
- IPs
- Domínios
- URLs
- Hashes de arquivos

Esses indicadores são essenciais para relatórios de inteligência e proteção de redes.

---

## 📂 Fontes de IOCs

### 1. Empresas de Segurança
- Oferecem feeds pagos com IOCs validados e contextualizados.

### 2. Fontes Open Source (OSINT)
- Sites, blogs e organizações compartilham IOCs publicamente.
- Exemplo: **Resource Cyber Threat Intelligence Feed**

### 3. Honeypots Próprios
- Sistemas que simulam serviços reais para capturar ataques.
- Geram IOCs próprios a partir de logs de interações maliciosas.

---

## 🧠 Contexto em IOCs
- IOCs devem vir com **contexto claro**: data, origem, criticidade.
- Sem contexto, a análise pode ser ineficiente ou levar a falsos positivos.

---

## 🛠️ Exemplo Prático: VirusTotal
- Ferramenta para verificação de IOCs (URLs, IPs, hashes).
- Exemplo com domínio malicioso: `omegaconsultoriacontabill.com.br`
  - Detectado por 8/71 motores como malicioso.
- Uso via linha de comando com **VirusGoatl** (requer API key do VirusTotal).

---

## ⚠️ Cuidados com IOCs

### Idade do IOC
- IOCs antigos podem não ser mais relevantes.
- Exemplo: IOC de maio encontrado em logs de dezembro → necessidade de análise contextual.

### Infraestrutura do IOC
- IPs podem estar em hospedagem compartilhada → bloquear um IP pode afetar sites legítimos.
- Exemplo: IP `74.63.242.18` associado a 1.809 domínios.

---

## 📡 Exemplos de Feeds OSINT Gratuitos

### Resource Cyber Threat Intelligence Feed
- **IPs Maliciosos**: Lista de IPs suspeitos.
- **Hashes de Malware**: Hashes de arquivos maliciosos.
- **Domínios Maliciosos**: Lista de domínios comprometidos.

### Emerging Threats
- Fornece regras de IDS para detecção de tráfego malicioso.
- Inclui listas para TOR, botnets, IPs comprometidos, etc.

### FireHOL IPSET
- Agregador de mais de 100 feeds de IOCs.
- Atualizado a cada minuto.
- Inclui lista `firehol_level1` com IPs maliciosos.

---

## 🍯 Honeypots como Fonte de IOCs
- Simulam serviços reais (ex.: Telnet, MySQL, WordPress).
- Registram tentativas de acesso e comandos executados por atacantes.
- Exemplo: Honeypot Telnet capturando tentativa de login com `root/admin`.

---

## ✅ Vantagens dos Feeds OSINT
- Conhecimento compartilhado.
- Complemento a ferramentas internas.
- Baixo custo.

## ❌ Limitações
- Qualidade variável.
- Falta de contexto.
- Risco de falsos positivos.

---

## 📚 Referências Citadas
- [VirusTotal](https://www.virustotal.com/)
- [Emerging Threats](https://rules.emergingthreats.net/)
- [FireHOL](https://iplists.firehol.org/)
- [REScure CTI Feed](https://rescure.fruxlabs.com/)
- [SecurityTrails](https://securitytrails.com/)
- [GitHub: virusgoatl](https://github.com/moldabekov/virusgoatl)
- [GitHub: awesome-honeypots](https://github.com/paralax/awesome-honeypots)

---

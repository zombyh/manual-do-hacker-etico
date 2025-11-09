## 🌐 Resumo: Elementos de Segurança de Redes

## 📌 Visão Geral
Com a crescente interconexão de redes e a exposição de serviços à Internet, tornou-se essencial adotar dispositivos e técnicas de segurança para proteger infraestruturas, dados e usuários. Esta aula apresenta os principais elementos de segurança utilizados em redes.

---

## 🎯 Objetivos
- Listar opções de elementos de segurança.
- Descrever funções de firewalls (camadas 3, 4 e 7), IDS, IPS e roteadores com ACL.

---

## 🔧 Elementos de Segurança de Rede

### Firewall
Dispositivo que controla o tráfego entre redes com base em regras predefinidas.

#### 🔹 Tipos de Firewall:

1. **Filtro de Pacotes (Camadas 3 e 4)**
   - Toma decisões com base em **IP, porta e protocolo**.
   - **Vantagem**: Simples e rápido.
   - **Desvantagem**: Não inspeciona o conteúdo do pacote.

2. **Firewall Stateful (Com Estado)**
   - Monitora o **estado da conexão** (início, meio, fim).
   - Mantém uma tabela de sessões.
   - Mais seguro, mas consome mais recursos.

3. **Proxy Firewall (Application Firewall)**
   - Atua como intermediário entre cliente e servidor.
   - Inspeciona tráfego na **camada de aplicação**.
   - Oferece maior segurança, mas pode ser um gargalo de desempenho.

4. **Firewall de Camada 7 (NGFW – Next Generation Firewall)**
   - Combina: firewall tradicional, IPS e controle de aplicações.
   - Toma decisões com base no **contexto da aplicação**.
   - Inspeciona tráfego criptografado e aplica políticas granulares.

---

## 🛡️ Sistemas de Detecção e Prevenção

### IDS (Sistema de Detecção de Intrusão)
- Funciona em **modo passivo**.
- Monitora o tráfego e gera alertas e logs.
- Não bloqueia tráfego.

### IPS (Sistema de Prevenção de Intrusão)
- Funciona em **modo ativo**.
- Bloqueia automaticamente tráfego malicioso.
- Pode encerrar sessões ou reconfigurar o firewall.

---

## 🧩 Roteadores com ACL (Lista de Controle de Acesso)
- Filtram tráfego com base em regras (PERMIT/DENY).
- Podem usar critérios como IP, porta, protocolo.
- São usados para:
  - Controle de acesso.
  - Políticas de QoS.
  - Redirecionamento de portas.

---

## 📐 Modelo de Gerenciamento de Rede: FCAPS (ISO)
Cinco áreas funcionais para gerenciamento sistemático de redes:

1. **Falhas**: Detecção, isolamento e correção.
2. **Configuração**: Controle de parâmetros de hardware/software.
3. **Contabilidade**: Registro de uso para cobrança ou auditoria.
4. **Desempenho**: Monitoramento e otimização de performance.
5. **Segurança**: Controle de acesso e prevenção de uso indevido.

---

## 🚨 Ameaças Atuais

### Ransomware
- Tipo de malware que **criptografa dados** e exige resgate.
- Exemplo: WannaCry, que paralisou hospitais e serviços.
- Antivírus sozinhos não são suficientes.

---

## ⚠️ Limitações dos Firewalls
- Não previnem ataques internos (que não passam por ele).
- Não impedem engenharia social ou acesso via redes alternativas (ex.: 3G).
- Não reforçam senhas fracas.
- Podem impactar o desempenho da rede.
- Exigem atualização constante de regras e políticas.

---

## ✅ Conclusão
A segurança de rede deve ser **multicamada**, combinando:
- Firewalls (diversos tipos)
- IDS/IPS
- Roteadores com ACL
- Conscientização de usuários
- Políticas de segurança bem definidas

Nenhum dispositivo é 100% eficaz sozinho. A arquitetura deve ser adaptada ao contexto e aos riscos específicos de cada organização.

---

## 🔎 Explore Mais
- Normas: ISO FCAPS
- Leitura: Kurose & Ross – *Redes de Computadores*; Stallings – *Criptografia e Segurança de Redes*
- Próxima aula: Uso de roteadores como elementos de segurança.

---

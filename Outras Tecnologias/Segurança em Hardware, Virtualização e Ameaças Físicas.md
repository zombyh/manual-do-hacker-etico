
### **Resumo para Estudo: Segurança em Hardware, Virtualização e Ameaças Físicas**

#### **1. Arquitetura de Computadores e Segurança de Hardware**

A segurança não é apenas software. Ela começa na base física e lógica do hardware.

*   **Ciclo de Instrução (Busca-Decodifica-Executa):** Entender este ciclo é fundamental para compreender como exploits (como injeção de código) funcionam e como contramedidas (como a bit NX - No eXecute) atuam.
*   **Anéis de Proteção (Ring Protection):**
    *   **Ring 0 (Kernel):** Máximo privilégio. O Sistema Operacional reside aqui.
    *   **Ring 1 e 2:** Raramente usados.
    *   **Ring 3 (User Mode):** Onde as aplicações do usuário são executadas, com privilégios mínimos.
    *   **Segurança:** O princípio é impedir que código no Ring 3 acesse ou modifique diretamente o Ring 0. Vulnerabilidades ou malwares que quebram esse isolamento são extremamente perigosos (e.g., rootkits).
*   **Memória:**
    *   **Proteção de Memória:** Mecanismo para impedir que um processo acesse a memória de outro processo ou do kernel.
    *   **ASLR (Address Space Layout Randomization):** Técnica de segurança que randomiza as posições de memória onde os componentes de um programa são carregados, dificultando a exploração de vulnerabilidades.
*   **Extensões de Segurança de Hardware (Cruciais para Provas):**
    *   **TPM (Trusted Platform Module):** Um chip dedicado no motherboard que armazena chaves criptográficas, certificados e hashes de integridade de forma segura. É a base para:
        *   **Medição de Integridade:** Mede o estado de boot do sistema (BIOS, Bootloader, OS) e armazena os valores no TPM.
        *   **Armazenamento Seguro de Chaves:** As chaves nunca deixam o chip seguro.
        *   **Criptografia de Disco (e.g., BitLocker):** Usa o TPM para proteger a chave de criptografia do disco, desbloqueando-o apenas se a integridade do boot for verificada.
    *   **Secure Boot:** Parte da especificação UEFI. Impede a execução de bootloaders, drivers ou sistemas operacionais não assinados digitalmente por uma autoridade confiável. Bloqueia malware de baixo nível (bootkits).

#### **2. Virtualização Segura**

Virtualização permite executar múltiplos sistemas operacionais (convidados/VMs) em um único hardware físico. A segurança foca em isolar essas VMs.

*   **Hipervisor (VMM - Virtual Machine Monitor):**
    *   **Tipo 1 (Bare Metal):** Executa diretamente no hardware (e.g., VMware ESXi, Microsoft Hyper-V, KVM). Considerado mais seguro por ter uma superfície de ataque menor.
    *   **Tipo 2 (Hosted):** Executa como um aplicativo sobre um SO (e.g., VMware Workstation, Oracle VirtualBox). Depende da segurança do SO hospedeiro.
*   **Pilares da Segurança na Virtualização:**
    *   **Isolamento (Sandboxing):** A VM não deve poder acessar os recursos de outra VM ou do hipervisor. Uma quebra de isolamento é uma falha crítica.
    *   **Consolidação de Segurança:** Permite centralizar políticas de firewall, antivírus e monitoramento no hipervisor ou em uma camada de gerenciamento.
    *   **Snapshots e Rollbacks:** Facilita a recuperação rápida após um incidente de segurança.
*   **Ameaças Específicas:**
    *   **VM Escape:** O ataque mais perigoso. Ocorre quando um código malicioso dentro de uma VM "escapa" e compromete o hipervisor ou outras VMs. É raro, mas crítico.
    *   **VMs Zumbis:** Máquinas virtuais esquecidas, não corrigidas e não monitoradas, tornando-se uma porta de entrada fácil para ataques.
    *   **Ataques à Camada de Gerenciamento:** Interfaces como o vCenter (VMware) ou o Hyper-V Manager são alvos valiosos. Devem ser fortemente protegidos com MFA e em redes segregadas.
*   **Boas Práticas:**
    *   *Hardening* do hipervisor (desativar serviços desnecessários).
    *   Isolar a rede de gerenciamento.
    *   Manter o hipervisor e as *tools* das VMs atualizados.
    *   Utilizar VMs dedicadas para segurança (e.g., NSX, Virtual Firewalls).

#### **3. Segurança de Firmware**

Firmware é o software "embutido" no hardware que controla o dispositivo. Comprometê-lo é ganhar persistência profunda e difícil de detectar.

*   **O que é Firmware?** Código de baixo nível armazenado em chips de memória não volátil (como EEPROM ou flash). Exemplos: BIOS, UEFI, firmware de placas de rede, drives, roteadores.
*   **Por que é um Alvo?**
    *   **Persistência:** O malware de firmware sobrevive a reinstalações do sistema operacional, formatação do HD e, às vezes, até à troca do disco.
    *   **Baixa Visibilidade:** A maioria dos antivírus tradicionais não inspeciona o firmware.
*   **Tipos de Ataques:**
    *   **Flashamento do BIOS/UEFI:** Modificação maliciosa do firmware da placa-mãe.
    *   **Rootkits de Firmware:** e.g., LoJax (compromete o firmware UEFI).
*   **Proteções:**
    *   **UEFI Secure Boot:** (Mencionado anteriormente) impede o carregamento de drivers ou OS não confiáveis.
    *   **Proteção contra Regravação de BIOS/UEFI:** Muitas placas-mãe possuem uma chave física ou opção no setup para impedir a gravação no chip do firmware.
    *   **Measured Boot (UEFI):** Vai além do Secure Boot, registrando cada etapa do processo de boot em um log no TPM para verificação posterior por um serviço de attestation.
    *   **Atualização Regular:** Fabricantes frequentemente lançam atualizações de firmware para corrigir vulnerabilidades de segurança.

#### **4. Proteção contra Ameaças Físicas**

Se um invasor tem acesso físico a um dispositivo, a maioria das defesas lógicas pode ser contornada.

*   **Ameaças Comuns:**
    *   **Furto de Equipamentos:** Roubo de servidores, laptops, HDs/SSDs, dispositivos de backup.
    *   **Acesso Não Autorizado:** Ligar e acessar um computador desbloqueado ou bypassar a senha de login.
    *   **"Shoulder Surfing":** Visualizar informações sensíveis na tela ou teclado de um usuário.
    *   **Interceptação de Dados:** Grampeamento de cabos ou uso de keyloggers físicos.
    *   **Danos Intencionais ou Acidentais:** Incêndio, alagamento, sabotagem.
*   **Contramedidas e Boas Práticas:**
    *   **Controles de Acesso Físico:**
        *   **Salas Cofre (Data Centers):** Acesso restrito com catracas, fechaduras eletrônicas, biometria, logs de entrada/saída.
        *   **Cadeados para Laptops (Kensington Lock).**
        *   **Armários ou gavetas trancadas** para dispositivos móveis e mídias.
    *   **Proteção de Dados em Repouso:**
        *   **Criptografia de Disco Completo (FDE):** Usando BitLocker (Windows), FileVault (macOS) ou LUKS (Linux). **Protege os dados mesmo em caso de furto.**
        *   **Criptografia de Mídias Removíveis:** Pen drives e HDs externos.
    *   **Políticas de Mesa Limpa e Tela Limpa:** Não deixar documentos sensíveis ou terminais desbloqueados ao sair da mesa.
    *   **Destruição Segura de Mídias:** Utilizar shredders (fragmentadoras) para documentos e dispositivos de degaussing ou destruição física para HDs/SSDs antigos.
    *   **Planos de Continuidade de Negócios (BCP) e Recuperação de Desastres (DRP):** Incluem backups off-site e infraestrutura redundante para se recuperar de desastres físicos.

---

### **Dica Final para a Prova da Procergs:**

Relacione sempre os conceitos técnicos com os **princípios da segurança da informação**:
*   **Confidencialidade:** Criptografia (TPM, BitLocker), Isolamento (Virtualização).
*   **Integridade:** Secure Boot, TPM (medição), checksums de firmware.
*   **Disponibilidade:** Proteção contra desastres físicos (BCP/DRP), prevenção contra danos.
*   **Não-repúdio e Autenticidade:** TPM (chaves criptográficas).

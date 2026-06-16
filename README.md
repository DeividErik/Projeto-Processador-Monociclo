# Projeto-Processador-Monociclo
Repositório destinado a elaboração do projeto da disciplina de Arquitetura e Organização de Computadores


## Equipe
* **Deivid Erik de Vasconcelos Filho**
* **Felipe Santana Cavalcanti**

**Professor:** Vítor A. Coutinho  
**Semestre Letivo:** 2026.1  

---

##  Aquitetura e Módulos Implementados

O projeto foi desenvolvido de forma hierárquica e modularizada. Abaixo estão os arquivos que compõem o processador:

*  **`mips.v` (Top-Level):** Módulo principal que integra todos os componentes, multiplexadores, somadores e lógica de desvio.
*  **`pc.v`:** Contador de Programa (Program Counter). Registrador síncrono atualizado na borda de subida do clock ou zerado via reset.
*  **`i_mem.v`:** Memória de Instrução (ROM assíncrona). Lê o código do arquivo `instruction.list`.
*  **`d_mem.v`:** Memória de Dados (RAM assíncrona). Responsável por operações de `Load` e `Store`.
*  **`regfile.v`:** Banco de Registradores. Contém 32 registradores de 32 bits, com o registrador `$0` travado em constante `0`.
*  **`ula.v`:** Unidade Lógica e Aritmética. Realiza as operações matemáticas/lógicas e emite a flag de zero.
*  **`ctrl.v`:** Unidade de Controle Principal. Decodifica o *opcode* da instrução e gera os sinais de controle adequados.
*  **`ula_ctrl.v`:** Controle da ULA. Auxilia a Unidade de Controle principal definindo a operação exata da ULA baseada no campo *funct*.
*  **`tb_mips.v`:** Testbench para simulação. Gera os sinais de `clock` e `reset` para visualização das ondas.
*  **`instruction.list`:** Arquivo de texto contendo o programa em binário a ser executado pelo processador.

---

## Conjunto de Instruções Suportadas (Subconjunto ISA MIPS)

A unidade de controle e a ULA foram projetadas para suportar o seguinte conjunto de instruções:

###  Tipo R (Registrador)
`add`, `sub`, `and`, `or`, `xor`, `nor`, `slt`, `sltu`, `sll`, `srl`, `sra`, `sllv`, `srlv`, `srav`, `jr`

###  Tipo I (Imediato)
`addi`, `andi`, `ori`, `xori`, `beq`, `bne`, `slti`, `sltiu`, `lui`, `lw`, `sw`

###  Tipo J (Salto pseudo-absoluto)
`j`, `jal`

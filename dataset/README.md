## 📌 Dataset

Esta pasta contém o dataset gerado usando a ferramenta em implementações de PQC em hardware com o modelo aberto Llama-3.3.

O arquivo principal do dataset está estruturado no formato CSV (`dataset.csv`), composto por códigos-fonte em Verilog/Hardware Description Language (HDL) que mapeiam blocos lógicos específicos dos algoritmos afetados.
  Ele traz variações maliciosas injetadas nos seguintes projetos e primitivas criptográficas:

* **DILITHIUM:**
    * *Link de Referência:* [GMUCERG/Dilithium](https://github.com/GMUCERG/Dilithium)
* **SABER:**
    * *Link de Referência:* [sujoyetc/SABER_HW](https://github.com/sujoyetc/SABER_HW/tree/master)
* **SPHINCS+:**
    * *Link de Referência:* [slh-dsa/sloth](https://github.com/slh-dsa/sloth/tree/main)
* **KYBER:**
    * *Link de Referência:* [xingyf14/CRYSTALS-Kyber](https://github.com/xingyf14/CRYSTALS-Kyber)

## 📊 Estrutura do Arquivo

O arquivo CSV é estruturado utilizando as seguintes colunas:

* `id`: Identificador numérico único da amostra/linha.
* `text`: O bloco de código HDL (Verilog) correspondente, contendo os módulos funcionais, máquinas de estados (FSMs), e os triggers/payloads dos hardware trojans gerados por LLM.
* `tj`: Classificação daquela respectiva amostra em relação à presença ou tipo de Trojan.

## 🛠️ Metodologia de Geração

Os hardware trojans contidos neste dataset foram desenvolvidos usando o modelo **Llama-3.3-70B**. Os ataques cobrem cenários como:
1.  **Vazamento de Informação (Information Leakage):** Modificações sutis que expõem chaves privadas ou estados internos por canais seriais.
2.  **Degradação de Segurança:** Alteração em componentes para reduzir a entropia ou enfraquecer o nível de segurança do algoritmo.
3.  **Negação de Serviço (DoS):** Travamento de máquinas de estado (`FSM`) sob gatilhos específicos e raros.

---
*Nota: Este conjunto de dados foi desenvolvido estritamente para fins de pesquisa em segurança de hardware (desenvolvimento de mecanismos de detecção mais resilientes), sendo vetado seu uso para tarefas ilegais.*

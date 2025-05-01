
# Hardware Trojan Generation and Detection using LLM

Este repositório apresenta uma abordagem baseada em LLMs (Large Language Models) para **geração e detecção de Hardware Trojans** em projetos de **hardware (Verilog/VHDL)** e **software (C)**. A execução é feita via **Inference API da Hugging Face**, sem necessidade de GPU, diretamente no **Google Colab**.

A metodologia aplica **análise estática** assistida por IA, com foco no apoio ao **avaliador humano**, usando prompts diversificados e simulações de papéis técnicos.

## 📁 Estrutura do Repositório

```
├── Hardware_Trojan_Generation_and_Detection_using_LLM.ipynb       # Exemplo principal (Hardware - SABER)
├── exemplos/
│   ├── (Dilithium)_Hardware_Trojan_Generation_and_Detection_using_LLM.ipynb   # Exemplo hardware adicional (Verilog)
│   └── (Crystals_KYBER_ML_KEM_liboqs)_Hardware_Trojan_Generation_and_Detection_using_LLM.ipynb  # Exemplo software (liboqs - C)
```

## ✅ Requisitos

- Conta no [Google Colab](https://colab.research.google.com/)
- Conta no [Hugging Face](https://huggingface.co/) com token (plano PRO pode ser necessário)

## 🔐 Como Configurar o Token da Hugging Face

Os notebooks usam a **Inference API da Hugging Face** para interagir com os modelos. Para isso:

### 1. Criar Conta e Gerar Token

1. Acesse: [huggingface.co](https://huggingface.co/)
2. Vá em [Settings → Access Tokens](https://huggingface.co/settings/tokens)
3. Clique em **New token**:
   - **Name**: `colab-token` (ou qualquer nome)
   - **Role**: `read`
4. Copie o token gerado

> ⚠️ **Não compartilhe seu token publicamente.**

### 2. Armazenar o Token com Segurança no Colab

#### 🔐 Opção A — Usar o sistema de Secrets do Colab

1. No Colab, clique na aba lateral `🔐` ou vá em `View > Table of Contents > Secrets`
2. Clique em `+ Add new secret`
   - **Name**: `HF_TOKEN`
   - **Value**: (cole seu token Hugging Face)

Acesso seguro no código:

```python
from google.colab import userdata
token = userdata.get("HF_TOKEN")
```

#### ⚠️ Opção B — Inserir manualmente (não recomendado)

```python
token = "seu_token_aqui"
```

## 📥 Golden Model

O código de referência é fornecido como string multilinha. A variável depende do tipo:

- **Hardware (Verilog/VHDL)**: `design = """..."""`
- **Software (C)**: `code = """..."""`

### Exemplos usados:

- [`keccak.vhd`](https://github.com/sujoyetc/SABER_HW/blob/master/Verilog_src/Keccak_Core/keccak.vhd)
- [`butterfly.v`](https://github.com/GMUCERG/Dilithium/blob/master/rtl_src/butterfly.v)
- [`kem.c`](https://github.com/open-quantum-safe/liboqs/blob/main/src/kem/ml_kem/mlkem-native_ml-kem-512_x86_64/mlkem/kem.c)

## 🧪 Instruções de Uso

1. Defina o modelo (`design` ou `code`)
2. Configure o token `HF_TOKEN`
3. Execute os notebooks

### Avaliações realizadas:

- Código original **com e sem comentários**
- Versões geradas com possíveis trojans
- Comparações com o golden model

### Prompts utilizados:

- Explicações conceituais
- Geração de trojans
- Role-playing com:
  - Avaliador humano
  - Engenheiro de verificação
  - Analista de segurança
  - Engenheiro de testes
- Checklists para avaliação estática

## 🚀 Execução no Google Colab

- [Notebook Principal (SABER - Hardware)](https://github.com/vthayashi/tj-generation-detection-llm/blob/main/Hardware_Trojan_Generation_and_Detection_using_LLM.ipynb)
- [Exemplo com DILITHIUM (Verilog)](https://github.com/vthayashi/tj-generation-detection-llm/blob/main/exemplos/(Dilithium)_Hardware_Trojan_Generation_and_Detection_using_LLM.ipynb)
- [Exemplo com liboqs/KYBER (Software)](https://github.com/vthayashi/tj-generation-detection-llm/blob/main/exemplos/(Crystals_KYBER_ML_KEM_liboqs)_Hardware_Trojan_Generation_and_Detection_using_LLM.ipynb)

## 🧠 Modelos LLM Utilizados

### 🔹 [Meta-Llama-3-70B-Instruct](https://huggingface.co/meta-llama/Meta-Llama-3-70B-Instruct)
- Modelo de 70 bilhões de parâmetros
- Geração de trojans, explicações, role-playing, checklist

### 🔹 [DeepSeek-R1](https://huggingface.co/deepseek-ai/DeepSeek-R1)
- Uso de reasoning para análises mais detalhadas
- Aplicado em prompts concisos de avaliação técnica

## 🛠️ Dependências

Instaladas diretamente nos notebooks:

```python
!pip install huggingface_hub
```

> **GPU não é necessária.** A inferência ocorre via API.

## 📄 Licença

Distribuído sob a [Licença MIT](LICENSE).

## 🤝 Contribuições

Sugestões e melhorias são bem-vindas.  
Abra uma [issue](https://github.com/vthayashi/tj-generation-detection-llm/issues) ou envie um [pull request](https://github.com/vthayashi/tj-generation-detection-llm/pulls).

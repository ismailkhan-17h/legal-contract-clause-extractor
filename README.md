# Legal Contract Clause Extractor using Fine-Tuned LLM

An end-to-end NLP system for extracting important legal clauses from contracts using a fine-tuned Large Language Model (LLM).

The project fine-tunes an instruction-following language model using parameter-efficient fine-tuning (LoRA) on the **CUAD (Contract Understanding Atticus Dataset)** and provides a clause extraction interface using Gradio.

---

## Project Overview

Legal contracts contain critical information distributed across lengthy documents. Manually identifying clauses such as termination terms, governing law, liability limitations, and exclusivity agreements is time-consuming.

This project builds an AI-powered contract analysis system that automatically extracts important contractual clauses and returns structured JSON output.

### Extracted Clauses

The model currently extracts:

* Governing Law
* Termination
* Indemnification
* Liability Cap
* Non-Compete
* Exclusivity

---

## Architecture

```
Contract Text
      |
      v
Text Preprocessing
      |
      v
Fine-Tuned Instruction LLM
(SmolLM2-360M-Instruct + LoRA)
      |
      v
Clause Extraction
      |
      v
Structured JSON Output
      |
      v
Gradio Web Interface
```

---

## Tech Stack

### Machine Learning

* Python
* PyTorch
* Hugging Face Transformers
* Hugging Face Datasets
* PEFT (Parameter Efficient Fine-Tuning)
* LoRA Fine-Tuning
* BitsAndBytes Quantization

### NLP

* CUAD Dataset
* Instruction Fine-Tuning
* Text Generation
* ROUGE Evaluation

### Interface

* Gradio

---

## Model Details

### Base Model

```
HuggingFaceTB/SmolLM2-360M-Instruct
```

### Fine-Tuning Method

```
LoRA (Low-Rank Adaptation)
```

Benefits:

* Reduced GPU memory requirements
* Faster training
* Smaller adapter weights
* Efficient domain adaptation

---

## Dataset

Dataset:

```
CUAD
(Contract Understanding Atticus Dataset)
```

CUAD contains legal contracts annotated with important contractual clauses.

Dataset splits:

```
train
validation
test
```

The dataset is not included in this repository. Follow the dataset setup instructions before running the notebooks.

---

## Project Structure

```
legal-contract-clause-extractor/

├── README.md
├── requirements.txt
├── .gitignore
│
├── notebooks/
│   ├── phase4_finetune_cuad_llm.ipynb
│   ├── phase5_evaluation_cuad_llm.ipynb
│   └── phase6_gradio_contract_analyzer.ipynb
│
└── sample_contracts/
    ├── sample_contract.txt
    └── demo_output.json
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/ismailkhan-17h/legal-contract-clause-extractor.git

cd legal-contract-clause-extractor
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Running the Project

### 1. Fine-Tuning

Open:

```
notebooks/phase4_finetune_cuad_llm.ipynb
```

This notebook performs:

* Dataset preparation
* Tokenization
* LoRA configuration
* Model fine-tuning
* Adapter saving

---

### 2. Evaluation

Open:

```
notebooks/phase5_evaluation_cuad_llm.ipynb
```

Evaluation includes:

* Model inference
* Prediction generation
* ROUGE score calculation

Example evaluation:

```
ROUGE-1: 0.1299
ROUGE-2: 0.0674
ROUGE-L: 0.0899
```

---

### 3. Run the Interface

Open:

```
notebooks/phase6_gradio_contract_analyzer.ipynb
```

The Gradio application allows users to:

1. Enter contract text
2. Run clause extraction
3. Receive structured JSON output

---

## Example Input

```
This Agreement shall be governed by the laws of the State of California.

Either party may terminate this Agreement by providing thirty days written notice.
```

---

## Example Output

```json
{
  "governing_law": "State of California",
  "termination": "Thirty days written notice",
  "liability_cap": "$500,000",
  "non_compete": "Twelve months after termination"
}
```

---

## Future Improvements

* Increase training dataset coverage
* Fine-tune larger instruction models
* Add PDF contract upload support
* Add OCR pipeline for scanned documents
* Deploy API using FastAPI
* Deploy application using cloud infrastructure
* Improve extraction accuracy with retrieval augmentation (RAG)

---

## Limitations

* The model is designed for research and demonstration purposes.
* Predictions should not be considered legal advice.
* Accuracy depends on contract format and clause complexity.

---

## Author

**Ismail Khan**

GitHub:
https://github.com/ismailkhan-17h

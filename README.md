# ECE219 – Project 3

This repository contains the notebooks for **ECE219 Project 3**.

The project is organized into three parts, each implemented in a separate notebook.

---

# Project Structure

### Part 1 – Teaching a Small Model to Reason: LoRA Fine-Tuning, Knowledge

Implemented in:

```
P3_Part1.ipynb
```

---

### Part 2 – Agentic Data Mining with ReAct

Implemented in:

```
P3_PartB.ipynb
```

---

### Part 3 – Regression Analysis

Implemented in:

```
219pset3partc.ipynb
```

---

# Environment Setup

All notebooks are designed to run in **Google Colab with GPU enabled**.

Enable GPU in Colab:

```
Runtime → Change runtime type → Hardware accelerator → GPU
```

---

# Hugging Face Login

Some models are downloaded from Hugging Face.

Before running the notebook, generate a Hugging Face access token:

https://huggingface.co/settings/tokens

Create a **Read Access Token** and replace the placeholder in the notebook:

```python
from huggingface_hub import login

HF_TOKEN = "ENTER_YOUR_TOKEN_HERE"
login(HF_TOKEN)
```

---

# Reproducing Results (Part 1)

### Base Model

The **base model will be automatically downloaded from Hugging Face** when running the notebook.

No manual download is required.

---

### LoRA Checkpoints

The LoRA checkpoints trained with **1000** and **3000** training examples are provided via **Google Drive**. These files are only accessible via **UCLA** accounts.

Download the checkpoints for 1k from:

```
https://drive.google.com/drive/folders/1cs1X3Uns9g8VAuOrTEbtDh_1ZB-iGns8?usp=sharing
```

Download the checkpoints for 3k from:

```
https://drive.google.com/drive/folders/1BWVnD_hgt6xNFW_kpWijdsGLAN7cYB3z?usp=sharing
```

Upload the folders to your Google Drive so the directory structure becomes:

```
MyDrive/
    qwen2_lora_1000examples/
        final_adapter/
    qwen2_lora_3000examples/
        final_adapter/
```

---

### Mount Google Drive in Colab

Before loading the checkpoints, mount Google Drive:

```python
from google.colab import drive
drive.mount('/content/drive')
```

---

### Loading the LoRA Adapter

In the notebook, the LoRA adapter is loaded using the following path:

```python
adapter_dir = f"/content/drive/MyDrive/qwen2_lora_{num_train}examples/final_adapter"
```

For example:

```
/content/drive/MyDrive/qwen2_lora_1000examples/final_adapter
/content/drive/MyDrive/qwen2_lora_3000examples/final_adapter
```

Ensure the checkpoints are placed in the correct directory so the notebook can load them successfully.

---

# Dataset

The **GSM8K dataset is automatically downloaded** when running the evaluation code in the notebook.

No manual dataset download is required.

---

# Notes

* All experiments were executed in **Google Colab with GPU enabled**.
* Results may vary slightly due to **generation randomness and sampling variability**.

# WiDS Transformer

This repository contains the evolution of a character-level language model developed during the **WIDS (Winter in Data Science)** 2026 project. It documents the transition from a primitive **Bigram Model** to a fully functional **Decoder-Only Transformer** (GPT architecture) capable of generating coherent, Shakespearean-style text.

---

## 1. Project Overview
The goal of this project was to move from "predicting based on the last letter" to "understanding context and sentence structure." The final implementation utilizes **Masked Self-Attention** to give the model context and memory, mimicking the architecture that powers modern LLMs like ChatGPT.

### **Phase 1: The Bigram Baseline**
* **Concept:** A simple model that predicts the next character based only on the current character.
* **Limitation:** Zero memory or context, resulting in "hilarious gibberish".
* **Result:** Validation Loss ~2.53.While the text is gibberish, you can see the model "learning" things like capitalization after newlines and common English character clusters.

### **Phase 2: The GPT Transformer**
* **Concept:** Implementing a decoder-only architecture with positional embeddings and self-attention.
* **Goal:** Achieve a validation loss between 1.5 and 2.0 with correct spelling and basic grammar.

---

## 2. Technical Architecture (`gpt.py`)
The final model implements the following core components of a very basic transformer based language model:



* **Head**: One head of self-attention that calculates Query, Key, and Value vectors.
* **MultiHeadAttention**: Multiple heads running in parallel to capture different types of linguistic relationships.
* **FeedForward**: Linear layers with non-linearity (ReLU) for per-token computation.
* **Block**: A complete Transformer block combining Attention, FeedForward, and Layer Normalization.
* **Positional Embeddings**: Ensures the model knows the order of words/characters in a sequence.

---

## 3. Implementation Details
* **Dataset**: `tinyshakespeare` (1.1M characters).
* **Tokenizer**: Simple character-level integer encoding (`stoi` and `itos`).
* **Hyperparameters**:
    * **Batch Size**: 64
    * **Block Size (Context Window)**: 256
    * **Embedding Dimension**: 384
    * **Heads**: 6
    * **Layers**: 6
    * **Training Iterations**: 5,000.

---

## 4. Performance & Results
The model was trained for **5,000 iterations** to ensure it moved beyond memorization to learning patterns.

| Metric | Value |
| :--- | :--- |
| **Initial Loss** | ~4.28 |
| **Final Validation Loss** | **1.4920** (Target: 1.5 - 2.0) |
| **Training Steps** | 5,000 |

### **Sample Output**
> But with prison: I will stead with you.
>
>ISABELLA:
>Carress, all do; and I'll say your honour self good:
>Then I'll regn your highness and
>Compell'd by my sweet gates that you may:
>Valiant make how I heard of you.
>
>ANGELO:
>Nay, sir, Isay!
>
>ISABELLA:
>I am sweet men sister as you steed.
>
>LUCIO:
>As it if you in the case would princily,
>I'll rote, sir, I did cannot now at me?
>That look thence, thy children shall be you called.
>
>DUKE VINCENTIO:
>Marry, though I do read you!
>
>LUCIO:
>O that mufflest than

---

## 5. How to Run
1.  **Environment**: Recommended to use **Google Colab** with a **T4 GPU** for training.
2.  **Dependencies**: Install PyTorch:
    ```bash
    pip install torch
    ```
3.  **Execution**: Run the final script:
    ```bash
    python gpt.py
    ```
    *The script automatically handles the download of `input.txt` if it is missing.*

---

## 6. Acknowledgments
* **Andrej Karpathy**: For the "Let's build GPT: from scratch" series.
* **Harvard NLP**: For "The Annotated Transformer" line-by-line implementation.
* **Jay Alammar**: For "The Illustrated Transformer" conceptual guides.


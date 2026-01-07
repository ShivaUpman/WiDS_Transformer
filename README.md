# WiDS_Transformer
# Bigram-GPT: The "Dumb" Transformer

This repository contains my implementation of a **Character-Level Bigram Language Model**, built as the mid-term assignment for WIDS Week 3. It serves as the primitive baseline before we transition into building a full-scale Transformer architecture.

---

## 1. Project Overview
The goal was to build a language model that predicts the next character in a sequence using **only** the current character as context. Since this model has zero memory (no attention or hidden states), the output is essentially a "stochastic vomit" of characters that look vaguely like English but make no sense.

I followed Andrej Karpathy's "Let's build GPT: from scratch" series, stopping at the manual bigram implementation.

## 2. Technical Stack & Dataset
* **Framework:** PyTorch
* **Dataset:** `tinyshakespeare` (1.1M characters)
* **Vocab Size:** 65 characters (A-Z, a-z, punctuation, and whitespace)
* **Tokenizer:** Simple character-level integer encoding (`stoi` and `itos`)

## 3. Implementation Details
The model is a simple `nn.Module` subclass that uses an `nn.Embedding` table as a direct lookup for character transition probabilities.

* **Architecture:** $V \times V$ Embedding Table (where $V = 65$)
* **Loss Function:** Cross-Entropy Loss
* **Optimizer:** AdamW with a learning rate of `1e-3`
* **Training Loop:** 5,000 steps with a batch size of 32

## 4. Performance & Results
Post-training, the loss dropped significantly from an initial **~4.87** to **~2.53**. While the text is gibberish, you can see the model "learning" things like capitalization after newlines and common English character clusters.

### Sample Output (The Gibberish)
```text
CHNCKIViver HelozR'd jemiok ft hat fo is -mZARSure, Yje'd ureckha;
ENCEngiAs! smiTId
W:
CE:Pich toto ito,'r. alyy f?

# Next Word Prediction using LSTM

## Project Overview

This project implements a **Next Word Prediction system** using a **Long Short-Term Memory (LSTM)** neural network.  
Given a sequence of words as input, the model predicts the most likely next word based on learned language patterns.

The objective of this project is to understand **sequence modeling**, **word embeddings**, and **LSTM-based language models**, and to deploy the trained model using an interactive **Gradio web interface**.

---

## Problem Statement

Language is sequential in nature, where the meaning of a word often depends on previous words. Traditional machine learning models struggle with such dependencies. This project addresses the problem of predicting the next word in a sentence using an LSTM, which is designed to capture long-term dependencies in sequential data.

---

## Dataset Description

- The dataset is a **custom-written, realistic text corpus** in article format.
- The text discusses topics related to **language, education, technology, and learning**.
- The dataset is continuous and coherent, resembling real-world text rather than isolated sentences.
- This design allows the LSTM to learn natural word transitions and contextual dependencies.

### Dataset Characteristics
- Medium-sized corpus (trains in minutes, not hours)
- Vocabulary size: ~200 words
- Generated training samples (n-grams): ~2000+
- Suitable for next-word prediction tasks

---

## Data Preprocessing

1. **Tokenization**
   - Text is tokenized using Keras `Tokenizer`.
   - Each word is mapped to a unique integer index.

2. **Sequence Generation**
   - N-gram sequences are generated from each sentence.
   - Example:
     ```
     "machine learning is useful"
     → ["machine", "learning"]
     → ["machine", "learning", "is"]
     → ["machine", "learning", "is", "useful"]
     ```

3. **Padding**
   - Sequences are padded to the length of the longest sequence.
   - Pre-padding is used to preserve recent context.

4. **Train Data Split**
   - Input (`X`): all words except the last
   - Target (`y`): the next word to be predicted

---

## Model Architecture

The model uses the following architecture:

- **Embedding Layer**
  - Learns dense vector representations of words.
- **LSTM Layer**
  - Captures sequential dependencies in text.
- **Dropout Layer**
  - Prevents overfitting.
- **Dense Output Layer**
  - Softmax activation over the vocabulary to predict the next word.

```text
Input → Embedding → LSTM → Dropout → Dense (Softmax)

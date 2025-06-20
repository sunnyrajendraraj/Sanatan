# 🧠 Custom Tokenizer for LLM Preprocessing  
### *Educational Simulation Using Edith Wharton’s “The Verdict”*

---

## 📘 Overview

This project demonstrates the creation of a custom tokenizer designed to preprocess text data for Large Language Model (LLM) training. Using Edith Wharton's short story *The Verdict* (20,479 characters), we walk through how to tokenize text into individual tokens (words, punctuation), map them to integer IDs, and later reconstruct the original input. This notebook simulates a simplified version of real-world tokenization used in LLMs such as GPT.

---

## 🎯 Objectives

- Tokenize narrative text into discrete units (tokens)
- Build a vocabulary dictionary of unique tokens
- Encode text into token IDs and decode them back to human-readable form
- Handle unknown tokens and simulate document boundaries using special tokens
- Reproduce key aspects of LLM preprocessing in a controlled, understandable environment

---

## 🧱 Project Structure

The tokenizer is implemented in two versions:

### 🔹 `CustomTokenizer-I`
- Basic encoding and decoding using a static vocabulary.
- **Limitation**: Crashes (`KeyError`) when unknown words are encountered.

### 🔹 `CustomTokenizer-II`
- Enhanced version supporting:
  - `<|unk|>` token for out-of-vocabulary (OOV) words
  - `<|endoftext|>` token to separate independent text segments
- Ensures graceful handling of unseen input and document boundaries.
- Reconstructs the original text using accurate punctuation placement.

---

## 📦 Key Components

| Component            | Description                                               |
|----------------------|-----------------------------------------------------------|
| `preprocessed`       | List of raw tokens extracted using regex                  |
| `vocab`              | A dictionary mapping tokens to unique integer IDs         |
| `CustomTokenizer-II` | Custom class with `encode()` and `decode()` methods       |
| `<|unk|>`            | Represents unknown words during encoding                  |
| `<|endoftext|>`      | Indicates end of a document or sentence batch             |
| Regular Expressions  | Used for token splitting and spacing fixes during decoding|

---

## 🔍 Example Usage

```python
text1 = "Hello, do you like tea?"
text2 = "In the sunlit terraces of the palace."

# Combine texts with document separator
text = " <|endoftext|> ".join((text1, text2))

# Encode into token IDs
ids = tokenizer.encode(text)
print("Token IDs:", ids)

# Decode back into readable text
decoded = tokenizer.decode(ids)
print("Decoded:", decoded)

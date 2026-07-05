# HexSoftwares_Summarize-News-Articles-with-ML
Task 3, project 1 Summarize News Article with ML


# Summarize News Articles with ML

This project implements an **Abstractive News Article Summarization** system using the **T5-small Transformer model**. The model takes a long news article as input and generates a concise summary in its own words.

The notebook was developed as **Project 1 for Hex Softwares Internship** and follows a complete machine learning workflow from dataset loading to model evaluation.

---

## Project Overview

News articles are often lengthy, and readers may not have enough time to read full articles. This project uses Natural Language Processing (NLP) and Transformer-based deep learning to automatically summarize news articles into short, meaningful summaries.

The project focuses on **abstractive summarization**, where the model does not simply copy sentences from the article. Instead, it learns to generate a new summary based on the meaning of the article.

---

## Dataset

The dataset used in this project is the Kaggle **News Summarization** dataset:

**Dataset Link:** https://www.kaggle.com/datasets/sbhatti/news-summarization

The dataset contains news article text and human-written summaries.

### Dataset Details Used in Notebook

| Item | Value |
|---|---:|
| Total rows loaded | 400 |
| Original columns | `Unnamed: 0`, `ID`, `Content`, `Summary`, `Dataset` |
| Article column | `Content` |
| Summary column | `Summary` |
| Cleaned dataset shape | 400 rows × 2 columns |
| Training rows | 320 |
| Testing rows | 80 |
| Train/Test split | 80% / 20% |

Only the first 400 rows were used because the complete dataset is large and the goal was to keep the notebook lightweight for Google Colab.

---

## Technologies Used

- Python
- Google Colab
- Kaggle API
- Pandas
- NumPy
- Scikit-learn
- PyTorch
- Hugging Face Transformers
- Hugging Face Datasets
- Hugging Face Evaluate
- ROUGE Score
- T5-small Transformer model

---

## Model Used

### T5-small

This project uses **T5-small**, a lightweight Transformer-based sequence-to-sequence model from Hugging Face.

T5 is suitable for abstractive summarization because it treats summarization as a text-to-text task:

```text
Input:  summarize: <news article>
Output: <generated summary>
```

### Model Configuration

| Setting | Value |
|---|---:|
| Model | `t5-small` |
| Max input length | 512 tokens |
| Max target length | 128 tokens |
| Epochs | 1 |
| Train batch size | 2 |
| Eval batch size | 2 |
| Learning rate | 2e-5 |
| Optimizer setup | Hugging Face Trainer default |
| GPU used in run | Tesla T4 |
---

## Data Preprocessing

The notebook performs the following preprocessing steps:

- Loads the dataset directly from Kaggle using Kaggle API.
- Automatically detects article and summary columns.
- Selects only the article and summary columns.
- Removes missing values.
- Removes duplicate rows.
- Cleans newline, tab, and extra whitespace characters.
- Filters invalid or very short article-summary pairs.
- Splits the dataset into training and testing sets.
- Tokenizes text using the T5 tokenizer.

---

## Training Results

The model was fine-tuned for 1 epoch on 320 training samples.

| Metric | Value |
|---|---:|
| Global steps | 160 |
| Train runtime | 29.32 seconds |
| Train samples/second | 10.91 |
| Train steps/second | 5.46 |
| Final logged training loss | 2.3931 |
| Validation loss | 2.7031 |
| Overall train loss | 2.8917 |

---

## Evaluation

The model was evaluated using **ROUGE score**, which is commonly used for text summarization tasks.

### ROUGE Results

| Metric | Score |
|---|---:|
| ROUGE-1 | 0.2844 |
| ROUGE-2 | 0.0643 |
| ROUGE-L | 0.1762 |
| ROUGE-Lsum | 0.1744 |

These results are based on a small training sample of 400 rows and only 1 training epoch. The performance can be improved by training on more rows, increasing epochs, and using larger models such as BART or PEGASUS.

---

## Sample Output

### Input Article

A news article about Monaco coach Leonardo Jardim warning his players before defending a 3-1 lead against Arsenal in the Champions League.

### Actual Summary

```text
Monaco beat Arsenal 3-1 at the Emirates in February in the first leg.
Arsenal will aim to win 3-0 to make it through the Champions League tie.
Monaco's Leonardo Jardim warns his players not to rest on their laurels.
```

### Predicted Summary

```text
Monaco coach Leonardo Jardim warned his players not to rest on their laurels as they defend their 3-1 lead at Stade Louis II against Arsenal on Tuesday night. The Portuguese coach stressed the threat of Mesut Ozil and Santi Cazorla and is trying to prepare his players for an expected attacking onslaught from Arsenal.
```

---

## Custom Article Test

The notebook also tests the model on a custom article about Pakistan's technology sector.

### Generated Summary

```text
Pakistan's technology sector has seen significant growth in recent years. Experts believe young developers, entrepreneurs, and freelancers can play an important role in improving the country's digital economy. Universities and training institutes should focus on practical skills, real-world projects and industry collaboration to prepare students for modern technology jobs.
```

---
## Conclusion

This project successfully demonstrates how NLP and Transformer-based models can summarize long news articles into concise summaries. It covers the complete machine learning pipeline, including dataset loading, preprocessing, tokenization, model fine-tuning, summary generation, and evaluation.
---

## Author
Fani2323
@HexSoftwares Intership
Computer Science "Machine Learning"

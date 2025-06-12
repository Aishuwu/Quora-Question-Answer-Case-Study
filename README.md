# Quora QA Case Study: Building a State-of-the-Art Question Answering System

**Author**: Aishwarya  Shrigiri  
**Notebook**: `Quora_Case_Study.ipynb`

## Table of Contents

- [Introduction](#introduction)
- [Dataset](#dataset)
- [Tools and Frameworks](#tools-and-frameworks)
- [Methodology](#methodology)
- [Evaluation](#evaluation)
- [Results](#results)
- [Insights and Recommendations](#insights-and-recommendations)
- [Installation](#installation)
- [Usage](#usage)
- [Examples](#examples)
- [Contributors](#contributors)
- [License](#license)

## Introduction

This project explores the development of a question-answering (QA) system using transformer-based models on the Quora Question Answer Dataset. Two popular NLP models — T5 and GPT-2 — were fine-tuned, evaluated, and compared in terms of their response quality and practical performance for real-world use cases, particularly in customer support and information systems.

## Dataset

The dataset used for this project is the [Quora Question Answer Dataset](https://huggingface.co/datasets/toughdata/quora-question-answer-dataset), available on Hugging Face Datasets. It contains over 56,000 question-answer pairs sourced from Quora discussions. After cleaning, around 43,000 entries were used for training and evaluation.

## Tools and Frameworks

- Python
- Google Colab
- HuggingFace Transformers & Datasets
- Matplotlib, Seaborn (for visualizations)

## Methodology

### Data Preparation

- Removed empty, duplicate, or extremely long entries.
- Cleaned data by removing HTML tags, special characters, and whitespace.
- Re-formatted inputs for each model:
  - **T5**: `question: <question>` → `<answer>`
  - **GPT-2**: Conversational format `Q: <question>\nA: <answer>`

### Model Training

- **T5-Small**
  - Fine-tuned using Hugging Face's `Trainer` API
  - Trained on 10,000 samples, 3 epochs, batch size of 2
- **GPT-2**
  - Fine-tuned for causal language modeling
  - Similar training setup with special formatting to handle input/response concatenation

### Evaluation Metrics

- **BLEU**
- **ROUGE** (ROUGE-1, ROUGE-2, ROUGE-L, ROUGE-Lsum)
- Qualitative answer review
- Visualization of training loss and answer lengths

## Results

| Metric       | T5-Small | GPT-2   |
|--------------|----------|---------|
| BLEU         | 0.0023   | 0.0174  |
| ROUGE-1      | 0.122    | 0.1794  |
| ROUGE-2      | 0.031    | 0.0268  |
| ROUGE-L      | 0.098    | 0.1074  |
| ROUGE-Lsum   | 0.1002   | 0.1074  |

- **GPT-2** produced longer and more natural responses.
- **T5** was more concise and stable but often lacked detail.

## Insights and Recommendations

- Data preprocessing and cleaning significantly affect performance.
- GPT-2’s autoregressive nature lends it to more fluent and conversational outputs.
- Evaluation should combine both metrics and qualitative human review.
- Future improvements:
  - Use larger models like GPT2-Medium or T5-Base
  - Integrate retrieval-augmented generation (RAG)
  - Explore hybrid approaches for dynamic QA pipelines


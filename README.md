# How Well Do Arabic Large Language Models Understand? A Prompt-Based Multi-Task Evaluation 

## Description

This project evaluates and compares the effectiveness of different prompting techniques for Large Language Models (LLMs).

Prompt engineering is an important approach for improving the way LLMs respond to different tasks without modifying or retraining the underlying model. Different prompting strategies can affect the quality, accuracy, consistency, and usefulness of model-generated responses.

The objective of this project is to experimentally evaluate different prompting techniques using a common evaluation setup. The project provides the prompts and codes required to reproduce the evaluation.

The techniques investigated in this project include:

* Zero-Shot Prompting
* Few-Shot Prompting
* Chain-of-Thought (CoT) Prompting

The experiments can be used to analyze how changes in prompt design influence the performance of an LLM on the selected tasks:
* News Clasification
* Sentiment Analysis
* Question Answering
* Text Summarization

---

## Project Objectives

The main objectives of this project are:

1. To implement multiple prompting techniques.
2. To evaluate the performance of different Arabic specific and multilingual LLMs performance on different tasks using different evaluation tasks.
3. To compare the generated outputs using consistent evaluation criteria.
4. To provide reproducible code and experimental results.
5. To investigate how prompt design influences LLM performance in low resource language (Arabic Language).

---

## Dataset Information

This project evaluates different prompting techniques across four publicly available Arabic NLP datasets. The datasets cover multiple NLP tasks, including text classification, sentiment analysis, summarization, and general knowledge/reasoning.

| Dataset             | Task                  | Language     | Data Type                 | Description                                                                                                                             |
| ------------------- | --------------------- | ------------ | ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **SANAD**           | News Classification   | Arabic (MSA) | News Articles             | A large-scale Arabic news dataset containing articles collected from multiple Arabic news portals and categorized into seven topics.    |
| **ASAD**            | Sentiment Analysis    | Arabic       | Tweets                    | A benchmark Arabic sentiment-analysis dataset containing Arabic tweets labeled as **Positive, Negative, or Neutral**.                   |
| **XL-Sum – Arabic** | Text Summarization    | Arabic       | News Articles             | The Arabic subset of XL-Sum, a multilingual dataset for abstractive summarization of news articles.                                     |
| **Arabic-MMLU**     | Knowledge & Reasoning | Arabic       | Multiple-choice Questions | An Arabic adaptation of the Massive Multitask Language Understanding (MMLU) benchmark covering multiple academic and knowledge domains. |

### Dataset Roles in the Evaluation

Each dataset represents a different type of NLP task, allowing the prompting techniques to be evaluated across diverse language understanding scenarios:

| Dataset             | Primary Task                   | What It Evaluates                                                                                                  | Identifier / DOI                                                         | URL
| ------------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------ |------------------------------------------------------------------------- |-------------------------------------------------------------------------------------------------------|
| **SANAD**           | Text Classification            | The ability of prompting techniques to classify Arabic news articles into predefined categories.                   | Paper DOI: 10.1016/j.dib.2019.104076; Mendeley DOI: 10.17632/57zpx667y9  | [SANAD URL](https://data.mendeley.com/datasets/57zpx667y9/1)                                |
| **ASAD**            | Sentiment Classification       | The ability to identify sentiment expressed in Arabic social-media text.                                           | Paper: arXiv:2011.00578                                                  | [ASAD URL](https://www.kaggle.com/competitions/arabic-sentiment-analysis-2021-kaust/data). |
| **XL-Sum (Arabic)** | Summarization                  | The ability to generate concise summaries that preserve the important information in Arabic news articles.         | Paper DOI: 10.18653/v1/2021.findings-acl.413                             | [XL-Sum URL](https://huggingface.co/datasets/csebuetnlp/xlsum).                              |
| **Arabic-MMLU**     | Question Answering / Reasoning | The ability of prompting techniques to answer Arabic multiple-choice questions across different knowledge domains. | Paper: arXiv:2402.12840                                                  | [Arabic-MMLU URL](https://huggingface.co/datasets/MBZUAI/ArabicMMLU).                             |

### Dataset Paper Citations

* **SANAD:** Einea, O., Elnagar, A., & Al Debsi, R. (2019). Sanad: Single-label arabic news articles dataset for automatic text categorization. Data in brief, 25, 104076.
* **ASAD:** Alharbi, B., Alamro, H., Alshehri, M., Khayyat, Z., Kalkatawi, M., Jaber, I. I., & Zhang, X. (2020). ASAD: A twitter-based benchmark arabic sentiment analysis dataset. arXiv preprint arXiv:2011.00578.
* **XL-Sum:** Hasan, T., Bhattacharjee, A., Islam, M. S., Mubasshir, K., Li, Y. F., Kang, Y. B., ... & Shahriyar, R. (2021, August). XL-sum: Large-scale multilingual abstractive summarization for 44 languages. In Findings of the Association for Computational Linguistics: ACL-IJCNLP 2021 (pp. 4693-4703).
* **Arabic-MMLU:** Koto, F., Li, H., Shatnawi, S., Doughman, J., Sadallah, A., Alraeesi, A., ... & Baldwin, T. (2024, August). ArabicMMLU: Assessing massive multitask language understanding in Arabic. In Findings of the Association for Computational Linguistics: ACL 2024 (pp. 5622-5640).

### Data Usage and Evaluation

For each dataset, the same underlying examples are evaluated using the different prompting techniques implemented in this project. This provides a consistent basis for comparing how prompt design affects LLM performance across different Arabic NLP tasks.

The evaluation results can be analyzed according to the characteristics of each dataset, including task type, input format, expected output, and evaluation metric.


## Code Information

The repository contains the implementation and experimental materials required to evaluate the prompting techniques.


### Main Components

| Component       | Description                                                 |
| --------------- | ----------------------------------------------------------- |
| Prompting Code  | Implements the different prompting techniques.              |
| Notebooks       | Provide the experimental workflow and analysis.             |
| README.md       | Documentation and instructions for reproducing the project. |

---

## Methodology

The evaluation follows a consistent experimental workflow.

### Step 1 — Dataset Preparation

The selected dataset is loaded and prepared for evaluation.

The same test examples are used for the different prompting approaches and different models. This helps reduce differences caused by variations in the input data.

### Step 2 — Prompt Construction

A separate prompt template is created for each prompting technique.

#### Zero-Shot Prompting

The model receives an instruction without providing examples.

#### Few-Shot Prompting

The prompt includes a small number of examples demonstrating the expected behavior before presenting the target input.

#### Chain-of-Thought Prompting

The model is instructed to reason through the problem before producing the final answer.


### Step 3 — Model Evaluation

Each prompting technique is applied to the selected LLM using the same underlying evaluation dataset.

### Step 4 — Performance Evaluation

The outputs are evaluated using the metrics appropriate for the selected task.


## Usage Instructions

### 1. Download the Files

### 2. Upload it locally to jupyter network software or to Google Colab

### 3. Install the Required Libraries

```bash
pip install transformers
pip install bitsandbytes
pip install accelerate
pip install trl
pip install peft
pip install datasets
pip install numpy
pip install openai
```

### 4. Configure API Credentials

To run GPT-4.1 and GPT-4o you need to configure API from OpenAI platform and paste it instead of API_KEY

```bash
client = OpenAI(api_key='API_Key')
```

To run other models you have to generate Hugging Face token and paste it instead of HF_TOKEN

```bash
huggingface_hub.login('HF_TOKEN')
```

### 5. Run all cells

### 6. Review the Results

## Requirements

The project requires Python 3.x and the Python packages used by the implementation.

Typical dependencies include:

```text
Python >= 3.x
pandas
numpy
transformers
trl
peft
accelerate
datasets
openai
jupyter
```

---

## Experimental Configuration

To reproduce the experiments, ensure that the following settings remain consistent:

* Dataset
* Test examples
* Prompt templates
* Model
* Temperature
* Maximum output tokens
* Number of examples used for few-shot prompting
* Evaluation metrics
* Random seed, where applicable

Changes to these parameters may affect the experimental results.

---

## Acknowledgements

This work was supported by Zayed University Research Incentive Fund (RIF) with grant number [23274].

---

## Author

**Sanaa Kaddoura**

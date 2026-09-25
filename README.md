# How Well Do Arabic Large Language Models Understand? A Prompt-Based Multi-Task Evaluation 

## Description

This project evaluates and compares the effectiveness of different prompting techniques for Large Language Models (LLMs) across different Arabic Natural Processing Tasks (NLP). The objective of this project is to experimentally evaluate different prompting techniques using a common evaluation setup. The project provides the prompts and codes required to reproduce the evaluation.

The evaluated prompting techniques include:
* Zero-Shot Prompting
* Few-Shot Prompting
* Chain-of-Thought (CoT) Prompting

The repository provides the code, prompts, and evaluation notebooks required to reproduce the experiments. Each experiment follows a common evaluation setup within its corresponding task, allowing the performance of different prompting techniques to be compared under consistent conditions.

The repository is organized into four main folders, with each folder corresponding to one of the evaluated Arabic NLP tasks:
* News Clasification
* Sentiment Analysis
* Question Answering
* Text Summarization

Each task folder contains multiple Jupyter notebooks. The notebooks are named according to the LLM and task being evaluated. For example, Allam_News_Classification_Different_Prompting_Techniques.ipynb contains the code used to evaluate the ALLaM model on the News Classification task using Zero-Shot, Few-Shot, and Chain-of-Thought prompting.

Each notebook is organized into clearly labeled sections corresponding to the different stages of the experiment. The main experimental sections evaluate the model using Zero-Shot, Few-Shot, and Chain-of-Thought prompting. These sections contain the prompts, model inference procedures, and evaluation steps required to assess model performance for the corresponding task.

---

## Dataset Information

This project evaluates different prompting techniques across four publicly available Arabic NLP datasets. The datasets cover multiple NLP tasks, including text classification, sentiment analysis, summarization, and general knowledge/reasoning.

| Dataset             | Task                  | Language     | Data Type                 | Description                                                                                                                             |
| ------------------- | --------------------- | ------------ | ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **SANAD**           | News Classification   | Arabic (MSA) | News Articles             | A large-scale Arabic news dataset containing articles collected from multiple Arabic news portals and categorized into seven topics.    |
| **ASAD**            | Sentiment Analysis    | Arabic       | Tweets                    | A benchmark Arabic sentiment-analysis dataset containing Arabic tweets labeled as Positive, Negative, or Neutral.                       |
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

### Data Usage and Evaluation

For each dataset, the same underlying examples are evaluated using the different prompting techniques implemented in this project. This provides a consistent basis for comparing how prompt design affects LLM performance across different Arabic NLP tasks.

The evaluation procedure depends on the characteristics of each task:
* News Classification: The model receives an Arabic news article and is prompted to assign it to one of the predefined news categories.
* Sentiment Analysis: The model receives an Arabic tweet and is prompted to classify its sentiment as Positive, Negative, or Neutral.
* Text Summarization: The model receives an Arabic news article and is prompted to generate an abstractive summary.
* Arabic-MMLU: The model receives an Arabic multiple-choice question and its answer options and is prompted to select the correct answer.

The same evaluation examples are used across the prompting conditions for a given task. The resulting model outputs are then compared with the corresponding reference labels or reference summaries using the evaluation procedure and metrics specified in the experimental notebooks.


## Code Information

The repository contains the implementation and experimental materials required to evaluate the prompting techniques.

The repository is organized by task. Each task has a dedicated folder containing the Jupyter notebooks used to run the corresponding experiments:
```
.
├── News_Classification/
│   └── <model>_News_Classification_Different_Prompting_Techniques.ipynb
│   └── News_Classification_Prompt.ipynb
│
├── Sentiment_Analysis/
│   └── <model>_Sentiment_Analysis_Different_Prompting_Techniques.ipynb
│
├── Question_Answering/
│   └── Biology
│       └── <model>_Biology_QA_Different_Prompting_Techniques.ipynb
│   └── Math
│       └── <model>_Math_QA_Different_Prompting_Techniques.ipynb
│   └── Physics
│       └── <model>_Physics_QA_Different_Prompting_Techniques.ipynb
│   └── Question_Answering_Prompt.ipynb
│
└── Text_Summarization/
│   └── <model>_Text_Summarization_Different_Prompting_Techniques.ipynb
    └── Text_Summarization_Prompt.ipynb
```

**Notebook Components**
Each notebook follows a consistent experimental structure. The main components are:
1. Environment and Library Setup: Imports and install the required Python libraries.
2. Dataset Loading: Loads the dataset used for evaluation.
3. Data Preparation: Formats the input examples according to the requirements of the corresponding task.
4. Prompt Construction: Defines the prompts used for the different prompting techniques.
5. Model: Load the model and sends the constructed prompts to the selected LLM and records the generated responses.
6. Output Processing: Processes the model responses into the format required for evaluation.
7. Evaluation: Compares the model predictions or generated summaries with the corresponding reference data using the task-specific evaluation metrics.
8. Results: Displays or stores the evaluation results for the corresponding prompting technique.

---

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
The project is organized into Jupyter notebooks, with each notebook corresponding to a specific NLP task and language model.

Each notebook is named according to the task being evaluated and the model used for the experiments.

Each notebook is divided into three main prompting sections:
* Zero-Shot Prompting
* Few-Shot Prompting
* Chain-of-Thought (CoT) Prompting

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

## Dataset Paper Citations

* **SANAD:** Einea, O., Elnagar, A., & Al Debsi, R. (2019). Sanad: Single-label arabic news articles dataset for automatic text categorization. Data in brief, 25, 104076.
* **ASAD:** Alharbi, B., Alamro, H., Alshehri, M., Khayyat, Z., Kalkatawi, M., Jaber, I. I., & Zhang, X. (2020). ASAD: A twitter-based benchmark arabic sentiment analysis dataset. arXiv preprint arXiv:2011.00578.
* **XL-Sum:** Hasan, T., Bhattacharjee, A., Islam, M. S., Mubasshir, K., Li, Y. F., Kang, Y. B., ... & Shahriyar, R. (2021, August). XL-sum: Large-scale multilingual abstractive summarization for 44 languages. In Findings of the Association for Computational Linguistics: ACL-IJCNLP 2021 (pp. 4693-4703).
* **Arabic-MMLU:** Koto, F., Li, H., Shatnawi, S., Doughman, J., Sadallah, A., Alraeesi, A., ... & Baldwin, T. (2024, August). ArabicMMLU: Assessing massive multitask language understanding in Arabic. In Findings of the Association for Computational Linguistics: ACL 2024 (pp. 5622-5640).

## Author

**Sanaa Kaddoura**

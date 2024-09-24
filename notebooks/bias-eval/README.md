# Bias Evaluation

A structured bias evaluation methodology is crucial for addressing potential fairness issues. To assess FinBERT's fairness, we developed a series of notebooks that evaluate the model's performance on news from both the Global North (GN) and Global South (GS). Despite the majority of training data originating from GN countries, we found no significant disparity in performance between the two groups. However, we observed inconsistencies in model performance when tested on news datasets from the Global South. Additionally, the model's predictions were influenced by altering sentence order, adding a single strongly positive statement to otherwise negative content, or introducing large numerical values that appeared positive. These findings are also limited to English-language news, as the model is designed for analyzing English sentiment. We encourage researchers to fork this repository and apply the notebooks to their own datasets and models, including those in different or multilingual contexts.

## Main Steps

Step 1 uses a synthetic dataset that explicitly reveals sources of bias, structured as probability- and embedding-based evaluation recipes:

- [Data Generation Notebook](./10-findata-generation.ipynb)
- [Mistral70 Model Outputs Evaluation](./11-finbert-eval-synthetic-mistral.ipynb)
- [Phi3.5 Model Outputs Evaluation](./12-finbert-eval-synthetic-phi.ipynb)

Step 2 evaluates the model against data released by another country (e.g. Indian News dataset) to assess its performance in relation to more implicit biases: 

- [Indian News Dataset Evaluation](./21-finbert-eval-indian-data.ipynb)
- [Stanze NER and Entity-based Evaluation](./22-entity-based-eval-with-stanza.ipynb)

Step 3 examines individual problematic samples using token-based interpretability methods (e.g. integrated gradients):

- [Using LIT Interface with FinBERT and Indian News](./30-demo-lit-nlp.ipynb)
- [Captum Integrated Gradients](./31-captum-integrated-gradients.ipynb)
- [LIME Example](./32-lime-finbert.ipynb)

## Fairness Performance

Our experiments showed that FinBERT does not exhibit significant group disparity when comparing synthetic and real-world datasets from both Global South and Global North samples. However, we observed inconsistencies in model performance when tested on news datasets from the Global South. You can read a detailed analysis in our paper.

**Synthetic Data Performance:**

| **Gen. Model** | **Global Pos.** | **TPR**  | **FPR**  |
|----------------|-----------------|----------|----------|
| Mistral70b     | Overall          | 0.9874   | 0.00247  |
| Mistral70b     | GN               | 0.9807   | 0.0038   |
| Mistral70b     | GS               | 0.9941   | 0.0011   |
| Phi3.5         | Overall          | 0.9802   | 0.0370   |
| Phi3.5         | GN               | 0.9770   | 0.0440   |
| Phi3.5         | GS               | 0.9835   | 0.0301   |

**Indian News 3-Category Accuracy Performance:**

| **Class**   | **Precision** | **Recall** | **F1-score** | **Support** |
|-------------|---------------|------------|--------------|-------------|
| Negative    | 0.75          | 0.54       | 0.63         | 8987        |
| Neutral     | 0.45          | 0.61       | 0.52         | 8987        |
| Positive    | 0.60          | 0.55       | 0.57         | 8987        |

*Overall Accuracy is 0.57 (total: 26961)*

**Indian News Binary (Positive Negative) Performance:**

| **Group**   | **TPR**  | **FPR**  |
|-------------|----------|----------|
| Overall     | 0.8723   | 0.1804   |
| India       | 0.8826   | 0.1658   |
| Non-India   | 0.8656   | 0.1882   |

## Reliability Performance

In our interpretability experiments, we identified two key issues that can manipulate model performance—issues that financial article writers could exploit to influence a model's decision. First, adding a strong positive statement at the end of a sentence can alter the model's interpretation of the overall sentiment. Second, incorporating large numerical figures can also shift the model's prediction. These vulnerabilities could be used to mislead financial market participants. Practitioners should safeguard their systems against news structured to exploit these weaknesses and manipulate the model’s decision.

### Model Reliability

Although the model is fair based on our evaluation, it turns out that the model can be tricked to give more "positive" classification results when (1) we add a strong positive outlook for the future, and (2) add some large quantities between sentences.
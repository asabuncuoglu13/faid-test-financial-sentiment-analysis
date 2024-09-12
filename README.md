# FAID Test: Financial Sentiment Analysis

This repository is using a set of algorithms to reduce bias in financial sentiment classification models such as FinBERT. The structure of this repository is based on FAID's project template which is also available on a seperate [Github repository](). You can use this template directly by forking.

# Fairness Financial Sentiment Analysis

In fairness experiments, researchers mainly utilise tabular data and binary classification tasks to demonstrate their algorithm's impact on the commonly used fairness notions such as equal opportunity or equalized odds. 

In the end, we also followed a similar strategy and tabularized our data and created binary sensitive characteristics based on the financial definitions. For example, rather than conducting a country-level analysis, we used the terms "global north" and "global south" to analyse the fairness outcomes of our experiments.

<a title="Jovan.gec, CC BY-SA 4.0 &lt;https://creativecommons.org/licenses/by-sa/4.0&gt;, via Wikimedia Commons" href="https://commons.wikimedia.org/wiki/File:The_Brandt_Line.png"><img width="512" alt="The Brandt Line" src="https://upload.wikimedia.org/wikipedia/commons/2/2c/The_Brandt_Line.png?20200925192502"></a>



## Structure
```
/project
|-- /data                # Data storage and versioning
|   |-- raw              # Raw data
|   |-- processed        # Processed data
|   |-- output           # Generated data
|
|-- /notebooks           # Jupyter notebooks for experiments and EDA
|
|-- /src                 # Source code for the project
|   |-- /data            # Data handling scripts
|   |-- /features        # Feature engineering scripts
|   |-- /models          # Model definitions and training scripts
|   |-- /evaluation      # Model evaluation scripts
|   |-- /deployment      # Scripts for deployment
|
|-- /tests               # Unit and integration tests
|
|-- /configs             # Configuration files (e.g., for hyperparameters)
|
|-- /utils               # Utility scripts and helpers
|
|-- /ci-cd               # CI/CD pipeline definitions (In our case .github)
|
|-- requirements.txt     # Dependencies
|-- README.md            # Project documentation
```
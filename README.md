# FAID Template

This project template is also available on a seperate [Github repository]() that you can directly fork and use as a template.

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
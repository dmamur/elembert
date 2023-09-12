# elementsem
Deep learning model for tasks related to chemical classification.
![Picture1](https://github.com/dmamur/elementsem/assets/60742014/c3158120-d6cf-4bb7-9b95-dcacfe4e97eb)

The 'data' folder contains .csv files already converted to the input data format, which helps save computational resources.

The 'Notebooks' folder contains examples of Jupyter notebooks for model V0, including data downloaded directly from the benchmark page before training.

The 'Models' folder contains PCA-KMeans models and dictionary files.

The main three notebooks are presented on the main page:
- elembert_classification.ipynb: This is a general file for all datasets. By changing the dataset name, it is possible to perform classification training. The BERT module code is taken from https://keras.io/examples/nlp/masked_language_modeling/.

- elembert_classification_matbench.ipynb: This notebook performs classification of the matbench dataset.

- element_classifier.ipynb: An example of how subelements can be calculated from PCA-KMeans models.

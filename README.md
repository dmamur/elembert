# elEmBERT - element Embeddings and Bidirectional Encoder Representations from Transformers
Deep learning model for tasks related to chemical classification.
![Picture1](https://github.com/dmamur/elementsem/assets/60742014/c807b5ff-187d-4514-a360-4ddcc5f2fd26)


The 'data' folder contains .csv files already converted to the input data format, which helps save computational resources.

The 'Notebooks' folder contains examples of Jupyter notebooks for model V0, including data downloaded directly from the benchmark page before training.

The 'Models' folder contains PCA-KMeans models and dictionary files.

The main three notebooks are presented on the main page:
- elembert_classification.ipynb: This is a general file for all datasets. By changing the dataset name, it is possible to perform classification training. The BERT module code is taken from https://keras.io/examples/nlp/masked_language_modeling/.

- elembert_classification_matbench.ipynb: This notebook performs classification of the matbench dataset.

- element_classifier.ipynb: An example of how subelements can be calculated from PCA-KMeans models.

## Perfomance

|Benchmark	|V0	            |V1           | Previous best   |
|--- |---|--- |---|
|Matbench	|0.961 ± 0.001	|***0.965 ± 0.001***| 0.950 $^{AtomSets}$|
|SG			|0.944 ± 0.003	|0.968 ± 0.002|***1***       $^{CegaNN  }$|
|LA			|0.475 ± 0.014	|0.980 ± 0.003| ***1***       $^{CegaNN  }$|
|DIM		|0.893 ± 0.013	|0.958 ± 0.003| ***1***       $^{CegaNN  }$|
|BACE		|0.827 ± 0.005	|0.856 ± 0.010| ***0.88***8 $^{GLAM    }$|
|BBBP		|0.900 ± 0.020	|0.905 ± 0.025| ***0.932*** $^{GLAM    }$|
|CLINTOX	|0.945 ± 0.011	|***0.951 ± 0.016***| 0.948 $^{TrimNET }$|
|HIV		|0.978 ± 0.002	|***0.979 ± 0.003***| 0.776 $^{GMT     }$|
|SIDER		|***0.778 ± 0.032***	|0.777 ± 0.028| 0.659 $^{GLAM    }$|
|TOX21		|***0.961 ± 0.006***	|0.958 ± 0.007| 0.841 $^{TrimNET }$|











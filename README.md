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
The table displays the ROC-AUC performance of two model versions applied to the datasets listed. Bold font indicates the best performance, and the last column showcases previous results obtained from other models. elEmBERT-V0 denotes models that utilize chemical element embeddings, while elEmBERT-V1 employs subelement embeddings as input for the BERT module.

|Benchmark	|elEmBERT-V0        |elEmBERT-V1   | Previous best   |
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
|TOX21		|***0.961 ± 0.006***	|0.958 ± 0.007| 0.860 $^{TrimNET }$|


ROC-AUC performances of various models on the SIDER dataset. Meta-MGNN denotes the prior top-performing results. 
|SIDER N|1|2|3|4|5|6|7|8|9|10|11|12|13|14|15|16|17|18|19|20|21|22|23|24|25|26|27|Average|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|V0|0.626|0.756|0.972|0.735|0.843|0.736|0.958|0.846|0.775|0.712|0.748|0.93|0.802|0.859|0.841|0.675|0.898|0.812|0.792|0.761|0.843|0.75|0.909|0.669|0.758|0.952|0.798|0.778|
|V1|0.635|0.723|0.976|0.7|0.881|0.677|0.957|0.865|0.757|0.662|0.769|0.918|0.785|0.838|0.877|0.732|0.921|0.833|0.781|0.798|0.873|0.781|0.918|0.545|0.726|0.962|0.731|0.777|
|Meta-MGNN|0.754|0.693|0.723|0.744|0.817|0.741|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|0.747|

ROC-AUC performances of 12 tasks from the Tox21 dataset.
Model|nr-ahr|nr-ar-lbd|nr-arom|nr-ar|nr-er-lbd|nr-er|nr-ppar-g|sr-are|sr-atad5|sr-hse|sr-mmp|sr-p53|Ave|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|V0|0.947|0.987|0.973|0.982|0.972|0.924|0.991|0.908|0.982|0.975|0.935|0.97|0.961|
|V1|0.953|0.981|0.972|0.982|0.976|0.93|0.989|0.911|0.984|0.976|0.941|0.97|0.958|
|Meta-MGNN|-|-|-|-|-|-|-|-|-|0.748|0.804|0.79|0.781|


The figures below illustrate the confusion matrix in (a), showcasing the performance of the elEmBERT-V1 model in classifying the MP metallicity (picture above) task and the SR-MMP task from the Tox21 dataset (picture below). The t-SNE plot in (b) displays the embeddings of the entire reference dataset, categorized by labels, revealing a smooth differentiation among labels within the feature space. Figure (c) demonstrates how our model classifies the reference dataset.
![modelR_matbenchV1](https://github.com/dmamur/elementsem/assets/60742014/8f30044e-5089-441f-868b-e74a01cf81f3)


![modelR_sr-mmpV1](https://github.com/dmamur/elementsem/assets/60742014/42960abc-17a2-478b-84d9-38899399c0ff)











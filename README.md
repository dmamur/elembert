# elEmBERT - element Embeddings and Bidirectional Encoder Representations from Transformers

This repository presents deep learning models for chemical classification tasks. These models use atomic pair distribution functions (PDF) and atom types (elements) as input data. 
In the initial stage, element embedding vectors are constructed by converting elements into tokens. These encoded inputs are then passed to the BERT module, omitting the positional encoding component, thereby establishing a comprehensive framework for chemical analysis. The BERT module could be constructed from various combinations of embedding sizes, encoder-decoder layers, and attention heads. Schematic Illustration of the elEmBERT-V0 model presented below: 

![ModelV0](https://github.com/dmamur/elementsem/assets/60742014/69492ddd-2dc0-492e-9090-e46380e578b5)


elEmBERT-V0 solely relies on compound composition, whereas elEmBERT-V1 generates tokens by separating (classifying) elements into sub-elements based on PDF information. This separation process is facilitated by K-means algorithm. As a result, we have expanded our vocabulary size from 101 to 565, along with the corresponding increase in model parameters. This expansion enables us to build another, more efficient, but resource-intensive model - elEmBERT-V1:

![Figure_1](https://github.com/user-attachments/assets/142f48cf-1e15-4d9b-a57a-552927488133)



The 'data' folder contains.csv files already converted to the input data format, which helps save computational resources.

The 'Notebooks' folder contains examples of Jupyter notebooks for model V0, including data downloaded directly from the benchmark page before training.

The 'Models' folder contains K-means models and dictionary files.

The main three notebooks are presented on the main page:
- elembert_classification.ipynb: This is a general file for all datasets. By changing the dataset name, it is possible to perform classification training. The BERT module code is taken from https://keras.io/examples/nlp/masked_language_modeling/.

- elembert_classification_matbench.ipynb: This notebook performs classification of the matbench dataset.

- element_classifier.ipynb: An example of how subelements can be calculated from k-means models. Inputs - PDFs - are calculated using the ASE library. 

## Perfomance
The table presents the ROC-AUC performance of two model versions applied to the datasets listed. The first four datasets are classification tasks of inorganic compunds, the remaining tasks involve organic molecules. Bold font indicates the best performance, and the last column shows previous results obtained from other models. elEmBERT-V0 denotes models that utilize chemical element embeddings, while elEmBERT-V1 employs subelement embeddings as input for the BERT module.
In both models, we have used an embedding size of 32, 2 layers, and 2 attention heads.
|Benchmark|elEmBERT-V0 |elEmBERT-V1| Previous best   |
|--- |---|--- |---|
|Matbench: is_metal|0.961 |***0.965***| 0.950 $^{AtomSets}$|
|Spacegroup|0.945 |0.952 |***1***       $^{CegaNN  }$|
|Liquid-Amorphous|0.475	|0.983| ***1***       $^{CegaNN  }$|
|Dimensionality|0.866	|0.958 | ***1***       $^{CegaNN  }$|
|BACE|0.732 |0.789| ***0.88***8 $^{GLAM    }$|
|BBBP|0.903	|0.909| ***0.932*** $^{GLAM    }$|
|CLINTOX|***0.962***|0.959| 0.948 $^{TrimNET }$|
|HIV|***0.982***	|0.972| 0.776 $^{GMT     }$|
|SIDER|***0.778***	|0.773 | 0.659 $^{GLAM    }$|
|TOX21|0.965	|***0.967***| 0.860 $^{TrimNET }$|


MP metallicity &  \underline{0.961} & \textbf{0.965}  & 0.950 \cite{Chen2021AtomSets} \\
SG & 0.945  & \underline{0.952} & \textbf{1.000} \cite{Banik2023CEGANN}\\
LA & 0.500  & \underline{0.983}  & \textbf{1.000} \cite{Banik2023CEGANN}\\
DIM & 0.866  & \underline{0.958}  & \textbf{1.000} \cite{Banik2023CEGANN}\\
BACE & 0.732  & \underline{0.789}  & \textbf{0.888} \cite{Li2022GLAM}\\
BBBP & 0.903  & \underline{0.909} & \textbf{0.932} \cite{Li2022GLAM}\\
ClinTox & \textbf{0.962}  & \underline{0.959}  & 0.948 \cite{{Li2021TrimNet}}\\
HIV & \textbf{0.982}  & \underline{0.972} & 0.776 \cite{Baek2021Accurate}\\
SIDER & \textbf{0.778} & \underline{0.773}  & 0.659 \cite{Li2022GLAM}\\
Tox21 & \underline{0.965}  & \textbf{0.967} & 0.860 \cite{{Li2021TrimNet}}\\

ROC-AUC performances of 27 tasks from the SIDER dataset. Meta-MGNN denotes the prior top-performing results. 
|SIDER N|1|2|3|4|5|6|7|8|9|10|11|12|13|14|15|16|17|18|19|20|21|22|23|24|25|26|27|Average|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|V0      | 0.684 | 0.709 | 0.985 | 0.676 | 0.847 | 0.738 | 0.945 | 0.839 | 0.739   | 0.775 | 0.908 | 0.819 | 0.853 | 0.809 | 0.723 | 0.926 | 0.822 | 0.724     | 0.724 | 0.759 | 0.764 | 0.700 | 0.927 | 0.598 | 0.747 | 0.925 | 0.698 | 0.778|
|V1      | 0.663 | 0.707 | 0.983 | 0.689 | 0.838 | 0.744 | 0.941 | 0.832 | 0.724  |  0.760 | 0.892 | 0.816 | 0.849  | 0.782 | 0.737 | 0.917 | 0.833 | 0.736  | 0.736 | 0.772 | 0.726 | 0.708 | 0.923 | 0.599 | 0.742 | 0.916 | 0.684  | 0.773 |
|Meta-MGNN|0.754|0.693|0.723|0.744|0.817|0.741|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|0.747|

ROC-AUC performances of 12 tasks from the Tox21 dataset.
Model|nr-ahr|nr-ar-lbd|nr-arom|nr-ar|nr-er-lbd|nr-er|nr-ppar-g|sr-are|sr-atad5|sr-hse|sr-mmp|sr-p53|Average|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V0 | 0.955 | 0.987 | 0.980 | 0.983 | 0.978 | 0.932 | 0.988 | 0.913 | 0.985 | 0.974 | 0.938 | 0.972 | 0.965 |
| V1 | 0.961 | 0.989 | 0.979 | 0.982 | 0.978 | 0.935 | 0.986 | 0.913 | 0.983 | 0.974 | 0.946 | 0.973 | 0.967 |
|Meta-MGNN|-|-|-|-|-|-|-|-|-|0.748|0.804|0.79|0.781|


The figures below illustrate the confusion matrix in (a), shows the performance of the elEmBERT-V1 model in classifying the MP metallicity task and the SR-MMP task from the Tox21 dataset. The t-SNE plot in (b) displays the embeddings of the entire reference dataset, categorized by labels (is metal or not, toxic or not), revealing a smooth differentiation among labels within the feature space. Figure (c) demonstrates how our model classifies the reference dataset.

![elembertRpos_matbench_Km_E_32_H_2_L_2_fold8_test_results pkl_tsnePaper](https://github.com/user-attachments/assets/efc66ea2-9b4b-4065-993c-c8b09e72171a)

![Figure_6](https://github.com/user-attachments/assets/50be6885-7330-4673-a89f-081d63a25ea2)


Further information concerning the development of elEmBERT can be found in our [publication](https://arxiv.org/abs/2309.09355):
```
@misc{shermukhamedov2023structure,
      title={Structure to Property: Chemical Element Embeddings and a Deep Learning Approach for Accurate Prediction of Chemical Properties}, 
      author={Shokirbek Shermukhamedov and Dilorom Mamurjonova and Michael Probst},
      year={2023},
      eprint={2309.09355},
      archivePrefix={arXiv},
      primaryClass={physics.chem-ph}
}
```






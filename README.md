# KG-MultiResCNN - Knowledge Guided Multi-filter Residual Convolutional Neural Network

This repository contains the Python Notebook file that I have created as part of my Master's thesis "Deep Learning for Differential Diagnosis and Prediction in EHR Data" from WeST at the University of Koblenz-Landau.
 
The thesis was supervised by [Prof. Dr. Matthias Thimm](https://www.mthimm.de/) and [Dr. Zeyd Boukhers](https://zeyd.boukhers.com/). This repository was made by [Prantik Goswami](https://scholar.google.com/citations?user=ei5YCgcAAAAJ).

The notebook file contains the Python code for the topic model, *KG-MultiResCNN*, which uses raw clinical text to predict ICD (ICD-9) codes related to the text. The model uses additional knowledge for medically enriching entities along with word embedding. The concatenated embeddings then pass through a multi-filter Convolution Neural Network followed by a series of two ResNet blocks. The model is equipped with a label attention layer for better prediction. Finally, a fully connected layer provides the output prediction.

This work is based on top of the work [MultiResCNN](https://github.com/foxlf823/Multi-Filter-Residual-Convolutional-Neural-Network)  

## Installation

### Requirements
The following packages are required to be pre-installed for the project.
* gensim                    3.4.0
* nltk                      3.3
* numpy                     1.15.1
* python                    3.6.7
* pytorch                   1.10.0
* scikit-learn              0.20.0
* allennlp                  0.8.4
* pytorch-pretrained-bert   0.6.2
* overrides   				3.1.0
* allennlp   				0.8.4
* transformers				4.4.2

### Data
In this thesis, [MIMIC-III](https://physionet.org/content/mimiciii/1.4/) v1.4 data is used. The data can be downloaded for research purposes only. A data protection agreement is required to access the data. More details can be found on the website.  

## Reproduce Results
-----
### 1. Prepare data
- Download the MIMIC-III full data and store it into a repository.
- Set the downloaded repository path to the *'args'* dictionary with key *'origin_path'*.
- Unzip to get these necessary files: *'DIAGNOSES_ICD.csv'*, *'PROCEDURES_ICD.csv,'* and *'NOTEEVENTS.csv'* files.
- Set output repository path to the *'args'* dictionary with key *'out_path'*.
- Run the function `DataProcessing(args)`. Before this the KG-Embedding need to setup.

### 2. Prepare KG-Embedding
- Create the wikidump and indexing using the below codes.(commented out code present in the notepad file).
```
import wikimapper
wikimapper.download_wikidumps(dumpname="enwiki-latest", path="<desired download path>")
wikimapper.create_index(dumpname="enwiki-latest",path_to_dumps="<desired download path>", 
                         path_to_db= "<desired download path>/index_enwiki-latest.db")
```
- Download pre-trained wikidata knowledge graph from the [Metaresearch](https://github.com/facebookresearch/PyTorch-BigGraph#pre-trained-embeddings) repository to a desired local drive. (commented out code present in the notepad file).
- Set the *'args'* dictionary with key *'graph_embedding_file'* as the local downloaded repository of the wikidata knowledge graph.

### 3. Train and test using full MIMIC-III data
- Set the *'args'* dictionary with key *'Y'* as *'full'*.
- Set the *'args'* dictionary with key *'MODEL_DIR'* as a desired local path to store the trained model.
- Run the function `Run(args)` to train and test on *'full'* codes.

### 4. Train and test using top-50 MIMIC-III data
- Set the *'args'* dictionary with key *'Y'* as *'50'*.
- Set the *'args'* dictionary with key *'MODEL_DIR'* as a desired local path to store the trained model.
- Run the function `Run(args)` to train and test on '50' codes.

## Acknowledgements
This project was developed on top of MultiResCNN as described by Fei Li and Hong Yu (2020) in their paper [*ICD Coding from Clinical Text Using Multi-Filter Residual Convolutional Neural Network*](https://doi.org/10.1609/aaai.v34i05.6331).


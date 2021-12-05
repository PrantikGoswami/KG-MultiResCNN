# KG-MultiResCNN - Knowledge Guided Multi-filter Residual Convolutional Neural Network

This repository contains the Python Notebook file that I have created as part of my Master's thesis "Deep Learning for Differential Diagnosis and Prediction in EHR Data" from WeST at the University of Koblenz-Landau.
 
The thesis was supervised by [Prof. Dr. Matthias Thimm](https://www.mthimm.de/) and [Dr. Zeyd Boukhers](https://zeyd.boukhers.com/). This repo was made by [Prantik Goswami](https://scholar.google.com/citations?user=ei5YCgcAAAAJ).

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



## Acknowledgements
This project was developed on top of MultiResCNN as described by Fei Li and Hong Yu (2020) in their paper [*ICD Coding from Clinical Text Using Multi-Filter Residual Convolutional Neural Network*](https://doi.org/10.1609/aaai.v34i05.6331).


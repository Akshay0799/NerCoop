
## Overview

This repo contains the code to perform NER as a Span PRediction Task, which was inspired from the "SpanNer: Named Entity Re-/Recognition as Span Prediction" paper written by Fu et al. SpanNER consists of a neural network model that operates on the span level, which means that it identifies named entities by predicting the starting and ending positions of the entity spans within a given text sequence. SpanNER has been shown to achieve state-of-the-art performance on several NER benchmarks. 

This repo contains the code of SpanNER which was modified to perform FewShot Learning for the task of CrossLingual NER.


## Quick Installation

- `python3`
- `PyTorch`
- `pytorch-lightning`

Run the following script to install the dependencies,
```
pip3 install -r requirements.txt
```


## Data Preprocessing

The dataset needs to be preprocessed, before running the model.
We provide `dataprocess/bio2spannerformat.py` for reference, which gives the CoNLL-2003 as an example. 
First, you need to download datasets, and then convert them into BIO2 tagging format. We provided the CoNLL-2003 dataset with BIO format in the `data/conll03_bio` folder and its preprocessed format dataset in the `data/conll03` folder.



## How to Run SpanNER?

Here, we give CoNLL-2003 as an example. You may need to change the `DATA_DIR`, `PRETRAINED`, `dataname`, and `n_class` to your own dataset path, pre-trained model path, dataset name, and the number of labels in the dataset, respectively. 

To load from a checkpoint locally and continue training from there, the 'pretrained_checkpoint' argument can be added to the Python command along with the path of the pretrained model. The 'proportion' argument can be modified to specify the percentage of training data to be used.

Make sure you have access to the GPU from and run this command to start training the Span NER model on the conll03 dataset.

```
./run_conll03_spanner.sh
```
## Models Used

Multilingual-BERT which was trained on more than 100 languages was used to
## How to evaluate ?

In the 'evaluate.py' file, add the path to the test set in the 'args['data_dir'] variable. To change the percentage of training data to be used, args['proportion'] can be modified.

In the main function, the path to the checkpoint of the model can be added in the 'midpath' variable along with the model name, before running the file.

```
python evaluate.py
```

## Bib

```
@article{fu2021spanner,
  title={SpanNer: Named Entity Re-/Recognition as Span Prediction},
  author={Fu, Jinlan and Huang, Xuanjing and Liu, Pengfei},
  journal={arXiv preprint arXiv:2106.00641},
  year={2021}
}
```



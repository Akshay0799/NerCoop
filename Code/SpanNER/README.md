## SpanNER: Named EntityRe-/Recognition as Span Prediction
[**Overview**](https://hub.fastgit.org/neulab/SpanNER#overview) | 
[**Demo**](https://hub.fastgit.org/neulab/SpanNER#demo) | 
[**Installation**](https://hub.fastgit.org/neulab/SpanNER#quick-installation) |
[**Preprocessing**](https://hub.fastgit.org/neulab/SpanNER#data-preprocessing) |
[**Prepare Models**](https://hub.fastgit.org/neulab/SpanNER#prepare-models) |
[**Running**](https://hub.fastgit.org/neulab/SpanNER#how-to-run) |
[**System Combination**](https://hub.fastgit.org/neulab/SpanNER#system-combination) |
[**Bib**](https://hub.fastgit.org/neulab/SpanNER#bib)

This repository contains the code for our paper [SpanNER: Named EntityRe-/Recognition as Span Prediction](https://arxiv.org/pdf/2106.00641v1.pdf) (ACL 2021).

The model designed in this work has been deployed into [ExplainaBoard](http://explainaboard.nlpedia.ai/leaderboard/task-ner/index.php).

## Overview

We investigate complementary advantages of systems based on different paradigms: span prediction model and sequence labeling framework. We then reveal that span prediction, simultaneously, can serve as a system combiner to re-recognize named entities from different systems’ outputs. We experimentally implement 154 systems on 11 datasets, covering three languages. Comprehensive results show the effectiveness of span prediction models that serve as base NER systems and system combiners.

<!-- Two roles of span prediction models (boxes in blue): 
* as a base NER system 
* as a system combiner. -->

<div  align="center">
 <img src="pic/spanner.png" width = "550" alt="d" align=center />
</div>

## Demo

We deploy SpanNER into the [ExplainaBoard](http://explainaboard.nlpedia.ai/leaderboard/task-ner/index.php).
<div  align="center">
 <img src="pic/demo.gif"  align=center />
</div>


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

The download links of the datasets used in this work are shown as follows:
- [CoNLL-2003](https://www.clips.uantwerpen.be/conll2003/ner/)
- [CoNLL-2002](https://www.clips.uantwerpen.be/conll2002/ner/)
- [OntoNotes 5.0](https://catalog.ldc.upenn.edu/LDC2013T19)
- [WNUT-2016](http://noisy-text.github.io/2016/ner-shared-task.html)
- [WNUT-2017](http://noisy-text.github.io/2017/emerging-rare-entities.html)



## Prepare Models

For English Datasets, we use [BERT-Large](https://github.com/google-research/bert).

For Dutch and Spanish Datasets, we use [BERT-Multilingual-Base](https://huggingface.co/bert-base-multilingual-uncased).






## How to Run?

Here, we give CoNLL-2003 as an example. You may need to change the `DATA_DIR`, `PRETRAINED`, `dataname`, and `n_class` to your own dataset path, pre-trained model path, dataset name, and the number of labels in the dataset, respectively. 

To load from a checkpoint locally and continue training from there, the 'pretrained_checkpoint' argument can be added to the Python command along with the path of the pretrained model. The 'proportion' argument can be modified to specify the percentage of training data to be used.

```
./run_conll03_spanner.sh
```

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


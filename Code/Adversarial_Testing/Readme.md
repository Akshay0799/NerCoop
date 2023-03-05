# Improving NER Robustness through Adversarial Testing

We explore methods for creating adversarial test sets for Named Entity Recognition (NER) in English, German, and Hindi by altering the occurrences of the named entities.
Our approaches use easily replicable and expandable methods to create new test sets by replacing entities and/or slightly altering their surrounding context in the original 
test set instances. and slightly altering their surrounding context. Our experiments reveal that NER models are not fully robust to these changes, leading to 
fluctuations in F1 scores. We show that re-training with data augmentation or fine-tuning with adversarial data can improve NER model performance on both original 
and adversarial test sets. We also provide the Adversarial Test sets in this repo.


## Adversarial Test Set Creation Approaches

### Random Sampling
In this approach, the goal is to substitute entity occurrences in the test set with an entity of the same category, maintaining the sentence structure and grammar. 
The rest of the sentence remains unchanged during the process.
### Gazetteers
This method uses an established gazetteer to substitute original entities with new ones of the same type. The replacement is performed using a Python library called 
Faker, which is capable of generating synthetic data for various applications and supports multiple languages and regions. The Person and Location entities in all 
datasets across the three languages were replaced using this tool.

### Masking
We utilized pre-trained transformer-based language models, trained with a masked language modeling objective, to modify the context of the original test datasets. 
The language model masks the tokens surrounding named entities in a test sentence that are not part of the entity.

### Paraphrasing
The aim of this method is to modify the input sentence structure while preserving the named entities. To achieve this, Quillbot, an online English paraphrasing tool
, was used to randomly select and rephrase 500 sentences from the test set.
### Masking + Parpahrasing
Previous methods aimed at changing either the context or the entities alone. However, the proposed approach combines both by using masking and random sampling. 
These techniques are simple and effective for all three languages, enabling the creation of a new adversarial test set by combining them.

## Robustness improving Methods

### Adversarial Fine-Tuning
A portion of adversarial test is used to fine tune the trained NER model further to enhance its performance.
### Augmented Re-Training
The portion of Adversarialk Test set is appended to the training data and the whole NER model is trained from scratch on the Augmented Train data.

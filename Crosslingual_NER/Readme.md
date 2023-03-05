# CrossLingual NER using Few Shot learning

Few Shot Learning refers to the training of a model using limtied number of annotated examples. Few-shot learning in the context of cross-lingual NER can be carried out 
with the help of multilingual models which have been trained on multiple languages. The goal here is to transfer the knowledge that the NER model gains by 
pre-training on a mixture of languages to generalize better in the future and train on a new language with less training data.

## NER Models Used 
* SpanNER
* Multilingual BERT
* XLM - Roberta

## File Structure

* SpanNER File contains the code to train a Span Based NER model in a Few-shot learning setup
* NER_nerda contains the code to train MBERT/XLM-R in a Few-shot learning setup

# NLP CW

Authors: Matthew Baugh, Kexin Gu, George Soteriou

## Introduction

This repo contains our experiments for Subtask 1 of SemEval-2020 Task 7.

`data/task-1` contains [Humicroedit dataset](https://www.cs.rochester.edu/u/nhossain/humicroedit.html) for this regression task, as well as FunLines dataset that we use to extend our training set.

* `dev.csv`: Humicroedit validation set

* `test.csv`: Humicroedit test est

* `train_funlines.csv`: FunLines training set for additional training samples

* `train.csv`: Humicroedit training set

## Pre-trained Approaches

### GloVe Based Model

### Transformer Based Model

`BERT.ipynb` contains the BERT based regression model, and `Roberta.ipynb` contains the RoBERTa based regression model.

Most of the implementians are the same in both notebooks. The only difference is the BERT or RoBERTa based model for the regressor.

In the second code cell for both notebooks, we have all the hyperparamters for the model:

```
ADD_UNEDITED = True
ADD_TF = False
ADD_TF_UNEDITED = False
VAL_ADD_UNEDITED = False

PRETRAINED_WEIGHTS = ...

BATCH_SIZE = 32
NUM_EPOCHS = 6
VAL_STEPS = 100

MODEL_PATH = ...
```

The first 4 are flags for our dataset extension tricks. The base training set contains edited Humicroedit headlines with their corresponding score. Enabling the flags will extend the training set/validation set as following:

* `ADD_UNEDITED`: add unedited headlines from Humicroedit training set with score of 0 to training set.

* `ADD_TF`: add edited headlines from FunLines training set with their corresponding score to training set.

* `ADD_TF_UNEDITED`: add unedited headlines from FunLines training set with score of 0 to training set.

* `VAL_ADD_UNEDITED`: add unedited headlines from Humicroedit validation set with score of 0 to validation set. **This flag is NOT used in any experiments**. We tried with setting this flag to `True` initially, but noticed significantly worse performance of the model. Thus this flag was set to `False` in all our experiments in the report.

`VAL_STEPS = 100` and `BATCH_SIZE = 32` are fixed in all experiments. `NUM_EPOCHS` varied during our experiments. Most of the models are trained with epoch of 6, but for model with larger training set we reduced the number of epochs. A full experiments record with their individual flags and epoch number could be found in [this sheet](https://docs.google.com/spreadsheets/d/14Z2V2v15gwpxJ5fGwdaLdaRUGhNI3KHaVu-nbzSCPvk/edit?usp=sharing).

## Non-pre-trained Approaches

# Sperm whale bioacoustics
> Sperm whale clan membership and coda type detection using inter click intervals


This repository builds on the work in [Deep Machine Learning Techniques for the Detection and Classification of Sperm Whale Bioacoustics](https://www.nature.com/articles/s41598-019-48909-4), a fascinating paper by Peter C. Bermant, Michael M. Bronstein, Robert J. Wood, Shane Gero & David F. Gruber.

The purpose of the repository is to:
* reproduce the RNN experiments, providing executable code with accompanying explanation to allow others to leverage these novel techniques on their data
* identify whether architectural changes and advanced training schedules (1cycle policy) could alleviate the need for the cumbersome pretraining step
* experiment with and report results of using Random Forest instead of the RNN, a model that can be trained to good effects without specialized deep learning knowledge, is not prone to overfitting, that can be trained without the need of a GPU and that lends itself very well to interpetation

Above all, the goal of the repository is to provide an introduction to the world of marine biology and modern machine learning techniques.

## Summary of results

We chose to focus on the clan detection and coda type detection tasks on the dominicana dataset. Those were the only tasks (apart from classification using CNN) where results were reported on the validation set and where we were able to reconstruct how the data was processed (based on [the paper](https://www.nature.com/articles/s41598-019-48909-4) and [the accompanying repository](https://github.com/dgruber212/Sperm_Whale_Machine_Learning)).

Our goal was not to go for the breadth of our inquiry, but rather to follow in the footsteps of the breakthrough paper to better understand the fascinating phenonemana of ICIs and their potential role in whale communication.

The notebooks were constructed in a way as to allow a broader audience to follow in our footsteps.

### Clan detection

|model|accuracy|
|:------:|:-----------|
|RNN (paper)|95.3%|
|RNN (ours) |93.7%|
|Random Forest |94.7%|

### Coda type detection

|model|accuracy|
|:------:|:-----------|
|RNN (paper)|99.9%|
|RNN (ours) |100%|
|Random Forest |99.6%|

Our RNN and Random Forest use the same sampling of the train and validation sets and thus these results are easiest to compare. The paper followed a different sampling of the train and validation sets.

Overall, the differences in performance, given the size of the validation set, are next to insignificant. All the models perform similarly.

An interesting result is the stronger performance of our Random Forest as compared to our RNN on the clan detection task.

We found no benefits to pretraining. For RNNs we got best results when training the entire model from scratch.

The main consideration that we would like to highlight is how much less compute and specialized knowledge was needed to get good results with Random Forest. Above all, the interpretability of the model is unparalleled. The robustness of the method to training on unbalanced data and its legendary ability to not overfit (while still packing enough variance to give good results) makes this a great model to have in one's toolbox.

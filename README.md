# One-Shot Drum Classification

Work-in progress. The aim is to experiment on automatic classification of drum one-shots from raw audio.

! Contributions are welcomed, notably for libraries of drum/percussion samples which are clearly associated with a class would be helpful to train the models !

! Please, get in touch if you would like to provide additional data to the experiment !

**Application 1:** Automatic creation of a large-scale dataset of drum samples e.g. for training synthesis models with conditioning on target drum classes such as

Clap, Cowbell, Cymbals, Hat, Kick, Snare, Tom

Visit the following repository for such a generative model: https://github.com/adrienchaton/neural_granular_synthesis

**Application 2:** An open-source tool for music producers to automatically organise their sound sample libraries.

**Application 3:** Creation of Drum Kits from non-drum samples e.g. take a database of environmental noises and select those with highest class probability to be assigned to a certain drum class of the kit.

## Experiment roadmap

* Setup a efficient and robust duplicate removal for audio files collected multiple times from different sources **(?)**

* Setup evaluation metrics and stratified 5-fold data split for balanced train/test sets. https://torchmetrics.readthedocs.io/

* Make a simple baseline using a pretrained audio embedding (e.g. OpenL3 trained on music data https://github.com/torchopenl3/torchopenl3) on top of which a statistical classifier is trained at predicting drum classes (e.g. Random Forest, AdaBoost)

* Train end-to-end and compare different neural network classifiers around the OpenL3 architecture:
  * OpenL3 audio encoder + MLP classifier
  * OpenL3 audio encoder + Deep Neural Decision Forests classifier (reference implementation in https://github.com/darth-c0d3r/deep-neural-decision-forests)
  * ... other ideas for transfer learning and unsupervised learning **(?)**

* Experiment on variable length classification (e.g. 1-3 sec. samples, RNN between embedding and classifier networks)

* Feedback Loop **(?)** Curate a larger dataset with high confidence and train again the classifiers

* Gather data from drumming performances using either onset annotations or automatic dectection to segment one-shots

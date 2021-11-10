---
# Please provide as much information here as possible. If you cannot fill in
# a field, leave it empty. There is no need for quotation marks if your entry
# consists of more than one word.

# list of authors (first name, last name), comma separated
# please put AIML researcher within <strong> XXX </strong> tags
authors: <strong>Konstantin Schürholt</strong>, Dimche Kostadinov, Damian Borth

# date of publication (YYYY-MM-DD)
date: 2021-11-09

# leave this as is
layout: post

# title of the publication
title: Self-Supervised Representation Learning on Neural Network Weights for Model Characteristic Prediction

# type of publication, please use captitalization (e.g., Journal Paper,
# Conference Poster, Workshop Contribution, ...)
itemtype: Conference Paper

# name of publisher/journal/conference; feel free to add additional
# information like volume number, page number, ...
publisher: NeurIPS 2021 - 35th Conference on Neural Information Processing Systems, Sydney, Australia.

# url to the official publication (could be conference, journal, arxiv)
puburl: https://neurips.cc/Conferences/2021/Schedule?showEvent=27428

# url to some pdf that is freely accessible (e.g., arxiv)
pdfurl: https://arxiv.org/abs/arXiv:2110.15288

# url to code repository (e.g., github)
codeurl: https://github.com/HSG-AIML/NeurIPS_2021-Weight_Space_Learning

# url to data repository (e.g., zenodo, github)
dataurl: https://zenodo.org/record/5645138

# email address of reponsible AIML author
contactemail: konstantin.schuerholt@unisg.ch

# publication language (e.g., English, German, ...)
language: English

# topical tags; try to cover the following topics:
# - general field (e.g., remote sensing, TTS, financial data, ...)
# - ML method (e.g., deep learning, gradient boosting, supervised learning,
#              semi-supervised learning, self-supervised learning ...)
# - task (e.g, classification, segmentation, representation learning, ...)
# important note: if your tag contains a whitespace, please replace the
# whitespace by an underscore!
tags: Representation_Learning Self-Supervised_Learning Weight_Space Parameter_Space Augmentation Model_Zoos
---

<!-- ![alt text](/images/2021-11-09-Self-Supervised_Representation_Learning_on_Neural_Network_Weights_for_Model_Characteristic_Prediction/scheme_v2.png) -->
{% include figure.html
url="/images/2021-11-09-Self-Supervised_Representation_Learning_on_Neural_Network_Weights_for_Model_Characteristic_Prediction/scheme_v2.png"
description="An overview of the proposed self-supervised representation learning approach. I. Populations of trained NNs form model zoos; each model is transformed in a vectorized form of its weights. II. Neural representations are learned from the model zoos using different augmentations, architectures, and Self-Supervised Learning tasks. III. Neural representations are evaluated on downstream tasks which predict model characteristics.
" %}
Self-Supervised Learning (SSL) has been shown to learn useful and information-preserving representations. Neural Networks (NNs) are widely applied, yet their weight space is still not fully understood. Therefore, we propose to use SSL to learn neural representations of the weights of populations of NNs. To that end, we introduce domain specific data augmentations and an adapted attention architecture.  Our empirical evaluation demonstrates that self-supervised representation learning in this domain is able to recover diverse NN model characteristics. Further, we show that the proposed learned representations outperform prior work for predicting hyper-parameters, test accuracy, and generalization gap as well as transfer to out-of-distribution settings.

# Background
Within Neural Network populations, not all model training is successful, i.e., some overfit and others generalize. This may be due to the non-convexity of the loss surface during optimization, the high dimensionality of the optimization space, or the sensitivity to hyperparameters, which causes models to converge to different regions in weight space. What is still not yet fully understood, is how different regions in weight space are related to model characteristics.  
Previous work investigating NN models often relies on data to compute the mapping of NN models, compares pairs of models or directly predicts single characteristics. In contrast, our idea is to investigate populations of models in representation space to identify model characteristics.
{% include figure.html
url="/images/2021-11-09-Self-Supervised_Representation_Learning_on_Neural_Network_Weights_for_Model_Characteristic_Prediction/population_to_representation.png"
description=""%}
Our goal is to learn task-agnostic, rich representations from populations of NN models which are able to reveal a diverse range of model characteristics. 

# Approach
Self-Supervised Learning is able to reveal latent structure in complex data without the need of labels. We propose a novel approach to apply SSL to learn representations of the weights of NN populations, as outlined in the scheme above. 
We introduce three augmentation methods for NN weights. In particular, the permutation augmentation leverages symmetries of the NN weight space to create samples that are equivariant in forward and backward pass. Empirically, we find the permutation augmentation necessary to learn generalizing representations. 
Further, we propose an attention-based architecture, which understands NN models as sequences of components, i.e., sequences of neurons. As SSL tasks, we evaluate reconstruction, a contrastive loss, and a combination of both.
As evaluation, we predict model characteristics, such as accuracy, epoch, or hyperparamters, from the learned representations.  

# Results
We evaluate our approach on eleven different model zoos. Across all of them, we find that neural representations can be learned and reveal the characteristics of the model zoos. We show that neural representations have high utility predicting hyper-parameters, test accuracy, and generalization gap, as the Table below shows. This empirically confirms our hypothesis on meaningful structures formed by NN populations. Furthermore, neural representations outperform the state-of-the-art for model characteristic prediction and generalize to out-of-distribution zoos. 
{% include figure.html
url="/images/2021-11-09-Self-Supervised_Representation_Learning_on_Neural_Network_Weights_for_Model_Characteristic_Prediction/results.png"
description="Downstream task performance on MNIST-Hyp, F-MNIST-Hyp, CIFAR10-Hyp and SVHN-Hyp model zoos. Comparison of our neural representations (EcD) against baselines W and s(W). Top 7 Rows: R2 score in % for the prediction of epoch, accuracy, generalization gap, learning rate, l2-regularization, dropout and training data fraction. Bottom 3 Rows: Accuracy score for the prediction of activation function, initialization method and optimizer."%}
For our experiments, we use publicly available NN model zoos and generate seven new model zoos with diverse generating factors. Our ablation study confirms that the various factors for generating a population of trained NNs play a vital role in how and which properties are recoverable for trained NNs. In addition, the relation between generating factors and model zoo diversity reveals that seed variation for the trained NNs in the zoos is beneficial.

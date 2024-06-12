---
# Please provide as much information here as possible. If you cannot fill in
# a field, leave it empty. There is no need for quotation marks if your entry
# consists of more than one word.

# list of authors (first name, last name), comma separated
# please put AIML researcher within <strong> XXX </strong> tags
authors: <strong>Linus Scheibenreif</strong>, Michael Mommert, Damian Borth

# date of publication (YYYY-MM-DD)
date: 2023-06-05

# leave this as is
layout: post

# title of the publication
title: Masked Vision Transformers for Hyperspectral Image Classification

# type of publication, please use captitalization (e.g., Journal Paper,
# Conference Poster, Workshop Contribution, ...)
itemtype: Workshop Contribution

# name of publisher/journal/conference; feel free to add additional
# information like volume number, page number, ...
publisher: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR) Workshops, 2023, pp. 2165-2175

# url to the official publication (could be conference, journal, arxiv)
puburl:

# url to some pdf that is freely accessible (e.g., arxiv)
pdfurl:

# url to code repository (e.g., github)
codeurl: https://github.com/HSG-AIML/MaskedSST

# url to data repository (e.g., zenodo, github)
dataurl:

# email address of reponsible AIML author
contactemail: linus.scheibenreif@unisg.ch 

# publication language (e.g., English, German, ...)
language: English

# topical tags; try to cover the following topics:
# - general field (e.g., remote sensing, TTS, financial data, ...)
# - ML method (e.g., deep learning, gradient boosting, supervised learning,
#              semi-supervised learning, self-supervised learning ...)
# - task (e.g, classification, segmentation, representation learning, ...)
# important note: if your tag contains a whitespace, please replace the
# whitespace by an underscore!
tags: remote_sensing self-supervised_learning vision_transformers hyperspectral deep_learning classification

---

<figure display="block" margin-left="auto" margin-right="auto">
<center>
<img class="center-block" width="80%" src="/images/2023-06-18-Masked_Vision_Transformers_for_Hyperspectral_Image_Classification/figure1_v3.png" alt="overview_figure">
</center>
<figcaption><b>A:</b> We propose the use of masked image modeling to pre-train spatial-spectral transformer networks on a large dataset of unlabeled hyperspectral EnMAP data. <b>B:</b> The pre-trained model can then be fine-tuned on small labeled datasets for supervised downstream tasks like land cover classification.</figcaption>
</figure> Transformer architectures have become state-of-the-art models in computer vision and natural language processing. To a significant degree, their success can be attributed to self-supervised pre-training on large scale unlabeled datasets. This work investigates the use of self-supervised masked image reconstruction to advance transformer models for hyperspectral remote sensing imagery. To facilitate self-supervised pre-training, we build a large dataset of unlabeled hyperspectral observations from the EnMAP satellite and systematically investigate modifications of the vision transformer architecture to optimally leverage the characteristics of hyperspectral data. We find significant improvements in accuracy on different land cover classification tasks over both standard vision and sequence transformers using (i) blockwise patch embeddings, (ii) spatial-spectral self-attention, (iii) spectral positional embeddings and (iv) masked self-supervised pre-training (Code available at [github.com/HSG-AIML/MaskedSST](github.com/HSG-AIML/MaskedSST)). The resulting model outperforms standard transformer architectures by +5% accuracy on a labeled subset of our EnMAP data and by +15% on Houston2018 hyperspectral dataset, making it competitive with a strong 3D convolutional neural network baseline. In an ablation study on label-efficiency based on the Houston2018 dataset, self-supervised pre-training significantly improves transformer accuracy when little labeled training data is available. The self-supervised model outperforms randomly initialized transformers and the 3D convolutional neural network by +7-8% when only 0.1-10% of the training labels are available.

Our work adapts the transformer architecture for hyperspectral data. We apply self-attention across the spatial **and** spectral dimensions by factorizing the transformer. Additionally, we utilize spectral positional embeddings together with an initial block-wise patch-embedding layer. The resulting spatial-spectral transformer is pre-trained with a masked image modeling objective on a large collection of hyperspectral remote sensing data from the EnMAP satellite. Downstream performance is evaluated on two datasets: the Houston2018 hyperspectral scene, and a land-cover task based on EnMAP hyperspectral data and DFC2020 labels in Mexico City. 

{% include figure.html
url="/images/2023-06-18-Masked_Vision_Transformers_for_Hyperspectral_Image_CLassification/figure2_v2.png"
description="Overview of our proposed transformer model for hyperspectral data with spatial-spectral factorization within the masked self-supervised pre-training framework. A: The hyperspectral data cube is first divided into spatial-spectral patches. The patches are randomly masked, embedded and processed by the transformer, which sequentially applies self-attention spatially and spectrally between all embeddings. A linear layer maps representations of the masked patches back to pixel space to compute the reconstruction error. B: Our spectral-spatial transformer consists of a patch embedding layer and transformer blocks that apply self-attention among tokens with the same spectral or spatial index. The colors indicate token locations in the hyperspectral cube." %}

{% include figure.html
url="/images/2023-06-18-Masked_Vision_Transformers_for_Hyperspectral_Image_Classification/reconstruction_example.png"
description="Reconstruction examples for randomly masked spatial-spectral tokens (70% masking ratio). Bottom plots correspond to the locations marked in the top left plot." %}


Our results show that unsupervised pre-training with a mask image modeling objective improves downstream hyperspectral image classification performance. 


{% include figure.html
url="/images/2023-06-18-Masked_Vision_Transformers_for_Hyperspectral_Image_Classification/data_fraction.png"
description="Classification results for training on different fractions of labelled Houston2018 dataset." %}

Moreover, we are able to show the efficiency of pre-training with our approach: with **only 1% of the labelled data**, the supervised spatial-spectral transformer outperforms baselines trained trained on the entire dataset. The performance rapidly increases with the amount of available labelled training data for all models.

{% include figure.html
url="/images/2023-06-18-Masked_Vision_Transformers_for_Hyperspectral_Image_Classification/enmap_dfc_segmentation5.png"
description="Top: Tiles from EnMAP L2 scenes over Mexico City. Center: Corresponding DFC2020 land cover labels. Bottom: Predicted land cover classes from the masked spatial-spectral transformer model." %}

To conclude, our approach illustrates the utility of Transformer models for hyperspectral remote sensing image classification.


The results of this study have been presented at the CVPR 2023 EarthVision workshop in Vancouver, Canada.

<!--
## Uploading your Posts

Once you are happy with your post, you can simply push it to our github repo (`https://github.com/HSG-AIML/HSG-AIML.github.io`). You have to be a contributor to be able to push directly. Please contact Michael to make you a contributor. Alternatively, you can also fork the repo and then issue a pull request.


If you have any additional questions, please contact Michael. -->

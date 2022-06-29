---
# Please provide as much information here as possible. If you cannot fill in
# a field, leave it empty. There is no need for quotation marks if your entry
# consists of more than one word.

# list of authors (first name, last name), comma separated
# please put AIML researcher within <strong> XXX </strong> tags
authors: <strong>Linus Scheibenreif</strong>, <strong>Joëlle Hanna</strong>, Michael Mommert, Damian Borth

# date of publication (YYYY-MM-DD)
date: 2022-06-16

# leave this as is
layout: post

# title of the publication
title: Self-supervised Vision Transformers for Land-cover Segmentation and Classification

# type of publication, please use captitalization (e.g., Journal Paper,
# Conference Poster, Workshop Contribution, ...)
itemtype: Workshop Contribution

# name of publisher/journal/conference; feel free to add additional
# information like volume number, page number, ...
publisher: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR) Workshops, 2022, pp. 1422-1431

# url to the official publication (could be conference, journal, arxiv)
puburl:

# url to some pdf that is freely accessible (e.g., arxiv)
pdfurl:

# url to code repository (e.g., github)
codeurl: https://github.com/HSG-AIML/SSLTransformerRS

# url to data repository (e.g., zenodo, github)
dataurl:

# email address of reponsible AIML author
contactemail: linus.scheibenreif@unisg.ch, joelle.hanna@unisg.ch

# publication language (e.g., English, German, ...)
language: English

# topical tags; try to cover the following topics:
# - general field (e.g., remote sensing, TTS, financial data, ...)
# - ML method (e.g., deep learning, gradient boosting, supervised learning,
#              semi-supervised learning, self-supervised learning ...)
# - task (e.g, classification, segmentation, representation learning, ...)
# important note: if your tag contains a whitespace, please replace the
# whitespace by an underscore!
tags: remote_sensing self-supervised_learning vision_transformers data_fusion deep_learning classification segmentation

---

{% include figure.html
url="/images/2022-06-16-Self_Supervised_Vision_Transformers_for_Land_cover_Segmentation_and_Classification/overview.png"
description="An overview of our self-supervised multi-modal contrastive learning approach for Vision Transformers. We propose to use large datasets of unlabelled multi-modal remote sensing data (Sentinel-1 and Sentinel-2) for self-supervised pre-training of vision Transformers using a contrastive loss. After self-supervised training of the backbone (A), the model and task-specific head can be fine-tuned on much smaller labelled datasets for different downstream tasks (B), such as land-cover segmentation and classification." %} Transformer models have recently approached or even surpassed the performance of ConvNets on computer vision tasks like classification and segmentation. To a large degree, these successes have been enabled by the use of large-scale labelled image datasets for supervised pre-training. This poses a significant challenge for the adaption of vision Transformers to domains where datasets with millions of labelled samples are not available. In this work, we bridge the gap between ConvNets and Transformers for Earth observation by self-supervised pre-training on large-scale unlabelled remote sensing data. We show that self-supervised pre-training yields latent task-agnostic representations that can be utilized for both land cover classification and segmentation tasks, where they significantly outperform the fully supervised baselines. Additionally, we find that subsequent fine-tuning of Transformers for specific downstream tasks performs on-par with commonly used ConvNet architectures. An ablation study further illustrates that the labelled dataset size can be reduced to one-tenth after self-supervised pre-training while still maintaining the performance of the fully supervised approach.

Our proposed approach is trained in two stages. We propose to use large datasets of unlabelled remote sensing data for self-supervised pre-training of vision Transformers. After self-supervised training of the backbone, the model and task-specific head can be fine-tuned on much smaller labelled datasets for different downstream tasks. For pretraining, we utilize the SEN12MS (Schmitt et al., 2019) dataset, which contains co-located pairs of Sentinel-1 and Sentinel-2 patches, disregarding available labels; for fine-tuning, we utilize the GRSS Data Fusion 2020 dataset, which comes with high-fidelity LULC segmentation labels.

{% include figure.html
url="/images/2022-06-16-Self_Supervised_Vision_Transformers_for_Land_cover_Segmentation_and_Classification/backbone.png"
description="Architecture of our task-agnostic backbone. For Sentinel-1 and Sentinel-2 input pairs, we pre-train a unique backbone consisting of two streams of Swin Transformers using a self-supervised contrastive loss." %}


{% include figure.html
url="/images/2022-06-16-Self_Supervised_Vision_Transformers_for_Land_cover_Segmentation_and_Classification/downstream.png"
description="Architecture of classification and segmentation heads. For the supervised training of both tasks, the two outputs of the backbone (Z<sub>1</sub>, Z<sub>2</sub>) are fed into
each head. Intermediate representations (Z<sub>1i</sub>, Z<sub>2i</sub>) are also used for the segmentation head. The final projection layer of the segmentation head consists of an up-sampling layer followed by a 1x1 convolutional layer.
" %}


Our results show that latent representations derived through self-supervised pre-training are task agnostic and can be utilized for both land cover classification and segmentation. They also show that SSL in combination with vision Transformers or ConvNets can yield large performance gains (up to +30% over supervised baselines) across different downstream tasks when finetuned with labelled data.


{% include figure.html
url="/images/2022-06-16-Self_Supervised_Vision_Transformers_for_Land_cover_Segmentation_and_Classification/label_fraction.png"
description="Classification and segmentation results for training on different fractions of labelled data." %}

Moreover, we are able to show the efficiency of pre-training with our approach: with **only 10% of the labelled data**, all self-supervised models outperform the best supervised baselines trained on the entire dataset. The performance rapidly increases with the amount of available labelled training data for all models.

{% include figure.html
url="/images/2022-06-16-Self_Supervised_Vision_Transformers_for_Land_cover_Segmentation_and_Classification/qualitative_results.png"
description="Qualitative comparison of results for 3 different regions. Results from left to right: Sentinel-2 true color (RGB), DFC groundtruth, UNet trained from scratch on fusion of both inputs, SwinUNet trained from scratch on both inputs, SwinUNet fine-tuned on both inputs, and finally an ensemble model of both UNet and SwinUNet." %}

To conclude, our approach illustrates the utility of Transformer models for Earth observation applications **without the need for large labelled datasets**.


The results of this study have been presented at the CVPR 2022 Earthvision workshop in New Orleans, USA. This work received the **Best Student Paper Award**.

<!--
## Uploading your Posts

Once you are happy with your post, you can simply push it to our github repo (`https://github.com/HSG-AIML/HSG-AIML.github.io`). You have to be a contributor to be able to push directly. Please contact Michael to make you a contributor. Alternatively, you can also fork the repo and then issue a pull request.


If you have any additional questions, please contact Michael. -->

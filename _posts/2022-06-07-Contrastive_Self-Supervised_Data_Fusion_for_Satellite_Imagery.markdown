---
# Please provide as much information here as possible. If you cannot fill in
# a field, leave it empty. There is no need for quotation marks if your entry
# consists of more than one word.

# list of authors (first name, last name), comma separated
# please put AIML researcher within <strong> XXX </strong> tags
authors: <strong>Linus Scheibenreif</strong>, Michael Mommert, Damian Borth

# date of publication (YYYY-MM-DD)
date: 2022-06-07

# leave this as is
layout: post

# title of the publication
title: Contrastive Self-Supervised Data Fusion for Satellite Imagery
# type of publication, please use captitalization (e.g., Journal Paper,
# Conference Poster, Workshop Contribution, ...)
itemtype: Conference Paper

# name of publisher/journal/conference; feel free to add additional
# information like volume number, page number, ...
publisher:  ISPRS 2022, Nice, France; ISPRS Annals of the Photogrammetry, Remote Sensing and Spatial Information Sciences, Volume V-3-2022, 705.

# url to the official publication (could be conference, journal, arxiv)
# puburl: 

# url to some pdf that is freely accessible (e.g., arxiv)
pdfurl: https://pdfs.semanticscholar.org/40b8/63abfe89b395491e7fe3476c0a9810a5aa5d.pdf

# url to code repository (e.g., github)
# codeurl: 

posterurl: https://hsg-aiml.github.io/images/2022-06-07-Contrastive_Self-Supervised_Data_Fusion_for_Satellite_Imagery/poster-isprs.pdf

# url to data repository (e.g., zenodo, github)
# dataurl: 

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
tags: remote_sensing self-supervised_learning data_fusion deep_learning classification

---

{% include figure.html
url="/images/2022-06-07-Contrastive_Self-Supervised_Data_Fusion_for_Satellite_Imagery/overview.png"
description="A schematic depiction of our multi-modal contrastive self-supervised learning approach: by leveraging a contrastive loss, we force latent representations generated from multi-band imaging (Sentinel-2) and SAR data (Sentinel-1) for the same location to attract in latent space, while forcing representations generated for different locations to repel each other. As a result, the model learns rich representations that can be fine-tuned for any downstream task." %}
Supervised learning of any task requires large amounts of labeled data. Especially in the case of satellite imagery, unlabeled data is ubiquitous, while the labeling process is often cumbersome and expensive. Therefore, it is highly worthwhile to leverage methods to minimize the amount of labeled data that is required to obtain a good performance of the given down-stream task. In this work, we leverage contrastive learning in a multi-modal setup to achieve this result.


{% include figure.html
url="/images/2022-06-07-Contrastive_Self-Supervised_Data_Fusion_for_Satellite_Imagery/dual_simclr.png"
description="The Dual-SimCLR architecture that we developed for this work. Instead of using data augmentations and a shared backbone as is utilized in SimCLR, our architecture uses a separate backbone for each modality, resulting in separate representations. In the pre-training of the model, we utilize an MLP as projection head to generate latent presentations, based on which the constrastive loss operates. For the training of a down-stream task, we fine-tune the backbone and implement a fully-connected layer as classification head. The model is pre-trained on large amounts of unlabeled data and fine-tuned on small amounts of labeled data." %}

We experiment with different self-supervised learning approached including SimCLR (Chen et al., 2020) and Multi-Modal Alignment (MMA, Windsor et al., 2021) to pretrain our model. Based on SimCLR, we build our own Dual-SimCLR approach, which is depicted above. In all our approaches, we abstain from utilizing data augmentations, which typically is required for contrastive self-supervised learning. Instead, we take advantage of the co-located nature of the data modalities to construct the contrastive power required for the learning process.

For pretraining, we utilize the SEN12MS (Schmitt et al., 2019) dataset, which contains co-located pairs of Sentinel-1 and Sentinel-2 patches, disregarding available labels; for fine-tuning, we utilize the GRSS Data Fusion 2020 dataset, which comes with high-fidelity LULC segmentation labels. The downstream task is learning in a single-label and multi-label approach. 

Our results show that especially Dual-SimCLR is very successful in learning rich representations. The results for both single-label und multi-label downstream tasks clearly outperform a range of fully-supervised baselines that utilize single modalities or different data fusion approaches, as well as the other contrastive self-supervised approaches that were tested. We can show that the learned representations are rich and informative.

{% include figure.html
url="/images/2022-06-07-Contrastive_Self-Supervised_Data_Fusion_for_Satellite_Imagery/label_fraction.png"
description="Results of our ablation study on the average accuracy of the classification task. The plot shows that Dual-SimCLR not only outperforms all other approaches based on the full labeled dataset, but it also outperforms all baseline approaches that were trained on the full labeled dataset with only 10% of the labeled data. " %}

More importantly, we are able to show the efficiency of pre-training with our approach: by fine-tuning the learned representations of the pretrained backbone, we are able to **outperform any fully-supervised baseline approach with only 10% of the labeled data**.

To conclude, our approach enables the label-efficient training of deep learning models for remote sensing by pretraining on a large amount of unlabeled data. 

The results of this study have been presented at the ISPRS 2022 congress in Nice, France (the results have been presented by Michael Mommert, but the work has been done by Linus Scheibenreif). More results related to this study will be presented at the CVPR 2022 Earthvision workshop. That publication will make the code and pretrained backbone architectures available for both works. Stay tuned!    

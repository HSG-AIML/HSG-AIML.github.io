---
# Please provide as much information here as possible. If you cannot fill in
# a field, leave it empty. There is no need for quotation marks if your entry
# consists of more than one word.

# list of authors (first name, last name), comma separated
# please put AIML researcher within <strong> XXX </strong> tags
authors: <strong>Linus Scheibenreif</strong>, Michael Mommert, Damian Borth

# date of publication (YYYY-MM-DD)
date: 2024-06-12

# leave this as is
layout: post

# title of the publication
title: Parameter Efficient Self-Supervised Geospatial Domain Adaptation

# type of publication, please use captitalization (e.g., Journal Paper,
# Conference Poster, Workshop Contribution, ...)
itemtype: Conference Paper

# name of publisher/journal/conference; feel free to add additional
# information like volume number, page number, ...
publisher: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), 2024, pp. 27841-27851

# url to the official publication (could be conference, journal, arxiv)
puburl: https://openaccess.thecvf.com/content/CVPR2024/html/Scheibenreif_Parameter_Efficient_Self-Supervised_Geospatial_Domain_Adaptation_CVPR_2024_paper.html

# url to some pdf that is freely accessible (e.g., arxiv)
pdfurl: https://openaccess.thecvf.com/content/CVPR2024/papers/Scheibenreif_Parameter_Efficient_Self-Supervised_Geospatial_Domain_Adaptation_CVPR_2024_paper.pdf

# url to code repository (e.g., github)
codeurl: https://github.com/HSG-AIML/GDA

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
# <p style="text-align:center;">
# </p>
tags: self-supervised_learning remote_sensing parameter-efficient_training
---

<figure display="block" margin-left="auto" margin-right="auto">
<center>
<img class="center-block" width="150%" src="/images/2024-06-13-Parameter_Efficient_Self_Supervised_Geospatial_Domain_Adaptation/overview_v2.PNG" alt="overview_figure">
</center>
<figcaption>We propose a method to adapt pre-trained visual foundation models to unseen remote sensing modalities in three steps: First, we add additional parameters, called SLR Adapters, to the foundation model. Then, the new parameters are trained with a masked autoencoding objective  on unlabeled data from the new domain. Finally, the adapter parameters are fine-tuned in supervised fashion for the task of interest.</figcaption>
</figure>


## Background

Pre-trained foundation models are widely used to solve computer vision problems, including with remote sensing imagery. The remote sensing field is characterized by widely varying imaging sensors and heterogeneous datasets. This limits the applicability of many visual foundation models, which are often pre-trained on a specific image modality. In this work, we present a self-supervised adaptation technique that makes it possible to efficiently adapt large, pre-trained foundation models to previously unseen imaging modalities.

## Method

We propose a method that adapts existing foundation models to new modalities by introducing a small number of additional parameters and training the new parameters in self-supervised fashion on the target modality. These scaled low-rank (SLR) adapter parameters are added throughout the layers of the model to augment linear transforms in the transformer feed-forward blocks and QKV projections. Each adapter consists of learnable input and output scaling vectors <b>s</b><sub>i</sub><sup>1,2</sup> and low-rank matrices <b>W</b><sub>i</sub><sup>1,2</sup> that form a residual connection around the pre-trained linear transform <b>W</b><sub>i</sub>.

<figure display="block" margin-left="auto" margin-right="auto">
<center>
<img class="center-block" width="50%" src="/images/2024-06-13-Parameter_Efficient_Self_Supervised_Geospatial_Domain_Adaptation/slr.PNG" alt="slr_figure">
</center>
<figcaption>Transformer block (left) with SLR adapters (right). We add individual SLR adapters to linear transformations in the <em>qkv</em> projection and <em>mlp</em> layers of the transformer block. SLR freezes the original transform <b>W</b><sub>i</sub> and introduces trainable scaling parameters <b>s</b><sub>i</sub><sup>1,2</sup> and low-rank matrices <b>W</b><sub>i</sub><sup>1,2</sup>.</figcaption>
</figure>

The adapters are trained with a masked-autoencoding approach on unlabeled data from target domain. For instance, an RGB foundation model can be adapted to SAR data by adding the adapters and training them on a SAR dataset. In the final step, we fine-tune the adapters along with a task-specific model head (e.g., segmentation or regression) on labeled dataset that could be much smaller. 


## Results

<figure display="block" margin-left="auto" margin-right="auto">
<center>
<img class="center-block" width="80%" src="/images/2024-06-13-Parameter_Efficient_Self_Supervised_Geospatial_Domain_Adaptation/avg_acc_v3.PNG" alt="avg_acc_figure">
</center>
<figcaption>Average performance (colored bars) and number of trainable parameters (gray bars) for different visual foundation models across 8 remote sensing datasets. Our Scaled Low-Rank (SLR) adapter method achieves significant performance improvements across datasets and models with no (SLR Linear) and as little as 1-2% (SLR fine-tuned) additional parameters.</figcaption>
</figure>

We test our method across different remote sensing datasets and visual foundation models. Average linear evaluation accuracy across eight classification and segmentation tasks significantly improves after incorporating and training SLR adapters for MAE, SatMAE and Scale-MAE foundation models. Fine-tuning of SLR adapters (1-2% of model parameters) results in performance that is on-par with supervised fine-tuning of the entire 300M ViT-L model.

<figure display="block" margin-left="auto" margin-right="auto">
<center>
<img class="center-block" width="80%" src="/images/2024-06-13-Parameter_Efficient_Self_Supervised_Geospatial_Domain_Adaptation/seg.PNG" alt="seg_figure">
</center>
<figcaption>Segmentation examples on Sentinel-1 SAR imagery from the BENGE-8k dataset. Predictions for 8 different land-cover classed obtained with SatMAE combined with a FCN segmentation head. Comparisons between full SatMAE fine-tuning and fine-tuning of SLR adapters.</figcaption>
</figure>

Qualitatively, we find that self-supervised adaptation improves the <b>segmentation</b> results on SAR data for foundation models that were trained on optical RGB data.

### SLR Adapters
In our experiments, SLR adapters outperform parameter efficient fine-tuning methods such as BitFit, (IA)<sup>3</sup>, low-rank adaptation (LoRA), and tuning of normalizations (see Tab. 5 in the paper).

Additionally, SLR adapter facilitate few-shot learning through their scaling vectors, which can be adjusted effectively on very small datasets. We also find that self-supervised training of the adapters before supervised fine-tuning improves downstream performance, even without access to additional unlabeled data.

## Conclusion
We present a new method to adapt foundation models to unseen modalities while avoiding costly fine-tuning. This enables supervised training of large models with a limited number of labeled samples and improves downstream performance on new modalities.
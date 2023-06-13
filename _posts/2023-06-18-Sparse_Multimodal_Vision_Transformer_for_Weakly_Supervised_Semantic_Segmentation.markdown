---
# Please provide as much information here as possible. If you cannot fill in
# a field, leave it empty. There is no need for quotation marks if your entry
# consists of more than one word.

# list of authors (first name, last name), comma separated
# please put AIML researcher within <strong> XXX </strong> tags
authors: <strong>Joëlle Hanna</strong>, Michael Mommert, Damian Borth

# date of publication (YYYY-MM-DD)
date: 2023-06-13

# leave this as is
layout: post

# title of the publication
title: Sparse Multimodal Vision Transformer for Weakly Supervised Semantic Segmentation

# type of publication, please use captitalization (e.g., Journal Paper,
# Conference Poster, Workshop Contribution, ...)
itemtype: Workshop Contribution

# name of publisher/journal/conference; feel free to add additional
# information like volume number, page number, ...
publisher: Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR) Workshops, 2023, pp. 2144-2153

# url to the official publication (could be conference, journal, arxiv)
puburl:

# url to some pdf that is freely accessible (e.g., arxiv)
pdfurl:

# url to code repository (e.g., github)
codeurl: https://github.com/HSG-AIML/sparse-vit-wsss

# url to data repository (e.g., zenodo, github)
dataurl:

# email address of reponsible AIML author
contactemail: joelle.hanna@unisg.ch

# publication language (e.g., English, German, ...)
language: English

# topical tags; try to cover the following topics:
# - general field (e.g., remote sensing, TTS, financial data, ...)
# - ML method (e.g., deep learning, gradient boosting, supervised learning,
#              semi-supervised learning, self-supervised learning ...)
# - task (e.g, classification, segmentation, representation learning, ...)
# important note: if your tag contains a whitespace, please replace the
# whitespace by an underscore!
tags: remote_sensing weakly-supervised_learning vision_transformers sparsity deep_learning semantic_segmentation

---

{% include figure.html
url="/images/2023-06-18-Sparse_Multimodal_Vision_Transformer_for_Weakly_Supervised_Semantic_Segmentation/overview.png"
description="Our primary objective is to perform semantic segmentation without relying on pixel-level annotations. Instead, we use image-level annotations, making the segmentation task more scalable and cost-effective. To accomplish this, we investigate attention modules in a Vision Transformer. These modules provide greater interpretability compared to CNN-based approaches and enable us to generate pseudo-segmentation masks. These masks are subsequently refined iteratively, leading to improved segmentation results." %} Vision Transformers have demonstrated their versatility and effectiveness in tackling complex computer vision tasks such as land cover segmentation in remote sensing applications. While they perform comparably or even better than Convolutional Neural Networks (CNNs), Transformers typically require larger datasets with detailed annotations, such as pixel-level labels for land cover segmentation. To address this limitation, we propose a weakly-supervised vision Transformer that utilizes image-level labels to learn semantic segmentation and reduce the need for extensive human annotation. This is achieved by modifying the architecture of the vision Transformer, incorporating gating units in each attention head to enforce sparsity during training and retain only the most meaningful heads. After training on image-level labels, we extract the representations from the remaining heads, cluster them, and construct pseudomasks serving as labels for training a segmentation model. Furthermore, we can refine our predictions through post-processing the pseudomasks and  iteratively training a segmentation model with high fidelity. Our code is available at [github.com/HSG-AIML/sparse-vit-wsss](github.com/HSG-AIML/sparse-vit-wsss). Evaluation on the DFC2020 dataset demonstrates that our method not only produces high-quality segmentation masks using image-level labels but also performs comparably to fully-supervised training relying on pixel-level labels. Our results also indicate that our method can accomplish weakly-supervised semantic segmentation even with small-scale datasets.

Our weakly-supervised semantic segmentation approach consists of a pipeline with three stages. In the first stage, we train a Transformer model for multi-label classification. During the training process, we enforce attention sparsity by adding learnable gating units to each head of the Multi-Head Self-Attention (MHSA). In the second stage, we generate pseudomasks by extracting attention maps from the last block of the Transformer, reshaping them and clustering them. Each cluster is assigned a label that will be used to create the corresponding pseudomask. In the final step, we refine the generated pseudomask through multiple stages of supervised training of a segmentation model, utilizing the pseudomasks generated in the previous iteration as supervision.


{% include figure.html
url="/images/2023-06-18-Sparse_Multimodal_Vision_Transformer_for_Weakly_Supervised_Semantic_Segmentation/pipeline.png"
description="Diagram of our approach. For training the classifier, we use co-registered Sentinel-1/2 image pairs (SEN12MS dataset) with labels from Data Fusion Contest 2020. Segmentation masks are used for generating image-level labels, and for assessing the accuracy of the generated pseudomasks." %}

Our results show that pruning over 70% of the heads in a vision Transformer has minimal impact on performance, highlighting their redundancy. The remaining heads, on the other hand, are meaningful and specialized, enabling their utilization for inferring pseudomasks in land-cover mapping.


{% include figure.html
url="/images/2023-06-18-Sparse_Multimodal_Vision_Transformer_for_Weakly_Supervised_Semantic_Segmentation/pseudomasks.png"
description="Qualitative comparison of our results, from left to right: Sentinel-2 true color(RGB), pseudomask generated from Grad-CAM, pseudomask generated using our method, pseudomask generated using our method with pruning, and finally the groundtruth" %}

Moreover, we are able to improve the generated pseudomasks with a refinement step. This consists of training a segmentation model in a supervised way by using as supervision the masks generated by the previous iteration.

{% include figure.html
url="/images/2023-06-18-Sparse_Multimodal_Vision_Transformer_for_Weakly_Supervised_Semantic_Segmentation/refinement.png"
description="Qualitative comparison of the iterative refinement process of pseudomasks. The initial pseudomask (iteration 0) undergoes 1 and 2 iterations of refinement" %}

To conclude, our work demonstrates the potential to create pseudomasks for segmentation using weak supervision (relying only on image-level labels as supervision) by leveraging representations learned by vision Transformers.


The results of this study have been presented at the CVPR 2023 EarthVision workshop in Vancouver, Canada.

<!--
## Uploading your Posts

Once you are happy with your post, you can simply push it to our github repo (`https://github.com/HSG-AIML/HSG-AIML.github.io`). You have to be a contributor to be able to push directly. Please contact Michael to make you a contributor. Alternatively, you can also fork the repo and then issue a pull request.


If you have any additional questions, please contact Michael. -->

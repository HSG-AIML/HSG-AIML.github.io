---
# Please provide as much information here as possible. If you cannot fill in
# a field, leave it empty. There is no need for quotation marks if your entry
# consists of more than one word.

# list of authors (first name, last name), comma separated
# please put AIML researcher within <strong> XXX </strong> tags
authors: <strong>Moritz Blattner</strong>, Michael Mommert, Damian Borth

# date of publication (YYYY-MM-DD)
date: 2021-11-17

# leave this as is
layout: post

# title of the publication
title: Commercial Vehicle Traffic Detection from Satellite Imagery with Deep Learning
# type of publication, please use captitalization (e.g., Journal Paper,
# Conference Poster, Workshop Contribution, ...)
itemtype: Conference Paper

# name of publisher/journal/conference; feel free to add additional
# information like volume number, page number, ...
publisher:  ICML'21 - Workshop on Tackling Climate Change with Machine Learning

# url to the official publication (could be conference, journal, arxiv)
puburl: https://www.climatechange.ai/papers/icml2021/19

# url to some pdf that is freely accessible (e.g., arxiv)
pdfurl: https://www.climatechange.ai/papers/icml2021/19/paper.pdf

# url to code repository (e.g., github)
# codeurl: 

# url to data repository (e.g., zenodo, github)
# dataurl: 

# email address of reponsible AIML author
contactemail: michael.mommert@unisg.ch

# publication language (e.g., English, German, ...)
language: English

# topical tags; try to cover the following topics:
# - general field (e.g., remote sensing, TTS, financial data, ...)
# - ML method (e.g., deep learning, gradient boosting, supervised learning,
#              semi-supervised learning, self-supervised learning ...)
# - task (e.g, classification, segmentation, representation learning, ...)
# important note: if your tag contains a whitespace, please replace the
# whitespace by an underscore!
tags: remote_sensing object_detection mobility sentinel-2 deep_learning

---

{% include figure.html
url="/images/2021-11-17-Commercial_Vehicle_Traffic_Detection_from_Satellite_Imagery_with_Deep_Learning/trucks.png"
description="Green boxes indicate commercial vehicles (CV) as they move on a Swiss freeway section. Due to a delay in the imaging of the different channels, moving objects exhibit a characteristic rainbow-like appearance in Sentinel-2 images. This project exploits this characteristic feature to identify and measure commercial vehicle traffic from space." %}
Commercial vehicle traffic is currently responsible for 7% of global CO2 emissions. While road freight will remain the dominant mode of surface freight transportation, its contribution to climate change is likely to increase in the short term. Therefore, the quantitative monitoring of commercial vehicle (CV) traffic is essential for implementing targeted road emission regulations. However, ground monitoring stations are costly and less than half of all countries worldwide collect road freight activity. In this work, we investigate the feasibility of detecting and monitoring CV traffic in freely available
satellite imagery from ESA's Sentinel-2 satellites.

{% include figure.html
url="/images/2021-11-17-Commercial_Vehicle_Traffic_Detection_from_Satellite_Imagery_with_Deep_Learning/setup.png"
description="Workflow of this project. We gather satellite imagery and ground-truth traffic count rates for CVs, identify individual CVs with an object detection model and finally train gradient-boosted tree-based models on CV counts to estimate hourly CV traffic rates for the locations considered." %}

For this task, we obtain [Sentinel-2](https://sentinel.esa.int/web/sentinel/missions/sentinel-2) satellite imagery for 33 locations centered on Swiss freeway sections to identify CVs with a deep learning approach.  We detect CVs with a modified [Faster R-CNN](https://proceedings.neurips.cc/paper/2015/file/14bfa6bb14875e45bba028a21ed38046-Paper.pdf) object detection model by exploiting a characteristic feature of moving objects in Sentinel-2 data: a constant delay between image acquisition in the different channels leads to a characteristic "rainbow-like" appearance for objects that move at sufficient velocity, which is easy to detect. After training our model, we find an average precision score of 72% for the detection of CVs in our imaging data. The model further shows similar performance results for freeway sections outside of Europe (see figure below).

{% include figure.html
url="/images/2021-11-17-Commercial_Vehicle_Traffic_Detection_from_Satellite_Imagery_with_Deep_Learning/brazil.png"
description="We test our object detection approach on out-of-distribution satellite imagery for different continents. In this example, the trained model correctly identifies all CVs on a freeway section in Brazil (extracted detections shown on the right)." %}

For each freeway section location considered in this project, ground-truth traffic count data is available from [ASTRA](https://www.astra.admin.ch/astra/en/home.html), allowing us to convert snapshot CV counts into hourly traffic rates for CVs. For this purpose, we trained gradient-boosted tree-based regression models in order to predict CV traffic rates from the number of CVs counted per freeway section from our imaging data in addition to other features. We find that it is possible to measure hourly CV traffic volumes for any freeway section in the world within 65% of the actual value or with a root mean square error (RMSE) of ∼160 vehicles per hour. For freeway sections with available but limited ground-truth data, we can predict CV traffic volumes up to within 4% and with an RMSE of ∼60 vehicles per hour. We find that our models are best applied to satellite images with low cloud coverage and for freeway sections above 1 kilometer in length.

{% include figure.html
url="/images/2021-11-17-Commercial_Vehicle_Traffic_Detection_from_Satellite_Imagery_with_Deep_Learning/covid.png"
description="Our combined model approach enables the detection of CV traffic rate variations in 2020 due to Swiss Covid-19 lockdown regulations for different ports of entry. In agreement with ground-truth traffic rates, we find that the border to Italy was most severly affected by a decrease in traffic, while the border to Germany was barely affected." %}

Additionally, our results enable the estimation of the relative decline in CV
traffic due to lockdown measures during the first wave of the COVID19 pandemic in Switzerland in 2020 (see figure above).

To conclude, our approach enables the estimation of CV traffic rates from remote sensing data only, which makes it applicable on a global scale. The methods presented here constitute a powerful tool to estimate CV traffic rates in areas in which ground-based traffic rate measurements are unavailable.

This publication presents the results of the Master thesis of MBI student Moritz Blattner. 
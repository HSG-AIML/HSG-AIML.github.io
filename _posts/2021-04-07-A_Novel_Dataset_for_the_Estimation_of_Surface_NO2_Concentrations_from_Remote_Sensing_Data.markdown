---
authors: <strong>Linus Scheibenreif</strong>, Michael Mommert, Damian Borth
date: 2021-04-07
layout: post
title: A Novel Dataset for the Prediction of Surface NO2 Concentrations from Remote Sensing Data
itemtype: Conference
publisher: IEEE International Symposium on Geoscience and Remote Sensing 2021 (IGARSS)
#puburl: https://arxiv.org/abs/2011.11344
#pdfurl: https://arxiv.org/pdf/2011.11344
#dataurl: https://github.com/HSG-AIML/NO2-dataset

contactemail: linus.scheibenreif@unisg.ch	
language: English
tags: remote_sensing climate_change air pollution regression 
---
{% include figure.html
url="/images/2021-04-07-A_Novel_Dataset_for_the_Estimation_of_Surface_NO2_Concentrations_from_Remote_Sensing_Data/figure1.png"
description="The NO2 dataset consists of spatially and temporally aligned measurements from the ESA Sentinel-5P satellite, EEA air quality stations on the ground and supplementray data." %} NO2 is an atmospheric trace gas that contributes to global warming as a precursor of greenhouse gases and has adverse effects on human health. This work present a novel dataset of NO2 measurements from air quality stations on the ground, temporally and spatially aligned with NO2 measurements from space by the ESA Sentinel-5P satellite. Additionally, geographic and meteorological variables as well as information on lockdown measures are included. The dataset offers access to diverse data on NO2, and facilitates data-driven research into the dynamics of NO2 pollution.

We showcase the value of the dataset with two applications. Firstly, the prediction of surface NO2 concentrations with gradient boosting which enables the identification of EU NO2 exposure limit breaches. Secondly, we investigate the influence of COVID-19 lockdowns on air quality in Europe and find a significant decrease in NO2 levels when lockdown measures are in place.

### Surface NO2 Prediction
Using a gradient boosting approach, the dataset facilitates prediction of surface NO2 with good accuracy and at high temporal frequency. When predicting NO2 concentrations at locations with ground based air quality stations, the boosting approach reaches an R2-score of 0.7 for annual and 0.55 for daily frequency, respectively.

{% include figure.html
url="/images/2021-04-07-A_Novel_Dataset_for_the_Estimation_of_Surface_NO2_Concentrations_from_Remote_Sensing_Data/figure2.png"
description="Annual and daily predictions for surface NO2 concentrations across Europe form our baseline models. Each dot corresponds to theh annual average or daily measurement of an air quality station in the test set. The red line corresponds to unity, the contour lines to 20% iso-poportions of kernel-density estimates." %}

### Lockdown Impact Quantification
The analysis of NO2 levels before and during lockdown measures due to the COVID19 pandemic reveals a drop in NO2 across Europe when strict lockdown measures such as stay-at-home orders are in place. For the example of Spain the surface NO2 concentration during lockdown (14.03.2020 to 03.05.2020) decreased by 48% compared to the previous year. Similarly, the average tropospheric NO2 column density decreased by 40%.

{% include figure.html
url="/images/2021-04-07-A_Novel_Dataset_for_the_Estimation_of_Surface_NO2_Concentrations_from_Remote_Sensing_Data/figure3.png"
description="Sample of surface NO2 concentrations in Spain for the 2019-2020 timespan. The thick lines correspond to 14-day, the thin lines to daily averages of all observations in the country. The dark shaded areas correspond to the time of stay-at-home orders, the light shades to the reference timeframe. Top plot shows surface NO2 measurements from ground stations, bottom plot tropospheric NO2 measurements from Sentinel-5P." %}


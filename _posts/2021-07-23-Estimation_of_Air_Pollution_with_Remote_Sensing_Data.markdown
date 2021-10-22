---
authors: <strong>Linus Scheibenreif</strong>, Michael Mommert, Damian Borth
date: 2021-07-23
layout: post
title: 'Estimation of Air Pollution with Remote Sensing Data: Revealing Greenhouse Gas Emissions from Space'
itemtype: Conference
publisher: Tackling Climate Change with Machine Learning workshop at ICML 2021 
puburl: https://www.climatechange.ai/papers/icml2021/23 
#puburl: https://arxiv.org/abs/2011.11344
#pdfurl: https://arxiv.org/pdf/2011.11344
#dataurl: https://github.com/HSG-AIML/NO2-dataset

contactemail: linus.scheibenreif@unisg.ch	
language: English
tags: remote_sensing climate_change air_pollution regression 
---
{% include figure.html
url="/images/2021-07-23-Estimation_of_Air_Pollution_with_Remote_Sensing_Data/figure2.png"
description="Exemplary NO2 predictions based on Sentinel-2 and Sentinel-5P input data. **Top:** RGB bands of the Sentinel-2 image, red dots mark locations of air quality stations, red text indicates the average NO2 concentration measured on the ground during the 2018-2020 timespan. **Bottom:** Predicted NO2 concentrations for the locations above (not seen during training) with predictions at the exact position of the air quality station in red. The heatmaps are constructed from individual predictions for overlapping 120x120 pixel tiles of the top image and corresponding Sentinel-5P data, resulting in an effective spatial resolution of 100m. This approach is equally applicable to locations without air quality stations, providing a means to map air pollution on the surface level to identify sources of air pollution and GHG emissions." %} Air pllution is a major driver of climate change. Anthropogenic emissions from the burning of fossil fuels for transportation and power generation emit large amounts of problematic air pollutants, including Greenhouse Gases (GHGs). Despite the importance of limiting GHG emissions to mitigate climate change, detailed information about the spatial and temporal distribution of GHG and other air pollutants is difficult to obtain. Existing models for surface-level air pollution rely on extensive land-use datasets which are often locally restricted and temporally static. This work proposes a deep learning approach for the prediction of ambient air pollution that only relies on remote sensing data that is globally available and frequently updated. Combining optical satellite imagery with satellite-based atmospheric column density air pollution measurements enables the scaling of air pollution estimates (in this case NO2) to high spatial resolution (up to ~10m) at arbitrary locations and adds a temporal component to these estimates. The proposed model performs with high accuracy when evaluated against air quality measurements from ground stations (mean absolute error <6 microgram/qm). Our results enable the identification and temporal monitoring of major sources of air pollution and GHGs. 

# Background
One of the primary anthropogenic air pollutants is Nitrogen Dioxide (NO2). Elevated levels of NO2 harm the vegetation, contribute to acid rain, and act as a precursor of potent GHGs like Ozone. Additionally, NO2 is jointly emitted with CO2 during the combustion of fossil fuels at high temperatures, making it a suitable proxy to identify CO2 emission sources. This work leverages a large body of publicly available NO2 concentration measurements on the ground by the European Environment Agency's (eea.europa.eu, EEA) network of air quality stations and satellite measurements from the European Space Agency's (ESA) Copernicus program to investigate the distribution of air pollutants through a deep learning approach. The results of this work enable the identification of major sources of GHG emissions and their temporal monitoring on a global scale.

# Approach
This work approaches the estimation of air pollution as a supervised computer vision problem. We collect a dataset of harmonized remote sensing data from Sentinel-2 and Sentinel-5P, spatially and temporally aligned with measurements from air quality monitoring stations. The proposed model is trained on pairs of remote sensing input and air quality target values (see Figure), which yields a system that predicts air pollution levels solely from globally available remote sensing data (code available on [Github](https://github.com/HSG-AIML/RemoteSensingNO2Estimation)).

{% include figure.html
url="/images/2021-07-23-Estimation_of_Air_Pollution_with_Remote_Sensing_Data/figure1.png"
description="Overview of the proposed air pollution prediction system." %}

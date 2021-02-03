---
title: Knowledge Extraction from Remote Sensing with Deep Neural Networks
layout: page
---

Remote Sensing satellites generate vast amounts of data over a wide range of the electromagnetic spectrum. The 
analysis of these data and the focused extraction of useful knowledge from them exceeds the capabilities of most
traditional analysis methods. In the recent years, deep neural networks have shown promising results in learning 
to extract knowledge from remote sensing data.


{% include figure.html url="/images/research/remote_sensing_sankt_gallen.png" 
description="Satellite image of the St. Gallen area as observed by one of the European Space Agency's Sentinel-2
satellites. The city of St. Gallen is located on the left with Lake Constance at the top and the Appenzell area to the 
right." %}


In our lab, we are utilizing a range of state-of-the-art deep neural network architectures to solve different tasks
like classification from images, regression, semantic segmentation, and object detection based on remote sensing data
and addressing different research questions: 

 
## Climate Change

Climate change is one of the -- if not the single -- most pressing issue on a global scale. We are interested in 
quantifying the effects that amplify climate change. This effort includes the estimation of greenhouse gas emissions
directly from remote imaging data and based on proxy data like detailed land use classification and traffic volume.

{% include figure.html
url="/images/2020-11-24-Characterization_of_Industrial_Smoke_Plumes_from_Remote_Sensing_Data/example_panel.png"
description="Example images from our smoke plume identification study. Each column corresponds to one of 624 
emitter locations. The top row shows the site during activity (smoke is present) and the bottom row during 
inactivity (smoke is absent). The origin region of the smoke plume is marked by red circles." %}


For instance,
[Mommert et al. (2020)](_posts/2020-11-24-Characterization_of_Industrial_Smoke_Plumes_from_Remote_Sensing_Data.markdown)
investigated the possibility to identify industrial smoke plumes from Sentinel-2 multiband images with promising results.
Our trained models reliable distinguish between natural clouds and smoke plumes. We are currently extending this study to
provide emission estimates from remote sensing data on a global scale.


We are also interested in topics that are related to climate change science, including the study of its 
effects on urbanization, ecology, and the economy, as well as providing assistance in disaster relief. 



## Human Health Hazards

Pollution adversely affects human health as well as our environment. Unfortunately, timely pollution measurements, for instance
concentrations of NO2 and other trace gases, are not available on a global scale. By combining remote sensing data with
ground-based measurements in a machine learning approach, we are able to estimate pollution levels on the ground where
no in-situ data are available. 

More information coming soon!

## Publications

Our research results have been published at international conference workshops at NeurIPS.

Please find below a list of feature publications from our lab that are related to remote sensing:

<ul>
{% for post in site.posts %}
  {% if post.tags contains "remote_sensing" %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
  </li>
  {% endif %}
{% endfor %}
</ul>

## Getting Involved

If you are interested in joining our team as a Bachelor or Master student, there is a good chance that we have a
project that suits your skill set and interests. Please have a look [here](theses.md) for more information.
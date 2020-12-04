---
title: Deep Learning and Assurance & Audit
layout: page
---

Our research focuses on a wide range of deep learning methods and their applications to real-world data and issues.

## Representation Learning of Financial Accounting Data

<img alt="Representation Learning Examples"
 src="/images/research/representation_learning-900x597.png"
 align="center"
 style="display:block; margin-left: auto; margin-right: auto; width:70%;"/>

**Motivation:** *"Representation Learning"* refers to the learning of data representations that correspond to more abstract, and ultimately more useful, information for a given downstream task ([Ridgeway, 2016](https://arxiv.org/abs/1612.05299)). The objective of *"unsupervised"* representation learning is to learn representations that expose semantic features as disentangled generative factors without human supervision ([Chen et al., 2016](https://arxiv.org/abs/1606.03657)). For example, for a dataset of faces, a useful disentangled representation may allocate a separate set of dimensions for each of the following attributes: facial expression, eye colour, hairstyle, presence or absence of eyeglasses. Formally, a disentangled representation can be defined as one where *"single latent units are sensitive to changes in single generative factors while being relatively invariant to changes in other factors"* ([Bengio et al., 2016](https://arxiv.org/abs/1206.5538)). <!-- Nowadays, the unsupervised learning of a disentangled posterior distribution over a dataset's underlying generative factors is the subject of active research \citep{kingma2013, rezende2015, higgins2016, dinh2016, kim2018}. -->

**Application in Assurance & Audit:** Accounting data arises from the interaction of a complex set of generative factors. Currently, the performance of *"Computer Assisted Audit Techniques (CAATs)"* significantly depends on the choice of data representations, also referred to as *"features"*, of the accounting data's inherent generative factors. The handcrafted engineering of such representations is a way to take advantage of a human auditor's ingenuity and prior knowledge. However, the inability of CAATs to extract and disentangle such discriminative information themselves highlights a disadvantage. Furthermore, the handcrafting of such representations often results in a labour intensive effort. Ultimately, it may introduce an undesired bias into the learned deep model. Therefore, the learning of such representation directly *"end-to-end"* and suitable for a given audit task defines a next evolutionary step in expanding the capabilities of CAATs.

**Derived Research Questions:** The research of the unsupervised learning of effective representations of accounting data without human supervision for downstream audit tasks is still in its infancy. Therefore, in this context, we investigate the following research questions regarding representation learning of accounting data:

* **Question 1:** Can deep learning techniques be applied to learn disentangled representations of the latent generative factors of variation evident in accounting data?
    
* **Question 2:** Can such learned representations be useful for downstream audit tasks, such as (i) the selection of representative audit samples or (ii) the detection of accounting irregularities? 

**Our Publications:** 

> M. Schreyer, T. Sattarov, D. Borth, A. Dengel, and B. Reimer, **"Detection of Anomalies in Large Scale Accounting Data using Deep Autoencoder Networks"**, NVIDIA’s GPU Technology Conference, San José, California, USA, 2017 ([link](https://arxiv.org/abs/1709.05254)). 

> M. Schreyer, T. Sattarov, C. Schulze, B. Reimer, and D. Borth, **"Detection of Accounting Anomalies in the Latent Space using Adversarial Autoencoder Networks"**, ACM KDD Workshop on Anomaly Detection in Finance, Anchorage, Alaska, USA, 2019 ([link](https://arxiv.org/abs/1908.00734)).

> M. Schreyer, T. Sattarov, A. Gierbl, B. Reimer, and D. Borth, **"Learning Sampling in Financial Statement Audits using Vector Quantised Autoencoder Neural Networks"**, ACM International Conference on AI in Finance, New York, USA, 2020 ([link](https://arxiv.org/abs/2008.02528)).

## Adversarial Learning

<img alt="Multimodal Data Examples"
 src="/images/research/visual_audio-1-900x1031.png"
 align="center"
 style="display:block; margin-left: auto; margin-right: auto; width:70%;">

ToDo... 


## Federated Learning

<img alt="Remote Sensing Examples"
 src="/images/research/remote_sensing-900x694.png"
 align="center"
 style="display:block; margin-left: auto; margin-right: auto; width:70%;">

ToDo... 

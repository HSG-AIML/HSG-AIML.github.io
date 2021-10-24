---
authors: <strong>Marco Schreyer</strong>, Timur Sattarov, Damian Borth
date: 2021-10-24
layout: post
title: Self-Supervised Learning of Accounting Data Representations for Downstream Audit Tasks
itemtype: Conference Paper
publisher: ICAIF'21 - ACM International Conference on Artificial Intelligence in Finance
puburl: https://ai-finance.org
pdfurl: https://www.alexandria.unisg.ch/264493/1/ICAIF_2021_finale.pdf
codeurl:
dataurl:
contactemail: marco.schreyer@unisg.ch
language: English
tags: audit_data_analytics financial_audit deep_learning self_supervised_learning
---
{% include figure.html url="/images/2021-10-24-Self_Supervised_Learning_Accounting_Data/self_supervised_learning-900x317.png" 
description="Learned task invariant accounting data representations z<sub>i</sub> in R<sup>2</sup> with &tau; = 0.5 of the 238,894 City of Philadelphia vendor payments. The visualisations on the left show the representations coloured according to selected payment characteristics: payment type (a) and posting month (b). The visualisations on the right show the same representations coloured according to the downstream audit task: anomaly detection (c) and audit sampling (d)." %} ED

International audit standards require the direct assessment of a financial statement's underlying accounting transactions, referred to as journal entries. Recently, driven by the advances in artificial intelligence, deep learning inspired audit techniques have emerged in the field of auditing vast quantities of journal entry data. Nowadays, the majority of such methods rely on a set of specialized models, each trained for a particular audit task. At the same time, when conducting a financial statement audit, audit teams are confronted with (i) challenging time-budget constraints, (ii) extensive documentation obligations, and (iii) strict model interpretability requirements. As a result, auditors prefer to harness only a single preferably `multi-purpose' model throughout an audit engagement. We propose a contrastive self-supervised learning framework designed to learn audit task invariant accounting data representations to meet this requirement. The framework encompasses deliberate interacting data augmentation policies that utilize the attribute characteristics of journal entry data. We evaluate the framework on two real-world datasets of city payments and transfer the learned representations to three downstream audit tasks: anomaly detection, audit sampling, and audit documentation. Our experimental results provide empirical evidence that the proposed framework offers the ability to increase the efficiency of audits by learning rich and interpretable `multi-task' representations.

---
authors: <strong>Marco Schreyer</strong>, Christian Schulze, Damian Borth
date: 2021-01-26
layout: post
title: Leaking Sensitive Financial Accounting Data in Plain Sight using Deep Autoencoder Neural Networks
itemtype: Workshop Paper
publisher: AAAI'21 - Workshop on Knowledge Discovery from Unstructured Data in Financial Services
puburl: https://aaai-kdf.github.io/kdf2021/accepted_papers
pdfurl: https://aaai-kdf.github.io/kdf2021/assets/pdfs/KDF_21_paper_8.pdf
codeurl:
dataurl:
contactemail: marco.schreyer@unisg.ch
language: English
tags: audit_data_analytics financial_audit deep_learning adversarial_learning
---

{% include figure.html url="/images/2021-01-26-Leaking_Sensitive_Accounting_Data/example_process.png" 
description="The data leakage process applied to learn a steganographic model of real-world accounting data. The process is designed to encode and decode sensitive Enterprise Resource Planing (ERP) system information into unobtrusive ‘day-to-day’ cover images." %} 
Nowadays, organizations collect vast quantities of sensitive information in 'Enterprise Resource Planning' (ERP) systems, such as accounting relevant transactions, customer master data, or strategic sales price information. The leakage of such information poses a severe threat for companies as the number of incidents and the reputational damage to those experiencing them continue to increase. At the same time, discoveries in deep learning research revealed that machine learning models could be maliciously misused to create new attack vectors. 

Understanding the nature of such attacks becomes increasingly important for the (internal) audit and fraud examination practice. The creation of such an awareness holds in particular for the fraudulent data leakage using deep learning-based steganographic techniques that might remain undetected by state-of-the-art 'Computer Assisted Audit Techniques' (CAATs). In this work, we introduce a real-world 'threat model' designed to leak sensitive accounting data. In addition, we show that a deep steganographic process, constituted by three neural networks, can be trained to hide such data in unobtrusive 'day-to-day' images. Finally, we provide qualitative and quantitative evaluations on two publicly available real-world payment datasets.

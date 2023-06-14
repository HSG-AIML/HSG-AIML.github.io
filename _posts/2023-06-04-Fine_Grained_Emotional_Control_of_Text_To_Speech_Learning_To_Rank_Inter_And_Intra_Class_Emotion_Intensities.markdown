---
# Please provide as much information here as possible. If you cannot fill in
# a field, leave it empty. There is no need for quotation marks if your entry
# consists of more than one word.

# list of authors (first name, last name), comma separated
# please put AIML researcher within <strong> XXX </strong> tags
authors: <strong>Shijun Wang</strong>, Jón Guðnason Damian Borth

# date of publication (YYYY-MM-DD)
date: 2023-02-15

# leave this as is
layout: post

# title of the publication
title: Fine-grained Emotional Control of Text-To-Speech Learning To Rank Inter- And Intra-Class Emotion Intensities

# type of publication, please use captitalization (e.g., Journal Paper,
# Conference Poster, Workshop Contribution, ...)
itemtype: Conference Poster

# name of publisher/journal/conference; feel free to add additional
# information like volume number, page number, ...
publisher: IEEE International Conference on Acoustics, Speech, and Signal Processing (ICASSP 2023)

# url to the official publication (could be conference, journal, arxiv)
puburl: 

# url to some pdf that is freely accessible (e.g., arxiv)
pdfurl: https://arxiv.org/abs/2303.01508

# url to code repository (e.g., github)
codeurl: 

# url to data repository (e.g., zenodo, github)
dataurl:

# email address of reponsible AIML author
contactemail: shijun.wang@unisg.ch

# publication language (e.g., English, German, ...)
language: English

# topical tags; try to cover the following topics:
# - general field (e.g., remote sensing, TTS, financial data, ...)
# - ML method (e.g., deep learning, gradient boosting, supervised learning,
#              semi-supervised learning, self-supervised learning ...)
# - task (e.g, classification, segmentation, representation learning, ...)
# important note: if your tag contains a whitespace, please replace the
# whitespace by an underscore!
tags: emotional_text-to-speech fine-grained_emotion_control rank_model deep_learning self-supervised_learning

---

{% include figure.html
url="/images/2023-06-04-Fine_Grained_Emotional_Control_of_Text_To_Speech_Learning_To_Rank_Inter_And_Intra_Class_Emotion_Intensities/Rank_model.png"
description="The pipeline of our Intensity Extractor model. The inputs are a pair of mixture speech samples. Each of these samples is a mix of the same non-neutral and neutral speech, but with different weights applied. The object is to accurately rank these two mixtures. If the ranking is done correctly, it indicates that the extracted intensity representation is meaningful.
" %} 

The goal is to develop a fine-grained emotional Text-To-Speech (TTS) model that allows control over the emotional intensity of each word or phoneme. This level of control can express different attitudes or intentions, even with the same emotion. However, it is nearly impossible to label intensity variations over time, so it's necessary to learn effective emotion intensity representations without labels.

We first train an Intensity Extractor to provide intensity representaions. The Extractor is built on a novel Rank model, which is straightforward yet efficient in extracting emotion intensity information, and both inter- and intra-distance are considered. The ranking is performed on two samples augmented by Mixup ("Mixup: Beyond Empirical Risk Minimization", ICLR 2017). Each augmented sample is a mix of the same non-neutral and neutral speech. By applying different weights to non-neutral and neutral speech, one mixture contains more non-neutral components than the other. In other words, the non-neutral intensity of one mixture is stronger than that of the other. By learning to rank these two mixtures, the Rank model must not only determine the emotion class (inter-class distance) but also capture the amount of non-neutral emotion present in mixed speech, i.e., the intensity of non-neutral emotion (intra-class distance).


{% include figure.html
url="/images/2023-06-04-Fine_Grained_Emotional_Control_of_Text_To_Speech_Learning_To_Rank_Inter_And_Intra_Class_Emotion_Intensities/TTS.png"
description="The training process of the TTS model involves the use of a pre-trained and frozen Intensity Extractor to supply intensity information. Then, using the phoneme, speaker ID, and intensity as inputs, the TTS model strives to reconstruct the Mel-Spectrogram." %}

With a pre-trained Intensity Extractor, we then train a FastSpeech 2 TTS model ("FastSpeech 2: Fast and High-Quality End-to-End Text to Speech", ICLR 2020). The architecture remains the same as in the original paper, but in this instance, the Intensity Extractor is incorporated to supply conditional intensity information.

{% include figure.html
url="/images/2023-06-04-Fine_Grained_Emotional_Control_of_Text_To_Speech_Learning_To_Rank_Inter_And_Intra_Class_Emotion_Intensities/Rate_acc.png"
description="Rate Accuracy of Emotion Intensities. Min, Median and Max are three intensity levels. Subjects are asked to select the sample with the stronger intensity from a pair." %}

The first subjective experiment shows that when the spoken content is the same, listeners find it easier to discern differences in intensity in the speech synthesized by our model.

{% include figure.html
url="/images/2023-06-04-Fine_Grained_Emotional_Control_of_Text_To_Speech_Learning_To_Rank_Inter_And_Intra_Class_Emotion_Intensities/Preference.png"
description="Preference test for emotion expressiveness" %}

Another subjective experiment is the A/B preference test on emotion expressiveness. The results indicate that listeners tend to perceive the expression of emotion as clearer in the speech synthesized by our model.

{% include figure.html
url="/images/2023-06-04-Fine_Grained_Emotional_Control_of_Text_To_Speech_Learning_To_Rank_Inter_And_Intra_Class_Emotion_Intensities/MOS.png"
description="Preference test for emotion expressiveness" %}

Finally, Mean Cepstral Distortion (MCD) and Naturalness Mean Opinion Score (MOS) evaluations are conducted on all synthesized samples. The results show that the quality and naturalness of the speech synthesized by our model surpass all baseline models.

To conclude, we propose a fine-grained controllable emotional TTS, based on a novel Rank model. The Rank model captures both inter- and intra-class distance information, and thus is able to produce meaningful intensity representations. We conduct subjective and objective tests to evaluate our model, the experimental results show that our model surpasses two state-of-the-art baselines in intensity controllability, emotion expressiveness and naturalness.


The results of this study have been presented at the ICASSP 2023 in Rhodes, Greece.

<!--
## Uploading your Posts

Once you are happy with your post, you can simply push it to our github repo (`https://github.com/HSG-AIML/HSG-AIML.github.io`). You have to be a contributor to be able to push directly. Please contact Michael to make you a contributor. Alternatively, you can also fork the repo and then issue a pull request.


If you have any additional questions, please contact Michael. -->

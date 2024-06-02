---
title: "Fake News Detection"
excerpt: "A model using CNN and RNN for automatic detection of fake news.<br/><img src='/images/embedding.png'>"
collection: portfolio
---

# Automatic Hoax News Detection Using Deep Learning Models

The widespread dissemination of hoax news on social media has become a serious challenge in terms of accurate and public-interest information. In this study, we introduce an approach using Deep Learning models for automatic hoax news detection.

## Model Architecture
We propose the use of naive Bayes architecture, feedforward neural networks, convolutional neural networks (CNN), and recurrent neural networks (RNN) to extract important features from text and understand the broader context in news. This method combines 3 types of embeddings (token, character, feature) to obtain deeper context and patterns in news text.

## Steps
1. **Data Collection**: We collect datasets from previous research and well-known media outlets, then separate them into two categories: genuine news and hoax news.
2. **Model Training**: We train Deep Learning models using labeled training data to recognize patterns and characteristics that distinguish between genuine and hoax news.
3. **Model Evaluation**: We test the performance of the model using independent testing datasets and apply standard evaluation metrics such as accuracy, precision, recall, and F1-score.

## Results
Our experimental results show that the proposed Deep Learning models can achieve good performance in detecting hoax news. With accuracy, precision, recall, and F1-score averaging around 96%, and the highest metrics found in the Tribrid Multimodal Embedding model with an accuracy rounded to 97%.

## Implications
This research has implications in the development of effective and efficient technological solutions to mitigate the negative impact of hoax news dissemination and promote accurate and public-interest information.

## References
Link to the paper: [Automatic Hoax News Detection](/files/paper.pdf)

[GitHub Repository](https://github.com/overfero/FakeNewsDetection)

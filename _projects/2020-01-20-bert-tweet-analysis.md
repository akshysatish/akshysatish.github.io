---
title: "Tweet Sentiment Analysis"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Post Formats
  - readability
  - standard
---

![Tweet](/assets/images/proj3tab.jpg "Tweet")

Keyword Extraction and Sentiment Analysis of Tweets using Google's BERT.

<!--more-->

Tweet data is mined using the Twitter API and analysed to extract keywords using Bidirectional Encoder Representations from Transformers(BERT). Extracted keywords are added to the dictionary of words to use as reference for new words. Summarization is performed by relating keywords to topics based on similar context which is a vector space consisting of multiple clusters of related words. Finally, Sentiment Analysis is done to classify positive, negative, and neutral tweets

Keyword extraction is tasked with the automatic identification of terms that best describe the subject of a document. It is a text analysis technique that consists of automatically extracting the most important words and expressions in a text. It helps summarize the content of a text and recognize the main topics which are being discussed. You can use a keyword extractor to pull out keywords or groups of two or more words that create a key phrase.

NLP is highly data consuming so transfer learning helps in building models on top of prebuilt models. The base BERT model is used to build a model that extracts keywords by tokenization, word embedding, attention mapping tweets to generate a dataset and then training on that dataset. From this, we can generate a summary as well as perform sentiment analysis.

Tools and Libraries used: Natural Language Toolkit(nltk), Textacy, Spacy, Torch, Keras, SKLearn, BERTTokenizer, BERTConfig, BERTAdam, Twitter API.

BERT is a highly extensive NLP tool that can be used as a baseline for many tasks and transfer learning can be used to build better and specific models on top of BERT.

Considering that more than 80 percent of the data we generate every day is unstructured ― meaning it is not organized in a predefined way and, therefore, is hard to analyze and process ― keyword extraction allows to lift the most important words from huge sets of data in just seconds and obtain insights about the topics.

Find code here: <https://github.com/akshysatish/BERT-TweetAnalysis>

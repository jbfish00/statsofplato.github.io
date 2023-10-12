---
layout: post
title:  "How to Find Hapax Legomena (Python)"
author: Jacob B. Fisher
description: A post on how to find singly used words in a corpus.
image: "assets/images/DALL·E 2023-10-11 17.16.10 - Natural language processing neural network picture.png"
--- 

## What is a Hapax Legomenon?  

For the many of you that aren't extraordinarily familiar with Greek, *hapax legomenon* literally means "being said once". Thus, in linguistics, a hapax legomenon is a word that is found only once within a corpus of language.
In linguistics, we talk about two main ways in which we can find words and their different forms: stemming and lemmatizing. When we stem, we take the parts of words that are in common (e.g. *improves* and *improving* both stem to *improv*). 
When we lemmatize, we take the original word from which others are derived (e.g. *improved* and *improving* share the lemma *improve*). The following instructions will be a method that lemmatizes each token in the corpus, thereby allowing us to find *true* hapax legomena.

STEP 1: Import Libraries and Load Corpus
---
The natural language tool-kit (nltk) is a very useful python package for performing a number of linguistic computing tasks.  
```
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
from collections import defaultdict

nltk.download('stopwords')
nltk.download('punkt')
```

```
corpus = """
You can copy and paste a sample corpus for testing, but normally you will want to use the following method, found below.
"""
corpus_path = "C:\\Users\\corpus.txt"
with open(corpus_path, 'r', encoding='utf-8') as file:
    corpus = file.read()
```

STEP 2: Data Preparation
---
Definitionally, stopwords are words that are incredibly common such as articles or forms of the verb 'to be'. Since they are so common, it is very unlikely that any given corpus will have a stopword as a hapax legomenon, thus we will eliminate them from our corpus before we run any computation using it.



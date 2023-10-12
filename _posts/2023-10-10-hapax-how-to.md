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
When we lemmatize, we take the original word from which others are derived (e.g. *improved* and *improving* share the lemma *improve*). The following instructions will not lemmmatize the corpus, so the hapax legomena found will arguably not be *true* hapax legomena, but the code can be modified to lemmatize if that is desired.

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
Before we can work with our corpus, we need to tokenize it. When we tokenize using the `word_tokenize` funciton, we get each word and all punctuation as a separate tokens. 

```
orig_tokens = word_tokenize(corpus)
```
For the sake of coimputation speed, we will remove all stopwords. Definitionally, stopwords are words that are incredibly common, such as articles or forms of the verb 'to be'. Since they are so common, it is very unlikely that any given corpus will have a stopword as a hapax legomenon, thus we will eliminate them from our corpus before we run any computation using it. **If you suspect that your corpus has a stopword as a hapax legomenon, skip this step.**

We will also change all letters to lowercase so that our program will not flag words that begin a sentence only once in the corpus as a hapax legomenon.
```
stop_words = set(stopwords.words('english'))
tokens = [word.lower() for word in orig_tokens if word.isalpha() and word.lower() not in stop_words]
```

STEP 3: Find and List Hapax Legomena
---
Now we will create a defaultdict to place our tokens and their corresponding word counts. We will then place each token with a frequency of 1 into a list.

```
word_freq = defaultdict(int)
for word in tokens:
    word_freq[word] += 1

hapax_legomena = [word for word, freq in word_freq.items() if freq == 1]
```
If we so desire, we can print out each token that is found once in the corpus with the following:
```
for word in hapax_legomena:
    print(word)
```

---
layout: post
title:  "How to Find Hapax Legomena (Python)"
author: Jacob B. Fisher
description: A post on how to find singly used words in a corpus.
image: "assets/images/DALL·E 2023-10-11 17.16.10 - Natural language processing neural network picture.png"
--- 

## What is a Hapax Legomenon?  

For the many of you that aren't extraordinarily familiar with Greek, *hapax legomenon* literally means "being said once". Thus, in linguistics, a hapax legomenon, or just hapax, is a word that is found only once within a corpus of language. Certainly, finding such words is very interesting, and that should be enough reason to want to find hapaxes in a corpus, but practical uses exist as well for this linguistic phenomenon. Finding singly used words in a corpus can help in a great many tasks ranging from simply finding typos to more complex analyses such as semantic analysis, authorship attribution, textual dating, and personal stylometric analysis.

STEP 1: Import Libraries and Load Corpus
---
The natural language tool-kit `nltk` is a very useful python package for performing a number of linguistic computing tasks. Here we will use the `stopwords` corpus and the `word_tokenize` function.
```
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
from collections import defaultdict

nltk.download('stopwords')
```
It may be useful to create a small sample corpus for testing your code. More commonly, you will load a corpus from your local machine. An example of both is shown below. 
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
Before we can do anything useful with our corpus, we need to tokenize it. When we tokenize using the `word_tokenize` function, we get each word and all punctuation as a separate tokens. 

```
orig_tokens = word_tokenize(corpus)
```
For the sake of computation speed, we will remove all stopwords. Definitionally, stopwords are words that are incredibly common, such as articles or forms of the verb 'to be'. Since they are so common, it is very unlikely that any given corpus will have a stopword as a hapax, thus we will eliminate them from our corpus before we run any computation using it. **If you suspect that your corpus has a stopword as a hapax, skip this step.**

We will also change all letters to lowercase so that our program will not flag words that begin a sentence only once in the corpus as a hapax. Here we have also removed all punctuation tokens since we do not want to count non-word tokens as hapaxes. 

Here we use a list comprehension to alter the tokens all at once. We take each token in our set of original tokens and make it lowercase and place it in our new list `tokens` if it (1) is a word, determined with the `isalpha` function, and (2) the lowercase version of the word is not in our set of stopwords, here named `stop_words`.
```
stop_words = set(stopwords.words('english'))
tokens = [word.lower() for word in orig_tokens if word.isalpha() and word.lower() not in stop_words]
```

* In linguistics, we talk about two main ways in which we can find words and their different forms: stemming and lemmatizing. When we stem, we take the parts of words that are in common (e.g. *improves* and *improving* both stem to *improv*). When we lemmatize, we take the original word from which others are derived (e.g. *improved* and *improving* share the lemma *improve*). The above code will not lemmatize the corpus, so the hapaxes found will arguably not be "true" hapax legomena, but the code can be modified to lemmatize if that is desired.
* Importantly, using the default lemmatizer in `nltk` requires you to define what the part of speech you are lemmatizing for, so multiple iterations must be gone through to lemmatize all words in the corpus. The `spacy` package does not allow for stemming, but has a more robust lemmatizing function.

STEP 3: Find and List All Hapax Legomena
---
Now, we create a `defaultdict` to place our tokens and their corresponding word counts. We will then place each token with a frequency of 1 into a list.

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
## Conclusion
While the above is simple, it can be taken further to recognize significant word usage in any collection of language. You may want to use it to look at your own writing and improve word choice. You may use it to look at significant books or religious texts. You can use additional linguistic tools such as TagAnt and ActConc or the `spacy` package in python in conjunction with this code to do more complex analysis of language. Exploring the fusion of computer science and the humanities opens you up to expansion of the mind and also the soul. 



<p style="text-align: center"><em>“Ignorance, the root and stem of every evil.”
― Plato</em></p>

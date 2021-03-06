---
layout: post
title: Building Stopword List for Information Retrieval System
categories: []
tags: [NLP, machine learning, papers]
description: In computing, stop words are words which are filtered out before or after processing of natural language data (text).
cover: "/assets/images/word-cloud.jpg"
cover_source: "https://orig00.deviantart.net/f759/f/2012/244/b/9/asoiaf_word_cloud___jon_snow_by_galanix-d5d83v0.jpg"
comments: true
mathjax: true
---

### What are stopwords ?
* Words in a document that are **frequently occuring but meaningless** in terms of Information Retrieval (IR) are called **stopwords**.
* Use of a fixed set of stopwords across various documents of different kinds is not suggested because as the context changes so does the utility of a word. For example, a word like economy might not be a stopword in context of automobiles but would be a stopword in an Economic Times Newspaper.
* Also the pattern of words changes over time as the trends change, so the list of stopwords used should keep up with the trends in word usages.
* They are also called **noise words** or the **negative dictionary**.

### [Zipf's law](https://en.wikipedia.org/wiki/Zipf%27s_law){:target="_blank"}

* **The law states that given some corpus of natural language, the frequency of any word is inversely proportional to its rank in the frequency table** i.e. the most frequent word will occur approximately twice as often as the second most frequent word, three times as often as the third most frequent word, etc.

* This law can be seen in action in the [Brown Corpus](https://en.wikipedia.org/wiki/Brown_Corpus){:target="_blank"} of English text, where **the** is the most frequently occuring word and accounts for 7% of the word occurences and **of** is the second most occuring word which is approximately 3.5% of the corpus, followed by **and**. And only 135 words in the vocabulary account for half the Brown Corpus.

* The same relationship can be seen in other rankings unrelated to language, such as population rank of cities etc.

* It is an empirical law formulated using mathematical statistics that states that many types of data in physical and social sciences can be approximated with a **Zipfian Distribution (ZD)**.

* ZD belongs to a family of discrete power law probabiliy distributions.

### Observations

* It can be seen from Zipf's Law that a relatively small number of words account for a very significant fraction of all text's size.

* These terms make very poor index terms because of their **low discriminative value**.

### [Kullback–Leibler Divergence](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence){:target="_blank"}

* It is the measure of how on probability distribution diverges from a second expected probability distribution.

* Applications lie in finding the **relative (Shannon) Entropy** in information systems, **randomness** in continuous time-series, and **information gain** when comparing statistical models of inference.

* In summary it can help find the amount of information a word provides in a corpus. And the lesser the information a word has the more likely it is to be a stopword.

### Classical Methods

* Zipf's Law can be mathematically represented by 

\\[F(r) = \frac{C}{r_\alpha}\\]
  * Where
    * \\(\alpha \approx 1\\)
    * \\(C \approx 0.1\\) 
    * \\(r\\) is the rank frequency

* Four different classical methods exist by replacing the term frequency \\(r\\) above with one of the four refinements given below.
  * **Term Frequency (TF)**: The number of times a term occurs in a specific collection. 
  * **Normalized TF**: Generated by normalizing the term frequency by the total number of tokens in the collection i.e. the size of the lexicon file given by 
  
  $$TF_{Norm} = -log (\frac{TF}{v})$$

    * Where
      * TF is the term frequency
      * \\(v\\) is total number of tokens in the lexicon file
  * **Inverse Document Frequency (IDF)**: Calculated using the TF distribution where IDF of term k is given by
  \\[idf_k = log (\frac{N_{Doc}}{D_k})\\]
    * Where 
      * \\(N_{Doc}\\) is the total number of documents in the corpus
      * \\(D_k\\) is the number of documents containing term k
    * So infrequently occuring terms have a greater probability of occuring in relevant documents and hence are more informative.
  * **Normalized IDF**: Many normalizing techniques are used in this case but one of the most frequently used ones is given by **Robertson and Sparck-Jones** which normalizes with respect to number of documents not containing the term and adds a constant to both numerator and denominator to moderate extreme values. 

  $$idf_{k Norm} = log (\frac{N_{Doc} - D_k + 0.5}{D_k + 0.5})$$

    * Where 
      * \\(N_{Doc}\\) is the total number of documents in the corpus
      * \\(D_k\\) is the number of documents containing term k

* A **threshold value** is to be determined to produce the best average precision. It cannont be chosen at random. It is needed to check the difference between the frequency of consecutive ranks say \\(F(r)\\) and \\(F(r+1)\\) because if the difference is big enough threshold can be set as \\(frequency \geq F(r)\\) for choosing the stopwords.

```python
# imports
import pandas as pd
from sklearn.feature_extraction.text import TfidfVectorizer

# documents is the list of documents in the collection

vocab = list(set([i for sub_doc in documents for i in sub_doc.strip().split()]))

# TfidfVectorizer from sklearn
vectorizer = TfidfVectorizer(
    stop_words=None,
    norm=None,
    min_df=0,
    sublinear_tf=True,
    token_pattern=r'(?u)\b\w+\b',
    vocabulary=vocab
)

# calculate tf-idf
def tf_idf(documents):
    return vectorizer.fit_transform(documents)

# create dataframe from pandas
tf_idf = pd.DataFrame({'word': vectorizer.vocabulary, 'idf': vectorizer.idf_}, index=None)
tf_idf.sort_values('idf')

def get_word_idf(word):
    return tf_idf.loc[tf_idf.word==word]
```

### Term Based Random Sampling Approach

* Based on how informative a particular term is.

* Importance of term is determined using **Kullback–Leibler divergence measure**.

* Approach is similar to idea of query expansion in which a query is expanded based on a particular query term. The idea is to find terms that complement the initially chosen query terms which follows from the idea that a individual term might be inadequate to express a concept accurately.

* It differs from the standard approach in that instead of finding the similar terms, find all the documents containing the current term and use them as the new sample and then extract the least informative term from the sample by measuring divergence of a given term distribution within the sampled document set from its distribution in the collection. After this Kullback–Leibler divergence can be used to measure the importance of each term.

* Weight of a term t in  the sampled document set is given by 

$$w(t) = P_x . log_2 \frac{P_x}{P_c}$$

  * Where
    * \\(P_x = \frac{tf_x}{l_x}\\)
    * \\(P_c = \frac{F}{token_c}\\)
    * \\(tf_x\\) is the frequency of the query term in the sampled documents
    * \\(l_x\\) is the sum of the length of the sampled document set
    * F is the term frequency of the query term in the collection
    * \\(token_c\\) is the total number of tokens in the whole collection

* Issues and Solutions

  * Selecting a random term has the possibility of finding only one document containing that term which would result in a relatively small sample.
  * This problem can be solved by repeating selection step Y times which would theoretically result in a better sample, creating a better view of term distribution and their importance.

* Advantages:

  * Easier to implement than the classical methods even though algorithm looks complex.
  * Because all steps here are automatic and do not require manual interventions like in the classical techniques for choosing proper threshold.
  * Classical techniques need to check \\(F(r)-F(r+1)\\) listing one by one and tf-idf graph is needed for zipf's law.

```python
# imports
import pandas as pd
from collections import Counter, defaultdict
import re
from math import log

# documents is the list of documents in the collection
# Collection Analysis
tokens = Counter(re.findall(r'\w+', " ".join(documents)))
def F(word):
    return tokens.get(word)
TOKEN_C = len(tokens)
def P_c(word):
    return float(F(word))/TOKEN_C

# creating inverted index
def create_index(data):
    index = defaultdict(list)
    for i, document in enumerate(data):
        for token in document.strip().split():
            index[token].append(i)
    return index
inv_index = create_index(documents)

# sample analysis
def P_x(word):
    sample = [documents[i] for i in inv_index[word]]
    tokens_sample = Counter(re.findall(r'\w+', ' '.join(sample)))
    L_x = 0
    for k, v in tokens_sample.items():
        L_x += v
    return float(tokens_sample[word])/L_x

# kullback leibler divergence
def kl_div(word):
    p_x = P_x(word)
    p_c = P_c(word)
    return p_x * log(p_x/p_c, 2)

# collection analysis if the dataset is not huge
terms = list(tokens.keys())
kl_div_val = []
for t in terms:
    kl_div_val.append(kl_div(t))

df_kl_div = pd.DataFrame({'term': terms, 'kl_div': kl_div_val})
df_kl_div.sort_values('kl_div')

def get_word_kl_metric(word):
    return df_kl_div.loc[df_kl_div.term == word]
```


## REFERENCES:

<small>[Automatically Building a Stopword List for an Information Retrieval System](http://terrierteam.dcs.gla.ac.uk/publications/rtlo_DIRpaper.pdf){:target="_blank"}</small><br>
<small>[Zipf's law](https://en.wikipedia.org/wiki/Zipf%27s_law){:target="_blank"}</small><br>
<small>[Kullback–Leibler Divergence](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence){:target="_blank"}</small>

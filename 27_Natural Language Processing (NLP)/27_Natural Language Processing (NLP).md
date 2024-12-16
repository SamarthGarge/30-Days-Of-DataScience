[<< Day 26](../26_Advanced%20ML%3A%20Hyperparameter%20Tuning/26_Advanced%20ML%3A%20Hyperparameter%20Tuning.md) | [Day 28 >>](../28_Time%20Series%20Forecasting/28_Time%20Series%20Forecasting.md)


# 🌟 Day 27: Natural Language Processing (NLP)

Welcome to **Day 27** of the 30 Days of Data Science series! Today, we dive into the fascinating world of **Natural Language Processing (NLP)**. NLP bridges the gap between human language and computers, allowing machines to understand, process, and generate human text. By the end of this lesson, you will have a solid understanding of the following key topics:

- **NLTK**
- **spaCy**
- **Hugging Face**
- **Topic Modeling with Gensim**
- **Text Summarization**
- **Word Embeddings with Word2Vec and GloVe**



## 📖 Table of Contents

- [🌟 Day 27: Natural Language Processing (NLP)](#-day-27-natural-language-processing-nlp)
  - [📖 Table of Contents](#-table-of-contents)
  - [🔍 What is Natural Language Processing?](#-what-is-natural-language-processing)
  - [📚 NLTK: The Natural Language Toolkit](#-nltk-the-natural-language-toolkit)
    - [1. Tokenization](#1-tokenization)
    - [2. Stopword Removal](#2-stopword-removal)
    - [3. Stemming and Lemmatization](#3-stemming-and-lemmatization)
  - [💡 spaCy: Industrial-Strength NLP](#-spacy-industrial-strength-nlp)
    - [1. Named Entity Recognition (NER)](#1-named-entity-recognition-ner)
    - [2. Part-of-Speech (POS) Tagging](#2-part-of-speech-pos-tagging)
  - [🤗 Hugging Face: Transformers for NLP](#-hugging-face-transformers-for-nlp)
    - [1. Sentiment Analysis](#1-sentiment-analysis)
    - [2. Text Generation](#2-text-generation)
  - [🧠 Topic Modeling with Gensim](#-topic-modeling-with-gensim)
  - [📝 Text Summarization](#-text-summarization)
  - [📖 Word Embeddings with Word2Vec and GloVe](#-word-embeddings-with-word2vec-and-glove)
  - [📓 Practice Exercises](#-practice-exercises)
  - [📜 Summary](#-summary)
    



## 🔍 What is Natural Language Processing?

**Natural Language Processing (NLP)** is a field within Artificial Intelligence that focuses on enabling machines to understand and interact with human language. It has wide applications, including:

- **Text Classification**: Spam detection, sentiment analysis.
- **Machine Translation**: Translating text between languages (e.g., Google Translate).
- **Named Entity Recognition (NER)**: Identifying entities like names, dates, and locations in text.
- **Question Answering**: Building systems like ChatGPT.



## 📚 NLTK: The Natural Language Toolkit

**NLTK** is a powerful Python library for working with text data. It provides tools for tokenization, stemming, lemmatization, and more. Let’s explore some common functionalities.

### 1. Tokenization

Tokenization is the process of breaking text into smaller components, such as words or sentences.

```python
import nltk
from nltk.tokenize import word_tokenize, sent_tokenize

nltk.download('punkt')

text = "Natural Language Processing is fascinating. Let's learn more!"

# Word Tokenization
words = word_tokenize(text)
print("Word Tokens:", words)

# Sentence Tokenization
sentences = sent_tokenize(text)
print("Sentence Tokens:", sentences)
```

### 2. Stopword Removal

Stopwords are common words (e.g., "is", "the") that are often removed in text preprocessing.

```python
from nltk.corpus import stopwords

nltk.download('stopwords')

stop_words = set(stopwords.words('english'))
filtered_words = [word for word in words if word.lower() not in stop_words]

print("Filtered Words:", filtered_words)
```

### 3. Stemming and Lemmatization

- **Stemming** reduces words to their root form (e.g., "running" -> "run").
- **Lemmatization** maps words to their base dictionary form (e.g., "better" -> "good").

```python
from nltk.stem import PorterStemmer
from nltk.stem import WordNetLemmatizer

nltk.download('wordnet')

stemmer = PorterStemmer()
lemmatizer = WordNetLemmatizer()

word = "running"
print("Stemmed:", stemmer.stem(word))
print("Lemmatized:", lemmatizer.lemmatize(word, pos='v'))
```



## 💡 spaCy: Industrial-Strength NLP

**spaCy** is an efficient library designed for large-scale NLP tasks. It supports features like Named Entity Recognition (NER), Part-of-Speech tagging, and dependency parsing.

### 1. Named Entity Recognition (NER)

NER identifies entities such as names, dates, and locations in text.

```python
import spacy

nlp = spacy.load("en_core_web_sm")
text = "Apple was founded by Steve Jobs in Cupertino, California."

doc = nlp(text)
for ent in doc.ents:
    print(ent.text, ent.label_)
```

### 2. Part-of-Speech (POS) Tagging

POS tagging assigns grammatical tags (e.g., noun, verb) to words in a sentence.

```python
for token in doc:
    print(token.text, token.pos_)
```



## 🤗 Hugging Face: Transformers for NLP

Hugging Face provides state-of-the-art NLP models, including BERT and GPT, through the `transformers` library.

### 1. Sentiment Analysis

Use a pre-trained model to classify the sentiment of a given text.

```python
from transformers import pipeline

classifier = pipeline("sentiment-analysis")
result = classifier("I love learning NLP!")
print(result)
```

### 2. Text Generation

Generate text using a language model like GPT-2.

```python
from transformers import pipeline

generator = pipeline("text-generation", model="gpt2")
result = generator("Natural Language Processing is", max_length=30, num_return_sequences=1)
print(result[0]['generated_text'])
```



## 🧠 Topic Modeling with Gensim

**Topic Modeling** is the task of identifying abstract topics within a collection of documents. The `gensim` library provides tools for Latent Dirichlet Allocation (LDA), a popular topic modeling technique.

```python
from gensim import corpora, models
from gensim.models.ldamodel import LdaModel

# Sample data
documents = ["I love data science", "Data science is the future", "NLP is fascinating"]

# Preprocessing
tokenized_docs = [doc.split() for doc in documents]
dictionary = corpora.Dictionary(tokenized_docs)
corpus = [dictionary.doc2bow(doc) for doc in tokenized_docs]

# LDA Model
lda_model = LdaModel(corpus, num_topics=2, id2word=dictionary)
for idx, topic in lda_model.print_topics(-1):
    print(f"Topic {idx}: {topic}")
```



## 📝 Text Summarization

Text summarization condenses a large text into a shorter version while retaining the main points. You can use Hugging Face for extractive summarization.

```python
from transformers import pipeline

summarizer = pipeline("summarization")
text = "Natural Language Processing has a variety of applications, including text summarization. Summarization aims to condense long texts."

summary = summarizer(text, max_length=50, min_length=25, do_sample=False)
print(summary[0]['summary_text'])
```



## 📖 Word Embeddings with Word2Vec and GloVe

Word embeddings are dense vector representations of words. Libraries like `gensim` support Word2Vec, while pre-trained GloVe embeddings are available for direct use.

### Word2Vec Example

```python
from gensim.models import Word2Vec

sentences = [["I", "love", "NLP"], ["Word2Vec", "is", "useful"]]
model = Word2Vec(sentences, vector_size=100, window=5, min_count=1, workers=4)

# Get vector for a word
vector = model.wv["NLP"]
print(vector)
```



## 📓 Practice Exercises

1. Tokenize the following text using NLTK:
   ```
   "The quick brown fox jumps over the lazy dog."
   ```
   Count the number of tokens and remove stopwords.

2. Use spaCy to extract entities from:
   ```
   "Tesla's stock price soared after Elon Musk's announcement in 2023."
   ```

3. Use Hugging Face's sentiment analysis pipeline to analyze:
   ```
   "The movie was a masterpiece, but the ending was disappointing."
   ```

4. Generate a short text completion starting with:
   ```
   "Data Science is the future of"
   ```

5. Use Gensim's LDA model to find topics from the following documents:
   ```
   ["Artificial intelligence is transforming industries", "Machine learning is a subset of AI", "NLP is a key AI application"]
   ```

6. Summarize the following text:
   ```
   "Machine learning is a branch of artificial intelligence that focuses on building systems capable of learning and improving from experience without being explicitly programmed."
   ```



## 📜 Summary

Today, you learned about the foundational tools and techniques for NLP:

- **NLTK**: Preprocessing text with tokenization, stopword removal, and lemmatization.
- **spaCy**: Performing advanced tasks like NER and POS tagging.
- **Hugging Face**: Leveraging pre-trained models for sentiment analysis and text generation.
- **Gensim**: Topic modeling with LDA.
- **Summarization**: Condensing text into shorter forms.
- **Word Embeddings**: Representing words as dense vectors with Word2Vec and GloVe.

NLP is a powerful field with applications in numerous domains. Keep practicing and explore these libraries further to master them!

---



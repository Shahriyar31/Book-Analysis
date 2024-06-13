# Book-Analysis
Book Analysis Project: "Miracle in the Andes" This book analysis project uses Python and Natural Language Processing (NLP) to process and analyze the text from "Miracle in the Andes." The project involves several key steps to extract insights and perform sentiment analysis.
### Description and Summary of the Book Analysis Project

This book analysis project involves multiple stages of processing the text from a book, "Miracle in the Andes," using Python and Natural Language Processing (NLP) techniques. Below is a summary of the key steps and the purpose of each code segment.

### 1. Loading and Preparing the Text

**Code:**
```python
with open("miracle_in_the_andes.txt", "r", encoding="utf-8") as file:
    book = file.read()
print(type(book))
```

**Description:**
The book's text is loaded from a file named `miracle_in_the_andes.txt` and stored as a string in the `book` variable. The type of the `book` variable is then confirmed to be a string.

### 2. Counting Chapters

**Code:**
```python
chapter_count_str = book.count("Chapter")
print("Chapters (string method):", chapter_count_str)

import re
pattern = re.compile(r"Chapter [0-9]+")
findings = re.findall(pattern, book)
print("Chapters (regex method):", len(findings))
```

**Description:**
The number of chapters in the book is counted using two methods:
- **String Method:** Counts occurrences of the word "Chapter".
- **Regex Method:** Uses regular expressions to find all instances of chapter headings formatted as "Chapter [number]".

### 3. Extracting Sentences with the Word "love"

**Code:**
```python
pattern = re.compile(r"[A-Z][^.]*\blove\b[^.]*\.")
findings = re.findall(pattern, book)
print("Sentences with 'love':", findings)
```

**Description:**
A regular expression is used to extract all sentences containing the word "love". The pattern ensures that the sentence starts with a capital letter and includes the word "love" surrounded by non-word characters to match it as a whole word.

### 4. Finding the Most Used Words

**Code:**
```python
pattern = re.compile(r"[a-zA-Z]+")
findings = re.findall(pattern, book.lower())
print("First 5 words:", findings[:5])

d = {}
for word in findings:
    if word in d:
        d[word] += 1
    else:
        d[word] = 1

d_list = sorted([(value, key) for (key, value) in d.items()], reverse=True)
print("5 most used words:", d_list[:5])
```

**Description:**
Words in the book are extracted and converted to lowercase. The frequency of each word is then counted and stored in a dictionary. The dictionary is converted to a list of tuples and sorted to find the most frequently used words.

### 5. Filtering Out Common English Stopwords

**Code:**
```python
import nltk
nltk.download("stopwords")
nltk.download('vader_lexicon')

from nltk.corpus import stopwords
english_stopwords = stopwords.words("english")

filtered_words = []
for count, word in d_list:
    if word not in english_stopwords:
        filtered_words.append((word, count))

print(filtered_words[:10])
```

**Description:**
The NLTK library is used to download and load English stopwords. The most frequent words list is filtered to remove common stopwords, resulting in a list of meaningful words and their counts.

### 6. Sentiment Analysis of the Entire Book

**Code:**
```python
from nltk.sentiment import SentimentIntensityAnalyzer
analyzer = SentimentIntensityAnalyzer()
print(analyzer.polarity_scores(book))
```

**Description:**
The Sentiment Intensity Analyzer from NLTK's VADER lexicon is used to analyze the overall sentiment of the book. It outputs sentiment scores for negativity, neutrality, positivity, and a compound score.

### 7. Sentiment Analysis of Individual Chapters

**Code:**
```python
pattern = re.compile("Chapter [0-9]+")
chapters = re.split(pattern, book)[1:]

for nr, chapter in enumerate(chapters):
    scores = analyzer.polarity_scores(chapter)
    print(nr + 1, scores)
```

**Description:**
The book is split into individual chapters using a regular expression. Each chapter's sentiment is analyzed using the Sentiment Intensity Analyzer, and the sentiment scores are printed for each chapter, helping identify the most positive and negative chapters.

### Summary

This project demonstrates how to load and analyze a book using Python and NLP techniques. It includes:
1. Loading and processing the text.
2. Counting chapters using different methods.
3. Extracting sentences containing specific words.
4. Finding and filtering the most frequently used words.
5. Performing sentiment analysis on the entire book and individual chapters.

The project provides insights into the text's structure, key terms, and sentiment, offering a comprehensive analysis of the book "Miracle in the Andes."

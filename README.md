Here’s a revised version with updated and working logos for NLTK and Jupyter Notebook:

---

# ![Book Icon](https://img.icons8.com/fluency/48/000000/book.png) Book Analysis Project: *"Miracle in the Andes"*

---

📖 **Book Analysis Project** is a comprehensive data analysis project that leverages Python and Natural Language Processing (NLP) techniques to analyze the text of the book *"Miracle in the Andes"*. This project involves various steps, including text processing, chapter analysis, word frequency analysis, and sentiment analysis, to extract meaningful insights from the book.

---

### **Key Features:**

- **Text Loading and Preparation**: Efficiently loads and prepares the text for analysis.
- **Chapter Count Analysis**: Uses multiple methods to accurately count the number of chapters in the book.
- **Word and Sentence Extraction**: Identifies specific words or phrases, such as "love," and extracts relevant sentences.
- **Word Frequency Analysis**: Determines the most frequently used words, filtering out common English stopwords.
- **Sentiment Analysis**: Analyzes the overall sentiment of the book and individual chapters, highlighting emotional trends.

---

### **Project Overview**

1. **Loading and Preparing the Text**

   - **Description**: The project begins by loading the text of *"Miracle in the Andes"* from a file. This step ensures that the text is in the correct format for subsequent analysis.

   - **Code Example**:
   ```python
   with open("miracle_in_the_andes.txt", "r", encoding="utf-8") as file:
       book = file.read()
   print(type(book))
   ```

2. **Counting Chapters**

   - **Description**: The number of chapters is counted using both string methods and regular expressions to ensure accuracy.

   - **Code Example**:
   ```python
   chapter_count_str = book.count("Chapter")
   import re
   pattern = re.compile(r"Chapter [0-9]+")
   findings = re.findall(pattern, book)
   print("Chapters:", len(findings))
   ```

3. **Extracting Sentences with Specific Words**

   - **Description**: The project uses regular expressions to extract sentences containing specific words like "love," providing insights into the context in which these words are used.

   - **Code Example**:
   ```python
   pattern = re.compile(r"[A-Z][^.]*\blove\b[^.]*\.")
   findings = re.findall(pattern, book)
   print("Sentences with 'love':", findings)
   ```

4. **Finding and Filtering the Most Used Words**

   - **Description**: The project identifies the most frequently used words in the book and filters out common stopwords, revealing the key terms that define the text.

   - **Code Example**:
   ```python
   from nltk.corpus import stopwords
   nltk.download("stopwords")
   pattern = re.compile(r"[a-zA-Z]+")
   findings = re.findall(pattern, book.lower())
   english_stopwords = stopwords.words("english")

   d = {}
   for word in findings:
       if word in d:
           d[word] += 1
       else:
           d[word] = 1

   d_list = sorted([(value, key) for (key, value) in d.items()], reverse=True)
   filtered_words = [(word, count) for (count, word) in d_list if word not in english_stopwords]
   print("Filtered words:", filtered_words[:10])
   ```

5. **Sentiment Analysis of the Entire Book**

   - **Description**: Sentiment analysis is performed on the entire book to assess the overall emotional tone, using NLTK’s Sentiment Intensity Analyzer.

   - **Code Example**:
   ```python
   from nltk.sentiment import SentimentIntensityAnalyzer
   analyzer = SentimentIntensityAnalyzer()
   print(analyzer.polarity_scores(book))
   ```

6. **Sentiment Analysis of Individual Chapters**

   - **Description**: The book is divided into chapters, and sentiment analysis is performed on each one, identifying the most positive and negative chapters.

   - **Code Example**:
   ```python
   pattern = re.compile("Chapter [0-9]+")
   chapters = re.split(pattern, book)[1:]

   for nr, chapter in enumerate(chapters):
       scores = analyzer.polarity_scores(chapter)
       print(nr + 1, scores)
   ```

---

### **Project Structure:**

```
Book-Analysis/
│
├── analysis/
│   ├── chapter_analysis.py   # Chapter counting and analysis
│   ├── word_frequency.py     # Word frequency analysis
│   ├── sentiment_analysis.py # Sentiment analysis of the book
│   └── sentence_extraction.py # Extracting specific sentences
│
├── data/
│   └── miracle_in_the_andes.txt # Book text file
│
├── notebooks/
│   ├── data_exploration.ipynb  # Jupyter notebook for exploratory analysis
│
├── requirements.txt           # Project dependencies
└── README.md                  # Project documentation
```

---

### **Technologies Used:**

- ![Python](https://img.icons8.com/fluency/48/000000/python.png) **Python**: Core programming language for text processing and analysis.
- <img src="https://www.vectorlogo.zone/logos/nltk/nltk-icon.svg" alt="NLTK" height="48"/> **NLTK**: Used for Natural Language Processing and sentiment analysis.
- <img src="https://raw.githubusercontent.com/github/explore/main/topics/jupyter-notebook/jupyter-notebook.png" alt="Jupyter" height="48"/> **Jupyter Notebooks**: For interactive data exploration and visualization.

---

### **Setup & Installation:**

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/YourUsername/Book-Analysis.git
   cd Book-Analysis
   ```

2. **Install Required Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run Analysis Scripts:**
   - Execute individual Python scripts or explore the data using Jupyter Notebooks.

---

### **Usage:**

- **Text Analysis**: Run the scripts to analyze the text for chapter counts, word frequencies, and sentiment.
- **Visualization**: Use the Jupyter Notebooks for further exploration and visualization of the analysis results.

---

### **Contact:**

For any inquiries or support, please contact:

- **Name**: Farhan Shahriyar
- **Email**: shahriyar@example.com
- **GitHub**: [Shahriyar31](https://github.com/Shahriyar31)

---

**Book Analysis Project** offers a powerful framework for analyzing books and extracting meaningful insights using modern NLP techniques. Perfect for anyone interested in text analysis and natural language processing!

---

**Technologies Used:**

<p align="center">
  <img src="https://img.icons8.com/fluency/48/000000/python.png" alt="Python" height=48/>
  <img src="https://www.nltk.org/images/logo.png" alt="NLTK" height="48"/>
  <img src="https://raw.githubusercontent.com/github/explore/main/topics/jupyter-notebook/jupyter-notebook.png" alt="Jupyter" height= 48/>
</p>

---

This README should now provide a clear and visually appealing overview of your project with working logos for all technologies used!

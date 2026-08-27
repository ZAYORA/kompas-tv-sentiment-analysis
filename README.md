# Kompas TV YouTube Sentiment Analysis

An Indonesian sentiment analysis project that compares audience reactions to two different types of YouTube content from **Kompas TV**.

The project analyzes YouTube comments from a **Short video** and a **news video**, then classifies the comments into **positive, negative, and neutral** sentiment using an Indonesian RoBERTa-based sentiment classifier.

---

## Project Overview

This project investigates whether different types of video content are associated with different patterns of audience sentiment.

Two Kompas TV YouTube videos are analyzed:

- **Video 1:** A YouTube Short featuring Megawati discussing the number of her followers.
- **Video 2:** A news video discussing the testimony of an ambulance driver during the evacuation of Brigadier J's body.

The comments are collected from YouTube and processed through a text preprocessing pipeline before sentiment classification.

---

## Objectives

The main objectives of this project are:

- Collect comments from two YouTube videos.
- Compare audience responses between different types of video content.
- Perform Indonesian text preprocessing.
- Apply sentiment classification using an Indonesian RoBERTa model.
- Compare positive, negative, and neutral sentiment distributions.
- Visualize sentiment distributions and frequently occurring words.

---

## Dataset

The data used in this project consists of YouTube comments collected from two Kompas TV videos using `yt-dlp`.

### Video 1

**Title:**  
*Megawati: Kalau Aku Mau Selfie, Pengikutku Pasti 'Akeh'*

**Type:** YouTube Short

**Video ID:** `5m31aKW6VyM`

### Video 2

**Title:**  
*Pengakuan Sopir Ambulans Saat Evakuasi Jenazah Brigadir J*

**Type:** News Video

**Video ID:** `ZriDaJlL0lU`

The original comments are collected when the notebook is executed. Because YouTube comments can change over time, the number of collected comments may differ between runs.

---

## Methodology

```text
YouTube Videos
      ↓
Comment Extraction
      ↓
Data Preparation
      ↓
Text Cleaning
      ↓
Tokenization
      ↓
Indonesian Stopword Removal
      ↓
Sastrawi Stemming
      ↓
Indonesian RoBERTa Sentiment Classification
      ↓
Sentiment Comparison
      ↓
Visualization & Word Frequency Analysis
```

### 1. Comment Extraction

Comments are collected from both YouTube videos using `yt-dlp`.

### 2. Data Preparation

The comments are combined into a single Pandas DataFrame and labeled according to their source video.

### 3. Text Cleaning

The comments are normalized by:

- Removing URLs
- Removing non-ASCII characters
- Removing numbers and symbols
- Converting text to lowercase
- Removing extra whitespace

### 4. Tokenization

The cleaned text is split into individual words.

### 5. Stopword Removal

Indonesian stopwords are removed using the NLTK Indonesian stopword list.

The words `tidak` and `bukan` are retained because they can affect the meaning and polarity of a sentence.

### 6. Stemming

The remaining words are transformed into their root forms using **Sastrawi**.

### 7. Sentiment Classification

Sentiment classification is performed using:

`w11wo/indonesian-roberta-base-sentiment-classifier`

The model classifies each comment into:

- Positive
- Negative
- Neutral

### 8. Sentiment Comparison

The sentiment distributions of the two videos are compared using comment counts and percentages.

### 9. Visualization

The project includes:

- Sentiment distribution comparison
- Stacked bar chart
- WordCloud for each video
- Top frequent words for each video

---

## Technologies

- **Python**
- **Pandas**
- **yt-dlp**
- **NLTK**
- **Sastrawi**
- **Hugging Face Transformers**
- **PyTorch**
- **Matplotlib**
- **WordCloud**
- **Jupyter Notebook**
- **Google Colab**

---

## Project Structure

```text
kompas-tv-sentiment-analysis/
│
├── notebook/
│   └── analisis_sentimen_kompas_tv.ipynb
│
├── README.md
├── requirements.txt
└── .gitignore
```

The raw comments and generated CSV files are not included in the repository.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/USERNAME/kompas-tv-sentiment-analysis.git
cd kompas-tv-sentiment-analysis
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

---

## Running the Notebook

The notebook is designed to be run using **Google Colab** or a Jupyter environment.

Open:

```text
notebook/analisis_sentimen_kompas_tv.ipynb
```

Run the cells sequentially from the beginning.

The notebook requires an internet connection during the data collection stage because comments are extracted directly from YouTube.

> YouTube comments can change over time, so rerunning the notebook may produce different results.

---

## Output

The notebook generates:

- Sentiment classification results
- Sentiment distribution tables
- Sentiment comparison visualization
- WordCloud for each video
- Top frequent words
- CSV files containing processed sentiment data

Generated files include:

```text
hasil_sentimen_kompas_tv.csv
video1_sentimen.csv
video2_sentimen.csv
```

These files are generated during notebook execution and are not required to be stored in the repository.

---

## Limitations

Several limitations should be considered:

- The analysis only covers two YouTube videos.
- The collected comments represent the comments available during the extraction process.
- YouTube comment availability may change over time.
- Sentiment classification relies on a pretrained Indonesian RoBERTa model.
- Sarcasm, slang, context, and ambiguous expressions may not always be classified correctly.
- The analysis describes sentiment patterns but does not establish a causal relationship between video type and audience sentiment.

---

## Reference

The sentiment classifier used in this project:

`w11wo/indonesian-roberta-base-sentiment-classifier`

The model is available through the Hugging Face Hub.

---

## License

This project is intended for educational and analytical purposes.

The YouTube comments analyzed in this project originate from publicly accessible YouTube content. The original content and associated rights remain with their respective owners.

Impact of Social Media on Mental Health
Overview
This project aims to analyze the impact of social media on mental health by examining user posts across various platforms. Utilizing data manipulation, text processing, sentiment analysis, and visualizations, this project seeks to understand the emotional tone of posts and how different platforms may contribute to mental health issues.

Table of Contents
Overview
Features
Technologies Used
Data
Installation
Usage
Results
Contributing
License
Features
Data Collection: Simulated social media posts from multiple platforms such as Instagram, Twitter, Facebook, Snapchat, YouTube, and more.
Data Preprocessing: Clean and prepare data using regular expressions, tokenization, and stopwords removal.
Sentiment Analysis: Analyze the emotional tone of posts using TextBlob to determine polarity (positive, negative, neutral).
Visualization: Create insightful visualizations to present findings on how different platforms influence mental health.
Accuracy Evaluation: Compare predicted sentiment with ground truth sentiment to assess the model’s accuracy.
Technologies Used
Python: For scripting and data manipulation.
Pandas: For handling and manipulating data structures.
NLTK: For natural language processing, including tokenization and stopwords removal.
TextBlob: For sentiment analysis and text processing.
Matplotlib: For creating visualizations and plots.
Data
The dataset used in this project includes simulated social media posts from various platforms. Each post includes information about the platform, user ID, post text, and timestamp.

Installation
To get started with this project, follow these steps:

Clone the Repository:
git clone https://github.com/ANURAGANAND7/IMPACT-OF-SOCIAL-MEDIA-ON-MENTAL-HEALTH.git

Install Dependencies:
pip install pandas nltk textblob matplotlib

Download NLTK Data:
import nltk
nltk.download('stopwords')
nltk.download('punkt')

Usage
To run the sentiment analysis and visualize the results, follow these steps:

Create a DataFrame:
import pandas as pd

data = {
    'platform': ['Instagram', 'Twitter', ...],  # Include all platform data
    'user_id': [101, 102, ...],  # Include all user IDs
    'post_text': ['Feeling really down today. Can’t seem to shake it off. 😔 #depression', ...],  # Include all post texts
    'timestamp': ['2024-06-30 10:00:00', ...]  # Include all timestamps
}
df = pd.DataFrame(data)

Preprocess Text:
import re
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

stop_words = set(stopwords.words('english'))

def preprocess_text(text):
    text = re.sub(r'[^\w\s]', '', text)
    tokens = word_tokenize(text)
    tokens = [word.lower() for word in tokens if word.lower() not in stop_words]
    return tokens

df['processed_text'] = df['post_text'].apply(preprocess_text)

Perform Sentiment Analysis:
from textblob import TextBlob

def get_sentiment(text):
    analysis = TextBlob(text)
    return analysis.sentiment.polarity

df['sentiment'] = df['post_text'].apply(get_sentiment)

Evaluate Accuracy:
df['ground_truth_sentiment'] = df['post_text'].apply(lambda x: 1 if 'positive' in x or '😊' in x else 0)
df['predicted_sentiment'] = df['sentiment'].apply(lambda x: 1 if x > 0 else 0)
accuracy = (df['ground_truth_sentiment'] == df['predicted_sentiment']).mean()
print(f"Accuracy: {accuracy:.2f}")

Visualize Results:
import matplotlib.pyplot as plt

plt.figure(figsize=(12, 8))
plt.bar(df['platform'], df['sentiment'], color='skyblue')
plt.xlabel('Platform')
plt.ylabel('Sentiment Polarity')
plt.title('Sentiment Analysis of Posts Across Platforms')
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.show()

Results
The project provides a detailed analysis of sentiment across various social media platforms, highlighting patterns and potential areas of concern related to mental health.




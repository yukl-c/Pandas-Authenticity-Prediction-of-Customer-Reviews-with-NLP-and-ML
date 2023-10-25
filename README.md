# Pandas-comment-default-prediction-with-NLP
Pandas comment default prediction with NLP

# Background:

E-commerce is gaining popularity, enabling customers to make purchases online without visiting physical stores. Customers increasingly rely on reviews and feedback from other users to make informed decisions. However, the presence of fake reviews can influence customer choices. In this case, I have a Yelp dataset that I'll use to predict whether comments are genuine or fake.

# Types of Data:

The dataset consists of 359,052 rows, with a label of 1 indicating real data and -1 indicating fake data. I merged Yelp Metadata and Yelp Dataset, resulting in 227,981 records. I removed irrelevant columns such as Review_id, Product_id, and Review_Date, as they do not contribute to the results.

# Data Manipulation and Cleansing:

After checking for null data (which was not found), I noticed an imbalance in the labeled data, with 205,145 records labeled as 1 and 22,836 records labeled as -1. To address this and improve efficiency, I randomly selected 1,000 representative samples from both labels, resulting in a balanced dataset for analysis and training.

# Natural Language Processing (NLP):

To prepare the comments for training, I applied NLP techniques. I removed stop words and punctuation, tokenized the sentences into words, and performed stemming and lemmatization. The processed words were then transformed into numerical data for further analysis using vectorization and count vectorization.

# Modelling:

I employed Naïve Bayes (NB) as the baseline model, as well as multilayer perceptron (MLP) and an ensemble method combining NB and MLP for comparison. To prevent overfitting, I used cross-validation (CV) in each model.

The table below shows the accuracy and modeling time for each model:

Model	Accuracy	Time (seconds)

NB	0.58	73.9

MLP	0.60	44.90

NB + MLP	0.61	115.42

NB w/ CV	0.61	369.29

MLP w/ CV	0.58	620.67

NB + MLP w/ CV	0.58	813.57

# Exploratory Data Analysis:

I analyzed the word counts of each record and observed that most comments had less than 1,000 words, indicating a significant skew. I calculated the sentiment index for each record and generated a correlation matrix graph, which revealed a strong positive correlation between length and sentiment (0.66). There were weak positive correlations between rating and polarity (0.27), length and label (0.18), polarity and label (0.17), and rating and label (0.026). A weak negative correlation was observed between length and rating (-0.16).

I also created a scatter diagram to visualize the strong positive correlation, demonstrating that most samples had lengths below 2,000 and polarity scores below 40. Additionally, a bar graph illustrated the feature importance to the label, indicating that length was the most important among the three features. Histograms based on label count and length showed left-skewness.

To assess the classification model's performance, I generated a confusion matrix, which indicated a high number of true positives and true negatives, and a low number of false positives and false negatives.

# Conclusion:

In conclusion, I calculated the polarity and length of comments for further analysis. I applied natural language processing techniques to convert textual data into numerical form for training. Based on the results, the ensemble method of Naïve Bayes and multilayer perceptron proved to be the most suitable model for this case.

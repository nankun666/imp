# Overview
The Efficient Market Hypothesis (EMH) asserts that stock prices fully incorporate all available information at any point in time. Traditional financial analysis often emphasizes structured numerical data, such as historical prices or financial ratios. However, unstructured news text contains valuable contextual information, including sentiment, tone, emerging developments, and implicit signals, which may not be captured through quantitative indicators alone. This study investigates the potential relationship between news headlines and stock market trends, aiming to determine whether sentiment and content within headlines can predict market movements. Using a comprehensive dataset of financial news and corresponding market indices, natural language processing (NLP) techniques are applied to quantify sentiment and extract key themes.

### **Setup Instructions**
In this project, I configured and provisioned a Spark cluster on **AWS EMR (Elastic Map Reduce)**, connecting it to a Jupyter Notebook to leverage transformations and actions using **PySpark**. 

##### 1. **Create and Configure Spark Cluster**

- Launch an **AWS EMR** cluster with Spark installed.
- Configure the necessary permissions and attach appropriate IAM policies.

##### 2. **Set Up Notebook Environment**

- Access **AWS Studio** and launch a workspace.
- Connect the EMR cluster to the notebook environment to enable **PySpark** for data processing and analysis.

##### 3. **Access Data**

- Load the dataset from a **AWS S3 bucket** into the cluster for analysis.

### Data Source
The data is read from a **AWS S3 bucket**.

### Analysis using pySpark

##### Part I: Installation and Initial Setup

In this part, I load the dataset into a **PySpark DataFrame** and import the necessary dependencies.

##### Part II: NLP pipeline

To prepare the datasets for analysis, several preprocessing steps are applied. Firstly, data cleaning is performed by converting all news headlines to lowercase, removing stopwords, and eliminating punctuations and special characters to standardize the text. Tokenization is then performed to split the news headlines into individual tokens. Lemmatization is applied using NLTK's WordNetLemmatizer, which reduces words to their base forms while leaving those unchanged that are not found in the WordNet corpus. Once the text preprocessing is complete, the news headline dataset is merged with the stock price dataset, enabling the integration of textual features with a corresponding stock market movement for the modeling process. The combined dataset is then split into two subsets: 80% for training and 20% for testing, ensuring reliable model evaluation.

##### Part III: Modeling

Feature extraction and engineering techniques were applied to prepare the text data for analysis. TF-IDF (Term Frequency-Inverse Document Frequency) was used to transform textual data into numerical features by emphasizing term importance, while sentiment scores—Positive, Negative, Neutral, and Compound—were generated using the VADER model to capture the emotional tone of the text. Named Entity Recognition (NER) was employed to extract meaningful entities, such as organizations, adding further context to the data. Lagged sentiment features were introduced to identify temporal patterns and improve predictive accuracy. Machine learning models, including Random Forest with SMOTE to address class imbalance, Logistic Regression with hyperparameter tuning, Naive Bayes incorporating NER features, and Linear Regression to infer relationships between features and DJIA, were implemented. To address high dimensionality, Principal Component Analysis (PCA) was applied to streamline the feature space while retaining essential information for model training and evaluation.

##### Part IV: Evaluation and Insights

To evaluate the performance of the models, various metrics were considered, including accuracy, precision, recall, F1 score, and ROC-AUC. The classification models—Random Forest, Logistic Regression, and Naive Bayes—were assessed based on their ability to predict stock price movements. While the models showed some potential, their performance was limited, as evidenced by the moderate F1 scores. One key factor contributing to this limitation is the inherent complexity of stock price fluctuations, which are influenced by a wide range of factors beyond just news sentiment, including economic indicators, market trends, and investor behavior. While news provides valuable insights, it cannot fully capture the multitude of variables that drive stock market dynamics.

![Alt Text](/ner.png)

In addition to the classification models, the linear regression model provided valuable insights into how sentiment and specific keywords influence DJIA. By analyzing the coefficients of the regression model, it was observed that certain words related to geopolitical issues, natural disasters, and health crises had a stronger influence on the DJIA. For instance, words like "cancer" and "hacking" were found to have a significant negative impact, indicating that such topics may trigger negative market sentiment.

![Alt Text](/example.png)

The complexity of market dynamics, combined with the presence of numerous external factors, suggests that while news sentiment can provide some indication of market trends, it is not sufficient to make reliable predictions on its own. Therefore, further research and the inclusion of additional features, such as economic indicators and investor sentiment, are necessary to improve the predictive power of these models.


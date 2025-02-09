# Overview

In this project, I configured and provisioned a Spark cluster on **AWS EMR (Elastic Map Reduce)**, connecting it to a Jupyter Notebook to leverage transformations and actions using **PySpark**. The goal was to perform nlp analysis to predict the index movements.



### **Setup Instructions**

##### 1. **Create and Configure Spark Cluster**

- Launch an **AWS EMR** cluster with Spark installed.
- Configure the necessary permissions and attach appropriate IAM policies.

##### 2. **Set Up Notebook Environment**

- Access **AWS Studio** and launch a workspace.
- Connect the EMR cluster to the notebook environment to enable **PySpark** for data processing and analysis.

##### 3. **Access Data**

- Load the IMDB dataset from a **AWS S3 bucket** into the cluster for analysis.

  

### Data Source
The data is read from a **AWS S3 bucket**.



### Analysis using pySpark

##### Part I: Installation and Initial Setup

In this part, I load the dataset into a **PySpark DataFrame** and import the necessary dependencies.

##### Part II: NLP pipeline

Here, I developed an NLP pipeline for advanced text preprocessing, including tokenization, normalization (punctuation, stemming)

##### Part III: Modeling

This part, I implemented TF-IDF, NER, and Sentiment Analysis to extract key features, and utilized Scikit-learn for model building

##### Part IV: Insights

Finally, I evaluted the models and provided the insight from analysis.
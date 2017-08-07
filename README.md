# Topic Modeling For Twitter Accounts
#### Burak Suyunu - Mehmet Akif Çördük
#### Advisor: Assoc. Prof. Ali Taylan Cemgil

Here is a 5 minute video which explains every aspects of this project with resluts: https://www.youtube.com/watch?v=pyTBeudsTYQ

## What are They Tweeting About?
* Makers, scientists, influencers and many other people share their ideas, products and innovations via the most intellectual social network **Twitter**.
* It is hard to find the information about a **topic** in the giant network of Twitter.
* Our aim is to find users who are tweeting about the same **topic**. With this aim we want to bring people interested in the same **community** together.
* In this project, we focused on **maker** communities and **influencers** in the context of computer science, such as **ML, Robotics, 3D Printing, Arduino**.
* We worked on **1.118** users and approximately **3.250.000** tweets.

## Dataset - Similar-Twtiiter
We created this tool to find similar users to a given user base on Twitter. It works like this:
1. Determine base users which will underlie our similar user database.
2. Get lists of our base users which they are a member of
3. Find common lists of base users
4. Get members of the common lists.

## Maintaining Tweets – NLP
* **Imagination is more important than knowledge: https://Einstein.co #Einstein**
* **Remove URLs**
  * Imagination is more important than knowledge: #Einstein
* **Tokenization**
* **Stop Words**
  * ['imagination', 'important', 'knowledge', 'einstein']
* **Remove non-English accounts**
* **Stemming**
  * ['imagin', 'import', 'knowledg', 'einstein']
* **Remove words that appears at most 10 times in the whole corpus**

## Clustering Words - word2vec
* **Word2Vec** uses word embedding to map words to a **vector** of real numbers. 
* We applied **k-means clustering** to the vectors to see the relevant words together.
* We chose the word at the **center** of the cluster to represent the other words from the same cluster in the word corpus.
* We **normalized** the number of occurrences in the corpus to handle the problem of less frequent words being more important.

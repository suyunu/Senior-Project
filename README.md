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

## Clustering Words - Word2Vec
* **Word2Vec** uses word embedding to map words to a **vector** of real numbers. 
* We applied **k-means clustering** to the vectors to see the relevant words together.
* We chose the word at the **center** of the cluster to represent the other words from the same cluster in the word corpus.
* We **normalized** the number of occurrences in the corpus to handle the problem of less frequent words being more important.

## Topic modeling
* In machine learning and natural language processing, a topic model is a type of statistical model for discovering the topics that occur in a collection of documents.
* We know that a document is about a particular topic, we expect particular words to appear more often than others since some words are more related to the subject.
* So we are trying to learn topic distribution over the vocabulary or word distributions of the topics.

##### Example:
1. I like to eat broccoli and bananas.
2. I ate a banana and spinach smoothie for breakfast.
3. Hamsters and kittens are cute.
4. My sister adopted a kitten yesterday.
5. Look at this cute hamster munching on a piece of broccoli.

* **Sentences 1 and 2:** 100% Topic A
* **Sentences 3 and 4:** 100% Topic B
* **Sentence 5:** 60% Topic A, 40% Topic B

* **Topic A:** 30% broccoli, 15% bananas, 10% breakfast, 10% munching, … (**Food**)
* **Topic B:** 20% chinchillas, 20% kittens, 20% cute, 15% hamster, … (**cute animals**)

### LDA (Latent Dirichlet Allocation)
* Assign each word in a document to one of **K topics** randomly
* To obtain a correct distribution, iterate over each document D and for each document iterate over each word W. 
* Then, for each topic T reassign the word W to a new topic T’:
* 𝑃(𝑊𝑜𝑟𝑑 𝑊 |  𝑇𝑜𝑝𝑖𝑐 𝑇)∗𝑃(𝑇𝑜𝑝𝑖𝑐 𝑇 |  𝐷𝑜𝑐𝑢𝑚𝑒𝑛𝑡 𝐷)

### NMF (Non-Negative Matrix Factorization)
* NMF decomposes the data into two **low rank matrices (W, H)** whose product constitutes the data matrix.
* At each iteration, update W and H with additive update rules to minimize the **squared error** to reach a good decomposition.

* **NMF** + Kullback-Leibler Divergence + Drichlet priors on distributions => **LDA**
* **NMF** trains much faster than **LDA** 

## Conclusion
* The hardest part of our project is the **evaluation** of results. Because all the results we got from topic modeling algorithms needs **human interpretation**. So, to make those interpretation clear and understandable we came up with the idea of **color coded charts**. Even it is hard to interpret, we got very promising and comparable results (see the video). While **NMF** generally gives **better** results than **LDA**; **Word2Vec** improved both methods significantly in capturing the general idea.
* All in all, one can find different datasets with **Similar-Twitter** and analyze them with our **Topic Modeling** approaches to create communities.

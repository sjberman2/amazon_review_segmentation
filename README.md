# Preforming Topic Modeling on Amazon Review Data
#### Author: Jillian Berman [Linkedin](https://www.linkedin.com/in/sarajillianberman/) 
### Contents 
- [Problem Statement](#Problem-Statement)
- [Data](#Data)
- [Executive Summary](#Executive-Summary)
- [Limitations](#Limitations)
- [Conclusion & Recommendations](#Conclusion-&-Recommendations)

### Problem Statement 
It is no secret that Amazon has completely changed the way people are shopping. What started as an online bookstore has grown to so much more, taking out much of the competition in their way. They've effectively lead to the shuttering of many brick and mortar bookstores. Book selling is really only a fraction of their business these days though, with the purchase in 2017 of Whole Foods, and their cloud computing and digital streaming services-- their many subsidiaries make them one of the largest companies in the world. According to research firm eMarketer, apparel and accessories represented 29% of Amazon's retail e-commerce sales in the U.S. in 2018, generating $35.79 billion (Lee, 2019).

While those are great results, there is always room for improvement. From the companies own actions they are looking to increase their share of the market for this department. Amazon Fashion recently begun a series of limited-edition influencer-designed collections called The Drop. The collections drop every Thursday and are available for purchase for only 30 hours, making the pieces extra exclusive. In even simpler ways, on the Amazon Fashion home page, they highlighting links to lists of items that have over a certain threshold of reviewers as, 'Customer's most loved styles'. Once you navigate to that page, they've even taken this up a step further with different product categories and influencer's reviews of popular products. This final example really highlights the ways in which Amazon is really dominating many different markets. Later this month, Amazon Prime, their streaming service, is releasing "Making The Cut" a fashion-based reality TV show with Heidi Klum and Tim Gunn, of Project Runway fame. The premise of the show is designers will compete to launch a new fashion brand and a 1 million dollar prize. The winning designs will then be available to shop on Amazon Fashion immediately afterwards.

These techniques are all really creative and standby Amazon's mission to be the world's most customer centric company, but there are certain standard techniques that they aren't currently using. Most retailers send customer's emails with product suggestions, this not a technique that Amazon is currently using. This project will be to do topic modeling using the Latent Dirichlet Allocation method on Amazon Review data to find the most relevant topics to help inform product suggestions for marketing emails. 

Working with Amazon Review data provided by Jianmo Ni at UCSD, we will process the text of reviews using NLP techniques, then process the data using the unsupervised method, Latent Dirichlet Allocation, for topic modeling. From there we will consider the models coherence 𝑐𝑣 scores to find the number of topics that best represent our dataset. Finally, we will then  run the model of the testing data and evaulate the the perplexity score and cohernce scores. 

The Amazon Review data can be found [here](https://nijianmo.github.io/amazon/index.html).

### Executive Summary 

We begin by reading in the 2 datasets, the first dataset is the Amazon Fashion review dataset and the second is the Metadata for the products being reviewed. From there we begin data cleaning by removing extraneous columns from the review dataset as well as any rows where there is missing data in the `reviewText` column.  We also then need to transform the `reviewerID` column and the `asin` column into the proper data types for modeling. 
Next, we began processing the text of the `reviewText` column for Topic Modeling. We use Regex to tokenize data, then removed any stopwords, lemmatized the data and created bi-grams of the reviews to increase model effectiveness.  From there we create our dictionary of words used and our bag of words corpus to use for modeling. We chose to use Latent Dirichlet Allocation modeling because it allows us to identify different topics in the documents and map those documents to different topics. 
We will tune over a range of values for the number of topics that  appropriate for our dataset by examining the coherence 𝑐𝑣 score and the perplexity scores.  From we create our working model which we then run our testing data through to evaluate the perplexity on untrained data. From there we dive into examining the topics that were created. The topics contain the most frequently occurring words along with the probability of their occurrence. 

### Limitations
There are a few limitations we should consider when it come to this model. First, the model was trained specifically on the data from the Amazon Fashion dataset, it will not perform as well on any other product group on Amazon. You would need to re-train the model for each different product group, as the words and topics in the reviews will be different.

LDA modeling works by creating topics based off the frequency of their appearance within the corpus, which explain why we got a few cluster that mostly represented customers emotions, like satisfaction and dissatisfaction. 

### Conclusions & Recommendations 
Using LDA modeling we were able to find the ideal number of topics for our dataset was 10. We then built our working model which had the following results: 

|Metric| Training Score| Testing Score| 
|---|---|---|
|Coherence 𝑐𝑣|0.659 | 0.663|
|Perplexity|-7.089 | -7.104| 

Our testing data actually performed slightly better than the training data. After examining the 10 topics created by the model it was pretty easy to identify what most of the topics were about, but not all of them were useful for segmenting types of products purchased, they also represented the customer's feelings about the products which makes sense because they are leaving reviews. The product groups that are represented in the topics are: women's clothing, jewelry, small accessories/ handbags, footwear, seasonal accessories, and gifting.These are all categories that would translate well to suggestion through a e-mailed marketing campaign. 

All data is prepped and processed to do additional modeling with the result from the LDA topic modeling. From here, it would be cool to build a classification model to try and predict what topic a review might fall under. These outputs could also be used along with the reviewer and product information to create customer segmentations. 

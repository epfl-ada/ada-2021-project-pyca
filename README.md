# Predicting Box-Office Receipts from News Quotations


## Abstract

TO DO: write short description here

***

## Introduction


The motion pictures industry has become a roaring success that breaks records of 42 billion U.S. dollars in the global box office in 2019. In U.S. and Canada, the box office receipt is over 10 billion U.S. dollars between the year of 2015-2019. Recent years, numerous of research work has uncovered which attributes might predict the financial success of motion pictures after they have been released, and why some movies could be “hits” or “flops” using automation methods. In our study, we explore the important role of word of mouth on predicting the financial success of box-office receipts in 2015-2019 from the longitudinal time sequence (i.e., before and after the release date). More specifically, our study will address the following key questions:

* *Does the quantity of quotations from movie associated persons provide a boost to box-office revenue?*
* *Which textual factors from quotations influence the financial performance of movies, and when (i.e., before or after the release date)?*
* Which model (e.g., SVM and Neural Network) has better predictive performance in forcasting the box-office receipts, given the spreading and content of quotations and influential power of speaker?*

***

## Dataset Used
In our study, we combine the Quotabank database with the IMDb movie information dataset and box-office receipts from box office mojo. The first dataset of IMDb movie database contains six types of movie data: (*i*) movie name title; (*ii*) the genre of movie, such as comedy, fantasy category; (*iii*) the release year (we select the movies in the year 2015-2019); (*iv*) region (focus on U.S. and U.K.); (*v*) runtime (in minutes). The second dataset from box office moji displayed the financial performance of movies in: (*i*) the gross revenue (in U.S. dollars, the average revenue??); (*ii*) ranking of box-office receipts; (*iii*) total gross revenue (???); (*iv*) release date and year. After that, we merge both IMDb movie and box-office receipts datasets together by movie name and release year. Further we extract key persons in the movie (e.g., actor or actress of casting, director, and producer) in order to retrieve their quotations from the Quotabank database. By doing so, we assume that the spreading of quotation from movie associated key figure might influence the financial performance of the movies. To understand the influence of quotations on box-office receipts, it is important to examine the **depth and size** (the quantity of movie associated person quotations before and after the release date of movie), the **breadth** (the number of movie associated persons involved in the quotations over time), the **dynamics of content in quotations** (e.g., the change of sentiment polarity in quotation over time, variations in topical categories of quotation) and **influential power of speaker** in the cast (the actor/actress/director's past revenue, the uniqueness/familiarity of pair in movie casting etc.) 

***

## Methods 

TO DO: More details here, combination of machine learning and statistical modeling

1. Sentiment Analysis 

2. Topical categories of quotations

3. Prediction methods (logical regressions, SVM, Random forest, Neural network etc.)

4. Speaker's Influential power caculation (cosine similarity between speakers etc.)

***

Old Text


# Project Repository for PYCA

## Pipeline
1. Create movie data set. For each movie:
   - title
   - release date
   - boxoffice
   - press ratings
   - people ratings
   - genre
2. Relate the two data sets: quotes and movies.
   - by speaker name (directors, actors)
   - by movie title mentions (hard and less accurate)
   - by director/actor name mentions (hard and less accurate)
   - other solutions
3. Analyse the merge data to answer the following questions
   - How does press activity influences boxoffice, ratings etc
     - counts of quotes as time series, for e.g. one month before/after release
     - deeper quote analysis (PCA, sentiment analysis)
   - COME UP WITH MORE PRECISE QUESTIONS, I THINK WE CAN COME UP WITH BUNCH OF THE

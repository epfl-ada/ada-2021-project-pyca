# Predicting Box-Office Receipts from the Actors and Director's Quotations
## Abstract

Recent research work has investigated the determinants of attributes (budget, actors, etc.) in predicting the box-office revenues. Particularly, lead actors have been considered as one of the critical drivers for success in the motion pictures industry [^word-of-mouth-for-movies].

[^word-of-mouth-for-movies]: [Word-of-Mouth for Movies: Its Dynamics and Impact on Box Office Revenue](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=1949819)

However, an important attribute in forecasting the box-office receipts has remained mostly unnoticed: what and how the movie main actors and director claim in the press.
Not only the fame of a lead actor can influence the box office revenue, but also the his public claims might shape the audience attitudes and intentions to watch movie. One salient research question in our study is to examine whether the director or a main actor's quotations in the press trigger an increase in the box office revenues over time.

We will perform various machine learning analysis using cross validation method to show what kind of characteristics in the director or a lead actor's quotation might be related to the box-office success.


## Introduction

The motion pictures industry has become a roaring success that breaks records of 42 billion U.S. dollars in the global box office in 2019. In U.S. and Canada, the box office receipt is over 10 billion U.S. dollars between the year of 2015-2019. Recent years, numerous of research work has uncovered which attributes might predict the financial success of motion pictures after they have been released, and why some movies could be “hits” or “flops” using automation methods. In our study, we explore the important role of word of mouth on predicting the financial success of box-office receipts in 2015-2019 from the longitudinal time sequence (i.e., before and after the release date). More specifically, our study will address the following key questions:

* *Does the quantity of quotations from movie associated persons provide a boost to box-office revenue?*
* *Which textual factors from quotations influence the financial performance of movies, and when (i.e., before or after the release date)?*
* *Which model (e.g., SVM and Neural Network) has better predictive performance in forecasting the box-office receipts, given the spreading and content of quotations and influential power of speaker?*

In our study, we combine the Quotebank database with the IMDb movie information dataset and box-office receipts from box office mojo. The first dataset of IMDb movie database contains six types of movie data: (*i*) movie name title; (*ii*) the genre of movie, such as comedy, fantasy category; (*iii*) the release year (we select the movies in the year 2015-2019); (*iv*) region (focus on U.S. and U.K.); (*v*) runtime (in minutes). The second dataset from box office mojo displayed the financial performance of movies in: (*i*) the gross revenue (in U.S. dollars, the average revenue??); (*ii*) ranking of box-office receipts; (*iii*) total gross revenue (???); (*iv*) release date and year. After that, we merge both IMDb movie and box-office receipts datasets together by movie name and release year. Further we extract key persons in the movie (e.g., actor or actress of casting, director, and producer) in order to retrieve their quotations from the Quotebank database. By doing so, we assume that the spreading of quotation from movie associated key figure might influence the financial performance of the movies. To understand the influence of quotations on box-office receipts, it is important to examine the **depth and size** (the quantity of movie associated person quotations before and after the release date of movie), the **breadth** (the number of movie associated persons involved in the quotations over time), the **dynamics of content in quotations** (e.g., the change of sentiment polarity in quotation over time, variations in topical categories of quotation) and **influential power of speaker** in the cast (the actor/actress/director's past revenue, the uniqueness/familiarity of pair in movie casting etc.)

For the post release period the 'power of critics' will be measured. This is identified as the ratio of positive to negative quotes attributed to critics. The data of critics are founded in the IMDb database. For sentiment classification, we use a term counting method (as it described in Kennedy and Inkpen paper). That means that if there are more positive than negative terms, the quote is considered positive and vice versa. We incorporate valence shifters into the term-counting method (e.g., the movie is not good) as well as intensifiers (e.g. very good) or diminishers (barely and good) taken from the general inquirer 'overstatements' and “understatements” database.

The second aim of the study is to explain box office revenue in a dynamic way (see Liu for a similar model). We hypothesize that the change of post release volume and the sentiment of the quotes after the release of the movie have an impact in the subsequent box office (the ratio of first week revenue to aggregate revenue). That means that means that the opinion of the changes after the first week of the release.

Consequently, our suggesting key factors that affect the box-office revenue of a movie, are:
1)The publicity volume before the release and during the first week
2)The popularity of the speaker and the sentiment of the quote
3)The power of the critics after the first week

References:
https://onlinelibrary.wiley.com/doi/10.1111/j.1467-8640.2006.00277.x
https://papers.ssrn.com/sol3/papers.cfm?abstract_id=1949819


## Dataset Used

In our study, we combine the Quotebank database with the IMDb movie information dataset and box-office receipts from box office mojo. The first dataset of ```IMDb movie database``` contains six types of movie data: (*i*) movie name title; (*ii*) the genre of movie, such as comedy, fantasy category; (*iii*) the release year (we select the movies in the year 2015-2019); (*iv*) region (focus on U.S. and U.K.); (*v*) runtime (in minutes). The second dataset from ```box office mojo``` displayed the financial performance of movies in: (*i*) the gross revenue (in U.S. dollars, the average revenue??); (*ii*) ranking of box-office receipts; (*iii*) total gross revenue (???); (*iv*) release date and year. After that, we merge both IMDb movie and box-office receipts datasets together by movie name and release year. Further we extract key persons in the movie (e.g., actor or actress of casting, director, and producer) in order to retrieve their quotations from the Quotebank database. By doing so, we assume that the spreading of quotation from movie associated key figure might influence the financial performance of the movies. To understand the influence of quotations on box-office receipts, it is important to examine the **depth and size** (the quantity of movie associated person quotations before and after the release date of movie), the **breadth** (the number of movie associated persons involved in the quotations over time), the **dynamics of content in quotations** (e.g., the change of sentiment polarity in quotation over time, variations in topical categories of quotation) and **influential power of speaker** in the cast (the actor/actress/director's past revenue, the uniqueness/familiarity of pair in movie casting etc.)


## Methods

TO DO: More details here, combination of machine learning and statistical modeling
<span style="color:blue">I would be more precise here and start with really basic analysis (realistic)</span>

1. Sentiment Analysis

2. Topical categories of quotations

3. Prediction methods (logical regressions, SVM, Random forest, Neural network etc.)

4. Speaker's Influential power calculation (cosine similarity between speakers etc.)

<span style="color:blue">Talk briefly about preliminary results?</span>
![Press Activity](./analysis/quotes_around_release.png)
![Press Activity](./analysis/gross_vs_occurrences.png)


## Project Timeline

**Week 1** (8 Nov-14 Nov): 
Project proposal, web scraping all available datasets, initial descriptive analysis

**Week 2** (22 Nov-28 Nov): 
Feature selection for all variables, compute textual characteristics of quotation (e.g., sentiment polarity, topic classification), compute influential power of speaker, data cleaning and standardized 

**Week 3** (29 Nov-5 Dec):
Training data to predictive models (e.g., SVM and neural network) with cross validation methods, evaluate the model performance 

**Week 4** (6 Dec-12 Dec):
Wrap up results, visualize data and write data story down

**Week 5** (13 Dec-17 Dec): 
Double check code and prepare the final storytelling about our data results 


## Organization within the team

* [Alex] (https://github.com/PhotonAmpere): web scraping for datasets, initial data analysis, pre-process datasets, develop algorithm, model selection
* [Christos] (https://github.com/Yo-art7): Data visualization, running tests and evaluate model performance
* [Pierre] (https://github.com/pgimalac): develop algorithm, feature engineering, model selection
* [Yiming] (https://github.com/yiming-li3008): analyze quotation text using NLP methods, write project data story

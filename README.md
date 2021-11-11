# Predicting Box-Office Receipts from the Actors and Director's Quotations
## Abstract

Recent research work has investigated the determinants of attributes (budget, actors, etc.) in predicting the box-office revenues. Particularly, lead actors have been considered as one of the critical drivers for success in the motion pictures industry[^word-of-mouth-for-movies].

However, an important attribute in forecasting the box-office receipts has remained mostly unnoticed: what and how the movie main actors and director claim in the press.
Not only the fame of a lead actor can influence the box office revenue, but also the his public claims might shape the audience attitudes and intentions to watch movie. One salient research question in our study is to examine whether the director or a main actor's quotations in the press trigger an increase in the box office revenues over time.

We will perform various machine learning analysis using cross validation method to show what kind of characteristics in the director or a lead actor's quotation might be related to the box-office success.


## Introduction

The motion pictures industry has become a roaring success that reached a all time high 42 billion U.S. dollars in the global box office in 2019[^global-box-office-revenue-per-year]. In U.S. and Canada, the box office receipt is over 10 billion U.S. dollars between the year of 2015-2019.

![global box office revenue per year by format](./assets/global-box-office-revenue-per-year.png)

[^global-box-office-revenue-per-year]: https://www.statista.com/statistics/259987/global-box-office-revenue

In recent years, numerous research work has uncovered which attributes might predict the financial success of motion pictures after they were released, and why some movies could be "hits" or "flops" using automation methods[^buzz-recommandation-internet][^blogs-advertising-local-market][^predicting-motion-picture].

[^buzz-recommandation-internet]: [Buzz et recommandations sur Internet: quels effets sur le box-office?](https://doi.org/10.1177%2F076737010702200304)
[^blogs-advertising-local-market]: [Blogs, Advertising, and Local-Market Movie Box Office Performance](https://doi.org/10.1287/mnsc.2013.1732)
[^predicting-motion-picture]: [Predicting box-office success of motion pictures with neural networks](https://doi.org/10.1016/j.eswa.2005.07.018)

In our study, we explore the important role of word of mouth on predicting the financial success of box-office receipts in 2015-2019 from the longitudinal time sequence (i.e., before and after the release date).
More specifically, we will address the following key questions:

* *Does the quantity of quotations from movie associated persons provide a boost to box-office revenue?*
* *Which textual factors from quotations influence the financial performance of movies, and when (i.e., before or after the release date)?*
* *Which model (e.g., SVM, Neural Network, etc) has better predictive performance in forecasting the box-office receipts, given the quotations, its spread and the influential power of speaker?*

For the post-release period the 'power of critics' will be measured. This is identified as the ratio of positive to negative quotes attributed to critics. The data of critics are founded in the IMDb database. For sentiment classification, we use a term counting method (as it described in the Kennedy and Inkpen paper[^sentiment-analysis-paper]). That means that if there are more (respectively less) positive than negative terms, the quote is considered positive (respectively negative). We incorporate valence shifters into the term-counting method (e.g., the movie is not good) as well as intensifiers (e.g. very good) or diminishers (barely and good) taken from the general inquirer 'overstatements' and "understatements" database.

[^word-of-mouth-for-movies]: [Word-of-Mouth for Movies: Its Dynamics and Impact on Box Office Revenue](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=1949819)
[^sentiment-analysis-paper]: [Sentiment classification of movie reviews using contextual valence shifters](https://www.cs.utoronto.ca/~akennedy/publications/sentiment_ci_2006.pdf)

The second aim of the study is to explain box office revenue in a dynamic way (see Liu[^word-of-mouth-for-movies] for a similar model). We hypothesize that the change of post release volume and the sentiment of the quotes after the release of the movie have an impact in the subsequent box office. The ratio of first week revenue to the total aggregate revenue is used to find the changes of the opinion after the first week of the release.

Consequently, our suggesting key factors that affect the box-office revenue of a movie, are:
1. The publicity volume before the release and during the first week
2. The popularity of the speaker and the sentiment of the quote
3. The power of the critics after the first week


## Dataset Used

In our study, we combine the Quotebank database with the ```IMDb movie information database``` [^imdb-database] and box-office receipts from ```Box Office Mojo```[^mojo-database].

The first, ```IMDb movie database```, contains six types of movie data: (*i*) movie name title; (*ii*) the genre of movie, such as comedy, fantasy category; (*iii*) the release year (we select the movies in the year 2015-2019); (*iv*) region (focus on U.S. and U.K.); (*v*) runtime (in minutes).

The second, ```Box Office Mojo```, displayed the financial performance of movies in: (*i*) the gross revenue (in U.S. dollars, the average revenue??); (*ii*) ranking of box-office receipts; (*iii*) total gross revenue (???); (*iv*) release date and year.

After that, we merge both datasets together by movie name and release year. Further we extract key people in the movie (e.g., actors and actresses, director, and producer) in order to retrieve their quotations from the Quotebank database. By doing so, we assume that the spreading of quotation from movie associated key figure might influence the financial performance of the movies.

To understand the influence of quotations on box-office receipts, it is important to examine the **depth and size** (the quantity of movie associated person quotations before and after the release date of movie), the **breadth** (the number of movie associated persons involved in the quotations over time), the **dynamics of content in quotations** (e.g., the change of sentiment polarity in quotation over time, variations in topical categories of quotation) and **influential power of speaker** in the cast (the actor/actress/director's past revenue, the uniqueness/familiarity of pair in movie casting, etc).

[^imdb-database]: [IMDb datasets](https://datasets.imdbws.com)
[^mojo-database]: [Box Office Mojo datasets](https://www.boxofficemojo.com/year/2015/)


## Methods

**box office receipts and quotations** 
In our preliminary analysis, we plot change of quantity in main crew’s quotations around the release date. There is a peak in the main crew’s quotations in the media coverage within one week after the movie has been released. Thus, we can assume that the main crew have been engaged in frequent media exposure for movie promotion around movie release dates. Further the spearman correlation graph shows, box office revenue and main crew’s quotations seem to follow some sort of power law (it is positive significant). 

**Genre difference in the effect of quotes on revenue**
Further we will examine the effect of the main crew’s quotations on revenue for each genre. We will perform a pair-wise KS statistic heatmap to show whether the genre differs in the main crew’s quotations, and plot the correlation graph between the main crew’s quotations and revenue for each movie category. 

**Main crew’s quotation frequency**
We compute the number of quotation occurrences for each movie related speaker. We consider top 20 speaker who have appeared the highest number of quotation occurrences in the media coverage (vs. 20 lowest number). By doing so, we expect to examine whether the main crew who appear more often in the media coverage (vs. who has lowest media exposure) greater influence on the box office revenue. 



1. Sentiment Analysis

2. Topical categories of quotations

3. Prediction methods (logical regressions, SVM, Random forest, Neural network etc.)

4. Speaker's Influential power calculation (cosine similarity between speakers etc.)

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

* [Alex](https://github.com/PhotonAmpere): web scraping for datasets, initial data analysis, pre-process datasets, develop algorithm, model selection
* [Christos](https://github.com/Yo-art7): Data visualization, running tests and evaluate model performance
* [Pierre](https://github.com/pgimalac): develop algorithm, feature engineering, model selection
* [Yiming](https://github.com/yiming-li3008): analyze quotation text using NLP methods, write project data story

## Organization of the repository
    .
    ├── moviePreprocessing
    │   ├── movieDataSetBuilder.ipynb #pre-process and merge IMDb movie and box-office revenue datasets
    │   └── movie_data_2015_2020.csv #movie dataset: 2015-2020
    ├── mergeDataSets 
    │   └── link_quotes_to_movies.ipynb #merge quotabank and movie dataset by main crew names 
    ├── analysis
    │   └── analysis_quote.ipynb #prelimilary analysis for correlation between main crew quotations and box office receipts 
    
**Note:** All datasets with quotations whose speaker is in the main crew of a 2015-2020 movie can be found on [this google drive](https://drive.google.com/drive/folders/1q0zKAa45PFMZUMzclg4tjHwOMBS6QptM?usp=sharing).


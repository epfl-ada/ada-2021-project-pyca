# Box-office and Quotebank

## Data story
Our **Data story** is hosted on [https://axgoujon.github.io/adatastory/](https://axgoujon.github.io/adatastory/).

It shows and explain our thought process and our findings for this project.

## Note

As per [https://ada2021epfl.zulipchat.com/#narrow/stream/302232-Project/topic/Deliverable.20notebook](https://ada2021epfl.zulipchat.com/#narrow/stream/302232-Project/topic/Deliverable.20notebook), we chose to use several notebooks. Their use is described below.

## Abstract

Recent research work has investigated the impact of attributes (e.g., budget, release time) in predicting the box-office revenues[^Early-Predictions-of-Movie-Success]. Particularly, lead actors have been considered as one of the critical drivers for success in the motion pictures industry[^The-Power-of-Stars].

[^Early-Predictions-of-Movie-Success]: https://arxiv.org/abs/1506.05382
[^The-Power-of-Stars]: https://journals.sagepub.com/doi/10.1509/jmkg.71.4.102

However, an important attribute in forecasting the box-office receipts has remained mostly unnoticed: what and how the main film crew claims in the media coverage. Not only does the fame of a lead actor/director can influence the box office revenue, but also the public claims from the main film crew might shape the audience attitude and intentions to watch movie.

One salient research question in our study is to examine *whether the main film crew's quotes in the press trigger an increase in the box office revenues over time.* We will perform different machine learning methods with cross validation to show what kind of characteristics in the main film crew's quotes might forecast the box-office results.

## Introduction

The motion pictures industry has become a roaring success that reached a all time high 42 billion U.S. dollars in the global box office in 2019[^box-office-revenue-2019]. In U.S. and Canada, the box office receipt is over 10 billion U.S. dollars in the year of 2015-2019[^global-box-office-revenue-per-year].

![global box office revenue per year by format](./assets/global-box-office-revenue-per-year.png)
*Global box office revenue per year by format*

[^box-office-revenue-2019]: https://www.billboard.com/articles/news/8547827/2019-global-box-office-revenue-hit-record-425b-despite-4-percent-dip-in-us
[^global-box-office-revenue-per-year]: https://www.statista.com/statistics/259987/global-box-office-revenue

In recent years, numerous research work has uncovered which attributes might predict the financial success of motion pictures after they were released, and why some movies could be "hits" or "flops" using automation methods[^buzz-recommandation-internet][^blogs-advertising-local-market][^predicting-motion-picture].

[^buzz-recommandation-internet]: [Buzz et recommandations sur Internet: quels effets sur le box-office?](https://doi.org/10.1177%2F076737010702200304)
[^blogs-advertising-local-market]: [Blogs, Advertising, and Local-Market Movie Box Office Performance](https://doi.org/10.1287/mnsc.2013.1732)
[^predicting-motion-picture]: [Predicting box-office success of motion pictures with neural networks](https://doi.org/10.1016/j.eswa.2005.07.018)

In our study, we explore the important role of the claims from the main film crew on predicting the financial success of box-office receipts in 2015-2019 from the longitudinal time sequence (i.e., before and after the release date).
More specifically, we will address the following key questions:

* *Does the quantity of quotes from the main film crew provide a boost to box-office revenue ?*
* *How much does the fame of the speaker influence the box-office revenue ?*
* *Which textual factors (e.g., sentiment polarity, the number of topics) from quotes might influence the financial performance of movies ?*
* *Which model (e.g., logistic regression, SVM) has better predictive performance in forecasting the box-office receipts ?*


## Datasets Used

In our study, we combine the quotation-centric version of the ```Quotebank``` database[^quotebank-database] with the ```IMDb movie information database``` [^imdb-database] and box-office receipts from ```Box Office Mojo```[^mojo-database].

Firstly, ```IMDb movie database```, contains six types of movie data: (*i*) movie name title; (*ii*) the genre of movie, such as comedy, fantasy category; (*iii*) the release year (we select the movies in the year 2015-2020); (*iv*) region (focus on U.S. and U.K.); (*v*) runtime (in minutes); (*vi*) main people involved in the movie.

Secondly, ```Box Office Mojo```, displayed the financial performance of movies in: (*i*) the total gross revenue (in U.S. dollars); (*ii*) ranking of box-office receipts; (*iii*) total gross revenue (in U.S. dollars); (*iv*) release date and year; (*v*) opening week gross; (*vi*) opening week gross percentage.

After that, we merge both datasets together by movie name and release year.

In the end, we extract key people in the movie (e.g., actors and actresses, director, and producer) in order to retrieve their quotes from the ```Quotebank``` database[^quotebank-database]. By doing so, we assume that the spread of a quote from a movie associated key figure might influence the financial performance of the movies.

We also extract, for the top 50 movies in term of box office revenue, all the quotes that mention these movies or a term related to these movies, in the 25 weeks around the release date.

[^imdb-database]: [IMDb datasets](https://datasets.imdbws.com)
[^mojo-database]: [Box Office Mojo datasets](https://www.boxofficemojo.com/year/2015/)
[^quotebank-database]: [QuoteBank datasets](https://zenodo.org/record/4277311)

**See [movieDataSetBuilder.ipynb](./moviePreprocessing/movieDataSetBuilder.ipynb), [movieBoxOffice.ipynb](./moviePreprocessing/movieBoxOffice.ipynb) and [linkQuotesToMovies.ipynb](./mergeDataSets/linkQuotesToMovies.ipynb) to extract and merge these datasets.**

## Methods

**Volume of quotes and box office revenue :**
In our preliminary analysis, we plot change of quantity in the main film crew???s quotes around the release date. There is a peak in the main crew???s quotes in the media coverage within one week after the movie has been released. Thus, we can assume that the main crew have been engaged in frequent media exposure for movie promotion around movie release dates. Further the Spearman correlation graph shows, box office revenue and main crew???s quotes seem to follow some sort of power law (it is positive significant).

Below are some early artifacts produced by our analysis, showing interesting correlations respectively between the number of quotes and the time to the release date, and between the number of quotes and the box office success.

![Press Activity](./assets/quotes_around_release.png)

![Press Activity](./assets/gross_vs_occurrences.png)

**See [analysisQuote.ipynb](./analysis/analysisQuote.ipynb) for the preliminary analysis.**

**Percentage of box office revenue after first week release**
We compute box office revenue in three categories below:
- (i) high % first WE (in this group, the percentage of opening revenue over total revenue is less than the third quantile);
- (ii) intermediate score (the percentage of opening revenue over total revenue is between the third and the two third quantile);
- (iii) high % after first WE (the percentage of opening revenue over total revenue is greater than the two third quantile).

**Sentiment analysis and semantic analysis :**
We plan to pre-process text using NLP libraries (namely `spacy`, `nltk`, `genism` and `sklearn`). First, we will detect the sentiment polarity score from quotes with dictionary-based package `Afinn`. Then, we compute values for five lexicon terms ("warmth", "fun", "love", "emotional", "disappointment", "hate") using package `Empath` for movie related quotes. 


## Project Timeline

**Week 1** (8 Nov-14 Nov): 
Project proposal, web scraping all available datasets, initial descriptive analysis.

**Week 2** (22 Nov-28 Nov): 
Data cleaning, feature selection for all variables, compute textual characteristics of the quotes (e.g., sentiment polarity, semantic analysis), compute percentage of opening revenue relative to total revenue for box-office. 

**Week 3** (29 Nov-5 Dec):
Visualize data and test statistically significant 

**Week 4** (6 Dec-12 Dec):
Wrap up results, and write down data stories.

**Week 5** (13 Dec-17 Dec): 
Double check code and prepare the final storytelling about our data results.


## Organization within the team

* [Alex](https://github.com/PhotonAmpere): Web scraping datasets, initial data analysis, pre-process datasets, data visialization
* [Christos](https://github.com/Yo-art7): running tests, prepare data story
* [Pierre](https://github.com/pgimalac): Develop algorithm, feature engineering, code quality
* [Yiming](https://github.com/yiming-li3008): Analyze quote text using NLP methods, write project data story


## Organization of the repository
### Project hierarchy

```
 .
 ????????? moviePreprocessing/
 ???   ????????? movieBoxOffice.ipynb
 ???   ????????? movieDataSetBuilder.ipynb
 ???
 ????????? mergeDataSets/
 ???   ????????? linkQuotesToMovies.ipynb
 ???
 ????????? analysis/
 ???   ????????? analysisQuote.ipynb
 ???   ????????? sentimentAnalysis.ipynb
 ???   ????????? Text_Analysis.ipynb
 ???
 ????????? data/
     ???   # Generated by `movieDataSetBuilder.ipynb`
     ????????? movie_data_2015_2020.csv
     ???
     ???   # Generated by `movieBoxOffice.ipynb`
     ????????? boxoffice.csv
     ???
     ???   # Downloaded from `QuoteBank`
     ????????? quotes-2015.json.bz2
     ????????? quotes-2016.json.bz2
     ????????? quotes-2017.json.bz2
     ????????? quotes-2018.json.bz2
     ????????? quotes-2019.json.bz2
     ????????? quotes-2020.json.bz2
     ???
     ???   # Downloaded from `IMDb`
     ????????? name.basics.tsv.gz
     ????????? title.akas.tsv.gz
     ????????? title.basics.tsv.gz
     ????????? title.crew.tsv.gz
     ????????? title.episode.tsv.gz
     ????????? title.principals.tsv.gz
     ????????? title.ratings.tsv.gz
     ???
     ???   # Generated by `linkQuotesToMovies.ipynb`
     ????????? movie_2015_crew_quotes.csv.gz
     ????????? movie_2016_crew_quotes.csv.gz
     ????????? movie_2017_crew_quotes.csv.gz
     ????????? movie_2019_crew_quotes.csv.gz
     ????????? movie_2018_crew_quotes.csv.gz
     ????????? movie_2020_crew_quotes.csv.gz
     ???
     ???   # Generated by `sentimentAnalysis.ipynb`
     ???   # and `Text_Analysis.ipynb`
     ????????? 50movies_sentiment_emotion.csv.gz
     ????????? 50movies_sentiment_polarity.csv.gz
     ????????? 50moviesquotes.csv.gz
     ????????? text_clean.csv.gz
     ????????? text_final.csv.gz
```

All datasets, in particular intermediate ones to avoid having to run everything, can be found at [https://drive.google.com/drive/folders/1Kwv7boEYxS1DRev6KCIJLhoYiBRBMHUV?usp=sharing](https://drive.google.com/drive/folders/1Kwv7boEYxS1DRev6KCIJLhoYiBRBMHUV?usp=sharing).

### Pre-existing datasets

The `quotes-{year}.json.bz2` datasets come from the ```Quotebank``` database[^quotebank-database].

The `title.{name}.tsv.gz` and `name.basics.tsv.gz` datasets come from the ```IMDb movie information database``` [^imdb-database].


### Creation of our own datasets

The `movieDataSetBuilder.ipynb` notebook merges the ```IMDb movie information database``` [^imdb-database] and box-office receipts from ```Box Office Mojo```[^mojo-database], to generate the `movie_data_2015_2020.csv` dataset containing all wanted information about a movie, including its box office results.

The `linkQuotesToMovies.ipynb` notebook filters the ```Quotebank``` database[^quotebank-database] to only keep the quotes whose speaker appears in the previously generated `movie_data_2015_2020.csv`, and generates `movie_{year}_crew_quotes.csv.gz` datasets.

**Note:** All `movie_{year}_crew_quotes.csv.gz` datasets (with quotes whose speaker is in the main crew of a 2015-2020 movie) can be found on [this google drive](https://drive.google.com/drive/folders/1q0zKAa45PFMZUMzclg4tjHwOMBS6QptM?usp=sharing) to avoid running the notebooks (which takes one hour).

The other datasets are intermediate results that have been exported to avoid having to run everything from scratch.

### Analyses

The `analysisQuote.ipynb` notebook contains the pre-analysis, it revealed a few interesting correlations and produces some nice artifacts.

The `Text_Analysis.ipynb` and `sentimentAnalysis.ipynb` notebooks contain sentiment analysis related computations, they also produce plots that show relations between sentiments extracted from quotes and box office results.

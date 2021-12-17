## Sentiment analysis

We first perform sentiment analysis to explore to what extent sentiment polarity from a speaker's quotation in coverage press affects the financial success of movies. We considered 50 blockbuster movies between the year 2015-2019 in the US. Further, we selected quotes about the relevant movies around release date. We decided to classify the movie related quotes into three categories: (i) the number of movie related quotes is less than 100; (ii) the number of movie related quotes is between 100 and 300; (iii) the number of movie related quotes is greater than 300.
 
We plot the correlation between box office revenue and average sentiment polarity score for movie related quotes in the Figure 3. To find out its correlation, we used Spearman Correlation and Pearson Correlation statistical tests. The results from both tests are not statistically significant, it is inconclusive to say whether sentiment polarity from quotes about movies influences a movie's financial success from our first data analysis. 

If we only focus on the total gross revenue, our finding could be biased and meaningless. A blockbuster movie with high budget is very likely to generate high box office, even if very bad rating, e.g., movie Star Wars always generate high box office revenues. 

## Sentiment Analysis part2 

Thus, we include opening revenue (the box office revenue in the first week) in our IMDb movie dataset. We compute the proportion of the opening revenue of the total gross revenue, to see whether opening revenue plays an important role in deciding the finanacial success of a movie. Further, we are interested in finding out, whether speaking positive about the movie in media actually influences audience's intention to go to cinema. 

We split our datasets into three groups: (i) high % first WE (in this group, the percentage of opening revenue over total revenue is less than one third; (ii) intermediate score (the percentage of opening revenue over total revenue is between one third and two third; (iii) high % after first WE (the percentage of opening revenue over total revenue is greater than two third).

Put it another way, if a movie has "high % after first WE", this movie normally has good reviews and ratings. More audiences might go to cinema to watch it after this movie has been released for a while, because they heard positive reviews from media or their friends. Vice Versa, if a movie has "high % first WE", more audiences might lose interest in watching this movie as they get to know negative reviews or only fans of this movies go to cinema in the first week. We can hypothesize that (i) a good movie will still attract people after it has been released for the first week (low first WE%), and (ii) a bad movie will attract fewer people after it has been released for the first week (high first WE%). 

From Figure 4, we can confirm our hypothesis that movies with more positive voice in the media are more likely to, be associated with the feature that they achieved more than 38% of revenue after the first release week (it is statistically significant). Thus, we can say that, speaking positive about movie in media, could affect more people's watch intention after they read the praise in news. 

## Lexicon Analysis 

To further confirm our findings from sentiment analysis, we computed scores for five lexical terms (warmth, fun, love, emotional, disappointment ad hate) from movie related quotes. The reason is that, those five lexical terms could be employed to understand how people feel and their experience about the movies, when they mentioned the movies in media. 

In Figure 5, we plot barchart for the average scores of five lexical terms, in three groups(high vs. intermediate vs. low percentage of box office revenue in the first week). Findings from t-test showed that people use more hate related 
words to describe movie that has high revenue proportion in the first week (compared to movies with high revenue proportion after first week). We can say, it seems that good movie gets more audiences for longer time period and more positive voices in media will boost its effects. 


```python

```


```python

```


```python

```


```python

```

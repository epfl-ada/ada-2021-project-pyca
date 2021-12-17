# Delving deeper into quotebank: can quote sentiment analysis help predict boxoffice?
Our first analysis could not allow for sentiement analysis: the quotes linked to movies were from the movie crew, which induces a bias. We now propose another approach.
## A first naïve attempt

We first perform sentiment analysis to explore to what extent sentiment polarity from a speaker's quotation in coverage press affects the financial success of movies. More precisely
- we considered **50 blockbuster movies** between the year 2015-2019 in the US;
- we selected quotes related to the relevant movies around release date (+- 10 days). For each selected movie we manually prepared some keys from the movie name to identify quotes related to the movie;
- in the visualization we split the movies into three categories: (i) the number of movie related quotes is less than 100; (ii) the number of movie related quotes is between 100 and 300; (iii) the number of movie related quotes is greater than 300. This procedure is meant to give more information to the reader.
 
We investigate a possible correlation between box office revenue and average sentiment polarity score for movie related quotes in the Figure 3. To find quantify our analysis, we used Spearman Correlation and Pearson Correlation statistical tests. The results from both tests are not statistically significant, **it is inconclusive to say whether sentiment polarity from quotes about movies influences a movie's financial success from our first data analysis**. 

![Figure 3](assets/polarityAnalysis_totalGross.png "Figure 3")

This is not too surprising. For instance a blockbuster movie with high budget is very likely to generate high box office, even if people are very critical about it. For instance can you imaging a Star Wars movie with very low box office revenues, regardless of how critical people talk about it? 

## Opening revenue, a more relevant descriptor

Thus, we include another metric, the opening revenue (the box office revenue in the first week) in our IMDb movie dataset. We compute the proportion of the opening revenue of the total gross revenue. We are indeed interested in finding out, **whether speaking positive about the movie in media actually influences audience's intention to go to cinema even after the opening period**. 

From Figure 4, it can be seen that movies with more positive voice in the media are more likely to generate a small percent of the total revenue the first release week (it is statistically significant). We propose a simple interpretation: good movie will be praised in the media during the first release week, which can result in more people wiling to watch the movie. This implies that movies with positive speaking will have an opening revenue small in proportion since the crowds might show up only later.

![Figure 4](assets/polarityAnalysis_percentGross.png "Figure 4")

In the sequel it will be helpful to consider the three following categories of movies
- (i) high % first WE (in this group, the percentage of opening revenue over total revenue is less than the third quantile);
- (ii) intermediate score (the percentage of opening revenue over total revenue is between the third and the two third quantile);
- (iii) high % after first WE (the percentage of opening revenue over total revenue is greater than the two third quantile).

Put it another way, if a movie has "high % after first WE", this movie normally has good reviews and ratings. More audiences might go to cinema to watch it after this movie has been released for a while, because they heard positive reviews from media or their friends. Vice Versa, if a movie has "high % first WE", more audiences might lose interest in watching this movie as they get to know negative reviews or only fans of this movies go to cinema in the first week. We can hypothesize that (i) a good movie will still attract people after it has been released for the first week (low first WE%), and (ii) a bad movie will attract fewer people after it has been released for the first week (high first WE%). 
## Lexicon Analysis 

To further confirm our findings from sentiment analysis, we computed scores for five lexical terms (warmth, fun, love, emotional, disappointment ad hate) from movie related quotes. The reason is that, those five lexical terms could be employed to understand how people feel and their experience about the movies, when they mentioned the movies in media. 

In Figure 5, we plot barchart for the average scores of five lexical terms, in three groups (high vs. intermediate vs. low percentage of box office revenue in the first week). Findings from t-test showed that **people use more hate related 
words to describe movie that has high revenue proportion in the first week (compared to movies with high revenue proportion after first week)** (p-value 0.03). We can say, it seems that good movie gets more audiences for longer time period and more positive voices in media will boost its effects. Although it is more delicate to conclude with the other lexical terms, the trend is (almost) always the expected one: positive terms are associated to movies with high opening revenue proportion while negative terms to movies with low opening revenue proportion.

![Figure 5](assets/sentimentAnalysis.png "Figure 5")

## Conclusion
The gold standard for the movie industry would be to be able to predict the total gross revenue of a movie before release. Although we were not able to tackle precisely the problem, our findings suggest a alternative way which require the knowledge of the two following *near release date metrics*:
- first WE revenue
- polarity of the quotes related to the movie around the release date


```python

```


```python

```


```python

```


```python

```

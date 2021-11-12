## Link quotebank and our movie dataset
Once again we chose not to upload the Quotebank datasets we use on github because they were too big ; this notebook filters the quotes to only keep those whose author appears in `movie_data_2015_2020.csv`.

The two data sources are:
- the **QuoteBank datasets** [link](https://zenodo.org/record/4277311) from the year 2015 to 2020 (quotation-centric versions), that have to be downloaded and put in the `data` folder. They contain quotes along with a list of potential authors and their probabilities.
- our own **movie dataset** extracted in `movieProcessing`.

The initial architecture to run this notebook should be the following:
```
    .
    ├── mergeDataSets
    │   └── link_quotes_to_movies.ipynb
    └── data/                             # the datasets we need
        ├── movie_data_2015_2020.csv      # from the moviePreprocessing notebook
        ├── quotes-2015.json.bz2
        ├── quotes-2016.json.bz2
        ├── quotes-2017.json.bz2
        ├── quotes-2018.json.bz2
        ├── quotes-2019.json.bz2
        └── quotes-2020.json.bz2
```
where each quotes files comes from the quotation-centric version of the QuoteBank datasets, described at the link above.

We simply link the quotes to the actors and crew members from our movie dataset, using the most probable author.

**The goal of this notebook is to generate datasets containing the filtered quotes. These datasets will be named `movie_{year}_crew_quotes.csv.gz` (where `{year}` is the year the quote was made) and located in the `data` folder.**

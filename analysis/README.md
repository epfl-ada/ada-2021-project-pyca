## First data analysis
This notebook performs a first set of analysis using the previously generated datasets.

The two data sources are:
- our own **movie dataset** extracted in `movieProcessing`.
- our own **quote datasets** extracted in `mergeDataSets`.

The initial architecture to run this notebook should be the following:
```
    .
    ├── analysis
    │   └── analysisQuote.ipynb
    │
    └── data/       # the datasets we need
        │    # from the `moviePreprocessing` notebook
        ├── movie_data_2015_2020.csv
        │
        │   # from the `mergeDataSets` notebook
        ├── movie_2015_crew_quotes.csv.gz
        ├── movie_2016_crew_quotes.csv.gz
        ├── movie_2017_crew_quotes.csv.gz
        ├── movie_2018_crew_quotes.csv.gz
        ├── movie_2019_crew_quotes.csv.gz
        └── movie_2020_crew_quotes.csv.gz
```
where each quotes files is created in the `mergeDataSets` notebook, and movie_data_2015_2020.csv is created in the `moviePreprocessing` notebook.

We run various analysis on these datasets to try and find any initial interesting correlations or other result between quotes and boxoffices results, in order to motivate the project.

**The goal of this notebook is to generate artifacts that can be used in the milestone 2 report, and find correlations or other useful information. The artifacts will be located in the `assets` folder.**

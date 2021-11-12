# Create a meaningful movie data set
We chose not to upload the datasets we use on github because they were too big ; this notebook downloads and merges them.

The two data sources are:
- the **IMDb datasets** [link](https://datasets.imdbws.com/) that have to be downloaded and put in a `data` folder. They contains many information (ratings, etc), but not the box-office, and not in a convenient format (each SQL table is in its own tsv file).
- the **Box Office Mojo stats** [link](https://www.boxofficemojo.com/year/), that are crawled and merged with the IMDb datasets in this notebook.

The initial architecture to run this notebook should be the following:
```
    .
    ├── moviePreprocessing
    │   └── movieDataSetBuilder.ipynb
    └── data/                           # the datasets we need
        ├── name.basics.tsv.gz
        ├── title.akas.tsv.gz
        ├── title.basics.tsv.gz
        ├── title.crew.tsv.gz
        ├── title.episode.tsv.gz
        ├── title.principals.tsv.gz
        └── title.ratings.tsv.gz
```
where each files comes from the IMDb datasets, whose specification can be found at https://www.imdb.com/interfaces/.

**The goal of this notebook is to generate a dataset containing the ratings, boxoffice, director names and main actor names, for each US and UK movie, from 2015 to 2020. This dataset will be named `movie_data_2015_2020.csv` and located in the `data` folder.**

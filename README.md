# Analyze IMDB data

Shenyue Jia | [jiashenyue.info](https://jiashenyue.info)

## Question to answer
- Analyze the movie data from IMDb to support decision-making on a successful movie production
  - Current goal of a successful movie: generate a high revenue with a low budget

## IMDb data
- [IMDb data dictionary](https://www.imdb.com/interfaces/)
- [IMDb API](https://developer.imdb.com/)

## Filtered IMDb data for analysis
- Focus on movies released in the U.S.
- Focus on movies produced after 2000 up until 2021
- Only consider the `movie` type

## TMDB data
- With more information than IMDb, such as
  - Revenue
  - Budget
- Has a shared key with IMDb to be combined with IMDb data
  - `imdb_id` = `tconst`
- [TMDB API](https://developers.themoviedb.org/3/getting-started/introduction)
- [TMDB wrapper](https://github.com/celiao/tmdbsimple)

## Use TMDB API to obtain financial data of movies for selected years
- [Data of 2000](https://github.com/jiashenyue/project3-imdb-data/blob/main/Data/final_tmdb_data_2000.csv.gz)
- [Data of 2001](https://github.com/jiashenyue/project3-imdb-data/blob/main/Data/final_tmdb_data_2001.csv.gz)
- [Data of 2000 and 2001 combined](https://github.com/jiashenyue/project3-imdb-data/blob/main/Data/tmdb_results_combined.csv.gz)

## Expalantory Data Analysis for TMDB data 2000 and 2001
### Movies with some valid financial data
![png]

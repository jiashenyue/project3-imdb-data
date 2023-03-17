# Analyze IMDB data

Shenyue Jia | [jiashenyue.info](https://jiashenyue.info)

## Question to answer
- Analyze the movie data from IMDb to support decision-making on a successful movie production
  - Current goal of a successful movie: generate a high revenue with a low budget

## Notebooks
- [x] [Create imdb database](https://github.com/jiashenyue/project3-imdb-data/blob/main/create-imdb-database.ipynb)
- [x] [Request tmdb data](https://github.com/jiashenyue/project3-imdb-data/blob/main/request-tmdb-data.ipynb)
- [x] [Explanatory data analysis](https://github.com/jiashenyue/project3-imdb-data/blob/main/explanatory-data-analysis.ipynb)
- [x] [Create a relational database using MySQL](https://github.com/jiashenyue/project3-imdb-data/blob/main/relational-database-construction.ipynb)
- [x] [Use hypothesis test to understand the factors influcing the ratings and revenues of movies](https://github.com/jiashenyue/project3-imdb-data/blob/main/hypothesis-test.ipynb)

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
### Revenue of all movies with valid financial information
![png](https://github.com/jiashenyue/project3-imdb-data/blob/main/PNG/revenue_combo_plot.png)
### Budget of all movies with valid financial information
![png](https://github.com/jiashenyue/project3-imdb-data/blob/main/PNG/budget_combo_plot.png)

### Count of movies by certification
![png](https://github.com/jiashenyue/project3-imdb-data/blob/main/PNG/certification_barplot.png)

### Average revenue generated by certification type

**certification** |	**revenue ($ millions)**
------------------|------------------
G	| 133
PG	| 129
PG-13	| 111
R	| 52
NR | 22

### Average budget by certification type

**certification** |	**budget ($ millions)**
------------------|------------------
PG | 52
PG-13	| 47
G |	44
R |	27
NR| 14

## Converted tables to a relational database
- A MySQL database named `movies` is created using the notebook [relational-database-constrution](https://github.com/jiashenyue/project3-imdb-data/blob/main/relational-database-construction.ipynb)

## Understand the factor influecing revenue and rating by hypothesis test
### 1. Does the MPAA rating of a movie (G/PG/PG-13/R) affect how much revenue the movie generates?

- We conducted Kruskal Wallis test over tmdb data and found 
  - **There is a significant difference between revenue generated for movies with different MPAA ratings.**

**Statistics** |	**p-value**
------------------|------------------
221.1	| 1.2e-47

- We also conducted post-hoc multiple comparison test and found `R` movies generate a significant **lower** revenue than `G`, `PG, and `PG-13` movies.

**group1** |	**group2** | p-value | reject $H_0$?
-----------|-------------|---------|-----------
G	| PG | 0.99 | False
G | PG-13 | 0.98 | False
G | R | 0.005 | True
PG | PG-13 | 0.37 | False
PG | R | 0.0 | True
PG-13 | R | 0.0 | True


**Tukey figure for post-hoc multiple comparison test** 

![png](https://github.com/jiashenyue/project3-imdb-data/blob/main/PNG/revenue_cert_tukey_2010_2019.png)


**Bar plot**
![png](https://github.com/jiashenyue/project3-imdb-data/blob/main/PNG/revenue_cert_barplot_2010_2019.png)

### 2. Do movies that are over 2.5 hours long earn more revenue than movies that are 1.5 hours long (or less)?

- We conducted Welch's T-Test and found
  - ** There is a significant difference in revenue generated by movies longer than 2.5 hours and those less or equal to 1.5 hours.**
  - The average revenue generated by movies longer than 2.5 hrs was $123,167,705.55
  - The average revenue generated by movies less than or equal to 1.5 hrs was $27,027,429.94
  
 **Statistics** |	**p-value**
------------------|------------------
4.24	| 4.4e-5


**Bar plot**

![png](https://github.com/jiashenyue/project3-imdb-data/blob/main/PNG/revenue_length_barplot_2010_2019.png)

### 3. Are some genres (`Action`) higher rated than others?

- Our result of t-test indicates the ratings of movie do not differ between movies with `Action` in genre and those who do not have `Action` in genre.

 **Statistics** |	**p-value**
------------------|------------------
0.21	| 0.83

**Bar plot**

![png](https://github.com/jiashenyue/project3-imdb-data/blob/main/PNG/action_genre_rating_barplot_2010_2019.png)

**Histogram**

![png](https://github.com/jiashenyue/project3-imdb-data/blob/main/PNG/action_genre_rating_hist_2010_2019.png)

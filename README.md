# Analyze IMDB data

Shenyue Jia | [jiashenyue.info](https://jiashenyue.info)

- Downloaded data and saved them in `/Data` folder
  - `title.basics.tsv.gz`
  - `title.ratings.tsv.gz`
  - `title.akas.tsv.gz`
- Applied a series of cleaning and filtering process over
  - Replace all `\N` in the original data to `NaN` values
  - Eliminate movies that are null for `runtimeMinutes`
  - Eliminate movies that are null for `genre`
  - Keep only `titleType`==`Movie`
  - Keep `startYear` 2000-2021
  - Eliminate movies that include "Documentary" in `genre` (see tip below)
  - Keep only US movies

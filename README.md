# Assignment 2 – Board Game Data Processing

Kaggle (www.kaggle.com)  is a remarkable web-based, data science resource, which contains a huge number of different datasets and tutorials on tools. (Highly recommended.) One particular dataset is the Board Games Geek dataset (https://www.kaggle.com/datasets/andrewmvd/board-games), which lists 20,000+ board games and for each game, a range of data including the average rating from BGG users, a measure of the game’s complexity, and information about the game’s mechanics (i.e. how the game is played) and “Domain”, i.e. the broad type. The research questions are:
- What is the most popular domain and most popular mechanics across the set of games. (Appearance in a given game's list counts as 1.)
- What is the correlation between publication year and average rating, e.g. newer games being preferred over older ones.
- What is the correlation between game complexity and average rating.

---

This repository contains a set of **Unix shell scripts** developed to process, clean, and analyze board game dataset files provided in text format.

---

## Scripts Included

1. [`empty_cells`](#1-empty_cells) – Check data quality by identifying missing values in each column.
2. [`preprocess`](#2-preprocess) – Clean the raw dataset file for further analysis.
3. [`analysis`](#3-analysis) – Analyze cleaned data to answer four research questions.

---

## Sample Dataset Files

- `bgg_dataset.txt` – Full dataset
- `sample.txt`, `sample1.txt`, `tiny_sample.txt` – Sample datasets
- `sample.tsv`, `sample1.tsv`, `tiny_sample.tsv` – Cleaned outputs for reference
---

## 1. `empty_cells`

This script checks for **empty cells** in a spreadsheet stored as a text file and reports the number of missing values per column.

### Features
- Accepts exactly **one argument**:
  1. Input `.txt` file (e.g., `bgg_dataset.txt`)
- Outputs count of empty cells per column to **standard output**.

### Example Usage

```bash
./empty_cells bgg_dataset.txt
```

## 2. `preprocess`

This script cleans input data by:
- Converting the semicolon separator to the  <tab> character
- Converting the Microsoft line endings to Unix line endings
- Changing format of floating-point numbers to use ‘.’ rather than ‘,’ as the decimal point.
- Dealing with non-ASCII characters by deleting them from the output. For example CO2 in a game title is rendered as CO.
- Generating new IDs for rows that are missing them by identifying the highest existing integer ID in the input file and assigning incrementing values starting from the next number.

### Features
- Accepts exactly **one argument**:
  1. Input `.txt` file (e.g., `sample.txt`)
- Outputs cleaned version of the input file to **standard output**.

### Example Usage

```bash
./preprocess sample.txt
```

## 3. `analysis`

This script uses data from the cleaned input file to analyse the research questions.

### Features
- Accepts exactly **one argument**:
  1. Input `.tsv` file (e.g., `sample.tsv`)
- Outputs result to **standard output**.
  - The most popular game mechanics is Hand Management found in 48 games
  - The most game domain is Strategy Games found in 77 games

  - The correlation between the year of publication and the average rating is 0.226
  - The correlation between the complexity of a game and its average rating is 0.426

### Example Usage  

```bash
./analysis sample.tsv
```

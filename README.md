# Athleisure Ads Strategy
This README.md lists project members, goals, responsibilities, and a summary of the files in the repository.

### Project File Summary
Within the project repository, the summary of files are as follows:

ALEX / JUSTIN - PROVIDE FINAL FILE SUMMARY HERE!!!

### Project Members
The members for this project are:

   - Alex Cheng
   - Justin Fleury

### Project Scenario
The scenario for the project is as follows:

Our client is a startup online clothing company that specializes in "athleisure" clothing in the US. Their marketing team wants to launch an ad campaign to increase online traffic on their website, which hopefully leads to more revenue. To best allocate time and effort for the launch of the ad campaign and maximize the audience to see their ads, they want to understand 3 things. 

   - Which keywords related to athleisure are consumers searching for most?
   - Which month are consumers searching for athleisure clothing most?
   - Which platform are consumers using most for their searches?

### Project Goals
The goals for the project are as follows:

   -  Based on our findings, we will provide at least 3 confident recommendations to the athleisure startup company's marketing team to figure out the best keywords, best timing, and best platform to run their ads.
   -  We will arrive at these recommendations by analyzing data from Wordtracker - a paid database service with a representative sample of Google, Youtube, and Amazon search query data volume for a 1-year period between June 2018 and May 2019.

### Methodology 
   -  Generate business application (online ad strategy to promote athleisure clothing).
   -  Generate 3 questions related to business application.
   -  Generate 3 null and alternative hypotheses to test and answer the 3 questions.
   -  Find and select a source of data to draw from and analyze (Wordtracker).
   -  Use API to understand database stats for Google, Youtube, and Amazon search volume.
   -  Generate a list of popular athleisure-related keywords (searched "athleisure" on Amazon, and found 77 terms associated with athleisure products on the first few pages of "featured" results).
   -  Call search volume by month, and totals for each keyword on the list from the Wordtracker API - split calls into small pieces so as not to go over the API call trial-account limit.
   -  Merge all API calls into one raw dataframe.
   -  Clean data, calculate June values and impute into the dataframe (for some reason June values came in as "0" from the API).
   -  Perform Exploratory Data Analysis (EDA) to investigate the data. Find total search volume for each search engine. Find average and total search volumes for each keyword across all search engines. Develop "wordclouds". Plot PDF and CDF for total keyword search volume across all search engines.
   -  Perform statistical testing on each of the 3 hypotheses (keywords, month, & search engine) via one-way Analysis Of Variance (ANOVA) with an established alpha value of 0.05 to find significant results compared to each other. Run Tukey test after that to find out specifically which results are different compared to each other.
   -  Perform 3-way ANOVA between keywords, month, and search engine with an established alpha value of 0.05. Run Tukey test after that to find out specifically which results are different compared to each other.
   -  Create a presentation to translate EDA and statistical testing into actionable insights for the online athleisure clothing startup. 

### Project Responsibilities
The project responsibilities are broken down as follows:

#### Alex Cheng
   -  SHARED - The README.md.
   -  SHARED - Project Overview Jupyter Notebook.
   -  SHARED - Wordtracker Data Extraction Jupyter Notebook.
   -  SHARED - Exploratory Data Analysis Jupyter Notebook.
   -  SHARED - Data Cleaning Jupyter Notebook.
   -  SHARED - Statistical Testing Jupyter Notebook.
   -  SHARED - Final project presentation design + export.

#### Justin Fleury
   -  SHARED - The README.md.
   -  SHARED - Project Overview Jupyter Notebook.
   -  SHARED - Wordtracker Data Extraction Jupyter Notebook.
   -  SHARED - Exploratory Data Analysis Jupyter Notebook.
   -  SHARED - Data Cleaning Jupyter Notebook.
   -  SHARED - Statistical Testing Jupyter Notebook.
   -  SHARED - Final project presentation design + export.

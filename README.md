# Athleisure Advertising Strategy

### Project File Summary
Within the project repository, the summary of files are as follows:
   - <b>[README.md](README.md)</b> - a summary of all contents in this repository.
   - <b>[data](/data)</b> - all data called from the Wordtracker API saved out as .csv files.
   - <b>[images](/images)</b> - all plots from data analysis.
   - <b>[jupyter notebook](https://github.com/jfleury20/athleisure-ads-strategy/tree/master/jupyter_notebook)</b> - all Jupyter Notebooks generated for this project.
   - <b>[project_prompt](/project_prompt)</b> - the prompt for this project.
   - <b>[Athleisure Ads Strategy.pdf](https://github.com/jfleury20/athleisure-ads-strategy/blob/master/Athleisure%20Ads%20Strategy.pdf)</b> - the final presentation for this project.
   - <b>[athleisure.csv](athleisure.csv)</b> - the final dataset for this project, extracted and merged together from the Wordtracker API.

#
### Project Members
The members for this project are:

   - <b>[Alex Cheng](https://github.com/alexwcheng)</b>
   - <b>[Justin Fleury](https://github.com/jfleury20)</b>

#
### Project Responsibilities

   -  All project responsibilities were shared equally between <b>[Alex Cheng](https://github.com/alexwcheng)</b> and <b>[Justin Fleury](https://github.com/jfleury20)</b>.

#
### Project Scenario
The scenario for the project is as follows:

Our client is a startup online clothing company that specializes in "athleisure" clothing in the US. Their marketing team wants to launch an ad campaign to increase online traffic on their website, which hopefully leads to more revenue. To best allocate time and effort for the launch of the ad campaign and maximize the audience to see their ads, they want to understand 3 things. 

   - Which **keywords** related to athleisure are consumers searching for most?
   - Which **month** are consumers searching for athleisure clothing most?
   - Which **platform** are consumers using most for their searches?

#
### Project Goals
The goals for the project are as follows:

   -  Based on our findings, we will provide at least 3 confident recommendations to the athleisure startup company's marketing team to figure out the best keywords, best timing, and best platform to run their ads.
   -  We will arrive at these recommendations by analyzing data from Wordtracker - a paid database service with a representative sample of Google, Youtube, and Amazon search query data volume for a 1-year period between June 2018 and May 2019.

#
### Data

Our data source is [Wordtracker](https://www.wordtracker.com/) - a paid database service for **Search Engine Optimization (SEO).** Search Engine Optimization is essentially just another way of saying: *“I want to figure out how make my website the top result for a given search.”*

Wordtracker helps clients to get more traffic to their website or better understand what consumers are searching for. Wordtracker is similar to Google Keywords Planner service, but allows access to search data on platforms beyond Google. Wordtracker offers a 1-year representative sample of search data from June 2018-May 2019 on Google, Youtube, Amazon, and Ebay. It provides over 2 billion unique keywords from 18 million global panelists, across 106 countries. Below is a synopsis of all data in the Wordtracker database related to search volume in the United States.

![Wordtracker_US_Database](/images/Slides/Wordtracker_US_Database.png)

So for our study, we pulled data from Wordtracker with the following constraints:

- **77 terms related to athleisure, using top Amazon keyword results when searching for "athleisure".**
- **Search volumes only in the United States.**
- **Search volume data pulled from Google, YouTube, and Amazon engines.**

According to [Search Engine Journal](https://www.searchenginejournal.com/seo-101/meet-search-engines/) - Google, YouTube, and Amazon are the three most popular search engines worldwide. According to [Bluelist](https://bluelist.co/blog/google-stats-and-facts/) in 2019 there are about 2 trillion Google searches per year. Wordtracker provides nearly 2 billion Google searches within a 1 year timeframe. **We assume that Wordtracker represents a sample roughly 1/1000th of the entire Google search database worldwide.**

Below is the method of how we decided on which terms related to "athleisure" to select for our search volume queries. We searched "athleisure" on Amazon, and found all of the most frequently occuring terms in the results.

![Amazon_Keywords](/images/Slides/Amazon_Keywords.png)

# 
### Data Collection Process

   -  Use API to understand database stats for Google, Youtube, and Amazon search volume.
   -  Generate a list of popular athleisure-related keywords (searched "athleisure" on Amazon, and found 77 terms associated with athleisure products on the first few pages of "featured" results).
   -  Call search volume by month, and totals for each keyword on the list from the Wordtracker API - split calls into small pieces so as not to go over the API call trial-account limit.
   -  Merge all API calls into one raw dataframe.
   
#
### Data Cleaning

   -  Clean data, calculate June values and impute into the dataframe (for some reason June values came in as "0" from the API).
   
#
### Exploratory Data Analysis

   -  Perform Exploratory Data Analysis (EDA) to investigate the data. Find total search volume for each search engine. Find average and total search volumes for each keyword across all search engines. Develop "wordclouds". Plot PDF and CDF for total keyword search volume across all search engines.
   
![Wordcloud_Google](/images/Slides/Wordcloud_Google.png)

![Wordcloud_Youtube](/images/Slides/Wordcloud_Youtube.png)

![Wordcloud_Amazon](/images/Slides/Wordcloud_Amazon.png)

![Month_Lineplot](/images/Slides/Month_Lineplot.png)

![Keywords_Bar_Plot](/images/Slides/Keywords_Bar_Plot.png)

![Search_Ratio_Bar_Plots](/images/Slides/Search_Ratio_Bar_Plots.png)

#
### Data Preprocessing

#
### Statistical Testing

   -  Generate 3 null and alternative hypotheses to test and answer the 3 questions.
   
   -  Perform statistical testing on each of the 3 hypotheses (keywords, month, & search engine) via one-way Analysis Of Variance (ANOVA) with an established alpha value of 0.05 to find significant results compared to each other. Run Tukey test after that to find out specifically which results are different compared to each other.
   
   -  Perform 3-way ANOVA between keywords, month, and search engine with an established alpha value of 0.05. Run Tukey test after that to find out specifically which results are different compared to each other.
   
#
### Multiple ANOVA

#
### Tukey Test

#
### Results

#
### Conclusions

![Recommendations](/images/Slides/Recommendations.png)

#
### Future Work

Future studies that may be helpful to improve the accuracy of these results:

- Explore search volume demographic statistics of each engine.
   - For example: age, gender, or income.
- Investigate "conversion rates".
   - Meaning: who actually buys the product after viewing the ad?
- Consider the costs of running an ad on a particular platform. 
   - For example, what is the cost of an ad on Google versus Amazon?

# Athleisure Advertising Strategy

### Project File Summary

   - <b>[README.md](README.md)</b> - a summary of all contents in this repository.
   - <b>[data](/data)</b> - all data called from the Wordtracker API saved out as .csv files.
   - <b>[images](/images)</b> - all plots from data analysis.
   - <b>[jupyter notebook](https://github.com/jfleury20/athleisure-ads-strategy/tree/master/jupyter_notebook)</b> - all Jupyter Notebooks generated for this project.
   - <b>[project_prompt](/project_prompt)</b> - the prompt for this project.
   - <b>[Athleisure Ads Strategy.pdf](https://github.com/jfleury20/athleisure-ads-strategy/blob/master/Athleisure%20Ads%20Strategy.pdf)</b> - the final presentation for this project.
   - <b>[athleisure.csv](athleisure.csv)</b> - the final dataset for this project, extracted and merged together from the Wordtracker API.

#
### Project Members

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
### Statistical Testing Methodology

**Alpha Value**

- **If alpha $\alpha$ < 0.05, then we reject the null hypothesis.**
- **If alpha $\alpha$ >= 0.05, then we fail to reject the null hypothesis.**
- This alpha value is not too lenient, nor is it too strict.
- Alpha values typically range between 0.01, and 0.1.

**ANOVA**
- One-Way Analysis Of Variance (ANOVA) was the statistical test of choice for our use case.
- Two-Way ANOVA was also used later on to determine which combinations of factors were statistically significant.
- Three-Way ANOVA was attempted, but was unable to run due to lack of processing power.

**Tukey Test**
- The problem with ANOVA, is that it only compares the means between groups and determines if any of those means are statistically significantly different from each other.
- In other words, ANOVA tells us if our results or significant or not, but does not tell us **where** the results are significant.
- Interpretability of statistical significance is crucial to communicate to our client. We have to be able to tell them which keywords perform best, which search engine is best, or which month is best to run ads!
- So, the Tukey Test allows us to interpret the statistical significance of our ANOVA test and find out which **specific** groups’s means (compared with each other) are different.
- So, after performing each round of ANOVA, we followed up with a Tukey Test to find out where the statistical significance was occuring in our data.

#
### Hypothesis Test 1: Keywords

**Are there any differences between athleisure-related keywords when considering search volume?**
- H01 - All athleisure-related keywords are equal in terms of average search volume.
- HA1 - Some athleisure-related keywords have greater average search volumes than others.

**One-Way ANOVA Result:**
- P-Value = 1.3293563590514185e-119 (This is nearly zero.)
- We reject the null hypothesis that mean search volume is equal across all athleisure-related keywords.
- Keyword on its own, does indeed constitute a difference in average search volume for athleisure-related items.

**Tukey Test Result:**
- Top 5 terms that are the "most" statistically different than the rest are:
   - "hoodie"
   - "running"
   - "sweatshirt"
   - "workout"
   - "flex"
#
### Hypothesis Test 2: Months

**Are there any differences between months when considering search volume?**
- H02 - People will be equally likely to search for activewear-related terms in any given month.
- HA2- People will be more likely to search for activewear-related terms depending on the month.

**One-Way ANOVA Result:**
- P-Value = 0.8831258135517717
- We fail to reject the null hypothesis that mean search volume is equal across all months.
- The month on its own, does not constitute a difference in search volumes for athleisure-related items.

**Tukey Test Result:**
- No need to run Tukey multiple comparisons test since we failed to reject the null hypothesis here.

#
### Hypothesis Test 3: Search Engine

**Are there any differences among search engines when considering search volumes?**
- H03 - There will be an equal search volume for activewear-related terms on any platform.
- HA3 - There will be a greater search volume for activewear-related terms on one particular platform.
   
**One-Way ANOVA Result:**
- P-Value = 7.19196465389629e-18 (This is nearly zero.)
- We reject the null hypothesis that mean search volume is equal across all search engines.
- Search engine on its own, does indeed constitute a difference in average search volume for athleisure-related items.

**Tukey Test Result:**
- In all cases, reject the null hypothesis that search engine 1 is equal to search engine 2 in terms of average search volume.
- Search volumes are unique to each platform.

#
### Multiple ANOVA + Tukey Test

Unfortunately, a full-fledged three-factor ANOVA between keywords, month, and search engine could not be run due to lack of processing power. However, two-factor ANOVA was run between all three factors to see if any two combinations of these factors was statistically significant. We essentially wanted to answer this question: **"Can we determine which specific 2-factor combinations of keyword/month/search engine generate the highest search volume?"**

**Hypothesis Test 1: Keyword + Engine**
- H01 - All keyword/engine combinations are equal in terms of mean search volume.
- HA1 - Some keyword/engine combinations have greater mean search volume.

**Two-Way ANOVA Result:**
- P-Value = 1.008919e-151
- Reject the null hypothesis that the mean search volume is equal among all Keyword/Engine combinations.

**Hypothesis Test 2: Keyword + Month**
- H02 - All keyword/month combinations are equal in terms of mean search volume.
- HA2 - Some keyword/month combinations have greater mean search volume.

**Two-Way ANOVA Result:**
- P-Value = 7.896266e-01
- Fail to reject the null hypothesis that the mean search volume is equal among Keyword/Month combinations.

**Hypothesis Test 3: Engine + Month**
- H03 - All engine/month combinations are equal in terms of mean search volume.
- HA3 - Some engine/month combinations have greater mean search volume.

**Two-Way ANOVA Result:**
- P-Value = 7.789742e-01
- Fail to reject the null hypothesis that the mean search volume is equal among Engine/Month combinations.

**Conclusion**
- Keyword/Engine combinations mean search volumes are statistically different from each other
- Keyword/Month and Engine/Month are not statistically different from each other.

**Tukey Test Result:**
From the Tukey Test, there were 10 Keyword/Engine combinations that were significantly different in search volume than the rest of the combinations. These 10 unique combinations will be our recommendations to our client.

- "running" / youtube
- "hoodie" / youtube
- "sweatshirt" / youtube
- "workout" / amazon
- "flex" / youtube
- "hoodie" / amazon
- "leggings" / amazon
- "workout" / youtube
- "joggers" / amazon
- "cotton" / youtube

#
### Conclusions

**Keywords:**

- We recommend that the ad campaign use these 5 buzzwords:
   - "hoodie"
   - "running"
   - "sweatshirt"
   - "workout"
   - "flex"

On average, these 5 keywords vastly outperform any other athleisure-related keyword tested across all platforms and months. 

**Platform**

- Ads should **not be launched on Google,** because it has the lowest search volume for athleisure-related keywords.
- If **search volume** is most important, then we recommend **YouTube.**
- If **market share** is most important, then we recommend **Amazon.**

**Month**

- The month by itself is not a statistically significant enough of a factor to provide a confident recommendation. 
- Month should only be considered as a factor when combined with a particular platform and set of keywords. 

**Below are the top 10 keyword / platform combinations that we would recommend to our athleisure clothing startup company to help them guide their advertising efforts online. Note that Google is not recommended as a platform to run athleisure advertisements.**

![Recommendations](/images/Slides/Recommendations.png)

#
### Improvements + Future Work

**Improvements**

- Ensure all word types being tested are similar.
   - For example, use all nouns, or all adjectives, etc…
- Limit results to clothing-related searches.
   - For example, consider pairing an “athleisure” related adjective to an article of clothing - ex: “breathable hoodie”, “ventilated shorts”, “striped joggers”, etc…
- Ensure all platforms being compared are the same in the service that they provide for better accuracy.
   - For example, compare Google to Bing, or YouTube and Vimeo, or Amazon and Ebay.

**Future Work**

- Explore search volume demographic statistics of each engine.
   - For example: age, gender, or income.
- Investigate "conversion rates".
   - Meaning: who actually buys the product after viewing the ad?
- Consider the costs of running an ad on a particular platform. 
   - For example, what is the cost of an ad on Google versus Amazon?

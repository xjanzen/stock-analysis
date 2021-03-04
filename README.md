# Kickstarting with Excel

## Overview of Project
We're presenting and visualizing data from a set of Kickstarter campaigns based on their launch dates and funding goals along with whether or not they were successful, failed, or were cancelled.

### Purpose
We're helping our friend Louise analyze how Kickstarter campaigns have done in the past so she can plan out her own campaign for her play to give it the best chance of success as well as seeing in general how theater and play categories are doing on Kickstarter.

## Analysis and Challenges
### Analysis of Outcomes Based on Launch Date
![Theater Outcomes vs Launch](resources/Theater_Outcomes_vs_Launch.png)

For this portion of the analysis we wanted to show the success/failure/cancelled distribution over the months of the year of all the 'theater' campaigns. We created a pivot table of the data by using the 'Date Created Conversion' and showing just the month portion of that date for the rows with the outcome of the campaign as the columns. We used this pivot table to create the above graph which allows you to better visualize the distirbution of the outcomes of the campaigns based on the month they launched.

### Analysis of Outcomes Based on Goals
![Outcomes vs Goals](resources/Outcomes_vs_Goals.png)

For this portion of the analysis we wanted to get a better idea of the outcomes of the campaigns based on how much money their initial goals for the campaign were for all campaigns labelled as 'plays'. To do this we took all campaigns with the 'plays' subcategory and split them into 12 ascending groups starting with <$1K and then going up by multiples of $5K with the last being all campaigns with over $50K as a goal. We setup columns to first count the number of campaigns and then to find the percentage of campaigns in each of the three different outcomes available. We took that data and input it onto the above graph to show the percentage of successful/failed/cancelled campaigns in each goal category we setup.

### Challenges and Difficulties Encountered
While I didn't run into any major difficulties it's important to carefully read the instructions to make sure you don't accidentally miss a step (ie. filtering the whole data set to only include 'plays' or 'theater' data) which can cause issues when double checking your results against the graphs shown. You must also be careful when making formulas for tables, especially if you're going to be copy/pasting or dragging them around as it's very important to make sure you have the correct cell references which can go wrong depending on which cell references you've locked and how you're copying the formula.

## Results
- **What are two conclusions you can draw about the Outcomes based on Launch Date?**
  - It appears that May/June/July have the best chances to successfully fund their campaigns, in that order
  - Even with the large fluctuation between the number of campaigns per month, the number of failed campaigns was fairly consistent. This implies that the number of campaigns in the month didn't have a large effect on the outcome of the campaign.
- **What can you conclude about the Outcomes based on Goals?**
  - The cheaper campaigns (<$5K) seem to have the best chances of success along with a sweetspot around $35K-45K which also had a decent success rate but was still lower than the cheaper campaigns. Going over $45K doesn't seem to be a great idea though with none of the campaigns between $45K-50k succeeding and only 13% of the campaigns above that succeeding
- **What are some limitations of this dataset?**
  - There isn't actually a whole lot of data for the plays and theater campaigns, while the entire data set is coming from 2009-2017 there's actually only really three years of campaign data for theater with very few campaigns coming in on the other years
- **What are some other possible tables and/or graphs that we could create?**
  - While our two analyses are useful on their own they're representing different sets of data (Theater/Plays). Because Lousie was looking at Kickstarter for her play we probably should've been more focused on that subcategory. So setting up an analysis of the outcomes based on launch date but have the data set filtered to only the 'plays' subcategory so we can compare two different graphs on the data about plays allowing us to further narrow down the best time and goal range to run a successful play Kickstarter. Keeping in the theater data could skew our data as the theater category doesn't always mean plays.
  - It also may be a good idea to do something that looks at more of a trend over time, maybe a graph similar to the 'Outcomes Based on Launch Date' but include the year along with the month so you can see if people have started to get more or less interested in plays in general as time has gone by. It may not be useful if she's putting this campaign out anyways but it would give her an idea of people's current interest on Kickstarter for plays.
  - We should probably have added a country filter to the data we pulled. While this doesn't necessarily matter for some campaigns, plays are usually fairly regional and so could the interest in funding said plays.
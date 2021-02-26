# Rent the Runway: Analyzing a Sequins of Events
## Table of Contents
1. [Description](#description)
2. [Data Overview](#DataOverview)
3. [Data Preparation](#DataPreparation)
4. [Exploratory Data Analysis](#ExploratoryDataAnalysis)
5. [Hypothesis Testing: Loyal User Ratings vs. Unique User Ratings](#HypothesisTesting)
6. [Summary](#Summary)



## Description <a name="description"></a>
Rent the Runway (RTR) is an online e-commerce website that allows women to rent clothing for special events and every day purposes. The dataset contains of over 150k rows of reviews. In this exploratory data analysis, we ultimately want to know how many unique reviewers are there compared to users who have posted a review more than once and whether or not their ratings differ.

## Data Overview <a name="DataOverview"></a>
UCSD has provided a dataset of over 150,000 rows of user reviews from November 3, 2010 to January 8, 2018. RTR has made it known in numerous [publications](https://digital.hbs.edu/platform-rctom/submission/rent-the-runway-wants-to-predict-your-fashion-choices-and-give-you-a-virtual-closet-will-you-let-them/) that their top priority is customer experience with clothing fit.
Given the former, this project observes the relationships between the average user and ratings.

**fit:** String information on wether user's review item 'fit', was too 'large', or too 'small'.

**user_id:** Unique user identification int.

**bust size** String of user bust sizes, contains two numbers with a letter or a series of letters.

**item_id:** Unique item id int.

**weight:** String weight of users with number and chars 'lbs' attatched.

**rating:** Float of user satisfaction rating. Values only include 2.0, 4.0, 6.0 and 10.0. Perhaps a 5-point rating scale.

**rented for:** String of occasion reviewer rented item for. Includes: wedding, formal affair, party, everyday, other, work, date, and vacation. One extra category is 'party: cocktail' but can be dropped.

**review_text:** String of user review text.

**body type:** String of user body types. Includes apple, athletic, full bust, hourglass, pear, petite, and straight & narrow.

**review summary** String that is a shorter blurb or title of the review_text.

**category:** String of item type such as dress, gown pants and more.

**height:** String heights of reviewers.

**size:** Int sizes of reviewer rental ranging from 0 - 59. Sizing may be a representation of multiple clothing types as RTR and standard dress sizes go from 0-20.

**age:** Float of reviewer ages. Ages 0-10 and 100-120 appear to be accidentally inputted.

**review_date:** String object of review date post.

**review date** Formated review_date to timestring format.

**bin:** String object of ages binned in counts of 10.

**cup_size:** String of cup sizes from slicing bust size string object.

**review_count:** Int count of number of reviews per given user_id int.

## Data Preparation <a name="DataPreparation"></a>
Cleaning was kept to a minimum due to the data being clean and organized already. The code can be found in this repo as RTR.ipynb. During the EDA process, I made visuals about the reviewers overall based on their attributes of height, age, and body type.

Some of the attributes needed to be formatted:
* review date to datetime format
* bin was created in order to bin the ages into groups easier to graph
* review_count was created from user_id in order to count number of reviews per person
* cup_size was created from bust size to shorten and group all the various band and cup size combinations


## Exploratory Data Analysis <a name="ExploratoryDataAnalysis"></a>

### Summary Statistics

This is the initial summary statisitics for the data with values as ints or floats.

<img src="dfdescribe.png"
     alt="data describe"
     style="float: left; margin-right: 10px;" />

### The Average Reviewer

Among the 150k reviewers, the majority lean toward rating their experience as an 8 or 10.

<img src="RatingsOverall.png"
     alt="reviwer ratings"
     style="float: left; margin-right: 10px;" />
     
They are predominantly ages 20-40.

<img src="ReviewerAges.png"
     alt="reviewer ages"
     style="float: left; margin-right: 10px;" />

Reviewers tend to be around 5'3 to 5'7 in height.

<img src="ReviewerHeights.png"
     alt="reviewer heights"
     style="float: left; margin-right: 10px;" />

The average reviewer size is a size 12.

<img src="ReviewerSizes.png"
     alt="reviewer size"
     style="float: left; margin-right: 10px;" />
     
 
Of the reviews, these words appeared most often

<img src="ReviewsWordCloud.png"
     alt="top review words"
     style="float: left; margin-right: 10px;" />
     
All of the occasions that the women in this dataset rented for are as follows:

<img src="occasions.png"
     alt="occasions"
     style="float: left; margin-right: 10px;" />

### Ratings by Attributes
Generally, women in the following categories gave ratings of 8 and above, similar to the overall ratings chart.

Here are women's ratings by how well their rental fit.

<img src="Fit-Rating.png"
     alt="rating by fit"
     style="float: left; margin-right: 10px;" />
     
Again, with ratings by body type, across the board, the average rating is above and 8.

<img src="BodyType-Rating.png"
     alt="rating by body type"
     style="float: left; margin-right: 10px;" />
     

## Hypothesis Testing: Loyal User Ratings vs. Unique User Ratings <a name="HypothesisTesting"></a>

Loyal users are reviewers who have posted a review more than once while Unique users are those who have posted a review only once. To find and filter out both types of users, I created a new column called review_count with the total of each person's review counts. 

> **H0:** There is no difference in the average ratings of Loyal and Unique shoppers

> **HA:** There is a significant difference in the average ratings of Loyal and Unique shoppers

**alpha** = 0.05

**Loyal users:** 33,707

**Loyal users' total reviews:** 120,720 


**Unique users:** 71,824

### Findings

Mean of ratings by Loyal users: 9.03
Mean of ratings by Unique users: 9.20

Loyal customers standard dev: 1.47
Unique customers standard dev: 1.35

### Mann Whitney U test result

**p-value** = 0.00

## Summary <a name="Summary"></a>

Given that the p-value is less than the alpha of 0.05, I reject the null hypothesis. I accept the alternative hypothesis the the average rating of unique users if significantly higher than that of the average ratings of loyal users. It appears that loyalty does not matter to ratings. Although this result is significantly different, it is not practical in making business decisions.

# An Analysis of Beer, Beer Styles, and Breweries
## by Carl Smith

<br>

## <u>Dataset</u>
<br>

Datasets used:
>- [Beer Advocate Beer Reviews dataset](https://data.world/socialmediadata/beeradvocate)
>- [Open Brewery DB](https://www.openbrewerydb.org/)

The primary dataset used for this analysis was the Beer Advocate dataset, which included all of the beer review data. While the secondary dataset used was the Open Brewery DB, which included additional brewery data, such as brewery type and location. These datasets were then merged on brewery names. After merging and some light cleaning, the master DataFrame `beer_df_clean` contained 563,517 unique beer reviews. 

In addition, there is also one feature engineered column `weighted_review`, which represents an aggregate review score of the other five review categories. Below is a brief description of these five review categories and `weighted_review`:
>- `weighted_review`: engineered variable that calculates a weighted average of all 5 review categories. This is the primary review score that is listed on BeerAdvocate's website. Each weight is defined by BeerAdvocate as 20%, 24%, 6%, 10% and 40% respectively to the following review categories.    
>- `review_overall`: overall review score given for overall impression of the beer. 
>- `review_aroma`: review score given for any malt, hops, yeast, and other aromatics present in the beer.
>- `review_appearance`: review score given for the beer's color, clarity, head retention, and lacing. 
>- `review_palate`: review score given for the beer's body, carbonation, warmth, creaminess, astringency and other palate sensations. 
>- `review_taste`: review score given for any malt, hops, fermentation byproducts, balance, finish or aftertaste and other flavor characteristics.

<br>

## <u>Summary of Findings</u>
<br>

### Univariate Analysis
<br>

During univariate analysis none of the quantitative variables were normally distributed. All review categories had a right skew, while `beer_abv` had a left skew. During the univariate analysis of qualitative variables in the dataset, I found that:
>- California is the most popular state for brewing beer. 
>- American IPA is the most popular beer style.
>- Microbreweries are the most popular brewery type. 
>- Sculpin India Pale Ale is the most popular beer.

<br>

### Bivariate Analysis
<br>

During bivariate analysis, I first looked at the correlations between the quantitative variables. I found that `review_taste` had the highest correlation with `review_overall`, which intuitively makes sense. Since `review_overall` represents the reviewer's overall impression of a beer, it made sense to find correlations with this variable, instead of say `weighted_review`.
<br>

After bivariate correlations, I wanted to create some visualizations that showed categorical rankings by average weighted review score. The purpose of this was to provide a reference of infomation for beer enthusiasts like myself. Some findings:
>- Top rated beer: Rare Bourbon County Stout
>- Top rated beer style: Lambic - Unblended
>- Top rated brewery: Hill Farmstead Brewery
>- Top rated brewery type: Planning, descriptions of brewery types can be found in exploratory analysis file. 
>- Top rated state: Kansas
>- Top rated city: Grennsboro Bend, VT

In addition, I created two geospatial visualizations of states and cities, to see if any geographical trends appeared. I found two insights: states and cities tend to have higher ratings along the coasts, and states and cities also tend to have higher ratings when near fresh water, specifically the Great Lakes. I also created a visualization that merged the two maps and overlayed the cities on states. However, after some critiques from my wife, who suggested that the map was too cumbersome to understand, I decided to leave it out of the explanatory analysis and slide presentation. This visualization can be found the exploratory analysis file. 

The final bivariate analysis I did was of `beer_abv`. I plotted beer styles and brewery types with the highest average ABV (Alcohol by Volume). The highest ABV beer style was, Eisbock, however with a relatively large errorbar. It's worth noting that 3 of the top 5 styles here were a "wine" brew, either Barleywine or Wheatwine. Wine brews are notorious for their alcohol content, so this didn't surprise me. Both the Eisbock and the "wine" brews were around 10-11 ABV. In terms of brewery type, regional breweries had the highest average ABV values, at just under 7.2 ABV.

<br>

### Multivariate Analysis
<br>

I started the multivariate analysis by looking at the same correlations between `overall_review` and the other four review categories. However, I wanted to look at these correlations with respect to individual reviewers. My initial idea was to see if I could find a way to determine who the "best" or "most trustworthy" reviewer was, by comparing their results with that of other reviewers. But I found this to be too subjective of a question to answer. Therefore, I decided to look at the variance of data points for each correlation variable to see if there was any "consensus" among reviewers. In other words, if the correlations of a said variable had a low variance and high correlation coefficients, then it could imply that most reviewers agree that the said variable is more important when determining an overall review. The vice versa could be said about variables with low variances and low correlation coefficients.

I analyized three groups of reviewers, the top 10, top 50, and top 100 most active reviewers, i.e. most reviews posted. Across all three groups, we found the same trend, taste and palate had the highest correlation coefficients and lowest variances. While aroma and appearance had lower correlation coefficients and higher variances. To me, this implies that the top reviewers tend to give overall reviews primarily based on taste and palate. These findings support what was found with bivariate relationships. Personally, I have always tried to analyze the taste and aroma of a new beer when trying it. However based on these insights I will definitely start analyzing the palate of new beers as well. 

The final multivariate analysis I did was top beers by average weighted review by `beer_abv` quartile. I wanted to look at the highest rated high alcoholic beers, median alcoholic beers, and low alcoholic beers. My idea was that someone could use this data to answer more practical questions a beer drinker may have. For example, let's say I wanted to find a highly rated beer to drink throughout the day in the summer. Therefore, since I want to drink throughout the day, I want to find a low alcoholic beer so that I do not become to overly intoxicated. I could then look at the visualization of top 25 low alcoholic beers, and find that the Carnie Fire, at 5% ABV, or the Southhampton Berliner Wise, at 2% ABV, might be great choices for my day long drinking session. 

<br>

## <u>Key Insights for Presentation</u>
<br>

I have two key insights:
> - Present a reference of information about different data on beer, that can be used by any data hungry beer enthusiast. 
> - Show which characteristics of a beer correlate with people giving high overall review scores.  

<br>

## <u>References</u>

1. [Beer Advocate Beer Reviews dataset](https://data.world/socialmediadata/beeradvocate)
2. [Open Brewery DB dataset](https://www.openbrewerydb.org/)
3. [Open Brewery DB - Python Wrapper](https://github.com/jrbourbeau/openbrewerydb-python)
4. [A lot of Stackoverflow (press for meme)](https://9gag.com/gag/aBmMBWD)



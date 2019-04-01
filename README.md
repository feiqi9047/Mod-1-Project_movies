# Maximizing Profit Opportunities Based on Movie Data from 2008 - 2018


## Project Motivation:
In this project, we used webscraping and API to scrape movie data from IMDB and and TheMovieDB. Using BeautifulSoup, we scraped the most popular 200 movies every year from 2008 - 2018. We then searched the API provided by TheMovieDB to gather the top 50 most revenue-generating movies every year from 2008 - 2018. We cross-referenced the two datasets by creating a relational SQL databased by inner-joining on movie titles, hence consolidating data for the most popular movies that are also the top-revenue generating ones. Visualizations were then created, using libaries Seaborn and Matplotlib, to explore correlations and make inferences.

## ETL:
The webscrape provided the following data points, which yielded 2,200 data points:
- Title
- Genres (multiple)
- Runtime
- Release Year
- IMDB Rating
- Number of Votes
- Certificate

The API search provided the following data points, which yielded 550 data points:
- Title
- Release Date
- Directors
- Budget
- Revenue

## SQL Database Schema
SQLite3 was used to construct the schema for the SQL database. Our database was joined on Title. We also added addition columns which helped further our analysis, including Profit (Revenue minus Budget) and Profit Margin (Profit divided by Revenue). Genres was broken down into additional columns to indicate the primary genre and subcategories of genres. Below is a snapshot of our dataset with the columns that we focused on boxed in.

<img width="738" alt="Screen Shot 2019-04-01 at 10 27 53 AM" src="https://user-images.githubusercontent.com/44821660/55335303-e1045400-5468-11e9-9057-9be0b0e3e230.png">


### Relationship Overview

<img width="477" alt="Movies_Relationship" src="https://user-images.githubusercontent.com/44821660/55293057-c924c580-53bf-11e9-80bd-e444991699c8.png">

Profit Margin has a higher correlations with Revenue and Budget, with a positive correlation with Revenue and a negative correlation with Budget. Ratings do not seem to have significant correlations with Budget, but does have a slight positive correlation with Revenue.

### Deeper Inspection of Relationships

![Corr_Rev_PM](https://user-images.githubusercontent.com/44821660/55293104-7566ac00-53c0-11e9-9a55-30840ac2821a.png)


![Corr_Budget_PM](https://user-images.githubusercontent.com/44821660/55293091-4ea87580-53c0-11e9-8e04-7a5ff13a6d06.png)


Confirming what we’ve just seen. ALthough, it seems that Budget is a greater driver of Profit Margin than Revenue.

### Which Genres to Consider


<img width="994" alt="Screen Shot 2019-03-31 at 2 25 45 PM" src="https://user-images.githubusercontent.com/44821660/55293135-f1f98a80-53c0-11e9-8dbf-b9a6717df2b2.png">

<img width="1005" alt="Screen Shot 2019-03-31 at 2 25 58 PM" src="https://user-images.githubusercontent.com/44821660/55293136-f625a800-53c0-11e9-8d97-29b623eaa413.png">

![Genre_PM](https://user-images.githubusercontent.com/44821660/55293147-0dfd2c00-53c1-11e9-812e-d490523b2e97.png)

Animation, Action, and Music appeared to top the list in terms of genres that generate the most revenue. This makes sense, since animated movies have been performing very well in the past few years, especially those from Pixar/Disney. Action movies have known to attract audiences to theaters as viewers look to experience action movies with proper theater effects. Music movies have also been performing well if we look at blockbusters such as La La Land or High School Musicals.

In terms of budget, Action/Adventure/Sci-Fi movies tend to have the highest production budgets given the need for special effects and CGI. The genres that typically requires the lowest forms of investments include Horror and Musicals.

Since profit margins are driven by more budget than revenue, it becomes intuitive that lower budget movies in the Horror and Musicals category tend to do better for a production company's bottom line.

### Which Directors to Consider

<img width="657" alt="Screen Shot 2019-03-29 at 2 03 42 PM" src="https://user-images.githubusercontent.com/44821660/55293229-3d606880-53c2-11e9-90ac-a23446ab6e1a.png">
<img width="614" alt="Screen Shot 2019-03-29 at 2 03 21 PM" src="https://user-images.githubusercontent.com/44821660/55293227-3a657800-53c2-11e9-828d-ce00c8448d03.png">

Depending on the production company's budget, we provided a list of movies and their associated directors for those that generated the most revenue and profit margin. Of course, many factors will need to be accounted for when signing on a new movie and deciding which director to bring on for that movie. Hence, the above charts could help executives explore possible candidates given their track records and successes. There are well-known big names as well as those that have had a one-time hit. Depending on the production budget, and hence genre, executives can make an informed decision regarding talent.

### Next Steps:
We would like to explore additional actionables such as the range of budget to consider for both large and low-budget productions. We would also like to see the relationship between IMDB ratings and votes and profit margin to provide insights into whether well-rated movies result in higher profit. Furthermore, analysis could be done to understand the effect of seaonality on revenue and profit margin.



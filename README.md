# datascience-stackexchange
This repository is mainly for data analysis and data engineering of the data corresponding to the data dump of datascience.stackexchange.com.

Initially, data converted into CSV (from XML) were provided by a recruiter. However, the .7z file was corrupted. Three CSVs were corrupted thus, needing to obtain the raw file from https://archive.org/details/stackexchange. Inside the compressed file that can be downloaded here: https://archive.org/download/stackexchange/datascience.stackexchange.com.7z, 8 XML files can be found. Since there are already converted CSVs given that needs no conversion, only the 3 corrupted files were converted. Note: the decompressed file (datascience.stackexchange.com - zip) was already uploaded here, please extract it first when you will be running the code.

All codes were run using Jupyter Notebook. The following are the packages used.
* matplotlib.pyplot
* pandas
* os
* datetime
* numpy
* matplotlib
* sqlite3
* csv
* glob

<h3>Explanation and steps:</h3>

1. Convert the three corrupted files (Tags, Users, and Votes) into CSVs by running 'xml-to-csv-to-db.ipynb'. This notebook also allows to store all the CSV files into one database (datascience-stackexchange.db).  For the other notebooks, you may run it as is.
2. Profiles:
  Three notebooks were inside the folder profiles. This notebooks shows data visualization that describes the top users who posts and comments based on the occurences of their posts/comments. 
    * First is the the top locations ('top-location-by-number-of-posts.ipynb'), this shows that the top 5 countries who are active - meaning commenting and postings occurences were the highest are: India, United States, Canada, Australia, and United Kingdom. ![top-location-by-number-of-posts-top-100](https://github.com/radlysevilla/datascience-stackexchange/blob/main/plots/top-location-by-number-of-posts-top-100.png)
    * Second is the post and comment count of every user in the history of the datascience.stackexchange ('post-comment-count-group-by-user-creation-date.ipynb'). This includes all the edit and new post/comment counts. Mostly, the the users who posted and commented frequently are from account generated 1-3 years ago. ![post-comment-count-group-by-user-creation-date](https://github.com/radlysevilla/datascience-stackexchange/blob/main/plots/post-comment-count-group-by-user-creation-date.png)
    * Lastly for the profiles, this describes the range of users who has the lowest to highest of number of reputation. This shows that most users has who already posted a thread or question has a reputation of 0-50. For the users who already posted a comment, most of them have a reputation of 100-150. ![user-count-group-by-reputation-range-0-500](https://github.com/radlysevilla/datascience-stackexchange/blob/main/plots/user-count-group-by-reputation-range-0-500.png)
3. For the guide question #2, this was described using two datasets. First is the overall mean for comment per post of all the users who posted a question (PostHistoryTypeId = 1). Second is the top 100 users who frequently posts (most number of posts) describing the mean of their comment per post. Here, it was shown that the mean for whole post history is 2.4826059593578926 and the mean for the top 100 posters is 2.6331328930784066. It can be described that mean for the top 100 posters is greater than compared to the whole post history. From this, it can be said that users who often post are also the often write comments. ![comments-per-post-question-all-val](https://github.com/radlysevilla/datascience-stackexchange/blob/main/plots/comments-per-post-question-all-val.png) ![comments-per-post-question-0-35](https://github.com/radlysevilla/datascience-stackexchange/blob/main/plots/comments-per-post-question-0-35.png)
4. For the guide question #3, this was described using the top 100 users who posts. From there, all of their post with tag (PostHistoryTypeId = 3) are compiled and being counted. From the number of post they did, the tag occurences of each user was counted. This occurences can be computed as percentage. Considering the top 5 most used tag of the user, the percentages was put in a single dataframe for all the top 100 users. From this, it was cluster from 0%-10% with increment of 10%. It was computed that the top 100 users has an average of 0.2879 topics per user. There are only 43/100 top 100 users who exceeded the 0.50 topics per user. This means not majority of the top 100 users who post are not posting in relation to a single topic. ![percentage-tag-user-](https://github.com/radlysevilla/datascience-stackexchange/blob/main/plots/percentage-tag-user.png)
5. Additional analysis for this could be the number of posts depending on the month so that it can showcase the traffic the site will use in the future.

   

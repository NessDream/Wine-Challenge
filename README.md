# Wine Challenge

This mini-project comes from a recruiting test I passed for a data science position. I enjoyed a lot this assignement, and decided to share it on my github.  
The subject is to answer 3 different business questions for a winery, using a dataset recording more than 86.000 different bottles evaluations.

### Assignement
The zip file contains a .csv with several information about wines, e.g., names, varieties, and price. Given these data, your goal is to answer the following questions at best.  

- Question 1 (4 points) Some winemakers have asked you to buy their wine. How would you exploit the data you have to estimate the best price to buy them? Please, notice that the prices reported in the file are related to the cost at which the corresponding wineries sell them.
- Question 2 (4 points) Since you will have customers from different countries, you want to create a wine list that presents wines from different parts of the world. How could you identify which areas are similar for production? Select the best wines from such areas to create the best wine list. Please, take into account that you will have different types of customers, from wine lovers to wealthy people, able to invest an interesting amount of money in your bottles.
- Question 3 (2 points) One of the most interesting project you want to carry out is a blind tasting night every Wednesday. Describe which approach would you follow to identify the characteristics of a wine, e.g., variety or denomination, given their description. Please, in your description specify how you would structure the project.

### Q1) Predict wine prices
To answer the first question I only used :
- country
- variety
- designation
- price (target)  

I **binary encoded** the first 3, and ended up with 34 more columns.  
I then decided to use a **decision tree** to be able to interpret the output of the algorithm.

I also made a predictive model using the **points** feature, in case we would have this data.

### Q2) Create a wine menu
I realised a clustering to identify similar production regions.    
My approach was the following :
- group regions (here this will be province) in cluster of same production type, using the grape variety
- select 5 best wines from each of these regions, in 3 categories of prices : under 10\$, under 50\$, and more than 50\$

I used the province, points, variety, designation and title to do this.  
I again **binary encoded**  the 630 varieties and 402 provinces to be able to handle the categories in it.  
I then used **Kmeans** clustering, and **elbow method** to categorize each bottle in a production type. I ended up with 4 different areas similar for production, very well balanced.  
FInally, to create the wine menu, I picked the 5 top bottles for each regions, and for each of the following category price : under 10\$, under 50\$ and more than 50\$.  
The edited menu can then present the best bottles in every range of prices, and every type of production !
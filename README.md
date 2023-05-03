# LDurham89.github.io

__Udacity Datascience Nanodegree Project 1: Writing a Data Scientist Blog Post__


__Project description:__ As part of Udacity's Data Scientist course the first project due is a blog post presenting the results of some data analysis.
For this project I chose to analyse data on Airbnb listings in Seattle and Boston to answer some questions of interest. The questions are:

1) Is there a difference in the average price per night of Airbnb's in Seattle and Boston?
2) What are people saying about their stays in Boston and Seattle?
3) When it comes to price, is it really all about location, location, location? Are downtown properties that much more expensive than those further out?
4) What are the most important factors in deciding the price per night of an Airbnb and is city one of them?

The Jupyter notebook presents the analysis of the data to answer these questions. You will be able to see how the data is loaded in and preprocessed
for analysis, how new variables are made, visualisations made and analysis is conducted. The note book is organised so that you can see this process done separately 
to answer each of the questions. The only caveat here is that Q1 is addressed in the same section as Q4, as the same data preprocessing was required for each.  

__Summary of the results & issues with analysis:__ The analysis offered some interesting and in some cases unexpected findings. The data shows that there is a 
significant difference in average price per night at Airbnb's in the two cities, with properties in Boston being around $50 more expensive. This is
true both before and after removing outliers.

What was surprising was the results of analysing the text data. When looking at the most common words and bigrams used in reviews the results
suggested that written reviews are quite generic. The two tables in the blog show that the lists of common words for each city are basically
identical - albeit with the words in slightly different orders. The same is true when looking at the most common bigrams. While stopwords were removed
from the text, if I were to repeat the project I would consider weighting the frquency of words by the number of reviews they appear in to get around this finding 
of the reviews being quite generic. Another point to note is that I was originally planning to doing sentiment analysis of the reviews using VaderSentiment in order to 
see how many positive reviews properties got in each city. However, this method is about 75% accurate, so I decided that using the review score data in the 'listings'
dataset would be simpler and produce more robust figures.

One of the most informative results in the project comes from mapping the properties, with colour coding showing the price band that each property
falls into. Normally we think of cities in terms of concentric circles, with property being the most expensive in the centre and gradually 
getting cheaper as one moves further out. The map of Seattle suggests that this relationship is very weak, with the most expensive properties
appearing in all parts of the city. The downtown area has a slightly higher concentration of above average priced properties, but the cluster
isn't very dense. In contrast, Boston appears to have a very expensive city centre, with cheaper properties being further away. I'm not familiar with
either city, so my explanation for this largely comes from looking at maps of the two cities. Boston appears to be a different kind of city to 
Seattle, with more economic activity and more world-renowned centres of learning. I feel this goes someway to explaining the 'Boston effect'
found when addressing question 4.

The final section of the notebook aims to use a regression model to find out which attributes of properties influence price per night the most.
One of these attributes is the city that the property is located in. In some ways this is difficult to model. The listings data frame offers
a lot of data on each property - however many features are likely to be related to each other. For example, after making dummy variables for
each value in the 'amentities' column the dataframe contains a variable called 'Pets live at this property' and another called 'dog(s)'. If a 
pet lives a property there is a significant chance of it being a dog, meaning the variables are not independent of each other. This is an exampe of multicolinearity,
which can cause linear models to give inaccurate results. To get around this I tried running several models and using Variance Inflation Factors
to identify sources of multicolinearity. You will see the iterations of the model that I ran in the notebook, gradually removing insignificant variables
and sources of multicolinearity. Across all of these models there is a significant difference between properties in Seattle and Boston, of around $30.
This suggests that around 40% of the price difference is to do with the attributes of properties in the two cities and 60% simply comes from the city they are in. 

__File descriptions:__ The main files of interest for this project are:
- 'Udacity Airbnb project.ipynb' which is the notebook containing the analysis. This can be found in the root of the directory
- 'Project_1_Blog_Post.md' which contains the blog post. This can be found in the 'posts' folder.
 
__Usage instructions:__ This project is simple to use. If you want to read the blog you only need to select the file in 'posts'. To run the notebook
you will need to download the file to your machine. The datasets are publically available on Kaggle at the urls below:

Seattle data-
https://www.kaggle.com/datasets/airbnb/seattle

Boston data-
https://www.kaggle.com/datasets/airbnb/boston

Once you have downloaded these, you will need to amend the cells where the data is read in, so that it reflects the file path on your machine.

Because the analysis for each question is contained in the same notebook, once this is done all that you - the user - need to do is select 'run all' under the 'cell' tab.

You will need to have Kaleidoscope installed if you want to use the Figure Factory for creating tables.
You will also need to have nltk.punkt installed for the Natural Language Processing part of the project.

__Packages used:__ There are quite a few packages used in this project.

Some are standard tools for analysing and visualising numerical data:
- pandas
- numpy
- matplotlib.pyplot
- seaborn

Other are tools for analysing text data, mostly derived from nltk:
- nltk
- nltk.corpus.stopwords
- nltk.tokenize.word_tokenize
- nltk.stem.WordNetLemmatizer
- nltk.util.ngrams
- nltk.probability.FreqDist

Some packages were used for specific data preprocessing tasks:

- re: this was used to format text data and remove punctuation from numerical values before converting to float
- string: provides a convenient way to remove punctuation
- counter: provides a convenient way to count frequency of ngrams

These packages were used for the regression analysis:
- statsmodels.api: this contains the linear regression model. I chose this package over sklearns solution as statsmodels allows you to access a report showing the results of the regression
- statsmodels.stats.outliers_influence.variance_inflation_factor: this is a useful tool for measuring the degree of multicolinearity in a set of variables

Finally, the package below is useful for export tables. Please note you will need kaleidoscope installed for this to work.
- plotly.figure_factory

__Contact information:__ The maintainer of this project is me - Laurence Durham - contactable at laurence.durham89@gmail.com

__Necessary acknowledgments:__ While working on this project a few sources have been particularly helpful for getting around programming issues
and fixing errors in my code. These include: the Knowledge section of the Udacity website, Udacity GPT and Stackoverflow.

Some particular mentions:

I struggled to work with the 'amenities' column in the listings dataset as many of my attempts to find unique value from this column resulted in impractical formatting or unexpected punctuation appearing in variables that I created. The answer provided by Alex Martelli on the Stackoverflow post below was a massive help to extracting unique values correctly into one long list:
https://stackoverflow.com/questions/952914/how-do-i-make-a-flat-list-out-of-a-list-of-lists

My first attempts to remove automated reviews from the 'reviews' data were generally unsuccesful at first as I wasn't getting the results I wanted.
This blog post from Bobby Hadz was very helpful - although the post seems to have been removed since:
https://bobbyhadz.com/blog/python-remove-elements-from-list-that-contain-string/

I found it tricky to get figures to look the way I wanted in figure factory, so while I learned about the package in the Stackoverflow post below, Udacity GPT provided several suggestions about how to use the different parameters to get the output I wanted.
https://stackoverflow.com/questions/66588116/why-does-the-title-text-argument-of-fig-update-layout-appear-not-to-be-worki

Finally, I previously used regression methods and Variance Inflation Factors quite often in STATA. However, I had to look into how to use Variance Inflation Factors in python. I found the post below that introduced me to the statsmodels.stats.outliers_influence package. I also followed the implementation in the post quite closely as I could not find ways to improve upon it
https://etav.github.io/python/vif_factor_python.html

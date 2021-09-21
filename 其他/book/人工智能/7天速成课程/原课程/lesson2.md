Hey Leaves-27, welcome back.

Yesterday, you got a high-level overview of the entire machine learning workflow.

Let's review answers to the pop quiz at the end of yesterday's lesson:
What are the 5 core steps of the machine learning workflow?
Exploratory Analysis
Data Cleaning
Feature Engineering
Algorithm Selection
Model Training
When the curious child learned that "red and bright means pain," what did he learn?
(D) He learned both a pattern and a model. 
"Red and bright means pain" is a pattern, and it became his model for dealing with bright, red objects.
Presumably, he could continue adding to that model. For example, a red and bright toy car would form a different pattern (and heat may become the distinguishing factor).
In the example of the curious child, what was the training data? What was the test data?
The training data was the candle flame.
The test data was the stove top. However, in this situation, we typically refer to the stove top as "unseen data."
In your own words, describe the 3 essential elements of great machine learning.
The first element is a "skilled chef." You must make dozens of decisions along the way.
The second element is "fresh ingredients." The quality of your data determines the effectiveness of your models.
The third element is to "avoid overcooking it." Overfitting a serious pitfall, and you must take precautions.
Awesome, we're already laying a strong foundation for applied machine learning.


Today, we're going to dive into the first step of the core workflow: Exploratory Analysis.

 
1. Introduction

The purpose of exploratory analysis is to "get to know" the dataset. Doing so upfront will make the rest of the project much smoother, in 3 main ways:
You’ll gain valuable hints for Data Cleaning (which can make or break your models).

You’ll think of ideas for Feature Engineering (which can take your models from good to great).

You’ll get a "feel" for the dataset, which will help you communicate results and deliver greater impact.

However, exploratory analysis for machine learning should be quick, efficient, and decisive... not long and drawn out!

Don’t skip this step, but don’t get stuck on it either.

You see, there are a infinite possible plots, charts, and tables, but you only need a handful to "get to know" the data well enough to work with it. In this lesson, we'll show you the visualizations that provide the biggest bang for your buck.

2. Basic information

First, you'll want to answer a set of basic questions about the dataset:

How many observations do I have?
How many features?
What are the data types of my features? Are they numeric? Categorical?
Do I have a target variable?
Then, you'll want to display example observations from the dataset. This will give you a "feel" for the values of each feature, and it's a good way to check if everything makes sense.

Here's an example from the real-estate dataset used in Project 2 of our Machine Learning Masterclass:
Image
The purpose of displaying examples from the dataset is not to perform rigorous analysis. Instead, it's to get a qualitative "feel" for the dataset.
Do the columns make sense?
Do the values in those columns make sense?
Are the values on the right scale?
Is missing data going to be a big problem based on a quick eyeball test?

3. Distributions of numeric features

Next, it can be very enlightening to plot the distributions of your numeric features.

Often, a quick and dirty grid of histograms is enough to understand the distributions.
Image
Here are a few things to look out for:
Distributions that are unexpected
Potential outliers that don't make sense
Features that should be binary (i.e. "wannabe indicator variables")
Boundaries that don't make sense
Potential measurement errors
At this point, you should start making notes about potential fixes you'd like to make. If something looks out of place, such as a potential outlier in one of your features, now's a good time to ask the client/key stakeholder, or to dig a bit deeper.

However, we'll wait until Data Cleaning to make fixes so that we can keep our steps organized.

 
4. Distributions of categorical features

Categorical features cannot be visualized through histograms. Instead, you can use bar plots.
Image
In particular, you'll want to look out for sparse classes, which are classes that have a very small number of observations.

By the way, a "class" is simply a unique value for a categorical feature. For example, the bar plot above shows the distribution for a feature called 'exterior_walls'. So Wood Siding, Brick, and Stucco are each classes for that feature.

Anyway, back to sparse classes... as you can see, some of the classes for 'exterior_walls' have very short bars. Those are sparse classes.

They tend to be problematic when building models.
In the best case, they don't influence the model much.
In the worse case, they can cause the model to be overfit.
Therefore, we recommend making a note to combine or reassign some of these classes later. We prefer saving this until Feature Engineering (Lesson 4).

5. Segmentations

Segmentations are powerful ways to observe the relationship between categorical features and numeric features.

Box plots allow you to do so:
Image
Here are a few insights you could draw from that chart:
The median transaction price (middle vertical bar in the box) for Single-Family homes was much higher than that for Apartments / Condos / Townhomes.
The min and max transaction prices are comparable between the two classes.
In fact, the round-number min ($200k) and max ($800k) suggest possible data truncation...
...which is very important to remember when assessing the generalizability of your models later!

6. Correlations

Finally, correlations allow you to look at the relationships between numeric features and other numeric features.

Correlation is a value between -1 and 1 that represents how closely two features move in unison. You don't need to remember the math to calculate them. Just know the following intuition:
Positive correlation means that as one feature increases, the other increases. E.g. a child’s age and her height.
Negative correlation means that as one feature increases, the other decreases. E.g. hours spent studying and number of parties attended.
Correlations near -1 or 1 indicate a strong relationship.
Those closer to 0 indicate a weak relationship.
0 indicates no relationship.
Correlation heatmaps help you visualize this information. Here's an example (note: all correlations were multiplied by 100):
Image
In general, you should look out for:
Which features are strongly correlated with the target variable?
Are there interesting or unexpected strong correlations between other features?
Again, your aim is to gain intuition about the data, which will help you throughout the rest of the workflow.

 
7. Conclusion

By the end of your Exploratory Analysis step, you'll have a pretty good understanding of the dataset, some notes for data cleaning, and possibly some ideas for feature engineering.

Here's a short quiz:
What types of features can have sparse classes? How would you check for them?
What does it mean if 'sqft' (size of property) has a correlation of 0.68 with 'baths' (# of bathrooms)?
What are 3 sanity checks to make by looking at example observations from the dataset?
We'll review the answers in tomorrow's lesson.

Plus, we'll learn about Data Cleaning, and we'll provide you with a systematic framework.
 
Until tomorrow,

~ EliteDataScience

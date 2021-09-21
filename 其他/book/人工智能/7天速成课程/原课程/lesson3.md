Hello again!

Yesterday, you learned about the essential data visualizations for "getting to know" the data.

Let's review answers to yesterday's quiz:
What types of features can have sparse classes? How would you check for them?
​Categorical features can have sparse classes, and you can check for them using bar plots.
What does it mean if 'sqft' (size of property) has a correlation of 0.68 with 'baths' (# of bathrooms)?
It means that 'sqft' and 'baths' have a fairly strong positive correlation.
In other words, larger properties have more bathrooms, which makes sense.
What are 3 quick checks you can make by displaying example observations from the dataset?
Do the columns make sense?
Do the values in those columns make sense?
Are the values on the right scale?
Is missing data going to be a big problem based on a quick eyeball test?
Now that we understand the data, it's time to get it into tip-top shape.

Today, we're going to dive into the second step of the machine learning workflow: Data Cleaning.

 
1. Introduction

Data cleaning is one those things that everyone does but no one really talks about. Sure, it’s not the "sexiest" part of machine learning. And no, there aren’t hidden tricks and secrets to uncover.


However, proper data cleaning can make or break your project. Professional data scientists usually spend a very large portion of their time on this step.

Why? Because of a simple truth in machine learning:
Better data beats fancier algorithms.

In other words... garbage in gets you garbage out. Even if you forget everything else from this course, please remember this point.
Image
In fact, if you have a properly cleaned dataset, even simple algorithms can learn impressive insights from the data!

Obviously, different types of data will require different types of cleaning. However, the systematic approach laid out in this lesson can always serve as a good starting point.

 

2. Unwanted observations

The first step to data cleaning is removing unwanted observations from your dataset.

This includes duplicate or irrelevant observations.

Duplicate observations most frequently arise during data collection, such as when you:
Combine datasets from multiple places
Scrape data
Receive data from clients/other departments
Irrelevant observations are those that don’t actually fit the specific problem that you’re trying to solve.
For example, if you were building a model for Single-Family homes only, you wouldn't want observations for Apartments in there.
This is also a great time to review your charts from Exploratory Analysis. You can look at the distribution charts for categorical features to see if there are any classes that shouldn’t be there.
Checking for irrelevant observations before engineering features can save you many headaches down the road.


3. Structural errors

The next bucket under data cleaning involves fixing structural errors.

Structural errors are those that arise during measurement, data transfer, or other types of "poor housekeeping."

For instance, you can check for typos or inconsistent capitalization. This is mostly a concern for categorical features, and you can look at your bar plots to check.

Here's an example:

Image
As you can see:
'composition' is the same as 'Composition'
'asphalt' should be 'Asphalt'
'shake-shingle' should be 'Shake Shingle'
'asphalt,shake-shingle' could probably just be 'Shake Shingle' as well
After we replace the typos and inconsistent capitalization, the class distribution becomes much cleaner:

Image
Finally, check for mislabeled classes, i.e. separate classes that should really be the same.
e.g. If ’N/A’ and ’Not Applicable’ appear as two separate classes, you should combine them.
e.g. ’IT’ and ’information_technology’ should be a single class.


4. Unwanted outliers

Outliers can cause problems with certain types of models. For example, linear regression models are less robust to outliers than decision tree models.

In general, if you have a legitimate reason to remove an outlier, it will help your model’s performance.

However, outliers are innocent until proven guilty. You should never remove an outlier just because it’s a "big number." That big number could be very informative for your model.

We can’t stress this enough: you must have a good reason for removing an outlier, such as suspicious measurements that are unlikely to be real data.

 
5. Missing data

Missing data is a deceptively tricky issue in applied machine learning.

First, just to be clear, you cannot simply ignore missing values in your dataset. You must handle them in some way for the very practical reason that most algorithms do not accept missing values.
 
"Common sense" is not sensible here

Unfortunately, from our experience, the 2 most commonly recommended ways of dealing with missing data actually suck.

They are:
Dropping observations that have missing values
Imputing the missing values based on other observations
Dropping missing values is sub-optimal because when you drop observations, you drop information.
The fact that the value was missing may be informative in itself.
Plus, in the real world, you often need to make predictions on new data even if some of the features are missing!
Imputing missing values is sub-optimal because the value was originally missing but you filled it in, which always leads to a loss in information, no matter how sophisticated your imputation method is.
Again, "missingness" is almost always informative in itself, and you should tell your algorithm if a value was missing.
Even if you build a model to impute your values, you’re not adding any real information. You’re just reinforcing the patterns already provided by other features.
Image
Missing data is like missing a puzzle piece. If you drop it, that’s like pretending the puzzle slot isn’t there. If you impute it, that’s like trying to squeeze in a piece from somewhere else in the puzzle.


In short, you should always tell your algorithm that a value was missing because missingness is informative. So how can you do so?
 
Missing categorical data

The best way to handle missing data for categorical features is to simply label them as ’Missing’!

You’re essentially adding a new class for the feature.
This tells the algorithm that the value was missing.
This also gets around the technical requirement for no missing values.
 
Missing numeric data

For missing numeric data, you should flag and fill the values.
Flag the observation with an indicator variable of missingness.
Then, fill the original missing value with 0 just to meet the technical requirement of no missing values.
By using this technique of flagging and filling, you are essentially allowing the algorithm to estimate the optimal constant for missingness, instead of just filling it in with the mean.

When used properly, this technique almost always performs better than imputation methods in practice.

 
6. Conclusion

After properly completing the Data Cleaning step, you'll have a robust dataset that avoids many of the most common pitfalls. This can really save you from a ton of headaches down the road, so please don't rush this step.

Here's a quick quiz to check that you got everything:
What are 2 types of unwanted observations to remove from the start?
What are 3 types of structural errors to look out for?
How should you handle missing data?
Why is it sub-optimal to drop observations with missing data or impute missing values?
As always, feel free to reply to this email with any questions or feedback you may have. We respond to every email.

Tomorrow, we'll review the answers and and we'll share a set of heuristics you can use for reliable Feature Engineering.

Until then,
 
~ EliteDataScience

Hey Leaves-27, we've hit the half-way mark!

Nice, let's keep going... lots of great stuff to get to in the second half.

Yesterday, you learned a reliable framework for cleaning your dataset.

Let's review answers to yesterday's quiz:
What are 2 types of unwanted observations to remove from the start?
Duplicate observations that can sometimes arise during data collection.
Irrelevant observations that don't fit the specific problem you're trying to solve.
What are 3 types of structural errors to look out for?
​Typos
Inconsistent capitalization
Mislabeled classes
How should you handle missing data?
​Missing categorical data should be labeled with a new class called 'Missing'
Missing numeric data should be flagged (with a new indicator variable) and filled with 0.
Why is it sub-optimal to drop observations with missing data or impute missing values?
​If you drop observations, you're dropping information.
If you impute missing values, you're obscuring the fact that the data was missing in the first place.
Remember, "missingness" is often informative.
Today, in day 4 of our 7-day crash course, we're going to discuss Feature Engineering.

 
1. Introduction

Feature engineering is about creating new input features from your existing ones.

This is often one of the most valuable tasks a data scientist can do to improve model performance, for 3 big reasons:
  You can isolate and highlight key information, which helps your algorithms "focus" on what’s important.
  You can bring in your own domain expertise.
  Most importantly, once you understand the "vocabulary" of feature engineering, you can bring in other people’s domain expertise!
In this lesson, we will introduce several heuristics to help spark new ideas.

Before moving on, we just want to note that this is not an exhaustive compendium of all feature engineering because there are limitless possibilities for this step.

The good news is that this skill will naturally improve as you gain more experience.

2. Domain knowledge

You can often engineer informative features by tapping into your (or others’) expertise about the domain.

Try to think of specific information you might want to isolate. Here, you have a lot of "creative freedom."

Going back to our example with the real-estate dataset, let's say you remembered that the housing crisis occurred in the same timeframe...
Image
Well, if you suspect that prices would be affected, you could create an indicator variable for transactions during that period.​ Indicator variables are binary variables that can be either 0 or 1. They "indicate" if an observation meets a certain condition, and they are very useful for isolating key properties.

As you might suspect, "domain knowledge" is very broad and open-ended. At some point, you'll get stuck or exhaust your ideas.

That's where these next few steps come in. These are a few specific heuristics that can help spark more.
’


3. Interaction features

The first of these heuristics is checking to see if you can create any interaction features that make sense. These are combinations of two or more features.

By the way, in some contexts, "interaction terms" must be products between two variables. In our context, interaction features can be products, sums, or differences between two features.

Back to our real-estate example:
Let's say we already had a feature called 'num_schools', i.e. the number of schools within 5 miles of a property.
Let's say we also had the feature 'median_school', i.e. the median quality score of those schools.
However, we might suspect that what's really important is having many school options, but only they are good.
Well, to capture that interaction, we could simple create a new feature 'school_score' = 'num_schools' * 'median_school' 
A general tip is to look at each pair of features and ask yourself, "could I combine this information in any way that might be even more useful?"

4. Sparse classes

The next heuristic we’ll consider is grouping sparse classes.

Sparse classes (in categorical features) are those that have very few total observations. They can be problematic for certain machine learning algorithms, causing models to be overfit.
There's no formal rule of how many each class needs.
It also depends on the size of your dataset and the number of other features you have.
As a rule of thumb, we recommend combining classes until each one has at least ~50 observations. As with any "rule" of thumb, use this as a guideline (not actually as a rule).
Let's take a look at the real-estate example:
Image
To begin, we can group similar classes. In the chart above, the 'exterior_walls' feature has several classes that are quite similar.
We might want to group 'Wood Siding', 'Wood Shingle', and 'Wood' into a single class. In fact, let's just label all of them as 'Wood'.
Next, we can group the remaining sparse classes into a single 'Other' class, even if there's already an 'Other' class.
We'd group 'Concrete Block', 'Stucco', 'Masonry', 'Other', and 'Asbestos shingle' into just 'Other'.
Here's how the class distributions look after combining similar and other classes:


Image

After combining sparse classes, we have fewer unique classes, but each one has more observations.

Often, an eyeball test is enough to decide if you want to group certain classes together.

 
5. Dummy variables

Most machine learning algorithms cannot directly handle categorical features. Specifically, they cannot handle text values. Therefore, we need to create dummy variables for our categorical features.

Dummy variables are a set of binary (0 or 1) variables that each represent a single class from a categorical feature. The information you represent is exactly the same, but this numeric representation allows you to pass the technical requirements for algorithms.

In the example above, after grouping sparse classes, we were left with 8 classes, which translate to 8 dummy variables:
Image​

6. Remove unused

Finally, remove unused or redundant features from the dataset.

Unused features are those that don’t make sense to pass into our machine learning algorithms. Examples include:
ID columns
Features that wouldn't be available at the time of prediction
Other text descriptions
Redundant features would typically be those that have been replaced by other features that you’ve added during feature engineering.

7. Conclusion

After completing Data Cleaning and Feature Engineering, you'll have transformed your raw dataset into an analytical base table (ABT). We call it an "ABT" because it's what you'll be building your models on.

As a final tip: Not all of the features you engineer need to be winners. In fact, you’ll often find that many of them don’t improve your model. That’s fine because one highly predictive feature makes up for 10 duds.

The key is choosing machine learning algorithms that can automatically select the best features among many options (built-in feature selection).

This will allow you to avoid overfitting your model despite providing many input features.

Alright, you know the drill by now. Quiz time!
What are indicator variables and why are they useful?
What are two criteria you can use to group sparse classes?
In a set of dummy variables created from the same feature, would there ever be multiple variables with value 1?
In our real-estate example, what would be the values for the 'exterior_walls' dummy variables if a property had metal walls?
Tomorrow, we'll take an in-depth look at Algorithm Selection, and give you our recommendations for the most useful algorithms.

You won't want to miss it,

~ EliteDataScience

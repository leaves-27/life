Welcome back,

Yesterday, you learned several different heuristics to help inspire ideas for feature engineering.

Let's review answers to yesterday's quiz:
What are indicator variables and why are they useful?
​Indicator variables are binary (0 or 1) variables that indicate if an observation meets a certain conditon.
They allow you to isolate key properties, and they help you bring in your domain knowledge.
What are two criteria you can use to group sparse classes?
You can group similar classes.
You can also group the remaining sparse classes into a single 'Other' class.
In a set of dummy variables created from the same feature, would there ever be multiple variables with value 1?
No, because each dummy variable represents 1 possible class, and the original feature only had 1 class per observation.
In our real-estate example, what would be the values for the 'exterior_walls' dummy variables if a property had metal walls?
'exterior_walls_Metal' = 1, all others = 0.
Today, we're going to dive into Algorithm Selection.

 
1. Introduction

In this lesson, we'll introduce 5 very effective machine learning algorithms for regression tasks. They each have classification counterparts as well.

And yes, just 5 for now. Instead of giving you a long list of algorithms, our goal is to explain a few essential concepts (e.g. regularization, ensembling, automatic feature selection) that will teach you why some algorithms tend to perform better than others.

In applied machine learning, individual algorithms should be swapped in and out depending on which performs best for the problem and the dataset. Therefore, we will focus on intuition and practical benefits over math and theory.

 
2. Flaws of linear regression

To introduce the reasoning for some of the advanced algorithms, let's start by discussing basic linear regression. Linear regression models are very common, yet deeply flawed.
Image
Simple linear regression models fit a "straight line" (technically a hyperplane depending on the number of features, but it's the same idea). In practice, they rarely perform well. We actually recommend skipping them for most machine learning problems.

Their main advantage is that they are easy to interpret and understand. However, our goal is not to study the data and write a research report. Our goal is to build a model that can make accurate predictions.

In this regard, simple linear regression suffers from two major flaws:
It's prone to overfit with many input features.
It cannot easily express non-linear relationships.
Let's take a look at how we can address the first flaw.


3. Regularization

This is the first "advanced" tactic for improving model performance. It’s considered pretty "advanced" in many ML courses, but it’s really pretty easy to understand and implement.

The first flaw of linear models is that they are prone to be overfit with many input features.
Image
Let's take an extreme example to illustrate why this happens:
Let's say you have 100 observations in your training dataset.
Let's say you also have 100 features.
If you fit a linear regression model with all of those 100 features, you can perfectly "memorize" the training set.
Each coefficient would simply memorize one observation. This model would have perfect accuracy on the training data, but perform poorly on unseen data.
It hasn’t learned the true underlying patterns; it has only memorized the noise in the training data.
Regularization is a technique used to prevent overfitting by artificially penalizing model coefficients.
It can discourage large coefficients (by dampening them).
It can also remove features entirely (by setting their coefficients to 0).
The "strength" of the penalty is tunable. (More on this tomorrow...)

4. Regularized regression

There are 3 common types of regularized linear regression algorithms.


Lasso

Lasso, or LASSO, stands for Least Absolute Shrinkage and Selection Operator.
Lasso regression penalizes the absolute size of coefficients.
Practically, this leads to coefficients that can be exactly 0.
Thus, Lasso offers automatic feature selection because it can completely remove some features.
Remember, the "strength" of the penalty should be tuned.
A stronger penalty leads to more coefficients pushed to zero.

Ridge

Ridge stands Really Intense Dangerous Grapefruit Eating (just kidding... it's just ridge).
Ridge regression penalizes the squared size of coefficients.
Practically, this leads to smaller coefficients, but it doesn't force them to 0.
In other words, Ridge offers feature shrinkage.
Again, the "strength" of the penalty should be tuned.
A stronger penalty leads to coefficients pushed closer to zero.


Elastic-Net

Elastic-Net is a compromise between Lasso and Ridge.
Elastic-Net penalizes a mix of both absolute and squared size.
The ratio of the two penalty types should be tuned.
The overall strength should also be tuned.
Oh and in case you’re wondering, there’s no "best" type of penalty. It really depends on the dataset and the problem. We recommend trying different algorithms that use a range of penalty strengths as part of the tuning process, which we'll cover in detail tomorrow.

 
调试后的回归




5. Decision trees

Awesome, we’ve just seen 3 algorithms that can protect linear regression from overfitting. But if you remember, linear regression suffers from two main flaws:
It's prone to overfit with many input features.
It cannot easily express non-linear relationships.
How can we address the second flaw? Well, we need to move away from linear models to do so.... we need to bring in a new category of algorithms.

Decision trees model data as a "tree" of hierarchical branches. They make branches until they reach "leaves" that represent predictions. 
Image

Due to their branching structure, decision trees can easily model nonlinear relationships.
For example, let's say that for Single Family homes, larger lots command higher prices.
However, let's that for Apartments, smaller lots command higher prices (i.e. it's a proxy for urban / rural).
This reversal of correlation is difficult for linear models to capture unless you explicitly add an interaction term (i.e. you can anticipate it ahead of time).
On the other hand, decision trees can capture this relationship naturally.
Unfortunately, decision trees suffer from a major flaw as well. If you allow them to grow limitlessly, they can completely "memorize" the training data, just from creating more and more and more branches.

As a result, individual unconstrained decision trees are very prone to being overfit.​

So, how can we take advantage of the flexibility of decision trees while preventing them from overfitting the training data?
 
6. Ensembles

Ensembles are machine learning methods for combining predictions from multiple separate models. There are a few different methods for ensembling, but the two most common are:
Bagging attempts to reduce the chance overfitting complex models.
It trains a large number of "strong" learners in parallel.
A strong learner is a model that's relatively unconstrained.
Bagging then combines all the strong learners together in order to "smooth out" their predictions.
Boosting attempts to improve the predictive flexibility of simple models.
It trains a large number of "weak" learners in sequence.
A weak learner is a constrained model (i.e. you could limit the max depth of each decision tree).
Each one in the sequence focuses on learning from the mistakes of the one before it.
Boosting then combines all the weak learners into a single strong learner.
While bagging and boosting are both ensemble methods, they approach the problem from opposite directions. Bagging uses complex base models and tries to "smooth out" their predictions, while boosting uses simple base models and tries to "boost" their aggregate complexity.


 
7. Tree ensembles

Ensembling is a general term, but when the base models are decision trees, they have special names: random forests and boosted trees!

Random forests train a large number of "strong" decision trees and combine their predictions through bagging.

In addition, there are two sources of "randomness" for random forests:
Each tree is only allowed to choose from a random subset of features to split on (leading to feature selection).
Each tree is only trained on a random subset of observations (a process called resampling).


In practice, random forests tend to perform very well right out of the box.
They often beat many other models that take up to weeks to develop.
They are the perfect "swiss-army-knife" algorithm that almost always gets good results.
They don’t have many complicated parameters to tune.
Boosted trees

Boosted trees train a sequence of "weak", constrained decision trees and combine their predictions through boosting.
Each tree is allowed a maximum depth, which should be tuned.
Each tree in the sequence tries to correct the prediction errors of the one before it.
In practice, boosted trees tend to have the highest performance ceilings.
They often beat many other types of models after proper tuning.
They are more complicated to tune than random forests.

8. Conclusion

Whew, that was a lot! If you need to, feel free to let it sink in a bit and then re-read the lesson.

Key takeaway: The most effective algorithms typically offer a combination of regularization, automatic feature selection, ability to express nonlinear relationships, and/or ensembling. Those algorithms include:
Lasso regression
Ridge regression
Elastic-Net
Random forest
Boosted tree
Here's a quiz to make sure you caught everything:
What are the two biggest flaws of linear regression?
How can you address the first flaw? (Which mechanism, and which algorithms?)
How can you address the second flaw? (Which mechanism, and which algorithms?)
What are two types of regularization penalty, and what do they do in practice?
What are two methods for ensembling and how do they work?

As a final note, we had two goals for this lesson: (1) to introduce powerful mechanisms in modern machine learning and (2) to tour several algorithms that use those mechanisms. We cover these (and others) in more detail in our masterclass, with plenty of guided hands-on practice.

Again, feel free to hit 'reply' and send us an email if you have any questions or comments. We'll respond to every message.

Now that you have some great algorithms in your toolkit, tomorrow's installment will teach you how to apply them the right way for Model Training.


Until then,

~ EliteDataScience
 
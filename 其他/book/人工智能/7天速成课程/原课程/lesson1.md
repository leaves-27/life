
1. Introduction

First, we must clear up one of the biggest misconceptions about machine learning:

When you open a textbook or a university syllabus, you'll often be greeted by a laundry list of algorithms. This has fueled the misconception that machine learning is about mastering dozens of algorithms. However, it's much more than that...


Machine learning is a comprehensive approach to solving problems...

...and individual algorithms are only one piece of the puzzle. The rest of the puzzle is how you apply them the right way.

 
2. WTF is machine learning?

Machine learning is the practice of teaching computers how to learn patterns from data, often for making decisions or predictions.
For true machine learning, the computer must be able to learn patterns that it's not explicitly programmed to identify.

Example: the curious child

A young child is playing at home... And he sees a candle! He cautiously waddles over.
Out of curiosity, he sticks his hand over the candle flame.
"Ouch!," he yells, as he yanks his hand back.
"Hmm... that red and bright thing really hurts!"
Two days later, he's playing in the kitchen... And he sees a stove-top! Again, he cautiously waddles over.
He's curious again, and he's thinking about sticking his hand over it.
Suddenly, he notices that it's red and bright!
"Ahh..." he thinks to himself, "not today!"
He remembers that red and bright means pain, and he ignores the stove top.
Behold... machine learning!
Stove Burner

#thanksmachinelearning
To be clear, it's only machine learning because the child learned patterns from the candle.

He learned that the pattern of "red and bright means pain."
On the other hand, if he ignored the stove-top simply because his parents warned him, that'd be "explicit programming" instead of machine learning.
 

3. Terminology

Let's just make sure we have a shared language going forward:
Model - a set of patterns learned from data.
Algorithm - a specific ML process used to train a model.
Training data - the dataset from which the algorithm learns the model.
Test data - a new dataset for reliably evaluating model performance.
Features - Variables (columns) in the dataset used to train the model.
Target variable - A specific variable you're trying to predict.
Observations - Data points (rows) in the dataset.
Image
For example, let's say you have a dataset of 150 primary school students, and you wish to predict their Height based on their Age, Gender, and Weight...
You have 150 observations...
1 target variable (Height)...
3 features (Age, Gender, Weight)...
You might then separate your dataset into two subsets:
Set of 120 used to train several models (training set)
Set of 30 used to pick the best model (test set)
By the way, we'll explain why separate training and test sets are super important in Lesson 6: Model Training.


4. Types of machine learning tasks

Academic machine learning starts with and focuses on individual algorithms. However, in applied machine learning, you should first pick the right machine learning task for the job.
A task is a specific objective for your algorithms.
Algorithms can be swapped in and out, as long as you pick the right task.
In fact, you should always try multiple algorithms because you most likely won't know which one will perform best for your dataset.
The two most common categories of tasks are supervised learning and unsupervised learning.

Supervised learning

Supervised learning includes tasks for "labeled" data (i.e. you have a target variable).
In practice, it's often used as an advanced form of predictive modeling.
Each observation must be labeled with a "correct answer."
Only then can you build a predictive model because you must tell the algorithm what's "correct" while training it (hence, "supervising" it).
Regression is the task for modeling continuous target variables.
Classification is the task for modeling categorical (a.k.a. "class") target variables.
Image

Unsupervised learning

Unsupervised learning includes tasks for "unlabeled" data (i.e. you do not have a target variable).
In practice, it's often used either as a form of automated data analysis or automated signal extraction.
Unlabeled data has no predetermined "correct answer."
You'll allow the algorithm to directly learn patterns from the data (without "supervision").
Clustering is the most common unsupervised learning task, and it's for finding groups within your data.
​Image

There are other tasks as well, but the concepts you'll learn in this course will be widely applicable.
 


5. The three elements of great machine learning

There are 3 essential elements for consistently getting great results.

#1: A skilled chef (human guidance)

First, even though we are "teaching computers to learn on their own," human guidance plays a huge role.
As you'll see, you'll need to make dozens of decisions along the way.
In fact, the very first major decision is how to road-map your project for guaranteed success.
Don't worry, we'll share our step-by-step blueprint with you.

#2: Fresh ingredients (clean, relevant data)

The second essential element is the quality of your data.
Garbage In = Garbage Out, no matter which algorithms you use.
Professional data scientists spend most their time understanding the data, cleaning it, and engineering new features.
While that sounds open-ended, you'll get our proven frameworks that you can always rely on as starting points.
 
#3: Don't overcook it (avoid overfitting)

One of the most dangerous pitfalls in machine learning is overfitting. An overfit model has "memorized" the noise in the training set, instead of learning the true underlying patterns.
An overfit model within a hedge fund can cost millions of dollars in losses.
An overfit model within a hospital can costs thousands of lives.
For most applications, the stakes won't be quite that high, but overfitting is still the single largest mistake you must avoid.
We'll teach you strategies for preventing overfitting by (A) choosing the right algorithms and (B) tuning them correctly.
 
6. The core workflow

Our machine learning blueprint is designed around those 3 essential elements.

There are five core steps:
Exploratory Analysis is for "getting to know" the data, and it should be quick, efficient, and decisive.
Data Cleaning can make or break your project. Better data beats fancier algorithms.
Feature Engineering allows you to help your algorithms "focus" on what's important.
Algorithm Selection is about choosing the best algorithms without wasting your time.
Model Training correctly is vital, but pretty formulaic once you've done the first 4 steps.
Image

Of course, there are other situational steps as well.
Project Scoping properly can save you many headaches.
Data Wrangling may be required to restructure your dataset.
Pre-Processing can improve performance by transforming features.
Ensembling can boost performance by combining multiple models.
However, for this course, we're going to focus on the 5 core steps. The other ones slot in once you understand the core workflow.

Key takeaway: Machine learning should not be haphazard and piecemeal. It should be be systematic and organized. Furthermore, even if you forget everything else taught in this course, please remember: 'Better data beats fancier algorithms' - this insight will serve you well.


7. Conclusion

Alright, that was a lot for day 1!

Here's a quick pop quiz to make sure you got everything:
What are the 5 core steps of the machine learning workflow?
When the curious child learned that "red and bright means pain," what did he learn?
(A) An algorithm.
(B) A pattern.
(C) A model.
(D) Both (B) and (C).
(E) None of the above.
In the example of the curious child, what was the training data? What was the test data?
In your own words, describe the 3 essential elements of great machine learning.
We'll review the answers tomorrow. In addition, we'll be delving into Exploratory Analysis, and exactly what to look for.

In the meantime, if you have any questions or comments, feel free to hit 'reply' and shoot us a note. We respond to every email.


~ EliteDataScience






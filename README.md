# NLP - Classification of Dadjokes and Antijokes

## Problem statement
This projects will examine two datasets of jokes from r/dadjokes and r/antijokes.

**What is a Dadjoke and Antijoke?**

Firstly, a dadjoke is:
- A **wholesome short joke typically told by fathers with a punchline that is often an obvious or predictable pun or play on words**.
    - Q1: My wife tells me I have 2 major faults,
    - A1: I don't listen - and something else.
    - Q2: I recently decided to learn sign language...
    - A2: So that I can tell jokes nobody has ever heard.
- Dadjokes are usually **inoffensive, told with sincere humorous intent and more accepted by the public**.


On the other hand, an antijoke is:
-  A **joke that starts like a standard joke, but then turns out not to be a joke at all**. The **surprise element** thus becoming the joke.
    - Q1: If this post reaches 1000 upvotes.
    - A1: That means at least 1000 people upvoted.
    - Q2: Ok, so a Muslim, an Atheist, and a Jew walk into a bar...
    - A2: And they have a really nice time.
- Antijokes may be **more offensive, and the format is not as widely accepted by the public** as Dadjokes.

**Aim of Project**

This project aims to assist **any services that need their employee to curate and pick dadjokes** from a large number of jokes containing both dadjokes and antijokes. Such services include magazines, newspapers (that has a jokes column) or applications that sent their subscriber jokes on a daily basis.

The aim of this project will be to:
1. **Create a model that classifies if a joke is a dadjoke** (or an antijoke)
2. Find out what **words are the most deterministic of dadjokes and antijokes**

In order to achieve the aim specified above, I will train multiple classification models on the two jokes dataset. I will look at the model statistics and ensure that it is not overfitting to the training data while producing the best model to tell dadjokes from antijokes.


## Data Information
This projects makes use of two dataset scrapped from reddit.

1. The first dataset consist of records scrapped from the **r/antijokes subreddit**. It contains information for 942 entries/records.

2. The second dataset consist of records scrapped from the **r/dadjokes subreddit**. It contains information for 1528 entries/records.

**Data Dictionary**

The data dictionary for both datasets are the same, as follow.

|Feature|Type|Description|
|---|---|---|
|subreddit|object|The subreddit from which the record originated (Label)|
|original_title|object|The title of the record|
|original_post|object|The post of the record|
|url|object|The URL of the record (for reference)|


## Conclusion
**Model Statistics**

With the **final precision score of 0.658**, this is higher than the baseline model precision of 0.5 by 0.158. This translate to about **24% reduction in time spent** by employee picking dadjokes from a number of jokes containing both dadjokes and antijokes.

The model has a higher recall score of 0.717, which means that the model is in fact better at identifying antijokes than identifying dadjokes. This could be because the antijokes have more "identifiable" words as compared to dadjokes.


**Top 20 Words**

Looking at the list of changes in odds of  top 20 words, it becomes apparent why the precision is quite low. Among the top 20 words, **only 4 of the words are identifiers of dadjokes** (with a change in odds above 1), while 16 of them are identifiers of antijokes (with a change in odds below 1).

Surprisingly, the **identifying words for dadjokes are relatively common words** such as: "my", "got", "it", "but". Although, these words had a higher frequency evident from the top N words, I did not expect them to be strong predictors of dadjokes.

On the other hand, **common words like "and", "what", "man", "you", "the" were strong predictors for antijokes**, this was not expected either. However, as expected, jokes with **"walked in a bar" were strong predictors of antijokes**. This was evident from the EDA portion as well.


**Conclusion & Limitations**

This project has obtained a classification model that **performs better than baseline prediction** for the classifying between dadjokes and antijokes.

However, the classification model **does not have very high precision** as:
1. both of type of jokes use **similar common English words** (not much specialized words)
2. whether a joke is a dadjoke or antijoke is **very context based**, which this model is unable to comprehend

To improve the model, **more sophisticated techniques that tries to explore the context of the jokes could be used**, such as POS tagging.

Furthermore, the amount of records looked at by this project is only about 650 per dataset. With this number of records, it is **easy for the frequency of words to be affected by 1 or 2 entries**.
- i.e. High frequency of "step step" from 1 single entry in bi-gram
If more entries can be obtained for both dataset, it will help to improve the model to generalize better.

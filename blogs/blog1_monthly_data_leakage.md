# When a 0.91 ROC-AUC Wasn't the Whole Story

While building a cost-overrun prediction model for infrastructure projects, I initially achieved a **ROC-AUC of 0.909**.

It looked great. Then I checked the dataset more carefully.

## The Problem

The dataset contained **7,590 monthly records**, but only **2,074 unique projects**.

A single project could appear multiple times:

- Project A - April
- Project A - May
- Project A - June
- Project A - July

With a normal random train-test split, observations from the **same project could end up in both training and testing data**.

This creates a form of **data leakage**.

The model had already seen information about a project during training, so testing it on another monthly record of that same project was not a true test of generalization.

## The Fix

Instead of splitting individual rows randomly, we split the data **by project**.

This resulted in:

- **1,659 projects** for training
- **415 projects** for testing

Now, a project could exist in either training or testing, but not both.

## The Result

The ROC-AUC changed from:

**0.909 → 0.832**

At first, a lower score might look bad.

But this is actually a better result because the evaluation is now more realistic. We are testing whether the model can generalize to **projects it has never seen before**.

## The Lesson

A high ML score does not always mean a good model.

Before trusting a metric, understand:

- What does one row represent?
- Are observations independent?
- Can the same entity appear in train and test?
- Does the validation setup match the real-world use case?

In our case, the biggest improvement wasn't a new algorithm.

It was simply **understanding the data correctly**.

The next challenge is **temporal validation**, because our real goal is to use a project's current state to predict its **future cost-overrun risk**.

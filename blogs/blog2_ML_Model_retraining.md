# From Baseline Model to Monthly Project Data: What We Learned About Data Leakage

After training our first model on **1,981 unique project records**, we successfully built our baseline ML model.

After that, we decided to go one step further.

Instead of using only one record per project, we wanted to use the **monthly reports** of each project. This gave us **7,590 monthly records from 2,074 unique projects**.

## The Problem

Initially, we used a normal **80/20 random train-test split**.

But because the same project appears in multiple months, a random split could put some monthly records of the same project into both the training and testing datasets.

For example:

- Project A - April → Training
- Project A - May → Training
- Project A - June → Testing

This can lead to **data leakage** and give us an overly optimistic model evaluation.

## How We Solved It

We changed the splitting strategy and grouped the data using the **project code**.

This ensured that the same project could not appear in both training and testing datasets.

The result was:

- **1,659 projects for training**
- **415 projects for testing**

This gave us a more reliable evaluation of how the model performs on projects it has not seen before.

## Two Models, Two Purposes

We now have two important stages in our ML process:

### 1. Baseline Model

Train the model using **unique project-level data**.

This gives us a simple and stable baseline for comparison.

### 2. Monthly Model

Train the model using **monthly project reports**.

This allows the model to learn from how a project changes over time and can potentially provide better early-warning predictions.

The monthly model requires a different validation approach because the same project appears multiple times.

## Why Keep Both?

The baseline model gives us a reference point.

The monthly model gives us a more detailed view of project progress over time.

Keeping both allows us to compare:

**Unique Project Model → Monthly Project Model**

Instead of replacing the baseline, the monthly model becomes a separate stage of experimentation and improvement.

## The Next Step

Our next focus is to properly validate the monthly model using **time-aware data**, so that past project information is used to predict future project risk.

This is an important step toward building a model that can actually support **early warning for cost overruns**.

# Student Performance Prediction

This is my project for class. The goal is to predict if a student will **Pass** or **Fail** based on things like study hours, attendance, and parental education.

This is a **classification** project. That means the answer is a category (Pass or Fail), not a number.

## Why I picked this project

- The dataset is simple and easy to understand
- It uses classification, which is different from my last project (that one was regression)
- Education data is something everyone can relate to
- The dataset is small, free, and easy to get on Kaggle

## What the project does

The code looks at student information like:

- Hours studied
- Attendance
- Sleep hours
- Previous scores
- Parental education level
- Family income
- Tutoring sessions
- and a few other things

Then it predicts if that student will Pass or Fail.

## Dataset

I used the **Student Performance Factors** dataset from Kaggle.

Link: https://www.kaggle.com/datasets/lainguyn123/student-performance-factors

The dataset does not come with a Pass/Fail column. It only has an `Exam_Score` column (0 to 100). So I made my own rule:

- If `Exam_Score >= 60` then the student gets **Pass**
- If `Exam_Score < 60` then the student gets **Fail**

This is how I turned the score into a Pass/Fail label for classification.

The dataset is downloaded automatically in the code using `kagglehub`, so you don't need to manually download any CSV file.

## Models I used

I tried 3 different classification models to see which one works best:

1. **Decision Tree** – asks yes/no questions about the data to split it into groups, like "Is attendance more than 80%?"
2. **K-Nearest Neighbors (KNN)** – looks at the 5 most similar students and guesses based on what most of them did (Pass or Fail)
3. **Random Forest** – builds many decision trees and lets them all vote on the final answer

## How the code works (step by step)

1. Download the dataset using kagglehub
2. Check for missing values and drop empty rows
3. Create the Pass/Fail column from Exam_Score
4. Change text columns (like "High School", "Low", "Yes") into numbers using LabelEncoder
5. Pick the input features (drop Exam_Score and Result, since those would be cheating)
6. Split the data into 80% training and 20% testing
7. Train the Decision Tree model and check its accuracy
8. Train the KNN model and check its accuracy
9. Train the Random Forest model and check its accuracy
10. Compare all 3 models in a table
11. Make 3 charts:
    - Bar chart comparing accuracy of all models
    - Confusion matrix for the best model
    - Feature importance chart (which feature matters most)

## How to run this project

1. Make sure you have Python installed
2. Install the libraries needed:

```
pip install pandas numpy matplotlib scikit-learn kagglehub
```

3. Run the script:

```
python student_performance_prediction.py
```

4. The first time you run it, kagglehub may ask you to log in to Kaggle. You need a free Kaggle account for this.

5. After it finishes running, you will see the results printed in the terminal, and 3 PNG chart images will be saved in the same folder.

## Files in this repo

| File | What it is |
|---|---|
| `student_performance_prediction.py` | Main code file with all 3 models |
| `model_accuracy_comparison.png` | Bar chart comparing the 3 models |
| `confusion_matrix_random_forest.png` | Confusion matrix for Random Forest |
| `feature_importance.png` | Chart showing which feature matters most |
| `README.md` | This file |

## What I learned

- How to turn a regression-style dataset (exam scores) into a classification problem (Pass/Fail) by setting a pass mark
- How to clean data and handle missing values
- How LabelEncoder turns text into numbers so models can use it
- How Decision Tree, KNN, and Random Forest are different from each other
- How to compare models using accuracy and confusion matrix
- Random Forest usually does better than a single Decision Tree because it combines many trees together

## Possible improvements (future work)

- Try a different pass mark, like 70 instead of 60, since most students in this dataset score pretty high
- Try other models like Logistic Regression or SVM
- Use cross validation instead of just one train/test split
- Balance the dataset better, since there are way more "Pass" students than "Fail" students

## Tools used

- Python
- pandas
- numpy
- matplotlib
- scikit-learn
- kagglehub

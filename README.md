
<h1 align="center">
  <a>Assignment 1 – Linear Regression</a>
</h1>
<h3 align="center">
  <a>Machine Learning @ Uni-Konstanz 2020</a>
</h3>

## Idea 📓

- Code a simple (multiple) linear regression model.

- Train the linear model (estimate parameters) on a given training dataset.

- Test the trained model on a given testing dataset.

- Plot the results for training and testing stages for various losses.

- Implement predictor and model selection with the help of LOOCV error used as a scoring funtion.

## Data 📦

- [mtcars dataset]: The data was extracted from the 1974 Motor Trend US magazine, and comprises fuel consumption and 10 aspects of automobile design and performance for 32 automobiles (1973–74 models). See description of variables at: https://stat.ethz.ch/R-manual/R-patched/library/datasets/html/mtcars.html
Taken from: Henderson and Velleman (1981), Building multiple regression models interactively. **Biometrics**, 37, 391–411.
The dataset is already provided in `mtcars.csv`.

## Tasks 📝

#### Preliminaries

- Load the dataset from `mtcars.csv`.

- Write a function

	```python
	train_sample, test_sample = split_sample(sample, train_size, permute)
	```

	that splits the sample into a *training sample* and a *test sample*.

	- `train_size` is a number between 0 and 1 that decides which percentage of the sample is to be used *for training*.

	- `permute` is a boolean value such that if `True` then the sample is *randomly permuted* before being split, if `False` then no permutation is used. Be careful about permuting pairs of input and target observations together.

#### Regression task: linear hypothesis classes

***

_In the following tasks you are asked to use *directly* the **normal equations**_ (see ***Chapter 3***) _to carry out some simple regression tasks on the mtcars dataset._

_At each round of **multiple** regression exercises center and standardize covariates._

_Implement the L1, L2, Huber losses_ (see ***Chapter 2***) _in three different functions (`loss_l1`, `loss_l2`, `loss_huber`). For all the losses the implemented functions compute the mean losses (empirical error) once evaluated on more than one observation. For the Huber loss write a function `loss_huber(Ŷ, Y, δ)` that computes this loss (average or mean loss when Ŷ and Y contain more than one observation) for a given value of hyperparameter δ_.


***

1. Construct a **simple linear regression model** that predicts the fuel consumption (mpg) of a given car provided the  **gross horsepower**.

  	- Use 90% of the sample length for the total training set and 10% for the testing set.

  	- Compute the training error (in-sample error, empirical error on a training set) using the implemented losses. Compute the Huber loss for the standard value of hyperparameter δ (look it up in the literature).

	- Compute the testing error (out-of-sample error, empirical error on a testing set) using the implemented losses. Compute the Huber loss for the standard value of hyperparameter δ (look it up in the literature).

	- Compute the LOOCV error and the k-fold cross-validation error (take k = 10, see the references in the beginning of Chapters 2 and 3) for L1, L2, and Huber loss. The LOOCV error for the case of L2 loss admits a shortcut expression (see Chapter 3).

  	- Plot:

  		- Predicted fuel consumption values (regression line), predicted data points and ground-truth data points for the **training data**.

  		- Predicted fuel consumption values (regression line) and ground-truth data points for the **test data**.

2. Construct an example of **multiple regression** using as predictors **gross horsepower** and **weight**.

  	- Compute the training (in-sample) and testing (out-of-sample) performance of such model using implemented losses.

  	- Plot *in 3D* the predicted fuel consumption values (regression plane) and the actual ones.


3. Implement predictor filtering for all possible predictors, make conclusions. Consider only the first 6 predictors (d = 6) in the dataset (cyl, disp, hp, drat, wt, qsec).

4. Implement stepwise forward subset selection for all the d predictors. Plot the associated training errors for all the best resulting models with k predictors, k=0,1,...,d. Use the nested cross-validation in order to obtain the estimate of the statistical risk commited by the models and to select the best model.

5. Compute the testing error for the **last 10%** of the dataset reserved as test data associated to the best model obtained with forward subset selection in the previous step. Compare the obtained testing error to the testing errors of the setups in part (1) and (2).

## Notes ⚠️

**Mind the normalization when you do the cross-validation**.

**Write your code in the `homework.py` file**. All the implementations should be in appropriate functions. In the function `main` only show and explain the answers to all tasks by calling the functions (keep other code to a minimum). Make it absolutely clear in the comments or via printing where the answer to each task is.

You may create auxiliary modules but only if absolutely necessary. Please keep your code as simple as possible.

**Good programming rules apply**:
- Use meaningful variable names.
- Comply with PEP8 or another reasonable style guide.
- Keep your code tidy.
- Add a minimum of comments (if you deem them necessary) and if required in the task.

<br>

***Have a good start!***

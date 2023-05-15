# Python_WrapperMethods

<h1>Wrapper Methods</h1>

In this project I analyzed data from a survey conducted by Fabio Mendoza Palechor and Alexis de la Hoz Manotas that asked people about their eating habits and weight. The data was obtained from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Estimation+of+obesity+levels+based+on+eating+habits+and+physical+condition+). Categorical variables were changed to numerical ones in order to facilitate analysis.

First, I fit a logistic regression model to try to predict whether survey respondents are obese based on their answers to questions in the survey. After that, I used three different wrapper methods to choose a smaller feature subset.

I used sequential forward selection, sequential backward floating selection, and recursive feature elimination. After implementing each wrapper method, I evaluated the model accuracy on the resulting smaller feature subsets and compare that with the model accuracy using all available features.

<h2>Evaluating a Logistic Regression Model</h2>

<h3>Step 1</h3>

The data set obesity contains 18 predictor variables. Here’s a brief description of them.
<ul>
    <li>Gender is 1 if a respondent is male and 0 if a respondent is female.</li>
    <li>Age is a respondent’s age in years.</li>
    <li>family_history_with_overweight is 1 if a respondent has family member who is or was overweight, 0 if not.</li>
    <li>FAVC is 1 if a respondent eats high caloric food frequently, 0 if not.</li>
    <li>FCVC is 1 if a respondent usually eats vegetables in their meals, 0 if not.</li>
    <li>NCP represents how many main meals a respondent has daily (0 for 1-2 meals, 1 for 3 meals, and 2 for more than 3 meals).</li>
    <li>CAEC represents how much food a respondent eats between meals on a scale of 0 to 3.</li>
    <li>SMOKE is 1 if a respondent smokes, 0 if not.</li>
    <li>CH2O represents how much water a respondent drinks on a scale of 0 to 2.</li>
    <li>SCC is 1 if a respondent monitors their caloric intake, 0 if not.</li>
    <li>FAF represents how much physical activity a respondent does on a scale of 0 to 3.</li>
    <li>TUE represents how much time a respondent spends looking at devices with screens on a scale of 0 to 2.</li>
    <li>CALC represents how often a respondent drinks alcohol on a scale of 0 to 3.</li>
    <li>Automobile, Bike, Motorbike, Public_Transportation, and Walking indicate a respondent’s primary mode of transportation. Their primary mode of transportation is indicated by a 1 and the other columns will contain a 0.</li>
</ul>

The outcome variable, NObeyesdad, is a 1 if a patient is obese and a 0 if not.

<h3>Step 2</h3>

In order to use a logistic regression model, you’ll need to split the data into two parts: the predictor variables and an outcome variable. Do this by splitting the data into a DataFrame of predictor variables called X and a Series of outcome variables y.

<h3>Step 3</h3>

Create a logistic regression model called lr. Include the parameter max_iter=100 to make sure that the model will converge when you try to fit it.

<h3>Step 4</h3>

Use the .fit() method on lr to fit the model to X and y.

<h3>Step 5</h3>

A model’s accuracy is the proportion of classes that the model correctly predicts. is Compute and print the accuracy of lr by using the .score() method. What percentage of respondents did the model correctly predict as being either obese or not obese? 

<h4>0.7655139744197063</h4>

<h2>Sequential Forward Selection</h2>

<h3>Step 6</h3>


Now that you’ve created a logistic regression model and evaluated its performance, you’re ready to do some feature selection.

Create a sequential forward selection model called sfs.
<ul>
    <li>Be sure to set the estimator parameter to lr and set the forward and floating parameters to the appropriate values.</li>
    <li>Also use the parameters k_features=9, scoring='accuracy', and cv=0.</li>
</ul>

<h3>Step 7</h3>

Use the .fit() method on sfs to fit the model to X and y. This step will take some time (not more than a minute) to run.

<h3>Step 8</h3>

Now that you’ve run the sequential forward selection algorithm on the logistic regression model with X and y you can see what features were chosen and check the model accuracy on the smaller feature set. Print sfs.subsets_[9] to inspect the results of sequential forward selection.

<h3>Step 9</h3>

Use the dictionary sfs.subsets_[9] to print a tuple of chosen feature names. Then use it to print the accuracy of the model after doing sequential forward selection. How does this compare to the model’s accuracy on all available features? 

<h4>0.7835149218379914</h4>
This is a little less than 2 percent higher than the model's accuracy

<h3>Step 10</h3>

It can be helpful to visualize the results of sequential forward selection and see how accuracy is affected as each feature is added. Use the code plot_sfs(sfs.get_metric_dict()) to plot the model accuracy as a function of the number of features used. Make sure to show your plot as well.

<h2>Sequential Backward Selection</h2>

<h3>Step 11</h3>

Before completing this task group, you should comment out all the code you wrote for the previous task group (Sequential Forward Selection). Your code will take a long time to run and this will ensure that the learning environment won’t time out.
Sequential forward selection was able to find a feature subset that performed marginally better than the full feature set. Let’s use a different sequential method and see how it compares.
Create a sequential backward selection model called sbs.
<ul>
    <li>Be sure to set the estimator parameter to lr and set the forward and floating parameters to the appropriate values.</li>
    <li>Also use the parameters k_features=7, scoring='accuracy', and cv=0.</li>
</ul>
<h3>Step 12</h3>

Use the .fit() method on sbs to fit the model to X and y.

<h3>Step 13</h3>

Now that you’ve run the sequential backward selection algorithm on the logistic regression model with X and y you can see what features were chosen and check the model accuracy on the smaller feature set. Print sbs.subsets_[7] to inspect the results of sequential backward selection.

<h3>Step 14</h3>

Use the dictionary sbs.subsets_[7] to print a tuple of chosen feature names. Then use it to print the accuracy of the model after doing sequential backward selection. How does this compare to the model’s accuracy on all available features? 

<h4>0.7820937944102321</h4>
The result is only slightly lower than the SFS. 

<h3>Step 15</h3>

You can visualize the results of sequential backward floating selection just as you did with sequential forward selection. Use the code plot_sfs(sbs.get_metric_dict()) to plot the model accuracy as a function of the number of features used. Be sure to include plt.clf() in order to clear the previous graph before trying to show the new graph.

<h2>Recursive Feature Elimination</h2>

<h3>Step 16</h3>


Before completing this task group, you should uncomment all the code you wrote for the previous task groups (Sequential Forward Selection and Sequential Backward Selection). Your code will take a long time to run and this will ensure that the learning environment won’t time out.
So far you’ve tried two different sequential feature selection methods. Let’s try one more: recursive feature elimination. First you’ll standardize the data, then you’ll fit the RFE model and inspect the results.
At a later step of this project, you’ll need to be able to access feature names. Enter the code features = X.columns for use later.

<h3>Step 17</h3>

Before doing applying recursive feature elimination it is necessary to standardize the data. Standardize X and save it as a DataFrame by creating a StandardScaler() object and using the .fit_transform() method.

<h3>Step 18</h3>

Create an RFE() object that selects 8 features. Be sure to set the estimator parameter to lr.

<h3>Step 19</h3>

Fit the recursive feature elimination model to X and y.

<h3>Step 20</h3>

Now that you’ve fit the RFE model you can evaluate the results. Create a list of chosen feature names and call it rfe_features. You can use a list comprehension and filter the features in zip(features, rfe.support_) based on whether their support is True (meaning the model kept them) or False (meaning the model eliminated them).

<h3>Step 21</h3>

Use the .score() method on rfe and print the model accuracy after doing recursive feature elimination. How does this compare to the model’s accuracy on all available features?

<h4>0.757934628138323</h4>
This is the lowest accuracy score I've seen since beginging. 
# Python_WrapperMethods

<h1>Wrapper Methods</h1>

In this project I analyzed data from a survey conducted by Fabio Mendoza Palechor and Alexis de la Hoz Manotas that asked people about their eating habits and weight. The data was obtained from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Estimation+of+obesity+levels+based+on+eating+habits+and+physical+condition+). Categorical variables were changed to numerical ones in order to facilitate analysis.

First, I fit a logistic regression model to try to predict whether survey respondents are obese based on their answers to questions in the survey. After that, I used three different wrapper methods to choose a smaller feature subset.

I used sequential forward selection, sequential backward floating selection, and recursive feature elimination. After implementing each wrapper method, I evaluated the model accuracy on the resulting smaller feature subsets and compare that with the model accuracy using all available features.

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
Build your 1st Deep Learning model using Keras Sequential

This is an application of Keras Sequential Neural Network model model on the Churn Modelling data set. 
Objective was to develop a tutorial that covers all the steps from the initial setup of the data to training the model and finally testing the model on the new dataset. 
At every stage I have created functions or used loops to help the user understand how to use them and how it can help in trimming down your code base. It also helps in scalability of your model.
Missing features in new data- model was trained on a larger sample, during the pre-processing encoding stage the object feature classes get transformed to a new feature space. It may happen that the new dataset might be missing the object classes and hence the required features post encoding. Steps written at testing stage help in overcoming that scenario.
The entire model can be used as a learning step to develop a deep Learning ML model using all the good stuffs from Scikit Learn like Pipelines, Feature extraction and Hyper parameter tuning.
There is no hardcoding involved in the entire script, hence you can deploy this entire script on any dataset with classification problem.

Steps involved

1) EDA- Exploratory data analysis & cleaning

Applications:
a) Drop columns and rows with NA
b) Function to- Convert all features with unique values less than 5 to object
c) Create a function to drop a variable if it is object but nunique>20
d) Create a function to select only numerical variables
e) Create a function to select only categorical variables

2) Pre-processing transformation of numerical and categorical data
Applications- 
a) Numerical transformation- SimpleImputer and StandardScaler
b) Categorical transformation- OneHotEncoder
c) Bundle preprocessing of numerical and categorical data using ColumnTransformer
d) Transform the X_train using the preprocessor pipeline
e) How to convert the numpy array to pandas Dataframe
f) How to parse out the column info from the transformed data using ColumnTransformer
g) Loop to rename the Categorical & numerical Columns



3) Feature Selection
Applications:
a) L1 regularization using LinearSVC to select the important features
b) How to parse out the list of selected features post fitting the LinearSVC using SelectFromModel
  b.1) How to get the position of selected features in form of list
  b.2) subset the X_df dataset using the above list positions to select only the important features
c) Create a function to pass the count of input layers neurons to the Keras Sequential Neural Net model

4) Keras- Sequential model implementation
a) Setup and compile the model
b) Define param_grid to pass it to GridSearchCV for Hyperparameter tuning
c) Pass your Neural network model using GridSearchCV
d) Print the best parameters and scores
e) print the Cross-validation scores across param_grid parameters like epochs, batch, Optimizer etc)

Now the below step is crucial if you are new to the ML space, most tutorials will help you reach out to the train and test evaluation, but remember we have done lot of pre-processing above to transform our train data. The shape of the data now passed on to the NN model is totally different from actual shape of the original data.

This is where the steps we did earlier to parse out the feature names for transformed data at the ColumnTransformer and Feature Extraction stage will be helpful. 
first, I list down the test pre-process steps and then finally we create a function to pre-process and predict our new data with one line of code

5) Preprocess the test dataset
a) This involves the same process we have done for training set, there could be a possibility that the new data might be missing the features that our ML model is trained on.
Here we will see how the reindex function with fill_value=0 comes in handy to reshape the data
b) Predict the Y churn (0,1) on the X_test_processed)
c) Generate the classification matrix report

6) Create a function to pre-process and predict on test data
This will help us to use the function in future using one line of code to pre-process and predict on new data.

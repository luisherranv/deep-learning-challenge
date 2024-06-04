# Overview 

The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. I have created a neural network binary classifier model that can predict whether applicants will be successful if funded by Alphabet Soup.

The dataset contains more than 34,000 organizations and the metadata contained is structured as follows:

- EIN and NAME—Identification columns
- APPLICATION_TYPE—Alphabet Soup application type
- AFFILIATION—Affiliated sector of industry
- CLASSIFICATION—Government organization classification
- USE_CASE—Use case for funding
- ORGANIZATION—Organization type
- STATUS—Active status
- INCOME_AMT—Income classification
- SPECIAL_CONSIDERATIONS—Special considerations for application
- ASK_AMT—Funding amount requested
- IS_SUCCESSFUL—Was the money used effectively

# Results
## Data Preprocessing
**What variable(s) are the target(s) for your model?**
The target variable is `IS_SUCCESSFUL` which is whether the money was effectively used or not. The output is 1 "YES' and 0 "NO"
<br />
<br />
**What variable(s) are the features for your model?**
For the final optimized model the variables are the 
1. Company Name
2. Type of application
3. Affiliation
4. Classification
5. Use-case type
6. Organization
7. Status
8. Income ammount
9. Any special considerations
10. Ammount requested

What variable(s) should be removed from the input data because they are neither targets nor features?
The EIN was removed from the data, as well as the name, however adding and binning the name was in the model optimization so it was added to increase accuracy.
<br />
<br />
<br />

## Compiling, Training, and Evaluating the Model
**How many neurons, layers, and activation functions did you select for your neural network model, and why?**
Originally, only 3 hidden layes plus the output layer were added. Rectified Linear Unit (RELU) activation functions were used as first intent. The model was trained and fit, with epochs=50.
![image](https://github.com/luisherranv/deep-learning-challenge/assets/150373234/8aeb33a8-4d39-4576-9b34-9a0f1d26fa66)
<br />
<br />
**Were you able to achieve the target model performance?**
This original model was not sufficient, with accuracy at 72%, and needed to be optimized.
![image](https://github.com/luisherranv/deep-learning-challenge/assets/150373234/d31e6a09-d54e-4fd3-ab8b-067cc680db1a)
<br />
<br />
**What steps did you take in your attempts to increase model performance?**
In order to optimized this model, other features were binned, as seen below. Note that binning and cleaning had already been done for the original model for `APPLICATION_TYPE` and `CLASSIFICATION`.
<br />
In the optimized model the first step was to also bin `AFFILIATION`. Since most of the values were taken by Independet and Company Sponsored projects, the remaining ones were labeled as 'other'.
![image](https://github.com/luisherranv/deep-learning-challenge/assets/150373234/05f6f170-c46d-48c6-bd51-b32ffefcded4)
<br />
Subsequently `INCOME_AMT` was also binned, to group any incomes above 1 million, since they had many features and were not as significant as lower incomes.
![image](https://github.com/luisherranv/deep-learning-challenge/assets/150373234/3da8c8b8-4481-4313-a2b3-481af8146614)
<br />
Also, the number of neurons and layers were increased (4 hidden layers and 1 output layer) and activation funtions were changed to Exponential Linear Unit (ELU). 
![image](https://github.com/luisherranv/deep-learning-challenge/assets/150373234/77416591-f7d2-4a4a-8d43-7a74971ddc79)
<br />
The accuracy was still not above 75%, therefore a final binning was done. The NAME feature was added back to the data set and it was binned so that names that are repeated less than 100 times will be just pooled as 'Other'. 
![image](https://github.com/luisherranv/deep-learning-challenge/assets/150373234/e4d9f592-be8c-4749-84e7-a46d961ef98e)
![image](https://github.com/luisherranv/deep-learning-challenge/assets/150373234/842b85dd-8157-460b-9469-d46e8ec6c33c)
<br />
Finally, the optimized model was trained and fit, with epochs=100, and an accuracy of **75.12%** was achieved!
![image](https://github.com/luisherranv/deep-learning-challenge/assets/150373234/7c643a9d-1e8e-4f31-9c4a-1a9477bfe6e3)
<br />
Both models, and notebooks, can be found in the repository:
<br />
**Optimized Files**
<br />
[AlphabetSoupCharityOptimized H5 Model](https://github.com/luisherranv/deep-learning-challenge/blob/main/AlphabetSoupCharityOptimized.h5)
<br />
[DeepLearningModel_Optimized Notebook](https://github.com/luisherranv/deep-learning-challenge/blob/main/DeepLearningModel_Optimized.ipynb)
<br />
**Original Files**
<br />
[AlphabetSoupCharity.h5](https://github.com/luisherranv/deep-learning-challenge/blob/main/AlphabetSoupCharity.h5)
<br />
[DeepLearningModel Notebook](https://github.com/luisherranv/deep-learning-challenge/blob/main/DeepLearningModel.ipynb)
<br />
<br />
<br />
# Summary
Overall, this model can be used to predict wether a project will be successful or not, with 75% accuracy. Potentially, looking into all other posible binary classification models such as KNN and Decision tress can be used, as potentially neural networks may cause overfitting for simpler and smaller datasets.

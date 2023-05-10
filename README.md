# Neural Network Report

**Overview:** 

The purpose of this analysis is to provide a tool to Alphabet Soup that can help it select the applicants for funding. I will be creating a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup using csv data from past funding recipients. 

**Results:**

**Data Preprocessing**

I immediately identified 2 non-beneficial ID columns in the raw data - "EIN" and "NAME" - and dropped them from the dataframe.
Target variable for the model is "IS_SUCCESSFUL"
Feature variables for the model is the rest of the dataframe, dropping the "IS_SUCCESSFUL" column:

<img width="422" alt="image" src="https://github.com/ltablas/deep-learning-challenge/assets/116695697/eade88d5-6cd9-4195-84f5-030ab99fb259">

**Compiling, Training, and Evaluating the Model**

For the neural network model I opted to keep it simple with 2 hidden layers -- 24 neurons for the first layer - roughly half the number of input dimensions; 12 neurons for the second layer - half the number of the first layer -- and decided to use ReLu as the activation function since it tends to run faster than Sigmoid or Tanh. 

<img width="651" alt="image" src="https://github.com/ltablas/deep-learning-challenge/assets/116695697/e933c914-1f26-4da1-b9aa-db2d0c46d199">

I'm aiming to reach a Target Model Performance of 75% accuracy. Using the 2 hidden layers with ReLu I got close with 73.38% accuracy. 

<img width="461" alt="image" src="https://github.com/ltablas/deep-learning-challenge/assets/116695697/28c4771e-7f05-49fc-b43e-f5223dfccb9e">

Original model has been exported as 'AlphabetSoupCharity.ipynb' and 'AlphabetSoupCharity.h5'.

I will be testing adding more layers or increasing/decreasing number of neurons to see if that might yield better results.

**Data Optimization**

First thing I did was check to see if using an Auto Optimization function could help in quickly identifying the best model. The function tries different activation modes - ReLu, Tahn, and Sigmoid - to see if one performs better than the other with the dataset, and cycles through trying different number of layers and neurons.

<img width="539" alt="image" src="https://github.com/ltablas/deep-learning-challenge/assets/116695697/fced5843-ff4d-4d36-a74a-60c817f64571">

The function was not as successful as I had hoped - the "best model" returned an accuracy rating of 73.27%, performing closely to my original test.

<img width="529" alt="image" src="https://github.com/ltablas/deep-learning-challenge/assets/116695697/9412b382-a75b-4d59-87cd-85ce21010312">

I then tried to change only a few variable at a time - changing the activation mode to Sigmoid and keeping the same number of hidden layers, but increasing the number of neurons to 80 and 30 respectively - to see if activation mode and number of neurons have a positive or negative affect on accuracy.  

<img width="648" alt="image" src="https://github.com/ltablas/deep-learning-challenge/assets/116695697/641fc101-7fee-43f5-b9db-61f1e8719632">

...Unfortunately it did not. Results were slightly worse at 72.64%

<img width="467" alt="image" src="https://github.com/ltablas/deep-learning-challenge/assets/116695697/9c2a1383-22ea-4739-9e5e-8ed8e1fe3458">

For the next test I added a few more hidden layers.

<img width="640" alt="image" src="https://github.com/ltablas/deep-learning-challenge/assets/116695697/57009776-0ee3-46bb-b8ba-36d93f61cd71">

Results were still not better than the original model, acheiving only 73% accuracy:

<img width="460" alt="image" src="https://github.com/ltablas/deep-learning-challenge/assets/116695697/80a65dce-04e6-45e0-9485-d349308e918d">

Results of this test are in the folder called "Optimization Notebook and h5 Test1".

For a last ditch effort at attaining 75% accuracy, I decided to try something different with the data set.

On the final optimization test I decided to increase the cutoff value of the Application bins to 700 and decrease the cutoff value of the Classification bins to 1000 to see if changing the parameters might make a difference. I also switched up the layers, neurons and activation mode with 3 layers (21, 14, and 7 neurons), and back to ReLu activation mode. 

<img width="645" alt="image" src="https://github.com/ltablas/deep-learning-challenge/assets/116695697/a3585e90-163e-46ea-b5ff-458a22d242ef">

All those changes still did nothing to improve accuracy compared to the original. This test model yielded 72.9% accuracy.

<img width="464" alt="image" src="https://github.com/ltablas/deep-learning-challenge/assets/116695697/f53721cb-af7b-46be-a3bf-baf27dd7d1a0">

Second test model is saved in folder "Optimization Notebook and h5 Test2".

**Summary: **
In summary, I was only able to achieve a 73% accuracy rating on average. Not sure what may help yield better results, but with more time, I would probably play around with decreasing number of input variables for higher efficiency, or potentially cleaning the data to scrub out any outliers.


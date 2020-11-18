# Python_Week_12_Exercise

Data set : https://drive.google.com/file/d/1DYJsHSWHq-ff6OAlVa9hN5cjWXE6vcO-/view?usp=sharing

Note: 
This data set is not very neat. For a more 'usual' data set i would sugest doing the exercise in the 12-3-Exercise-Perceptrons notebook instead.

Info about the columns in the data set:
   1. Age of patient at time of operation (numerical)
   2. Patient's year of operation (year - 1900, numerical)
   3. Number of positive axillary nodes detected (numerical)*
   4. Survival status (class attribute)
         1 = the patient survived 5 years or longer
         2 = the patient died within 5 year
         
*A positive axillary lymph node is a lymph node in the area of the armpit (axilla) to which cancer has spread.

# Exercise

1)
- Download the data set manualy and place it somewhere somewhere in your my_notebook structure (for instance the data folder)

- Change the 2's in the "Survival Status" column to -1's. (Not sure this is necesary, but it follows more closely to what we are familiar with in the Iris exercise)
   - Hint: df['survival_status'] = df['survival_status'].map({1:1,2: -1})
 
 
- Make a numpy array of the class labels.
  - Hint: class_labels = df['survival_status'].to_numpy()

 
- Make a numpy array for each of the other columns in the data set.
  - Hint: year_of_operation_data = df['year_of_operation'].to_numpy()


- Make trainining data with only the age numpy array and your class labels.

- Find the learned weights and weight history using the age training data.

- Find the amount of correct predictions this learned weight would produce. (the weights and therefore the predictions can change every time you run it)
  - Hint:   
  for td in age_training_data:  
    if td[1] == predict_with_bias(td[0], learned_weights):  
        age_count +=1 
        
2) 

- Make a new set of training data where you use the data from the year_of_operation numpy array you created aswell as the age. 

- Find learned weights, weight history and amount of correct predictions with this new training set.

- Run both training sets a few times and compare the number of correct predictions. (For me the difference was almost always 0 or +1 correct prediction for the training set with year aswell)   
  - Try to explain why adding another dimension doesn't increase our accuracy by more.
- Now make a new training set with age, year and positive_axillary_nodes, find weights and correct predictions. Run it a few times and compare with output from the other two training sets. (I get between -1 and +5 correct predictions compared to the other two)
  - Try to explain why adding the third dimension made a bigger impact on our correct predictions, though still a pretty small one.
  
3)

- Plot the error rates of the three different training sets (it takes quite a long time, so you can also just do it with one training set, they look very similar)

- Plot the data from the training set with age and year.

- Can the plot of the training set explain why our error rate is so bad?


**Final musings - Should be read after doing the exercises if you want to draw your own conclusions**
Scroll down to read.
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>

I think the reason our predictions don't get much better with more dimensions and that our error rate is so bad, is because it's a more messy data set than we saw in the Iris exercise. There isn't a clear relation between age and how long you survive after an operation or between what year the operation took place and how long you survive. It seems adding the third column with "posive_axillery_nodes" to our training set helps a bit and i think that makes sense because that is actually an indication of how sick the person was before the operation. Hence the more sick, the less likely to survive 5+ years. 

The plot of the training set with age and year also quite clearly shows that it would not be easy to draw a line to have the people who survived for 5+ years on one side and the people who did not on the other. The points are a big mess and not two areas that can easily be told apart from each other, like it was in the iris exercise.

This exercise is made from playing around with the data set I found a bit and trying to make sense of the outputs. It turned out the data set maybe wasn't as suited for an exercise as I had hoped, but learning why is hopefully valuable aswell.




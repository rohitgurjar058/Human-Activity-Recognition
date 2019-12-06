# Human-Activity-Recognition
The objective of this case study is to build a model that predicts human activities such as Walking, Walking Upstairs, Walking Downstairs, Standing, Sitting or laying using sensors like accelerometer to measures acceleration and gyroscope to measure angular velocity that we have in the Smartphone.

### Dataset Description
The dataset is collected from 30 persons performing different activities with a smartphone to their waist and it is recorded from the tri-axial reading of the accelerometer and gyroscope measured w.r.t time. So, we have 6 time series data as a input to solve a 6-class multi class classification problem.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window).

### Attribute Information:
For each record in the dataset it is provided:

- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope.
- A 561-feature vector with time and frequency domain variables.
- Its activity label.(WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING)
- An identifier of the subject who carried out the experiment.

### Data Analysis

- __No. of data points per Activity - No problem of Imbalance__

![](https://github.com/rohitgurjar058/Human-Activity-Recognition/blob/master/Images/datapoints_count.png)

- __Stationary and Moving activities__

![](https://github.com/rohitgurjar058/Human-Activity-Recognition/blob/master/Images/stationary_vs_moving.png)

- __Magnitude of an acceleration - Well seperate static and dynamic activities__ 

![](https://github.com/rohitgurjar058/Human-Activity-Recognition/blob/master/Images/mag_acceleration.png)

- __T-SNE Plot: Lot of Confusion between the standing and sitting activities__

  - Perplexity - 10 & No. of iterations - 1000
![](https://github.com/rohitgurjar058/Human-Activity-Recognition/blob/master/Images/tsne_perp_10_iter_1000.png)

  - Perplexity - 50 & No. of iterations - 1000
![](https://github.com/rohitgurjar058/Human-Activity-Recognition/blob/master/Images/tsne_perp_50_iter_1000.png)

### Model Evaluation

- We have 561 handcoded features which is engineered by the domain experts and obtained as a frequency and amplitide variation of time series data.

- Apart from that, we have raw time series collected directly from the sensors which is then fed into the deep learning Algorithms to auto engineer all the features and make the predictions. 

  __Machine Learning Models__
  
  Hyper-tuned all the relevant machine learning models on the Handcoded 561 features for the human activity recognition problem

   Algorithm | Test Accuracy
    ------------ | -------------
    Logistic Regression | 96.27%    
    Linear SVC          | 96.61%       
    rbf SVM classifier  | 96.27%      
    DecisionTree        | 86.43%      
    Random Forest       | 91.31%       
    GradientBoosting DT | 91.31%  
    
    __Best performing model is Linear Support Vector Classifier__
    
    ![](https://github.com/rohitgurjar058/Human-Activity-Recognition/blob/master/Images/linear_svc_best_model.png)
    
   __Deep Learning Models__

    In the deep learning, the most effective algorithm for the raw time-series data is __LSTM__
    
    > __1-Layer LSTM Layer with hidden layer = 128 with dropout = 0.5__ - 92.53
    
    > __1-Layer LSTM Layer with hidden layer = 324 with slight change in dropout = 0.6__ - 92.22%
    
    > __1-Layer LSTM Layer with hidden layer = 324 with slight change in dropout = 0.6__ - 89%
    
    > __2-Layer LSTM Layer with hidden layer, h1 = 128 & h2 = 64 with dropout 0.2 & 0.5 respectively__ - 92.77%
    
    <br/>
    Rely on the single algorithm is always not to be the best idea and this statement will makes sense when we apply CNN and got accuracy of 92.80% which is slightly better than the LSTM approach. <br/>
    
    ![](https://github.com/rohitgurjar058/Human-Activity-Recognition/blob/master/Images/cnn_acc_92.80.png)
    
    #### Divide and Conquer(using CNN) -  Implementation of Reserach Paper
    Divide and Conquer Approach
    ![](https://github.com/rohitgurjar058/Human-Activity-Recognition/blob/master/Images/Divide%20and%20conqure%20CNN%20Approach.png)
    
    Confusion Matrix
    ![](https://github.com/rohitgurjar058/Human-Activity-Recognition/blob/master/Images/divide_and_conquer.png)
    
    <br/>
    Algorithm | Test Accuracy
    ------------ | -------------
    LSTM	| 92.77%
    CNN	| 92.80%
    Divide and Conquer-Based with CNN	| 94.6%
    
### References:

  Deep Learning Models for Human Activity Recognition by machinelearningmastery.com<br/>
  Applied AI Course<br/>
  Divide and Conquer-Based 1D CNN Human Activity Recognition Using Test Data Sharpening paper
   
   
   
   









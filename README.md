# **Behavioral Cloning** 
---

**Behavioral Cloning Project**

The goals / steps of this project are the following:
* Use the simulator to collect data of good driving behavior
* Build, a convolution neural network in Keras that predicts steering angles from images
* Train and validate the model with a training and validation set
* Test that the model successfully drives around track one without leaving the road
* Summarize the results with a written report

This project is done based on NVIDIA's End-To-End Deep Learning for Self-Driving Cars which can be found [in this link] and a [video here].

[video here]: https://www.youtube.com/watch?v=NJU9ULQUwng
[in this link]: https://devblogs.nvidia.com/deep-learning-self-driving-cars/

### Model Architecture and Training Strategy

### Use the simulator to collect data of good driving behavior

To collect the good driving behavior data, we use a simulator provided by Udacity. It can be downloaded from [here]. There are two different tracks which we can perform our behavioral cloning in which they are of different difficulties. At the beginning, the training data can be collected by clicking on the recording button and have the training data saved into a data folder. The data saved will be in form of a csv file. The csv file will contain few information separated by comma, eg. Center Camera Image, Left Camera Image, Right Camera Image, Steering Angle, Acceleration and Braking.


<img src="./examples/Homepage_simulator.png" width="300" height="300"/>
<img src="./examples/training.png" width="300" height="300"/>


[here]: https://d17h27t6h515a5.cloudfront.net/topher/2016/November/5831f3a4_simulator-windows-64/simulator-windows-64.zip

### Pre-processing the data
The pre-processing sequence is first to crop the top and the bottom of the image to remove the sky and the part of the bonnet to improve the accuracy of the neural network. The pipeline is followed by a resize to (66,200,3) as stated by the NVIDIA's CNN input shape. Color space change to the YUV format is optional as there hasn't been much improvement at least in this simulation's case. The original images goes from: 

[original]
[tweaked]

![original][original_image.jpg]
![tweaked][tweaked_image.jpg]

<img src="./examples/original_image.png"/>

<img src="./examples/tweaked_image.png"/>

#### 1. An appropriate model architecture has been employed

My model consists of a convolution neural network with 3x3 filter sizes and depths between 32 and 128 (model.py lines 18-24) 

The model includes RELU layers to introduce nonlinearity (code line 20), and the data is normalized in the model using a Keras lambda layer (code line 18). 

#### 2. Attempts to reduce overfitting in the model

The model contains dropout layers in order to reduce overfitting (model.py lines 21). 

The model was trained and validated on different data sets to ensure that the model was not overfitting (code line 10-16). The model was tested by running it through the simulator and ensuring that the vehicle could stay on the track.

#### 3. Model parameter tuning

The model used an adam optimizer, so the learning rate was not tuned manually (model.py line 25).

#### 4. Appropriate training data

Training data was chosen to keep the vehicle driving on the road. I used a combination of center lane driving, recovering from the left and right sides of the road ... 

For details about how I created the training data, see the next section. 

### Model Architecture and Training Strategy

#### 1. Solution Design Approach

The overall strategy for deriving a model architecture was to ...

My first step was to use a convolution neural network model similar to the ... I thought this model might be appropriate because ...

In order to gauge how well the model was working, I split my image and steering angle data into a training and validation set. I found that my first model had a low mean squared error on the training set but a high mean squared error on the validation set. This implied that the model was overfitting. 

To combat the overfitting, I modified the model so that ...

Then I ... 

The final step was to run the simulator to see how well the car was driving around track one. There were a few spots where the vehicle fell off the track... to improve the driving behavior in these cases, I ....

At the end of the process, the vehicle is able to drive autonomously around the track without leaving the road.

#### 2. Final Model Architecture

The final model architecture (model.py lines 18-24) consisted of a convolution neural network with the following layers and layer sizes ...

Here is a visualization of the architecture (note: visualizing the architecture is optional according to the project rubric)

![alt text][image1]

#### 3. Creation of the Training Set & Training Process

To capture good driving behavior, I first recorded two laps on track one using center lane driving. Here is an example image of center lane driving:

![alt text][image2]

I then recorded the vehicle recovering from the left side and right sides of the road back to center so that the vehicle would learn to .... These images show what a recovery looks like starting from ... :

![alt text][image3]
![alt text][image4]
![alt text][image5]

Then I repeated this process on track two in order to get more data points.

To augment the data sat, I also flipped images and angles thinking that this would ... For example, here is an image that has then been flipped:

![alt text][image6]
![alt text][image7]

Etc ....

After the collection process, I had X number of data points. I then preprocessed this data by ...


I finally randomly shuffled the data set and put Y% of the data into a validation set. 

I used this training data for training the model. The validation set helped determine if the model was over or under fitting. The ideal number of epochs was Z as evidenced by ... I used an adam optimizer so that manually training the learning rate wasn't necessary.

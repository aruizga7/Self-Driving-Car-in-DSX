# **Behavioral Cloning** 

[//]: # (Image References)

[image1]: https://cloud.githubusercontent.com/assets/10526591/24032112/b7a5090e-0b29-11e7-8d0a-d54419d4c278.jpg "Left"
[image2]: https://cloud.githubusercontent.com/assets/10526591/24032113/b7c63c14-0b29-11e7-878f-663096e30985.jpg "Center"
[image3]: https://cloud.githubusercontent.com/assets/10526591/24032111/b7843300-0b29-11e7-9b89-6f4da4eaf539.jpg "Right"
[image4]: https://cloud.githubusercontent.com/assets/10526591/24032254/5cad128e-0b2a-11e7-8e3f-07e8d2d298e7.png "Nvidia Model"
[image5]: https://cloud.githubusercontent.com/assets/10526591/24032546/f21630b6-0b2b-11e7-8380-f6a415427f35.jpg "Video Image"

### Deliverables

#### 1. File Explanations

My project includes the following files:
* `model.py` contains the code for building the keras model based on the [Nvidia architecture](https://devblogs.nvidia.com/parallelforall/deep-learning-self-driving-cars/). 
* `model.h5` is the trained keras model needed to run the vehicle autonomously.
* `drive.py` is used to drive the vehicle autonomously in the simulator. It accepts an h5 file as a parameter.
* `video.mp4` is the video produced from the vehicle's camera view during the autonomous run.

#### 2. How to run the model in autonomous mode
Using the Udacity provided simulator and my drive.py file, the car can be driven autonomously around the track by executing 
```sh
python drive.py model.h5
```

#### 3. Model Pipeline

The model.py file contains the code for training and saving the convolution neural network. The file shows the pipeline I used for training and validating the model, and it contains comments to explain how the code works.

### Model Architecture and Training Strategy

#### 1. Data Collection
 
 Image data and corresponding steering angle were collected by manually driving the vehicle in the simulator for 3 laps. The vehicle has 3 cameras to record the images - left, center, and right. The steering angles for the images from the left camera were adjusted by 0.1, while the angles for the images from the right camera were adjusted by -0.1 to consider different perspective view from each camera. This resulted in a total of 10,446 (3,482 x 3) images. 

 The following are the left, center, and right images recorded at the same location:

![Left][image1]
![Center][image2]
![Right][image3]

#### 2. Model and Approach

The overall strategy for deriving a model architecture was to start with a simple architecture such as the original LeNet and to build from there by fine tuning various parameters. Unfortunately, the vehicle failed to finish the track even on low speed despite various modifications of the model.

In order to gauge how well the model was working, I split my image and steering angle data into a training and validation set with a ratio of 8:2. I found that my first model had a low mean squared error on the training set but a high mean squared error on the validation set. This implied that the model was overfitting. To combat the overfitting, I added a dropout layer with varying keep probabilities between 0.5 and 0.9. However, the model still could not keep the vehicle on track.

I then decided to explore more complex architectures with deeper layers and found the [Nvidia architecture](https://devblogs.nvidia.com/parallelforall/deep-learning-self-driving-cars/) to be appropriate for this purpose.

![Nvidia Model][image4]

Using this model showed significant improvements right away as the vehicle finally made a successful run, although it still showed some erratic behaviors in corners. 

I started fine-tuning to improve performance by experimenting with various activation functions including ReLU, PReLU, and ELU. At the end, ReLU showed the best performance, contary to my expectation that  PReLU and/or ELU would perform better. The default learning rate of 0.001 for adam optimizer proved to be the most effective.

To further improve the driving behavior, I decided to add more training data.

#### 3. Additional Data

As the vehicle struggled in corners, I added short segments of driving data making smooth turns, increasing the dataset to 17,949 (5,983 x 3) images.  I also added horizontally flipped images and opposite steering angles as the vehicle runs counterclockwise in the training track, which can cause left turn bias. The addition of data did the magic and made the vehicle take smooth turns around the corners.

#### 4. Final Model Architecture

Input images are first normalized and cropped using the keras functions to take advantage of the power of GPU. The top 70 pixels that include features like sky, trees, etc and the bottom 20 pixels that show the hood of the vehicle are not needed and thus removed - which helps reduce the computing power needed. 

The model consists of 3 convolution layers with 5x5 filter sizes and depths of 24, 48, and 64, followed by 2 convolution layers with 3x3 filter sizes and depth of 64. RELU layers are used to introduce nonlinearity and a dropout layer with a keep probability of 0.8 is added before reaching the 4 fully connected layers. The final output of this model is a single value for the steering angle.

The model was compiled after 5 epochs, which was the ideal number before validation loss stopped decreasing and the model started to overfit.
## Traffic Sign Recognition 

### Overview

In this project we will learn to use a deep neural networks and convolutional neural networks to classify traffic signs. You will train a model so it can decode traffic signs from natural images by using the [German Traffic Sign Dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset). After the model is trained, you will then test your model program on new images of traffic signs you find on the web.


### Dataset

- [Download the dataset](https://d17h27t6h515a5.cloudfront.net/topher/2016/November/581faac4_traffic-signs-data/traffic-signs-data.zip). This is a pickled dataset in which we've already resized the images to 32x32.

### Model 
The architecture is single CNN with four hidden layers. 
A CNN consists of a succession of convolutional and maxpooling layers, and each layer only receives connections from its previous layer. The last layer is a fully connected layer with one ouput unit per class in the recognition task.

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x1 grayscale image   					| 
| Convolution 5x5     	| 1x1 stride, same padding, outputs 28x28x6 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride, outputs 14x14x6  				    |
| Convolution 5x5	    | 1x1 strinde, outputs 10x10x16        		    |
| Max pooling	      	| 2x2 stride, outputs 5x5x16  				    |
| Flatten               | outputs 400                                   |
| Fully connected		| output = 120     								|
| RELU					|												|
| Fully connected		| output = 84     								|
| RELU					|												|
| Fully connected		| output = 43     								|

 ![](https://github.com/aruizga7/Self-Driving-Car-in-DSX/raw/master/3.%20Traffic%20Sign%20Recognition/image/grayscale.jpg)

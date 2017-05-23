# Self Driving Car tutorials with Data Science Experience

Self-driving cars promise to transform roadways. There’d be fewer traffic accidents and will provide greater mobility for people who can’t operate a vehicle. The cars could fundamentally change the way we think about getting around. To have a self-driving car we need to be able to sense the surroundings and detect unexpected encounters.

The solution proposed uses deep learning across which means we are teaching self-driving cars somewhat like how you’d teach a human. That involves providing a host of examples of situations, objects and scenarios and then letting the system extrapolate how the rules it learns there might apply to novel or unexpected experiences. It means logging a huge number of driving hours to provide the system with basic information.

The solutions of this project show the first steps toward having a real self-driving car. The result will demonstrate how to drive a car in a simulator using 100% deep learning model without any human interaction. My wish would be to demo the power of the IBM Watson Data Platform with one of the most challenging use cases in the industry.
- [Lane Line detection](https://github.com/aruizga7/Self-Driving-Car-in-DSX/tree/master/1.%20Line%20Lane%20Detection): lines on the road show us a constant reference for where to steer the vehicle. This notebook we detect lane lines in images and videos using Python and OpenCV (Open-Source Computer Vision). We apply techniques for distortion correction to raw images, color transforms and gradients. 
- [Advanced Lane Line detection](https://github.com/aruizga7/Self-Driving-Car-in-DSX/tree/master/2.%20Advanced%20Line%20Lane%20Detection): this second notebook provides enhancements for lane line detection like apply a perspective transform ("birds-eye-view") and detect lane pixels and fit to find the lane boundary. It also detects the curvature of the lane and vehicle position with respect to center.
-  [Traffic Sign Classifier](https://github.com/aruizga7/Self-Driving-Car-in-DSX/tree/master/3.%20Traffic%20Sign%20Recognition): decode traffic signs from natural images and test the model with new images of signs from the web.
-  [Vehicle Detection](https://github.com/aruizga7/Self-Driving-Car-in-DSX/tree/master/4.%20Vehicle%20detection): detect vehicles in a dash camera video. It is an object detection problem and for that we pre-process the images and we re-use a very popular Object Recognition pre-trained model called Yolo (9 convolutional layers and 3 full connected layers). That technique is called Transfer Learning.
- [Behavioral cloning](https://github.com/aruizga7/Self-Driving-Car-in-DSX/tree/master/5.%20Behavioral%20cloning): train, validate and test a model using Keras to clone driving behavior. The model will output a steering angle to an autonomous vehicle. 

![Advanced Lane Finding for Udacity Self Driving Car Nanodegree](https://github.com/aruizga7/Self-Driving-Car-in-DSX/raw/master/DSX-selfdrivingcar.png) 

#### DSX Notebooks:
- [Lane Line detection](https://apsportal.ibm.com/analytics/notebooks/62cd9573-d8c0-4fab-b30c-deeef4378086/view?access_token=c8fab7b9ca82e0cd5ff36a2b260b4f61bf6efa9378ede945e452a7a49f30012a)
- [Advanced Lane Line detection](https://apsportal.ibm.com/analytics/notebooks/0849b7a8-d79b-4dc9-a104-0020b2b350f7/view?access_token=b2abf8704d456ae2254a32746f4af0e0d9eed41a8ffebdd3cd16dec20dcbd592)
- [Traffic Sign Classifier](https://apsportal.ibm.com/analytics/notebooks/fb588e1e-88bc-41ff-b905-35e37bed0365/view?access_token=30a9cd9e10b4fd977bd1c83d658537d68c9664f014a1773954f01395ac9a493e)
- [Vehicle Detection](https://apsportal.ibm.com/analytics/notebooks/97a109cb-bb67-49ca-9a16-d94dee39f200/view?access_token=97f64e6d53458bdbb837f3072d9dec122406853112b85597a3bfcdc1a965e2aa)
- [Behavioral cloning](https://apsportal.ibm.com/analytics/notebooks/4f6e8d05-46d9-4702-afbb-693197ffb1f1/view?access_token=1dd856efa647cb184937c4a07a41107124b900a124d4492ef10747a51f739285)

#### Demonstration videos on Youtube
- [Lane Line detection](https://www.youtube.com/watch?v=X9UDUDsFSfU)
- [Advanced Lane Line detection](https://www.youtube.com/watch?v=DO40OF0l2x8)
- [Vehicle Detection](https://www.youtube.com/watch?v=CvmmCx0gkes)
- [Behavioral cloning](https://www.youtube.com/watch?v=MB-ii0qzUmQ)


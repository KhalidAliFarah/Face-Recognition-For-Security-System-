# Face Recognition (For Security System)

## A. PROJECT SUMMARY

**Project Title:** Face Recognition (For Security System)

**Team Members:** 
- [Md Ashraful Islam B032020050 ]
- [Khalid Ali Farah  B032020051]
- [Abdulrahman derhem  B031910490]
- [Jurham Rahman  B031920506]
- [Abohatem Aiman  B031920508 ]


- [ ] **Objectives:**
- Break out the project goal into more specific objectives
- [insert]
- [insert]
- [insert]


##  B. ABSTRACT 

Today’s institutions are facing major security issues; consequently, they need several specially trained personnel to attain the desired security. These personnel, as human beings, make mistakes that might affect the level of security. 
A proposed solution to the mentioned matter is a Face Recognition Security System, which can detect intruders to restricted or high - security areas and help in minimizing human error.
This project is about an anti-theft security system using face recognition based on Raspberry pi. Anti-theft security system has been launched for many years but most of them are just a CCTV, IP camera or door sensor alert system. It could be more efficient with uses of face recognition. The design of anti-theft security system is based on human face recognition and remote monitoring technology. It will verify the person identity that goes near to the camera within certain distance. Only the people who match the identity with database and key in the correct password have the right to entry. A mobile application telegram and image processing technique LBP based have been involved in this system. Electric door lock solenoid, keypad and LCD display will combined operate the accessibility of door. An ultrasonic sensor is used to detect the person distance between the door. Face recognition will only start to function when someone goes near the door within certain distance. An alert message and photo taken will send to owner mobile phone via telegram with WIFI when the face recognition algorithms detect a stranger comes near the door and also a buzzer will be triggered to act as an alarm system. Owner can control the door locker and check the camera with the telegram application. The security system is designed for actual use in home condition with the uses of a microcontroller ARM Quad Cortex-A53.


![Coding](https://miro.medium.com/max/1400/1*fyfSOSKswsmV0n7Wdy6R4Q.jpeg)
Figure 1 shows the AI output of detecting which user is not wearing a face mask or inappropriate face mask.

## C.  INTRODUCTION

This project is for provide a precise solution with a new design with improvement embedded system to protect the household with giving higher security level and notification on time. Anyway, there are a few problems that are still exist on security product on market. The issues like the face detection only will start to function when someone press the doorbell. Surveillance system will destroy by theft and without notify owner when stranger come in. Lastly, face recognition can be passed with owner face photo. 
Nowadays, the home security with only door locker is not enough to protect your house and family. However, the smart home security system on market still not popular for household uses because of the high price tag. Besides that, the smart home security system on market still can be improved to higher security level and build with low-cost material to fulfil the need of market. Regarding to this issue, anti-theft security system using face recognition project have been started for solve this issue. It can help to solve the issues like it can trigger the alarm and capture an image send to owner when a stranger is detected in front of door. The theft will get alert so he got no time to start breaking the door and destroy the security system. For overcome the weakness of face recognition that can be passed with owner face image so the door will only unlock with the correct password input with a keypad.


## C.  DATASET     no need 

In this project, we’ll discuss our two-phase COVID-19 face mask detector, detailing how our computer vision/deep learning pipeline will be implemented.

From there, we’ll review the dataset we’ll be using to train our custom face mask detector.

I’ll then show you how to implement a Python script to train a face mask detector on our dataset using Keras and TensorFlow.

We’ll use this Python script to train a face mask detector and review the results.

Given the trained COVID-19 face mask detector, we’ll proceed to implement two more additional Python scripts used to:

- Detect COVID-19 face masks in images
- Detect face masks in real-time video streams

We’ll wrap up the post by looking at the results of applying our face mask detector.


There is two-phase COVID-19 face mask detector as shown in Figure 2:

![Figure 2](https://www.pyimagesearch.com/wp-content/uploads/2020/04/face_mask_detection_phases.png)
Figure 2: Phases and individual steps for building a COVID-19 face mask detector with computer vision and deep learning 

In order to train a custom face mask detector, we need to break our project into two distinct phases, each with its own respective sub-steps (as shown by Figure 1 above):

- Training: Here we’ll focus on loading our face mask detection dataset from disk, training a model (using Keras/TensorFlow) on this dataset, and then serializing the face mask detector to disk

- Deployment: Once the face mask detector is trained, we can then move on to loading the mask detector, performing face detection, and then classifying each face as with_mask or without_mask

We’ll review each of these phases and associated subsets in detail in the remainder of this tutorial, but in the meantime, let’s take a look at the dataset we’ll be using to train our COVID-19 face mask detector.


Our COVID-19 face mask detection dataset as shown in Figure 3:

![Figure 3](https://www.pyimagesearch.com/wp-content/uploads/2020/04/face_mask_detection_dataset.jpg)

Figure 3: A face mask detection dataset consists of “with mask” and “without mask” images. 

The dataset we’ll be using here today was created by PyImageSearch reader Prajna Bhandary.

This dataset consists of 1,376 images belonging to two classes:

- with_mask: 690 images
- without_mask: 686 images

Our goal is to train a custom deep learning model to detect whether a person is or is not wearing a mask.

How was our face mask dataset created?
Prajna, like me, has been feeling down and depressed about the state of the world — thousands of people are dying each day, and for many of us, there is very little (if anything) we can do.

To help keep her spirits up, Prajna decided to distract herself by applying computer vision and deep learning to solve a real-world problem:

- Best case scenario — she could use her project to help others
- Worst case scenario — it gave her a much needed mental escape


## D.   PROJECT STRUCTURE  no need

The following directory is our structure of our project:
- $ tree --dirsfirst --filelimit 10
- .
- ├── dataset
- │   ├── with_mask [690 entries]
- │   └── without_mask [686 entries]
- ├── examples
- │   ├── example_01.png
- │   ├── example_02.png
- │   └── example_03.png
- ├── face_detector
- │   ├── deploy.prototxt
- │   └── res10_300x300_ssd_iter_140000.caffemodel
- ├── detect_mask_image.py
- ├── detect_mask_video.py
- ├── mask_detector.model
- ├── plot.png
- └── train_mask_detector.py
- 5 directories, 10 files


The dataset/ directory contains the data described in the “Our COVID-19 face mask detection dataset” section.

Three image examples/ are provided so that you can test the static image face mask detector.

We’ll be reviewing three Python scripts in this tutorial:

- train_mask_detector.py: Accepts our input dataset and fine-tunes MobileNetV2 upon it to create our mask_detector.model. A training history plot.png containing accuracy/loss curves is also produced
- detect_mask_image.py: Performs face mask detection in static images
- detect_mask_video.py: Using your webcam, this script applies face mask detection to every frame in the stream

In the next two sections, we will train our face mask detector.



## E   TRAINING THE COVID-19 FACE MASK DETECTION

We are now ready to train our face mask detector using Keras, TensorFlow, and Deep Learning.

From there, open up a terminal, and execute the following command:

- $ python train_mask_detector.py --dataset dataset
- [INFO] loading images...
- [INFO] compiling model...
- [INFO] training head...
- Train for 34 steps, validate on 276 samples
- Epoch 1/20
- 34/34 [==============================] - 30s 885ms/step - loss: 0.6431 - accuracy: 0.6676 - val_loss: 0.3696 - val_accuracy: 0.8242
- Epoch 2/20
- 34/34 [==============================] - 29s 853ms/step - loss: 0.3507 - accuracy: 0.8567 - val_loss: 0.1964 - val_accuracy: 0.9375
- Epoch 3/20
- 34/34 [==============================] - 27s 800ms/step - loss: 0.2792 - accuracy: 0.8820 - val_loss: 0.1383 - val_accuracy: 0.9531
- Epoch 4/20
- 34/34 [==============================] - 28s 814ms/step - loss: 0.2196 - accuracy: 0.9148 - val_loss: 0.1306 - val_accuracy: 0.9492
- Epoch 5/20
- 34/34 [==============================] - 27s 792ms/step - loss: 0.2006 - accuracy: 0.9213 - val_loss: 0.0863 - val_accuracy: 0.9688
- ...
- Epoch 16/20
- 34/34 [==============================] - 27s 801ms/step - loss: 0.0767 - accuracy: 0.9766 - val_loss: 0.0291 - val_accuracy: 0.9922
- Epoch 17/20
- 34/34 [==============================] - 27s 795ms/step - loss: 0.1042 - accuracy: 0.9616 - val_loss: 0.0243 - val_accuracy: 1.0000
- Epoch 18/20
- 34/34 [==============================] - 27s 796ms/step - loss: 0.0804 - accuracy: 0.9672 - val_loss: 0.0244 - val_accuracy: 0.9961
- Epoch 19/20
- 34/34 [==============================] - 27s 793ms/step - loss: 0.0836 - accuracy: 0.9710 - val_loss: 0.0440 - val_accuracy: 0.9883
- Epoch 20/20
- 34/34 [==============================] - 28s 838ms/step - loss: 0.0717 - accuracy: 0.9710 - val_loss: 0.0270 - val_accuracy: 0.9922
- [INFO] evaluating network...

|      |    precision    | recall| f1-score | support |
|------|-----------------|-------|----------|---------|
|with_mask|0.99|1.00|0.99|138|
|without_mask|1.00|0.99|0.99|138|
|accuracy| | |0.99|276|
|macro avg|0.99|0.99|0.99|276|
|weighted avg|0.99|0.99|0.99|276|


![Figure 4](https://www.pyimagesearch.com/wp-content/uploads/2020/04/face_mask_detector_plot.png)

Figure 4: Figure 10: COVID-19 face mask detector training accuracy/loss curves demonstrate high accuracy and little signs of overfitting on the data

As you can see, we are obtaining ~99% accuracy on our test set.

Looking at Figure 4, we can see there are little signs of overfitting, with the validation loss lower than the training loss. 

Given these results, we are hopeful that our model will generalize well to images outside our training and testing set.


## F.  RESULT AND CONCLUSION  need

Detecting COVID-19 face masks with OpenCV in real-time

You can then launch the mask detector in real-time video streams using the following command:
- $ python detect_mask_video.py
- [INFO] loading face detector model...
- INFO] loading face mask detector model...
- [INFO] starting video stream...

[![Figure5](https://img.youtube.com/vi/wYwW7gAYyxw/0.jpg)](https://www.youtube.com/watch?v=wYwW7gAYyxw "Figure5")

Figure 5: Mask detector in real-time video streams

In Figure 5, you can see that our face mask detector is capable of running in real-time (and is correct in its predictions as well.



## G.   PROJECT PRESENTATION   need

In this project, you learned how to create a COVID-19 face mask detector using OpenCV, Keras/TensorFlow, and Deep Learning.

To create our face mask detector, we trained a two-class model of people wearing masks and people not wearing masks.

We fine-tuned MobileNetV2 on our mask/no mask dataset and obtained a classifier that is ~99% accurate.

We then took this face mask classifier and applied it to both images and real-time video streams by:

- Detecting faces in images/video
- Extracting each individual face
- Applying our face mask classifier

Our face mask detector is accurate, and since we used the MobileNetV2 architecture, it’s also computationally efficient, making it easier to deploy the model to embedded systems (Raspberry Pi, Google Coral, Jetosn, Nano, etc.).

[![demo](https://img.youtube.com/vi/-p7HGwOWxtg/0.jpg)](https://www.youtube.com/watch?v=-p7HGwOWxtg "demo")



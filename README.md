# Black.ai ML Technical Challenge
The purpose of this challenge is to test your ability to implement and adapt modern neural networks. 

## Introduction
You are tasked with modifying Tiny YOLO [found here](https://pjreddie.com/darknet/yolo/), to efficiently classify single-channel depth data. YOLO is a shallow single-pass neural network architecture developed by P.J. Reddie that is built for speed; YOLO performs 1000x faster than R-CNN and 100x faster than Fast R-CNN on similarly sized input data. Tiny YOLO moreso. 

## The task

1. Implement Tiny YOLO using your framework and language of choice. 
2. Download our training and test datasets [here](#) or from the cli:

    wget -t 15 https://challenge.black.ai/datasets/dSHTeBjKiyc.tar.gz

3. Prepare the input data for training. 
4. Modify your Tiny YOLO implementation to run on single-channel depth images. 
5. Optimise your modified network around this data type as much as you can.
6. Train! 

## Submission

Upload your codebase to a public github repository, and submit a link to a .zip file containing:
- Your testing data
- Your training data
- A training script
- Your trained model
- A testing script which runs the testing data on your model and reports 
    - accuracy
    - loss
    - evaluation speed

Final submission should be made to contact@black.ai, with the subject line "ML_CHALLENGE | <your_name>"

*note:* please also include instructions for simple setup and testing, so that we can easily run your model against our own test data. Be sure to include a list of dependencies, to simplify the installation process. 

## Evaluation
We are primarily looking to assess the accuracy of detection, speed of inference, and the implementation itself. We will be testing/training both the implementation and model on a machine running 64-bit Ubuntu 16.04 LTS, with a Nvidia GTX 1080 graphics card.  

## Bonus
Would you be tempted to approach this classification task using any machine learning technique other than deep learning? If so, include a short (<200 word) explanation as to which and why. 

## Happy hacking! 

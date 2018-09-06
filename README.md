# Black.ai ML Technical Challenge
The purpose of this challenge is to test your ability to implement and adapt modern neural networks. 

## Introduction
You are tasked with modifying Tiny YOLO ([found here](https://pjreddie.com/darknet/yolo/)) to efficiently classify single-channel depth data. YOLO is a shallow single-pass neural network architecture developed by P.J. Reddie that is built for speed; YOLO performs 1000x faster than R-CNN and 100x faster than Fast R-CNN on similarly sized input data. Tiny YOLO moreso. 

## The task

1. Implement Tiny YOLO using your framework, approach, and language of choice.  You're also free to use any version you want v1,v2 or v3.
2. Download our training dataset [here](https://s3-ap-southeast-2.amazonaws.com/public.data.black.ai/ml_challenge_dataset.tar.gz) or from the cli:

    wget -t 15 https://s3-ap-southeast-2.amazonaws.com/public.data.black.ai/ml_challenge_dataset.tar.gz

3. Prepare the input data for training.

    Depth images (and labelled coordinate bounds) are rotated 90 degrees clockwise from upright. The depth images themselves are saved as 16bit, single-channel PGM images [640x480]. They contain raw sensor data content from a Kinectv1 sensor. Namely, each pixel has value between [0,1084]. Please check [this page](http://wiki.ros.org/kinect_calibration/technical) in case you are interested in metric values.

    Split the dataset out for training and testing as you feel is appropriate. 

    Image labels can be found in the labels.txt file, with bounding box labels structured as follows: 

        image_id x_topleft_coord y_topleft_coord width height visability
        
    where: 
    
      * image_id : depth image filename, ie. seq0_0001_2.pgm.
      * x_topleft_coord, y_topleft_coord : top-left **x** and **y** bounding-box coordinates within this depth image.
      * width, height : pixel size of the bounding-box within this depth image that is labelled as human.
      * visibility : visibility of human within the bounding-box for this depth image:
    
    ```
    visibility key:
    0. hidden
    1. fully visible
    2. partially visible 
    ```
    ![depth image label overlay](https://s3-ap-southeast-2.amazonaws.com/public.data.black.ai/seq0_0023_1_label_overlay.png)


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
What we are looking for:
Your understanding of parameters and hyperparameters is a mandate with this task. You are expected to be able to explain your reasoning for any changes made to the architecture and hyperparameter choices.

Tips:
Read the yolo research paper to understand the different post processing steps they do with respect to your version found [here](https://pjreddie.com/publications/)

## Bonus
Would you be tempted to approach this classification task using any machine learning technique other than deep learning? If so, include a short (<200 word) explanation as to which and why. 
Please note that, while just changing the input size to accept depth instead of rgb would get you through the task, think about how to optimise the whole network for depth like chopping off layers, different convolution techniques and give us a comparison of different techniques.If you're assuming certain things, please list them out in your submission.

## Happy hacking! 

The linked rgb-d dataset was taken from:
[1] L. Spinello, K. O. Arras. People Detection in RGB-D Data. IEEE Int. Conf. on Intelligent Robots and Systems (IROS), 2011.
[2] M. Luber and L. Spinello and K. O. Arras People Tracking in RGB-D Data With On-line Boosted Target Models. IEEE Int. Conf. on Intelligent Robots and Systems (IROS), 2011.


[![Udacity - Robotics NanoDegree Program](https://s3-us-west-1.amazonaws.com/udacity-robotics/Extra+Images/RoboND_flag.png)](https://www.udacity.com/robotics)

## Deep Learning Project ##

## Model ##
![image1](model.png)

## Hyperparameters ##
![image2](hyperparam.png)

* The hyperparameters were empirically tested. Given the limited computational power of the setup, I was conservative with the parameters.  Overall, the analysis still took over 4 hours to complete.

## Scoring ##

To score the network on the Follow Me task, two types of error are measured. First the intersection over the union for the pixelwise classifications is computed for the target channel. 

In addition to this we determine whether the network detected the target person or not. If more then 3 pixels have probability greater then 0.5 of being the target person then this counts as the network guessing the target is in the image. 

We determine whether the target is actually in the image by whether there are more then 3 pixels containing the target in the label mask. 

Using the above the number of detection true_positives, false positives, false negatives are counted. 

** Final score**

The final score is the pixelwise `average_IoU*(n_true_positive/(n_true_positive+n_false_positive+n_false_negative))` on data similar to that provided in sample_evaulation_data
![image3](final_score.png)


**Ideas for Improving your Score**

* Collect more data from the sim. 

* Decreasing the stride --The amount by which the filter slides. Decreasing the stride increases the size of your model by increasing the number of total patches each layer observes- which results in improved accuracy at the expense of increased computational load.

* Increase the connections of neurons to each patch by increasing the filter depth.  This can be done by increasing hyperparameter height of K in the layers.






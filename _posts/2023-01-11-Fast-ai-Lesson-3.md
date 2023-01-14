# Chapter 4


In chapter 4 we get an overview of what steps are involved in the training process, namely; making predictions, calculating loss and gradients. Then updating weights and biases. Other tensor operations are covered.

### How is a grayscale image represented on a computer? How about a color image?
An image is made up of pixels, in a grayscale image the image is represented by a 2D matrix of values, each value determines the intensity of the pixel, from white to black, 0 to 255. To produce colour images Red, green and blue channels are arranged in 2d arrays from 0 to 255. These three arrays combine to form a final coloured image.

### How are the files and folders in the MNIST_SAMPLE dataset structured? Why?

![](/images/mnist_dataset.png "dataset screenshot")

This is the layout of the training set, there is a similar file that contains the validation imageset. The validation set allows us to check the accuracy of the model.


### Explain how the “pixel similarity” approach to classifying digits works.

The inital step is to identify the pattern for each class. So in identifying what a 3 looks like we must find the mean average pattern of all the threes in our training set. By comparing unknown numbers to this pattern, you can determine what they are.

### What is a list comprehension? Create one now that selects odd numbers from a list and doubles them.


Python code and output:

```python

list = range(5)
odd = []
for i in list;
    if i % 2 == 1;
    odd.append(i * 2)
print(odd)
```


  
    


### What is SGD?

Stochastic Gradient Descent is a function that minimizes/optomises the loss value. It initializes the weights and biases with random values. It multiplies the learning rate by the gradients to determine how much to change the weights and biases. Calculates the gradients of the loss function to how to influence the weights and biases in order to minimise the loss value.

###  What is “loss”?

 The loss refers to the loss function, this will return a value based on the given predictions and targets, lower values result in better model predictions.
 
###  What is a “gradient”?



The gradient signals by how much the weight should change, in order to make the model better. It measures how much the loss function is affected as the weights change.


### Draw the sigmoid function. What is special about its shape?

 Sigmoid function, essentially turns all vaules into a range of 0 to 1.
 
 
![](/images/sigmoid.png "sigmoid function from the wikipedia")



###  What is an “activation function”?

 
 The activation function of a node takes input coming into the node and tells it to "activate " upon recieving a vaule/set of values. The importance of this can be seen when compared to a linear function, the layers will only activate in a linear fashion.  With the activation function, the node is able to become more specific with what input it activates to. Extrapolating this to multiple layers leads to a much more flexible system capable of significantly more complicated functions.





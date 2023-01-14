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


  
    
 
 ### What is a “rank 3 tensor”?

The rank of a tensor is the number of dimensions it has. An easy way to identify the rank is the number of indices you would need to reference a number within a tensor. A scalar can be represented as a tensor of rank 0 (no index), a vector can be represented as a tensor of rank 1 (one index, e.g., v[i]), a matrix can be represented as a tensor of rank 2 (two indices, e.g., a[i,j]), and a tensor of rank 3 is a cuboid or a “stack of matrices” (three indices, e.g., b[i,j,k]). In particular, the rank of a tensor is independent of its shape or dimensionality, e.g., a tensor of shape 2x2x2 and a tensor of shape 3x5x7 both have rank 3.
    Note that the term “rank” has different meanings in the context of tensors and matrices (where it refers to the number of linearly independent column vectors).


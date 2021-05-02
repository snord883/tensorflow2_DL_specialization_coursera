# **GETTING STARTED WITH TENSORFLOW2**

## **Sequential:**
- if **activation** parameter is left off (the dense layer will have a linear activation or by default no activation)
- (optional) you can include an **input_shape** paramenter
![alt_text](./images/sequential.JPG 'image')

Option2:
![alt_text](./images/sequentialv2.JPG 'image')

<hr>
<hr>

## **Convolutional and Pooling Layers:**
- 2 Required arguments:
    1. Number of filters
    2. Shape of the convolutional kernel
        - Shortcut: Since kernel and pooling often have the same (w x h), it can also be written with a single value not in parentheses

![alt_text](./images/convolutional.JPG 'image')

<hr>

## **Adding weight initialisers**
- Each layer has optional arguments *kernel_initialiser* and *bias_initialiser*, which are used to set the weights and biases respectively.
    - If a layer has no weights or biases (e.g. it is a max pooling layer), then trying to set either kernel_initialiser or bias_initialiser will throw an error.
- It is also possible to define your own weight and bias initialisers. Initializers must take in two arguments, the *shape* of the tensor to be initialised, and its *dtype*.

<hr>

## **Compiling Method**
- *Optimizer* types:
    - *sdg*:
- *Loss* types:
    - *binary_crossentropy* (binary classification)
    - *categorical_crossentropy* (multiclass classification):
        - returns array for probability of it belonging to the respective classes (all summing to 1 or 100%)
    - *sparse_categorical_crossentropy* (multiclass classification):
        - returns a single integer corresponding to the class with the highest probability
- *Metrics* types:
    - *accuracy*
    - *mae* (Mean Absolute Error)

![alt_text](./images/compile_method.JPG 'image')
- For even more granular control of the attributes, Keras has features that can also be passed in.
    - Otherwise, default *learning_rate* is 0.01

![alt_text](./images/compile_method2.JPG 'image')

<hr>

## **Fit Model**
- **Fit**:  it returns a TensorFlow history object. This object contains a record of the progress of the network during training in terms of the loss and the metrics that we defined when we compiled the model. This object is actually an example of something called a **callback**
Defaults:
- *epochs*: 1
- *batch_size*: 32
- *verbose*: 1
    - 0: turns off the print outs
    - 1: prints every iteration of the epoch
    - 2: prints only the end of each epoch

![alt_text](./images/fit_model.JPG 'image')

## **Evaluate Model**
- **evaluate**: returns the loss and metric(s) 
    - In below example there are 2 metrics for the model so it'll return 2 metrics (accruacy & mae)

![alt_text](./images/evaluate_model.JPG 'image')


<hr>
<hr>
<hr>

## **Validation Sets**
![alt_text](./images/validation_set.JPG 'image')
![alt_text](./images/validation_set2.JPG 'image')

<hr>

## **Model Regularisation**
![alt_text](./images/regularisation.JPG 'image')
- *l1* can be changed to *l2* 
- Or you could add both as show below. Even add regularisation to the bias terms of the model.

![alt_text](./images/regularisation2.JPG 'image')

- Dropout regularisation added to a model:

![alt_text](./images/dropout.JPG 'image')

<hr>

## **Introduction to Callbacks**
- **Callbacks** are an important type of object TensorFlow and Keras that are designed to be able to monitor the loss in metrics at certain points in the training run and perform some action that might depend on those loss in metric values.
    - There are built-in callbacks.
    - We can customize our own *callbacks*:

![alt_text](./images/custom_callbacks.JPG 'image')

<hr>

## **Early Stopping and Patience**
- *monitor*: can be used to set which performance metric to use.
    - default: *val_loss*
- *patience*: In this case, the training will terminate only if there is no improvement in the monitor performance measure, the five epochs, in a row.
    - default: *0*
        - That means that as soon as the performance measure gets worse from one epoch to the next, then the training is terminated. Now, this might not be ideal since of course, the model's performance is noisy, and it might go up or down from one epoch to the next. What we really care about is that the general trend should be improving.
- *min_delta*: This option can be used to define what qualifies as an improvement in the monitor performance measure.
    - default: *0*
        - which means that any improvement in the performance is enough to reset the patience.
- *mode*: depending on the choice of quantity that we're monitoring, an improvement could be either an increase or a decrease in that quantity. If we're monitoring the validation loss, then we want the loss to go down. But if we're monitoring the validation accuracy, then we'd want that to go up.
    - default: *auto*
        - which means that the direction is automatically inferred by the quantity name

![alt_text](./images/early_stopping.JPG 'image')

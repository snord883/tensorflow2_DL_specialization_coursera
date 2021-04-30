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
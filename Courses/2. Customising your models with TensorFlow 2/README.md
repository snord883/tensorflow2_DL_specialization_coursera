# **Welcome to Customising your Models with TensorFlow 2**

## **The Keras Functional API**
- Main difference is, instead of passing each layer of the model in with a list through *Sequetial*, we pass the last layer into the next as an argument to a function call

![alt_text](./images/keras_api.JPG 'image')

- Previous approach:

![alt_text](./images/keras_api2.JPG 'image')

- We'll want to use it for networks that can't easily be defined using the sequential API.
    - This example has 2 inputs and 2 outputs
        - INPUT: Just before the final dense layer it's the flattened layer. And this outputs and unrolls tensor h. The next line takes this output tensor h, and concatenates it with the auxiliary input to make a single one-dimensional vector. This concatenation can be done with the new layer type I'm using here called the concatenate layer.
        - OUTPUT: The main output is 20 units with a sigmoid activation. The auxiliary output is just a single real value.
            - Need to pass a list of loss functions to the last keyword argument in the model dot compile method.
                - These losses are in the same order as the order of outputs we defined when we created the model instance. (if not given a name - see example below)
            - If we have two loss functions though, we need to combine them somehow.
                - That's what the new loss_weights keyword argument is doing here. These weights tell the model how to combine the loss functions. So here, the final loss is the binary_crossentropy plus 0.4 times the mean squared error.

![alt_text](./images/keras_api3.JPG 'image')

- If *name*s are given to each layer (Same example as above):

![alt_text](./images/keras_api4.JPG 'image')

<hr>

## **Variables**

![alt_text](./images/variable.JPG 'image')


<hr>

## **Tensors**
- You can think of tensors as being multidimensional versions of vectors and arrays.

![alt_text](./images/tensors.JPG 'image')

- Constants:

![alt_text](./images/variable2.JPG 'image')

<hr>

## **Accessing Layer Variables**
![alt_text](./images/accessing_model.JPG 'image')
![alt_text](./images/accessing_model2.JPG 'image')

- Can you names to access layers by name:

![alt_text](./images/accessing_model3.JPG 'image')

<hr>

## **Accessing Layer Tensors**
- Good for *transfer learning*:
![alt_text](./images/accessing_model5.JPG 'image')

- Another way of writting the same sequence:

![alt_text](./images/accessing_model6.JPG 'image')

<hr>

## **Freezing Layers**
- Layers have a *trainable* attribute that needs to be set to *False* before compiling. 
    - May want to do this because of *transfer learning* (pulling a *pre-trained* layer from another model)
    - Done 1 of 2 ways:


![alt_text](./images/freeze1.JPG 'image')

- or

![alt_text](./images/freeze2.JPG 'image')

- Entire models can also be frozen:

![alt_text](./images/freeze3.JPG 'image')


<hr>
<hr>
<hr>

## **Dataset Generators**
- Used when you have datasets that are too large to fit into memory.

![alt_text](./images/generator1.JPG 'image')
![alt_text](./images/generator2.JPG 'image')

<hr>

## **Keras Image Data Augmentation**
![alt_text](./images/generator3.JPG 'image')
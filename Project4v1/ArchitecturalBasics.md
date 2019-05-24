1. How many layers,

   **Input layer:** Represents the various input channels that the input image comprises of.

   **Hidden layer:** This layers is formed after certain operations like activation function, batch normalization etc are performed on input layer. There is no predefined number of layers that should be present in the neural network, it depends on the features to be extracted. Also, the number of neurons in a layer matter - if they are less than complexity of the problem data set, then they may not retrieve the required feature and if they are more, then the problem of over fitting may occur.

   **Output layer:** This layer is formed as an output of all the operations in the hidden layer. Also, this layer will be input to the training model for the next epoch.

   

   ![img](https://cdn-images-1.medium.com/max/1600/1*hczvrCYgU_JQt5sx-UGM1A.gif)

   

   

2. MaxPooling,

   This is an operation that is applied on one of the hidden layers in the neural network. This is generally applied after 11x11 receptive field is achieved where the edges, gradient, patterns, parts of object are more prominent in the learning phase. Even other wise, this could be used at any layer after the first convolution. This operation modifies the values in the neurons so that "Max value" of set of pixels of kernel size will only be used. This operation reduces the number of channels to half.

   

3. 1x1 Convolutions,

   After certain number of convolutions with 3x3 kernel and Max Pooling, we many not be able to train the network much further with 3x3 convolutions. Then we can use 1x1 convolutions which is sum pooling of features across various channels of a given layer. This operation is linear and hence, ReLU should be applied after this.

   ![the Convolution with Kernel of size 1x1](https://raw.githubusercontent.com/iamaaditya/iamaaditya.github.io/master/images/conv_arithmetic/full_padding_no_strides_transposed_small.gif)

4. 3x3 Convolutions,

   3x3 is the common kernel size used to convolve in the image pixels to extract the features. This is run on all the channels in the image. The number of channels increase and the size of channels decrease with each convolution operation as the kernels increase. 

5. Receptive Field,

   Receptive field is equal to the number of pixels that a kernel can see. With a 3x3 kernel size, the first convolution operation has a receptive field of 3. The next operation has the receptive field of 5 and the next of 7 and so on. So, receptive field is the total field of information that a pixel in convolution layer sees across other convolution layers until the actual image.

   ![Image result for receptive field](data:image/png;base64,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)

6. SoftMax

   Softmax is a probability function applied on the output layer to catergorize the output to a specific  image. 

   ![Related image](https://developers.google.com/machine-learning/crash-course/images/EmbeddingExample3-6.svg)

7. Learning Rate,

   Deep neural networks are trained using stochaistic gradient descent algorithm. In the process of training the network, the weights in each layer of the network are changed according to the error calculated in back propagation. The amount of change in weights that we want to set is called learning rate. Learning rate can vary between 0.1 to 1.0. For example, if learning rate is 0.1, then the weights in the network will be adjusted by 10% depending on the error calculated during back propagation.

   ![Image result for learning rate image](https://cdn-images-1.medium.com/max/2400/0*K0ltbXIgtNLEXsXN.png)

8. Kernels and how do we decide the number of kernels?

   Kernel extracts features from the available channels and creates another set of channels depending on the number of kernels used and the kernel size for the next layer in the network for further training.

   Number of kernels depends on complexity of the images - if the image is of the size 28x28, then number of kernels in each layer could be small, say 10. But if the image size is large - 400x400, then the number kernels could start from 32 in first layer and go upto 512.

   

9. Batch Normalization,

   Input values to a neural network could have different sources ex: images from the web and images taken on a high resolution camera could be inputs. Generally, we divide the input values by 255 to have all the pixel values between 0 and 1. But since the source of information is different, this general formula will not normalize the values properly. Also, as the network is training, the variance of values of weights in the hidden layers will be very large which results in the covariance shift of the network. Because of this the network does not train properly.

   So, to avoid this, the input values could be subject to batch normalization where the mean of the values is maintained at 0 and variance at 1. 

   ![img](https://i0.wp.com/mlexplained.com/wp-content/uploads/2018/01/batchnorm_algorithm-1.png?resize=471%2C336)

   With this approach, the values of the input values will be normalized appropriately even if the sources of information is different. 

   Effect of batch normalization reduces the loss in the network is as below.

   ![img](https://i0.wp.com/mlexplained.com/wp-content/uploads/2018/01/curvature.png?resize=491%2C257)

10. Image Normalization,

    Images available for training could be of various resolutions ex: 400x400 (square), 500x400(rectangular), 28x28(very small size). To start training the network with different kinds of data, image normalization or pre-processing has to be done which involves:

    1. Uniform aspect ratio: Ensure that all images have same size and aspect ratio ie. images could be cropped to a uniform size.

    2. Image scaling: Depending on the desired size for starting the training, images height and width can be scaled up or down.

    3. Normalizing image inputs:

       1. ‘mean image’ obtained by taking the mean values for each pixel across all training examples

       2. Standard deviation is the deviation of each pixel value from the mean.

       3. Data normalization is done by subtracting the mean from each pixel and then dividing the result by the standard deviation. The distribution of such data would resemble a Gaussian curve centred at zero.

       4. Dimensionality reduction: The number of channels could be collapsed. Ex: RGB could be collapsed to grey scale.

          

11. Position of MaxPooling,

    MaxPooling operation reduces the number of channel to half. So, this layer should be used consciously depending on the image size. If the image size is large, then max pooling could be applied for every set of 5 hidden layers where the receptive field will be 11x11 where gradients, patterns and textures are more prominent. If the images sizes are small, say 28x28, then the max pooling could be applied much earlier than reaching 11x11 receptive field.

    Also, max pooling layer should not be the last layer.

12. Concept of Transition Layers,

    The operations done on the output of the convolution layers to optimize the inputs or weights in the neural network are called transition layers. Following are the transition layers

    1. Batch Normalization: input values could be subject to batch normalization where the mean of the values is maintained at 0 and variance at 1. 

       ![img](https://i0.wp.com/mlexplained.com/wp-content/uploads/2018/01/batchnorm_algorithm-1.png?resize=471%2C336)

    2. 1x1 convolution: The features from all the layers are summed up at each kernel level. This is not the regular convolution operation where the dot product of pixel value and kernel value is output. Generally, this will be use to reduce the number of channels after a defined set of convolution operations.

    3. MaxPooling layer: When 2x2 kernel is used to push the max value when it is used to stride on each channel in the convolution layer, this operation reduces the number of channels remain the same but the receptive field is halved. This will help in reducing the number of convolution layers in the complete network.

13. Position of Transition Layer,

    1. Batch normalization layer can be applied at each convolution layer.
    2. 1x1 convolution is generally used to reduce the number of channels by summing up the features across all the available channels.
    3. MaxPooling - this will be used to push the maximum impact features to the next layer. Generally, this could be applied after a receptive field of 11x11 is achieved so that sufficient number of features are available for this operation and the output captures the same without reducing the number of channels.

14. Number of Epochs and when to increase them,

    Generally, as the number of epochs increase the training will overfit the data i.e the network is not trained but it memorizes the data. The number of epochs have to be increased when the batch sizes are getting large. 

15. DropOut

    Set of neurons are switched off in a training model. Based on the % value mentioned, appropriate neurons are not used in training. This is called Dropout.

16. When do we introduce DropOut, or when do we know we have some overfitting

    When the network training accuracy does not vary much with each epoch, then its possible that the network is entering the overfitting zone. If a network is over fitted, noise or random features in the input are also learned as valid features and impacts the classification of the new data.

    Dropouts could be added at each convolution layer to switch off random neurons so that network trains to compensate for the missing neuron. The number of neurons that can be dropped is configurable.

17. The distance of MaxPooling from Prediction,

    MaxPooling should be applied at least one convolution layer before the flatten and softmax operations. The last convolution could be 3x3 or 1x1 convolution. 

18. The distance of Batch Normalization from Prediction,

    Batch normalization could be applied for each convolution layer except the final convolution operations of aggregating all the channels.

19. When do we stop convolutions and go ahead with a larger kernel or some other alternative (which we have not yet covered)

    Generally, convolution operations which generate a 11x11 receptive field will have most of the features available. At this layer, we can maxpooling and then again start the fresh set of convolutions until next 11x11 receptive field is achieved and at the same time reducing the number of channels. We would reach a point where doing convolutions with 3x3 will not yield any tangible output as we reach towards the end of the neural network layers. At this point, we can use large convolutions which could less than 11x11.

20. How do we know our network is not going well, comparatively, very early

    1. We can recognize this by the accuracy and validation accuracy at each epoch - if the % of of these parameters is not near 98 or 99, then our network is not going in the right direction.
    2. As the number of parameters in the network is getting large, it would require lot of RAM for storing output of each layer. This may lead to Out of Memory as the number of parameters increase.
    3. If the training accuracy keeps flat, then we have entered an over fitting zone. 

21. Batch Size, and effects of batch size

    Batch size is the set of images in the training set that will be considered for training against the test data set.  The batch size is fixed for each epoch. After each epoch, i.e after training over the batch size of images, the weights are modified in the neural network. Smaller the batch size, it fits well in the memory but that could lead to many epochs depending on the complexity of the input data - which could lead to over fitting. The batch size could be increased so that it can fit with the RAM available and epochs appropriately tuned so we get optimum validation accuracy. As the batch size is increased beyond this, the validation accuracy falls.

22. When to add validation checks

    Validation checks can be added after optimizing the neural network to have:

    1. Well tuned less number of parameters
    2. batchnormalization and dropouts
    3. add the LearningRateScheduler which can be tuned in the program.

    After step 3, we can tune the learning rate so that we can check the validation accuracy after each epoch.

23. LR schedule and concept behind it

    Learning rate scheduler is a function that can be defined by the user. This can be used to tune the learning rate so that the model trains smooth over the gradient descent rather that too fast or too slow.

24. Adam vs SGD

    **Adam** is an optimization algorithm that can used to update network weights iterative based in training data. This combines the advantages of the following two extensions of stochaistic gradient descent. 

    1. **Adaptive Gradient Algorithm** (AdaGrad) that maintains a per-parameter learning rate that improves performance on problems with sparse gradients 

    2. **Root Mean Square Propagation** (RMSProp) that also maintains per-parameter learning rates that are adapted based on the average of recent magnitudes of the gradients for the weight (e.g. how quickly it is changing).

       Instead of adapting the parameter learning rates based on the average first moment (the mean) as in RMSProp, Adam also makes use of the average of the second moments of the gradients (the uncentered variance).

       ##### Adam Configuration Parameters

       - **alpha**. Also referred to as the learning rate or step size. The proportion that weights are updated (e.g. 0.001). Larger values (e.g. 0.3) results in faster initial learning before the rate is updated. Smaller values (e.g. 1.0E-5) slow learning right down during training
       - **beta1**. The exponential decay rate for the first moment estimates (e.g. 0.9).
       - **beta2**. The exponential decay rate for the second-moment estimates (e.g. 0.999). This value should be set close to 1.0 on problems with a sparse gradient (e.g. NLP and computer vision problems).
       - **epsilon**. Is a very small number to prevent any division by zero in the implementation (e.g. 10E-8).

       Further, learning rate decay can also be used with Adam. The paper uses a decay rate alpha = alpha/sqrt(t) updted each epoch (t) for the logistic regression demonstration.

    **SGD**

    Gradient Descent can be described as an iterative method which is used to find the values of the parameters of a function that minimizes the cost function as much as possible. The parameters are initially defined a particular value and from that, Gradient Descent is run in an iterative fashion to find the optimal values of the parameters, using calculus, to find the minimum possible value of the given cost function. The word ‘*stochastic*‘ means a system or a process that is linked with a random probability. Hence, in Stochastic Gradient Descent, a few samples are selected randomly instead of the whole data set for each iteration.

25. etc (you can add more if we missed it here)


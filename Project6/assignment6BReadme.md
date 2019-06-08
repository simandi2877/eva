# Spatial Separable Convolution

The spatial separable convolution is so named because it deals primarily with the **spatial dimensions** of an image and kernel: the width and the height. 

A spatial separable convolution simply divides a kernel into two, smaller kernels. The most common case would be to divide a 3x3 kernel into a 3x1 and 1x3 kernel.

In a normal 3x3 convolution, there are 9 multiplications. But with below approach, we do two convolutions with 3 multiplications each (6 in total) to achieve the same effect.

Separable convolutional layers usually can learn simple to near-complex features in the image very efficiently and effortlessly. Therefore, intuitively **it makes sense to use these separable layers more in initial layers that try to capture simple features **compared to the final layers that try to capture much more complex features.

![img](https://cdn-images-1.medium.com/max/1000/1*o3mKhG3nHS-1dWa_plCeFw.png)







# Depth wise seperable convolution

This convolution deals with width, height and depth of the image. The convolution is done in 2 steps as below

**Step-1** : Instead of using a single filter of size 3 x 3 x 3 in 2D convolution, we used 3 kernels, separately. Each filter has size 3 x 3 x 1. Each kernel convolves with 1 channel of the input layer (1 channel only, not all channels!). Each of such convolution provides a map of size 5 x 5 x 1. We then stack these maps together to create a 5 x 5 x 3 image. After this, we have the output with size 5 x 5 x 3.

![img](https://cdn-images-1.medium.com/freeze/max/1000/1*TT2ldUUD2JM2eSayC3i9Lw.png?q=20)

**Step-2**: To extend the depth, we apply the 1×1 convolution with kernel size 1x1x3. Convolving the 5 x 5 x 3 input image with each 1 x 1 x 3 kernel provides a map of size 5 x 5 x 1. After applying 128 1×1 convolutions, we can have a layer with size 5 x 5 x 128.

![img](https://cdn-images-1.medium.com/freeze/max/1000/1*3y5a2WPWbjnZK6bwZw6U1g.png?q=20)

![img](https://cdn-images-1.medium.com/freeze/max/1000/1*jqNtWIEJ_lIRrp9nohquLQ.png?q=20)

Number of operations involved in Depthwise convolution compared to normal Convolution:

Consider an image of 64x64x3, if we want to increase the number of channels to 256, then the convolution operation would be 64x64x256x3x3

If the same image going thru depth wise convolution:

Step 1: 64x64x3 (output channels)x3x3 (1 kernel) = Output channels 62x62x3

Step 2: 62x62x3x1x1x256 = output channels of 62x62x256

So, in normal convolution at layer 1 has 9437184

Depthwise convolution has 36864 + 984064 = 1020910. The ratio of operations between normal convolution and depth wise convolution is 9.24. **So, the number of operations in depth wise convolutions are very less compared to normal convolution - hence depth wise convolution is a good choice for constrained hardware. **



# Grouped Convolutions

![img](https://cdn-images-1.medium.com/max/1250/0*7mD7QoJTtJDDFjuL.png)

Grouped convolutions is a method where the multiple convolution models can run in parallel and the output of each model is concatenated towards the end. This will help in defining custom models and experiment with various options. Based on this approach, various network architectures are defined like Inception, RexNet, RexNeXt, VGGNet, GoogleNet, Ensemble, eNAS etc.

**Advantages of grouped convolution:**

1. deep neural network can be trained on less powerful GPUs with smaller RAM available at that time

2. we can build networks as wide as we want. Take one modular block of filter group and replicate them

3. We can parallelize the training in two ways: 

   **Data parallelism:** where we split the dataset into chunks and then we train on each chunk. Intuitively, each chunk can be understood as a mini batch used in mini batch gradient descent. However, smaller chunks also mean that we are doing more like stochastic than batch gradient descent for training. This would result in slower and sometimes poorer convergence.

   **Model parallelism:** here we try to parallelize the model such that we can take in as much as data as possible. Grouped convolutions enable efficient model parallelism
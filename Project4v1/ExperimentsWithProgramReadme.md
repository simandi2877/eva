Logic used for the Programs uploaded:

1st_DNN: The default program

#### 2nd_DNN:

**Experiment with**

1. convolutions of 10, 16, 32.

2. Include Batch normalization at each layer

3. Add dropout before maxpooling layer and the final layer

   **Observations:**

After step 1 and 2, the number of parameters is at around 18K and the accuracy is at 99.1%

After step 3, after 10 epochs, the accuracy is at 99.02% which has reduced. But after increasing the number of epochs to 20, the accuracy increased to 99.21% but the training accuracy has not improved much after epoch 14.

#### 3rd_DNN

In the 2nd_DNN, with convolution layers of 10, 16, 32 channels, batch normalization and dropouts before maxpooling and last convolution has resulted in 18K parameters, 99.21% accuracy with 20 epochs.

**Now, Experiment with**

1. convolutions of 10, 16, 10 (1x1), maxpool, 16, 16, 16, 10(1x1) - target is to reduce the parameters to less than 15K
2. Include Batch normalization at each layer - as done in 2nd_DNN
3. Add dropout after each convolution layer with dropout as 0.1 wherease in 2nd_DNN it was 0.25.
4. Made a change to model.fit to print validation accuracy at each epoch

**Observations**:

With the above change, the number of parameters has come to 12K and the accuracy could be improved to 99.33% at epoch 16.

#### 4th_DNNs:

In the 3rd_DNN, with convolution layers of 10, 16, 10 (1x1), maxpool, 16, 16, 16, 10(1x1), batch normalization and dropouts(0.1) at each convolution layer has resulted in 12K parameters, 99.23% accuracy with 16 epochs.

**Now, Experiment with**

1. Define custom learning rate procedure linked to epoch. Also, add customize the optimizer learning rate.
2. Increase the batch size.

**Observations**: **For each observation, separate programs are uploaded.**

Accuracy pf 99.41% at epoch 14 with batch size of 32

Accuracy pf 99.41% at epoch 19 with batch size of 64

Accuracy pf 99.4% at epoch 28 with batch size of 128

Accuracy of <99.4% even after 50 epochs with batch size of 256.

As the batch size increases, the epochs should be increased to achieve 99.4% validation accuracy.


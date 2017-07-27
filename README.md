This is a proposal to solve the speed prediction challenge posted by https://comma.ai/. We use 3D Convolutional Network [1] to predict car speed using dashcam footage. 3D Convolutional Network seems to be the perfect solution for this problem as the MSE on the validation dataset reduces to 4.8 after the 4 epoches. LSTM for video understanding [2] gets stuck at 70 MSE after 8 epoches. The trained network is good enough to make reasonable prediction on arbitrary footages.

Another advantage of 3D Convolutional Network for speed predicttion from dashcam is that it works in chunks of frames. This is especially suitable for real-time speed prediction as we don't usually want to know the speed at every frame.

This is the results on the validation footage:

<video demo>

This is the results on a random dashcam camera:

<video demo>

[1] Learning Spatiotemporal Features with 3D Convolutional Networks (https://arxiv.org/abs/1412.0767)
[2] Unsupervised Learning of Depth and Ego-Motion from Video (https://arxiv.org/abs/1704.07813)
Take a look at a similar attempt at https://github.com/JonathanCMitchell/speedChallenge

# Information

<network architecture>

<training and validation losses>

# Usage

1. Download the weights pretrained on the Sports-1M dataset [https://goo.gl/tsEUo2]
1. Download the training data from comma.ai website [https://goo.gl/ERi7Uh]
2. Follow the steps in "Dashcam Speed - C3D.ipynb" for a walk-through of the training and testing of the network

# Todo list

1. Use shorter look-back time window to allow more fine-grained speed prediction. At the moment, the network looks 16 frames back in time and predicts the average speed during this period.
2. Use semantic segmentation to cut off moving objects. Moving objects such as vehicles confuses the speed prediction w.r.t. the road. More data with diverse conditions may also be able to clear this issue.
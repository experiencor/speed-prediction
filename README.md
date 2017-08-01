This is a proposal to solve the speed prediction challenge posted by https://comma.ai/. 3D Convolutional Network [1] is used to predict car speed using dashcam footage. The trained network is good enough to make reasonable prediction on arbitrary footages.

**The final mean squared error on validation set is 3.1!**

The result on comma.ai validation footage (MSE of 3.1):

<a href="https://www.youtube.com/watch?v=384IEndkPYc" rel="some text"><p align="center">![Foo](https://j.gifs.com/O7mjjp.gif)</p></a>

The result on 28 minute udacity footage (MSE of 23.28):

<a href="https://www.youtube.com/watch?v=67a-iTXKlKY" rel="some text"><p align="center">![Foo](https://j.gifs.com/WnxrrJ.gif)</p></a>

Note that this is the result when the network is purely trained on comma.ai data and tested on udacity data with completely different lighting conditions and different scene dynamics. Most of the error on the udacity footage occurs at the turns, which is limitedly seen in comma.ai dataset.

[1] Learning Spatiotemporal Features with 3D Convolutional Networks (https://arxiv.org/abs/1412.0767)

[2] Unsupervised Learning of Video Representations using LSTMs (https://arxiv.org/abs/1502.04681)

Take a look at a similar attempt at https://github.com/JonathanCMitchell/speedChallenge

# Information

Network architecture

<p align="center">
<img width="200" src="model.png"/>
</p>

Validation losses

<p align="center">
<img width="400" src="val_loss.png"/>
</p>

# Usage

1. Download the weights pretrained on the Sports-1M dataset [https://goo.gl/tsEUo2]

2. Download the training data from comma.ai website [https://goo.gl/ERi7Uh]

3. Follow the steps in "Dashcam Speed - C3D.ipynb" for a walk-through of the training and testing of the network

# Todo list

1. Use shorter look-back time window to allow more fine-grained speed prediction. At the moment, the network looks 16 frames back in time and predicts the average speed during this period.
2. Use semantic segmentation to cut off moving objects. Moving objects such as vehicles confuses the speed prediction w.r.t. the road. More data with diverse conditions may also be able to clear this issue.
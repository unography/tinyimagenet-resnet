# tinyimagenet-resnet
A modified ResNet network, trained from scratch on [Tiny ImageNet](https://tiny-imagenet.herokuapp.com/) dataset.

This was done mainly as a learning exercise - to learn how to train neural networks from scratch, and also the patience required to do so.

Training was done on Google Colab. Certain training decisions, like batch size and number of kernels, were taken to avoid OOM errors on Colab.

This repository contains the notebook which has the raw training logs, as well as a cleaned up notebook, with better code, without the logs. 

Modifications done - 

1. Changed number of layers based on required receptive field for the dataset (image sizes are 64x64)
2. Instead of `add` while merging skip connections, used `concat`, similar to WideResNet and DenseNet models
3. Trained using progressive size of images (random crops to get images of size 32x32, 48x48). This allowed the network to train fast as well as served as a data augmentation technique.
4. All fully connected layers were removed, GlobalAveragePooling was added as the final layer.
5. Used One Cycle Policy of Cyclic Learning Rate while training.

Final model has 12.9M parameters, and acheived a validation accuracy of 60%.
Training was stopped after that.
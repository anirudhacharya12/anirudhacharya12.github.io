---
layout: post
title: "Auto-Quantize Deep Networks"
date: 2018-10-30
---

The following was an interesting idea I had, documenting it here for future reference - 

## UI Tool for optimizing a deep learning model for target resource utilization and target performance and accuracy

- The system will offer manual and automated interface that takes a pre-trained model and a labeled data set, searches the neural network space, and identifies modifications that improves performance with minimal impact to accuracy.
- The manual interface will have a user interface that allows the user to interactively modify layers and individual operators: quantize, change activations, remove layers, etc. and outputs the impact to accuracy and performance. The tool will also output the resource consumption of the network, so that the user can design their modifications to meet certain resource constraints like - memory footprint and processor speed.
- The automated interface will take as input target accuracy and target resource constraints and will search the space of neural network architecture to identify changes that improve performance while meeting target accuracy and target resource constraints. These changes will be suggested to the user, who can later pick and choose among the optimizations.

This tool will be very useful when we trained models that will need to be deployed on machines with different resource and accuracy constraints such as embedded devices and other IoT devices. This tool will help modify the model to be usable on such devices, and it will also automate the process.

## Design of the automated interface -

- Decrease memory footprint of the model based on target constraints. Incrementally replace operators such as - convolution, Fully Connected, activation functions, pooling operations and concatenation with their corresponding lower precision implementations( in other words quantize the operator) and after every change re-evaluate and check if the target conditions input by the user have been met.
- Increase accuracy of the model - This can be achieved by using a customized implementation of Neural Architecture Search. 
- Apart from the layers that are present in given pre-trained model, we will have a collection of frequently used layers such as - Identity, Convolution with different kernel sizes, average pooling, max pooling, dilated convolution, depthwise convolution etc.. 
- We will have a controller RNN algorithm that will sample layers from the above set with a particular probability distribution.
- The control algorithm will make incremental changes to the pre-trained model with the above sampled layer and based on the accuracy of the held-out validation dataset and the memory footprint of the newly updated model, we will update the probability distribution of the control algorithm.
- This process is repeated over iterations till the desired accuracy and resource constraints are met.
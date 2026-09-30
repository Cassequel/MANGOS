# PyTorch Intro MOdule
## Goal: Understand PyTorch Basics and make a small working Neural Network with multiple datasets and understand basic building blocks

I've been exposed to PyTorch before but, I was wanting to dive more into Tensors and why they are considered so important with Deep Learning. 
I followed along mainly with the PyTorch Quickstart tutorials to get a hold of the main topics 

- Tensors
- Dataset / Dataloaderes
- Transforms
- Neural Networks
- Autograd
- Optimizing Model Parameters

Once I had gone through all of those I went back to QuickStart and recreated it with a different dataset using the FGVCAircraft dataset instead of the FashionMNIST dataset. The differences I had to handle differently were resolution of the images were inconsistent and had to be resized. I initially resized to 64 * 64 but, that was too small for the model to have any significant accuracy or increase in accuracy. This was assumed however based on the naked eye. Another thing I had to change was the amount of varient labels the model ended up with, FashionMNIST had 10 but, FGVCAircraft needed 100 with their default labels. 

Experiments and Optimizations that were made:
When I first ran the first iteration of the train and test dataloaders I was receiving on average accuracy of 1% and loss of 4.6. These numbers are not good and essentially are no better than guessing at random chance. These numbers came from a crossentropy optimizer and no shuffling the order when iterating through epochs. To improve this accuracy we remade the model with a random seed and switched the optimizer to Adam and shuffled the training batches. This increased the accuracy slightly with the ending accuracy being 2.3%. The good news being that the accuracy was increasing after every epoch, this was not the case before.

AI recommends to change the network to a pretrained convolutional neural network since they're pretrained to learn visual patterns like edges, shapes, and parts of objects. While this code uses a multilayer perceptron network, copied from the PyTorch quickstart, an MLP is much better with is the best for a tutorial and to tunderstand the basics of defining models, calculating losses, backpropagation, and updating weights. A CNN is better architecture for image recognition. Plus the FashionMNIST and FGVCAircraft are very different in terms of how the images look and what the models are looking for.

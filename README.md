# GoogLeNet or Inception V1
This summery pertains the winning *Convolutional Neural Network* (CNN) with ***INCEPTION***-architecture of *ImageNet Large-Scale Visual Recognition Challenge* (ILSVRC) in 2014.  Especially its inception module, which made it a state-of-the-art CNN at this time. The network submittted for this competition was called **GoogLeNet**.

**Motivations**
> - Produce a network that can handle smaller sizes of training data sets, which would reduce overall cost of labeling the training data.
>- Keep the computational effort in a affordable relation to the network size and performance quality.
>- Reduce the amount of paramenter in the network to decrease the overhead of lookups and cache misses.

## Common architecture

### Overview
The 22 or (27 with pooling layers, ca. 100 in complete) layer deep CNN was designed with an focus on computational efficiency and practicality.

### Receptive and early layers
The receptive layer takes 224x224x3 data blocks which equals the data size of an three channel (RGB) 224x224 pixel image. The beginning layers are constructed after classical CNN architecture (see as an example AlexNet). These layers are used to strenghten loud/important features and structurize the raw data through the implementation of lateral inhibition.

### Auxiliary calssifiers
These additional outputs are especially helpful in backpropagation. Later research shows, that the effect is minor (0.5%) and only one of them would have solved the problem of very discriminative features in the middle of the network. The architectural structure uses one average pooling layer, a convolutaional layer for the adjustance of dimensionality, a fully connected layer with 1024 units, a 70% dropout layer and a linear layer with softmax activation.



## Special architecture

### The inception module
The Inception-architecture of GoogLeNet is primarily driven by the idea of the *inception module*, which also gave it its name. This architectural feature also led to the great success of the network. From the beginning modest gains were observable in comparision with networks based on the *Network in Network* (NIN) model. Perfectly balanced an inception network performs 3 – 10x faster than qualitatively similar performing networks without an inception architecture.

> Through usage of a 1x1 convolution the spacial output size stays the same and reduces the dimensionality while it saves raw unconvoluted data for later layers. Also before the 3x3 & 5x5 convolutional layers this 1x1 layer reduces the dimensionality what saves precious computational resources. These are called dimensionality-reducing linear projection layers.

> Aferwards the depth concationation function gets the spatial input size as a highest value and with reduced dimensionality where it pads all the expensive spatial size reduced outputs in. Regarding memory efficency during training, it seems beneficial to use inception modules only in higher layers. 

> This architecture enables networks to have an increased number of units (convolutions, pooling, etc.) at oncce without an overhead of computational complexity in later layers. Through the constant use of dimensionality reduction immediately before expensive convolutions with large filters.

The module is best used for features of higher abstraction. Therefore it is recommended to use the module in *deeper* layers, when the original data is already very abstract and spatial features decreased.

## Training
The GoogLeNet networks were trained with an asyncronous stochastic gradient descent (SGD) with an learning rate of 0.9 and a fixed learning rate schedule which applies a 4 % reduction every 8 epochs. 

## ILSVRC 2014
GoogLeNet won the ILSVRC in 2014 with an top-5 error rate of 6.67 % The team trained seven equal networks in paralell to perform ensemble prediction. 


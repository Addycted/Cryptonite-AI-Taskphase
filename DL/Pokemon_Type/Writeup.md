
For the Pokemon Type Classification task, I implemented a custom InceptionNet-based architecture after iterating through several model designs. My approach evolved as follows:

1. Simple CNN: Started with a two basic convolutional neural networks, which yielded feasible results but was computationally heavy.
2. Single network with dual output: Implemented a CNN with two outputs, which was quicker but led to significantly worse results.
3. ResNet: Moved to a ResNet architecture, which showed only slight improvement.
4. Various architectures: Experimented with AlexNet, VGGNet, and custom deeper CNNs, but faced issues with one type having high accuracy while the other plateaued.
5. InceptionNet: Implemented an InceptionNet architecture, which provided the best outcomes with 50% accuracy on type1 and 63% on type2.
6. Custom PokeCeption: Finally, developed a custom InceptionNet-based architecture with separate classification blocks for each type.

Preprocessing pipeline:

1. Resized images to 128x128 pixels
2. Converted images to tensors
3. Matched images with their corresponding type information from the CSV file
   
The final model, named PokeCeption, is a custom InceptionNet-based architecture designed for dual-type Pokemon classification. Key components include:

1. Input layer: Accepts 128x128 RGB images
2. Initial layers: Convolutional and max pooling layers for initial feature extraction
3. Inception modules: Multiple inception modules with varying filter sizes and depths
4. Dual classification blocks: Two separate classification paths, each containing:
i) Adaptive average pooling
ii) Flattening layer
iii) Dropout for regularization
iv) Fully connected layer for final classification

The use of inception modules allows for multi-scale feature extraction, which is beneficial for capturing diverse Pokemon characteristics. The model uses two separate classification blocks to specialize in predicting Type1 and Type2 independently.

Hyperparameter tuning: Found optimal performance with learning rate of 0.0001, Adam optimizer, and 35 epochs.

This approach achieved the best balance between accuracy for both Pokemon types, overcoming the challenge of one type dominating the other in previous iterations.

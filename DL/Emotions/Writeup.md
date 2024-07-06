For the Human Emotion Detection task, I implemented a custom ResNet architecture after iterating through several model designs. My approach evolved as follows:

1. Simple CNN: Started with a basic convolutional neural network, which yielded poor accuracy on both training and testing sets.
2. AlexNet-inspired model: Moved to a deeper architecture inspired by AlexNet. This improved training accuracy to 87% but led to severe overfitting, with test accuracy dropping to 13%.
3. VGGNet attempt: Implemented a VGGNet-inspired model, which proved computationally complex. It achieved 98% training accuracy but only 23% testing accuracy.
4. Custom ResNet: Developed a custom ResNet architecture, which improved generalization, achieving 83% training accuracy and 40% testing accuracy.
5. Residual weight tuning: Finally, I introduced a residual weight parameter to fine-tune the impact of skip connections.

Preprocessing pipeline:

1. Random horizontal flips and slight rotations for data augmentation to handle the class imbalance 
2. onversion to tensor
3. Normalization using ImageNet mean and standard deviation
4. Conversion to grayscale

The final model is a custom ResNet architecture designed for emotion detection. Key components include:

1. Input layer: Accepts grayscale images
2. Initial convolution: A convolutional block that processes the input image
3. Four residual stacks: Each stack contains:
i) A convolutional block that may downsample
ii) Two convolutional blocks in a residual connection with tunable residual weight
4. Classifier:
i) Adaptive average pooling to reduce spatial dimensions
ii) Flattening layer
iii) Two fully connected layers with dropout for regularization
iv) Output layer with neurons corresponding to the number of emotion classes

The use of residual connections with tunable weights allows for more flexible training. The model progressively increases the number of filters (64 -> 128 -> 256 -> 512) while reducing spatial dimensions, capturing increasingly complex features.

Hyperparameter tuning: Found optimal performance with learning rate of 0.001, Adam optimizer, 40 epochs, and a residual weight of 0.4.

For the dog breed classification task, I implemented a custom ResNet architecture after iterating through several model designs. My approach evolved as follows:

1) Simple CNN: Started with a basic convolutional neural network, which yielded low accuracy, indicating it was underfitting the complex task of breed classification.
2) AlexNet-inspired model: Moved to a deeper architecture inspired by AlexNet. This improved accuracy significantly but led to overfitting, as evidenced by high training accuracy but poor generalization to the test set.
3) Modified AlexNet: Added dropout layers to combat overfitting. This improved generalization but slowed down training considerably.
4) Hyperparameter tuning: Adjusted learning rate, batch size, and optimizer parameters to find a balance between training speed and model performance.
5) ResNet implementation: Finally, I designed a custom ResNet architecture. This model includes multiple stacks of convolutional blocks with skip connections, allowing for deeper training without the vanishing gradient problem.

Preprocessing pipeline:

1. Resized images to 32x32 pixels
2. Implemented data augmentation with random horizontal flips and slight rotations
3. Applied normalization using ImageNet mean and standard deviation

The final model is a custom ResNet (Residual Network) architecture designed for dog breed classification. Key components include:

1. Input layer: Accepts 32x32 RGB images.
2. Initial convolution: A convolutional block that processes the input image.
3. Four residual stacks: Each stack contains:
  i) A convolutional block that may downsample (stride=2)
  ii)Two convolutional blocks in a residual connection
4. Classifier:
  i)Adaptive average pooling to reduce spatial dimensions
  ii)Flattening layer
  iii)Two fully connected layers with dropout for regularization
  iv)Output layer with neurons corresponding to the number of dog breeds

The use of residual connections allows for deeper training by mitigating the vanishing gradient problem. The model progressively increases the number of filters (64 -> 128 -> 256 -> 512) while reducing spatial dimensions, capturing increasingly complex features.

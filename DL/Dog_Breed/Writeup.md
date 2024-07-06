For the Dog Breed classification task, I implemented a custom CNN architecture after iterating through several model designs. My approach evolved as follows:

1. Simple CNN: Started with a basic 3-layer convolutional neural network using ReLU, which didn't reach the required accuracy on both training and testing sets.
2. VGGNet-inspired model: Moved to a deeper architecture inspired by VGGNet. This improved training accuracy significantly (close to 99%) but led to poor generalization, with test accuracy dropping to 39%.
3. Simplified custom architecture: Developed a simplified version using ReLU, AvgPool, and Conv layers. This improved generalization, achieving around 89% training accuracy and 85% testing accuracy.
4. LeakyReLU implementation: Finally, I designed a custom architecture using LeakyReLU activations, which provided the best performance.

Preprocessing pipeline:

1. Resized images to 32x32 pixels as the dataset images were not uniform in dimensions
2. Converted images to tensors so it is compatible with PyTorch

The final model is a custom CNN architecture designed for image classification. Key components include:

1. Input layer: Accepts 32x32 RGB images
2. Feature extraction: Three convolutional blocks, each containing:
i) A convolutional layer with increasing filter sizes (64 -> 128 -> 256)
ii) LeakyReLU activation
iii) Max pooling for downsampling
3. Classifier:
i) Flattening layer
ii) Two fully connected layers (512 units, then num_classes)
iii) LeakyReLU activation between fully connected layers

The use of LeakyReLU activations helps address potential vanishing gradient problems. The model progressively increases the number of filters while reducing spatial dimensions, capturing  complex features.

Hyperparameter tuning: Found optimal performance with learning rate of 0.001, Adam optimizer, and 25 epochs.

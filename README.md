# Crop Identification

## Introduction
This project focuses on developing a machine learning-based **task recognition system** to classify various **crop types from images**. The primary objective is to accurately identify different crops using a given dataset, which includes ten distinct crop types and bare land. Each class in the dataset consists of **300 images** with a resolution of **224x224 pixels**, ensuring balanced data for training and evaluation.

The project employs a robust training and evaluation pipeline using **PyTorch**, integrating data augmentation techniques and regularization to enhance the model's performance. The ultimate goal is to achieve a high accuracy in crop recognition, which has significant implications for **agricultural analysis** and **precision farming**.

## Data Description
The dataset used in this project contains images of the following ten crop types along with a class for bare land:

- **Guava**
- **Atemoya**
- **Carrot**
- **Cabbage**
- **Banana**
- **Grape**
- **Pineapple**
- **Mango**
- **Papaya**
- **Pumpkin**
- **Bare land**

Each class comprises **300 images**, and all images are uniformly sized at **224x224 pixels**. This standardization ensures consistency in the model training and evaluation processes.

### Data Transformation
To enhance the model's learning capabilities, specific preprocessing steps are applied to both training and test data, as described below:

1. **Training Data Transformations**:
   - **Resizing**: All images are resized to **224x224 pixels** to maintain uniformity across the dataset.
   - **Random Horizontal Flip**: The images are flipped horizontally with a probability of **50%**, introducing variation to prevent the model from overfitting.
   - **Random Vertical Flip**: The images are also flipped vertically with a **50% probability**, further augmenting the training data.
   - **Color Jitter**: Random adjustments to the brightness of images (up to **50%**) are applied, creating variations in lighting conditions to make the model more robust.
   - **Conversion to Tensor**: Images are converted into tensor format to make them suitable for neural network input.

2. **Test Data Transformations**:
   - **Resizing**: Test images are resized to **224x224 pixels** to ensure they match the dimensions of the training data.
   - **Conversion to Tensor**: Test images are converted into tensors without additional augmentations to provide a standardized dataset for evaluating the model's performance.

These transformations are designed to increase the model's generalization capability by creating diverse variations in the training data while maintaining the consistency of the test data for accurate performance evaluation.

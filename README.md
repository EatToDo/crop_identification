# Crop Identification

## Introduction
This project focuses on developing a machine learning-based **task recognition system** to classify various **crop types from images**. The primary objective is to accurately identify different crops using a given dataset, which includes ten distinct crop types and bare land. Each class in the dataset consists of **300 images** with a resolution of **224x224 pixels**, ensuring balanced data for training and evaluation.

The project employs a robust training and evaluation pipeline using **PyTorch**, integrating data augmentation techniques and regularization to enhance the model's performance. The ultimate goal is to achieve a high accuracy in crop recognition, which has significant implications for **agricultural analysis** and **precision farming**.

## Data Description
The dataset used in this project contains images of the following ten crop types along with a class for bare land:

- **Guava**
![Guava Image](pictures/guava.15.png)
- **Atemoya**
![Atemoya Image](pictures/atemoya.13.png)
- **Carrot**
![Carrot Image](pictures/carrot.61.png)
- **Cabbage**
![Cabbage Image](pictures/cabbage.6.png)
- **Banana**
![Banana Image](pictures/banana.19.png)
- **Grape**
![Grape Image](pictures/grapes.26.png)
- **Pineapple**
![Pineapple Image](pictures/pineapple.14.png)
- **Mango**
![Mango Image](pictures/mango.3.png)
- **Papaya**
![Papaya Image](pictures/papaya.20.png)
- **Pumpkin**
![Pumpkin Image](pictures/pumpkin.19.png)
- **Bare land**
![Bare land Image](pictures/bareland.11.png)

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

## Methodology and Model Selection

### Algorithm Selection
The primary algorithm used in this project is the **Convolutional Neural Network (CNN)**. CNNs are a type of deep learning algorithm that are particularly well-suited for image classification tasks due to their ability to automatically and adaptively learn spatial hierarchies of features from input images. We chose CNNs because of their proven effectiveness in recognizing patterns, textures, and shapes in image data, which is essential for accurately classifying different crop types from their visual representations.

### Model Architecture
The architecture of our model is based on a multi-layer convolutional neural network that includes the following layers:
- **Convolutional Layers**: Extract low-level features like edges, textures, and patterns from the images.
- **Activation Functions**: We use ReLU (Rectified Linear Unit) to introduce non-linearity, which helps the network learn complex patterns.
- **Pooling Layers**: Max-pooling layers are applied to reduce the spatial dimensions of the feature maps, thereby lowering computational cost and controlling overfitting.
- **Fully Connected Layers**: These layers take the high-level features learned by the convolutional layers and translate them into class scores.
- **Softmax Layer**: The output layer uses the softmax activation function to produce probability distributions for each class in the dataset, enabling multi-class classification.

This architecture is specifically designed to handle the classification of multiple crop types and has been optimized for accuracy and computational efficiency.

### Hyperparameter Tuning
For hyperparameter tuning, we focused on optimizing several key parameters to improve model performance:
- **Learning Rate**: We experimented with different learning rates, starting from an initial value (e.g., 0.01) and adjusting it dynamically based on the model's convergence.
- **Batch Size**: A batch size of 16 was selected to balance training speed and memory efficiency.
- **Optimizer**: We used the **Stochastic Gradient Descent (SGD)** optimizer with a momentum of 0.9. The momentum helps in accelerating gradients vectors that are in the right directions, thus leading to faster converging.
- **Data Augmentation**: Techniques like horizontal and vertical flipping, as well as color jittering, were used to artificially increase the diversity of the training dataset.

These hyperparameters were fine-tuned using a combination of grid search and empirical analysis to find the optimal configuration that maximizes the model's accuracy while minimizing the loss.

## Experimental Design

### Training/Test Split
The dataset was divided into two main subsets to train and evaluate the model:
- **Training Set**: 80% of the data was used for training the model. This subset was used to learn the features and patterns associated with each crop type.
- **Test Set**: The remaining 20% of the data was reserved as the test set, which provides an unbiased evaluation of the model's performance on unseen data.

This split ensures that the model is trained on a sufficiently large portion of the dataset while being evaluated on a separate set to gauge its generalization capabilities.

### Model Training
The model training process involved the following steps:
1. **Data Preprocessing**: The input images were resized to 224x224 pixels and underwent data augmentation to improve the model's robustness against overfitting.
2. **Training Loop**: The training was conducted over a fixed number of epochs (controlled by the `config["epoch"]` parameter), during which the model's parameters were updated using backpropagation and the optimizer's learning rule.
3. **Batch Processing**: A batch size of 16 was used to process the data in smaller chunks, making the training process more memory efficient.
4. **Learning Rate and Optimizer**: We used an initial learning rate defined in the configuration file and the SGD optimizer with momentum to ensure faster convergence and stable updates.

### Evaluation Metrics
To comprehensively evaluate the model's performance, we used the following metrics:
- **Accuracy**: Measures the overall percentage of correctly classified samples in the dataset.
- **Precision**: Evaluates the accuracy of positive predictions, i.e., how many of the predicted positive instances were actually positive.
- **Recall**: Measures the ability of the model to identify all relevant instances, i.e., how many actual positives were correctly identified by the model.
- **F1 Score**: The harmonic mean of precision and recall, which provides a balanced measure that considers both false positives and false negatives.

These metrics were chosen to provide a thorough understanding of the model's strengths and weaknesses in handling class imbalances and to give insight into its ability to generalize to new data.

The performance of the model was tracked and logged using TensorBoard, allowing for real-time visualization of the training and validation metrics such as loss, accuracy, precision, recall, and F1 score.

This experimental design enables systematic evaluation and continuous monitoring, ensuring that the model's improvements are guided by data-driven insights.


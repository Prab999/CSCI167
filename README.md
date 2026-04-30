# Deep Learning Portfolio

A collection of deep learning models built using Python. The primary goal of these projects was to design, train, and evaluate different architectures across distinct datasets. Following an iterative approach, I started with fundamental baseline models and progressively increased performance through hyperparameter tuning and scaling model complexity.

## Projects

### 1. CIFAR-10 Image Classification: Deep MLP vs. CNN (`/CIFAR-10-CNN-Classification`)
* **Objective:** Classify 32x32 RGB images across 10 classes to test how much benefit is gained from using CNNs over traditional deep networks for spatial data.
* **Process:** Started with a baseline Deep MLP (3 hidden layers), which immediately overfit the training data and generalized poorly. I then swapped to a 2-layer CNN. To fix initial underfitting, I increased the model capacity to 64 channels, added data augmentation (horizontal flips and random crops), and applied Batch Normalization to stabilize activations.
* **Results:** The CNN hit 74.4% validation accuracy in just 10 epochs (limited by hardware/training time constraints), easily beating the Deep MLP's 55%. Spatial feature extraction and architectural inductive bias were the clear winners here.

### 2. NBA Hall of Fame Prediction: Tabular Data (`/NBA-Hall-Of-Fame-Prediction`)
* **Objective:** Binary classification to predict Hall of Fame induction using a tabular dataset of ~3,000 rows and ~40 features.
* **Process:** I engineered custom features (adding MVP, All-NBA, All-Defensive selections, and Finals appearances) to the baseline dataset to make the classification task viable. I then compared a shallow MLP (1 hidden layer, 64 units) against a deep MLP (3 hidden layers). Because the dataset is highly imbalanced, I swapped MSELoss for BCEWithLogitsLoss to reduce false positives, applied a positive class weight of 3, and tested learning rates across optimizers.
* **Results:** The deep model barely outperformed the shallow baseline. It correctly identified 7 out of 11 true HOFers (compared to the shallow net's 6), with zero false positives for both. The extra depth didn't provide a justifiable advantage for this specific tabular data.

### 3. Additional Notebooks (`/Additional-Notebooks`)
* **Overview:** A collection of notebooks detailing core mathematical implementations and algorithm exercises.

## Key Takeaways
* **Architecture Matching:** Deep learning isn't just about choosing the deepest model; it's about matching the architecture to the dataset's complexity and structure.
* **Hyperparameters vs. Architecture:** Adjusting learning rates, adding weight decay, and utilizing class weights often dictated success more heavily than simply adding hidden layers.
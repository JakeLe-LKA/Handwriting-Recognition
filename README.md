# Handwritten character recognition using Convolutional Neural Networks (CNN)

## Project overview

This project focuses on building an end-to-end **handwritten character recognition system** using **Convolutional Neural Networks (CNNs)** on the **EMNIST Balanced dataset**.

Handwritten character recognition has broad **scientific and industrial applications**, including:
- Digitization of historical documents
- OCR for scanned texts
- Automated check processing in banks
- Reading addresses in postal services
- Grading handwritten exams in education

The goal is to design a lightweight yet effective CNN model that classifies 47 character classes (digits, uppercase and lowercase letters) with high accuracy and efficiency.

---

## Dataset Structure

| Property           | Description                                                                 |
|--------------------|------------------------------------------------------------------------------|
| **Dataset Name**   | EMNIST Balanced                                                              |
| **Source**         | [TensorFlow Datasets](https://www.tensorflow.org/datasets/catalog/emnist)   |
| **# of Classes**   | 47 (digits + uppercase + lowercase letters)                                  |
| **Image Size**     | 28 × 28 pixels                                                               |
| **Color Mode**     | Grayscale (1 channel)                                                        |
| **Label Format**   | Integer mapped to Unicode character                                          |

This dataset poses more challenges than MNIST due to the inclusion of **case-sensitive letters** and **visually similar characters** (e.g., ‘O’ vs ‘0’, ‘l’ vs ‘1’, ‘S’ vs ‘5’).

---

## Insights Summary

### Model performance

| Metric         | Value       |
|----------------|-------------|
| **Test Accuracy** | ~88%     |
| **Test Loss**     | 0.3473   |
| **Trainable Parameters** | 229,807 |

- The model generalizes well to unseen handwritten characters.
- Accuracy of **88%** means that about **1 in every 8 characters is misclassified**.

### 2. Frequent misclassifications

![](pictures/error_prediction.png)

- Characters that are visually similar are common sources of error:
  - 'O' vs '0'
  - 'l' vs '1'
  - 'q' or 'g' vs '9'

These errors are expected in grayscale single-character classification tasks, especially with similar pixel structures.

### 3. Model architecture

The CNN consists of:
- **2 Convolutional layers** (32 and 64 filters)
- **Max Pooling layers** for downsampling
- **Fully-connected Dense layers**
- **Dropout (50%)** to prevent overfitting

Configured with:
- Optimizer: Adam
- Loss Function: Sparse Categorical Crossentropy
- Batch Size: 128
- Epochs: 10

This compact architecture is lightweight and can be **deployed on mobile or edge devices**.

---

## Recommendations

### 1. Data augmentation
- Apply **rotation, shifting, zooming, or noise** to make the model more robust to diverse handwriting styles.
- Helps reduce overfitting and improve generalization to real-world input.

### 2. Increase model depth
- Consider using more convolutional filters or adding **Residual Blocks (ResNet-style)** to improve feature extraction without overfitting.

### 3. Transfer learning
- Replace the CNN with **pre-trained architectures** such as **MobileNetV2** or **EfficientNet** for better performance with fewer training epochs.

### 4. Multi-dataset training
- Combine **EMNIST** with other datasets (e.g., **IAM**, **HW-R**) to cover wider writing styles and improve robustness.

### 5. Move to word-level modeling
- Upgrade the project to recognize **sequences of characters** (words or sentences) using **CNN + RNN/Transformer architectures**.

### 6. Build interactive demo
- Deploy the model using **Streamlit** or **Gradio** to:
  - Visualize predictions on user input
  - Collect feedback for future model improvement
  - Demonstrate real-time OCR capability

---

## Conclusion

This project demonstrates that a relatively simple CNN model can effectively recognize handwritten characters with **88% accuracy** on a challenging, multi-class dataset. The model has potential to serve as the backbone for OCR systems in education, logistics, finance, and healthcare.

With further improvements such as data augmentation, deeper models, or transfer learning, this system can be scaled to full OCR pipelines.

#  **Training for AI Generated Image Detection**
##  **Datasets**
1. CIFAKE - https://www.kaggle.com/datasets/birdy654/cifake-real-and-ai-generated-synthetic-images
2. Artifact - https://www.kaggle.com/datasets/divyanshrastogi44/artifacts-cleaned
3. Genimage - https://www.kaggle.com/datasets/yangsangtai/tiny-genimage

All models take 32x32 images as input and classify each as REAL or FAKE

## **DenseNet-121**
*Initialize*: Model, optimizer, and data loaders.
*Training Loop*:
1. Train the model on batches.
2. Validate the model after each epoch.
3. Log metrics and update training history.
*Early Stopping*: Stops training when validation performance no longer improves.
*Final Evaluation*: Returns validation metrics and the complete training history.

*Metrics Summary*
1. Loss: Average loss across the dataset.
2. Accuracy: Ratio of correct predictions to total predictions.
3. Precision: Focuses on minimizing false positives.
4. Recall: Focuses on minimizing false negatives.
5. F1-Score: Harmonic mean of precision and recall.
6. Confusion Matrix: Provides detailed insight into prediction errors.

### **Trained on**
CIFAKE, Genimage and Artifact

##  **VIT tiny**
### **Trained on**
CIFAKE and Genimage

##  **PatchCraft**
### **Trained on**
CIFAKE and Genimage

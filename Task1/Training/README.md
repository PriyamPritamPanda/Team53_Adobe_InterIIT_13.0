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
*Dataset Preparation:*
1. Input images are processed into batches using the custom collate_fn.
2. Ground truth labels are also batched.

*Collate Function:*
The collate_fn function processes batches of examples into a suitable format for training:
1. pixel_values: Stacks image tensors into a batch tensor using torch.stack().
2. labels: Converts labels into a PyTorch tensor.
3. Returns: A dictionary with keys pixel_values (image data) and labels (ground-truth labels).
This ensures that batches are created with uniform tensor shapes during training and evaluation.

*Metrics:*
1. Accuracy Metric:
The accuracy metric is loaded using the evaluate library.
2. compute_metrics Function:
Extracts predictions and labels from the evaluation output.
Calculates predicted class labels by taking the argmax of the prediction logits.
Computes accuracy using the evaluate library and returns it in a dictionary.

### **Trained on**
CIFAKE and Genimage

##  **PatchCraft**
### **Trained on**
CIFAKE and Genimage

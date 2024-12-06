# **Adobe Task 1 Inference - Inter IIT Tech Meet 13.0**
This folder contains the inference notebook for Task 1 of the mid-prep Inter IIT Tech Meet 13.0 problem statement provided by Adobe. The objective of Task 1 is to classify images as fake or real.

**Model Overview**
For this task, we utilized three distinct models to classify the images:
1. ***DenseNet-121***:
   A convolutional neural network known for its compact and efficient feature extraction capabilities.
2. ***ViT-Tiny***:
   A vision transformer model that leverages self-attention mechanisms for image classification.
3. ***PatchCraft***:
   A custom model designed to capture fine-grained image artifacts.

# **Inference Strategy**
The following approach was used for inference:
1. ***Predictions***:
   Each of the three models was used to infer the labels of the test images.
2. ***Ensemble***:
   An ensemble strategy was applied to combine the predictions:
   

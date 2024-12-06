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
1. **Preprocessing**:
   * The test images were initially provided in .png format with filenames such as 1.png, 2.png, etc.
   * All .png images were converted to .jpg format to ensure compatibility with the models. 
2. ***Predictions***:
   * Each of the three models was used to infer the labels of the .jpg test images.
3. ***Ensemble***:
   * An ensemble strategy was applied to combine the predictions:
      * An image was classified as fake(1) if any one of the models assigned it as fake.
      * An image was classified as real(0) only if all three models assigned it as real.

# **Notebook Structure**
The notebook includes the following steps:
1. Loading the pre-trained weights for DenseNet-121, ViT-Tiny, and PatchCraft models.
2. Loading the test dataset.
3. Converting .png test images to .jpg.
4. Performing predictions using each model.
5. Applying the ensemble logic to finalize the predictions.
6. Saving the output.

# **Workflow**

![task1 pipeline (1)_page-0001](https://github.com/user-attachments/assets/98c88442-7f06-468e-94f8-085fc124ece1)

# **Output**
The output of the inference process is a list of dictionaries as follows:

[
  {
    "index": 1,
    "prediction": "real"
  },
  {
    "index": 2,
    "prediction": "fake"
  },
  ...
]

* index: Extracted from the image filename (e.g., 1 for 1.png).

# **State dicts of models used:**
* Densenet-121: https://www.kaggle.com/datasets/priyampritampanda/densenet-without-v2
* ViT-Tiny: https://www.kaggle.com/datasets/priyampritampanda/vit-tiny
* PatchCraft: https://www.kaggle.com/datasets/priyampritampanda/patchcraft

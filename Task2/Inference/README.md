# Inferencing Finetuned Qwen2-7B-VL-Instruct 

- This folder contains two Jupyter notebooks designed for artifact detection, classification, and explanation in images using the finetuned **Qwen-2 VL 7B Instruct** modeat

- Our Finetuned model can be found at https://www.kaggle.com/datasets/ghatotkachh/qwen7bfinetuned
---

## **Notebooks Overview**

### 1. **`exp_inference_groupwise.ipynb`**
This notebook focuses on **group-wise artifact classification and explanation**. It provides a structured pipeline for analyzing images by categorizing artifacts into predefined groups and generating explanations for each detected group.

#### **Key Features**:
- **Artifact Categories**: The notebook evaluates artifacts across six primary groups:
  - AI Defects
  - Biological Defects
  - Overprocessing
  - Reality Breaks
  - Scene Oddities
  - Texture Defects
- **Classification and Explanation**:
  - Detects relevant artifact categories in input images.
  - Generates localized, context-specific explanations for artifacts in each group.
- **Inference Time**:
  - ~230 seconds per image

---

### 2. **`task-2-inference.ipynb`**
This notebook emphasizes **artifact detection and detailed explanation at the individual artifact level**, leveraging a comprehensive list of the 70 predefined artifact types.

#### **Key Features**:
- **Artifact Detection**:
  - Detects specific artifact types such as inconsistent object boundaries, texture anomalies, and lighting inconsistencies.
- **Explanation Generation**:
  - Produces concise, context-specific explanations when artifacts are detected.
- **Visualization**:
  - Annotates analyzed images with detected artifacts and their evaluations.
- **Inference Time**:
  - ~78 seconds per image  

#### **Applications**:
- Forensic image analysis for detecting unnatural features.
- Detailed image dataset validation.


---

## **Summary of Differences**
| Feature                           | `exp_inference_groupwise.ipynb`              | `task-2-inference.ipynb`              |
|------------------------------------|---------------------------------------------|---------------------------------------|
| **Granularity**                    | Group-wise artifact classification          | Individual artifact detection         |
| **Artifact Categories**            | 6 predefined groups                         | 70+ specific artifact types           |
| **Inference Time**                 | ~230 seconds per image                      | ~78 seconds per image                 |
| **Processing Mode**                | Grouped artifact processing                 | Detailed individual artifact processing |

--- 

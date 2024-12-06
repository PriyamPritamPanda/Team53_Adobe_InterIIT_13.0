# Finetuning Qwen2-VL-7B-Instruct

- This folder contains an end-to-end implementation for classifying image artifacts into predefined groups using a Hugging Face `Qwen2-VL-7B-Instruct` model. The script handles dataset preparation, feature engineering, and fine-tuning with LoRA for efficient model adaptation. 

- Our Finetuned model can be found at https://www.kaggle.com/datasets/ghatotkachh/qwen7bfinetuned

---

## Table of Contents
1. [Overview](#overview)  
2. [Dataset Description](#dataset-description)  
3. [Preprocessing Steps](#preprocessing-steps)  
4. [Model Architecture and Configuration](#model-architecture-and-configuration)  
5. [Dependancies](#dependancies)  
6. [Training Details](#training-details)  
---

## Overview

This project trains a vision-language model to classify image artifacts into six categories:
- **Overprocessing**
- **Reality Breaks**
- **AI Defects**
- **Scene Oddities**
- **Surface, Depth and Edge**
- **Biological Defects**

Using Hugging Face's Qwen2-VL-7B-Instruct model with LoRA-based parameter-efficient fine-tuning, the script is optimized for high performance with limited computational resources.

---

## Dataset Description

The dataset includes image files categorized into artifact groups. Key steps:
- Two directories are processed: 
  - `Manually Annotated Dataset`
  - `Labeled Fake Artifacts`
- Each image is labeled with one or more artifact groups.  
- Final labels map to six predefined artifact categories.

---

## Preprocessing Steps

1. **Directory Processing**: Image paths and associated defect types are extracted and stored in a structured dictionary.
2. **Class Mapping**: Artifact group names are normalized to match predefined categories.
3. **Dataset Conversion**: Data is formatted for Hugging Face's `Dataset` class, supporting multi-label classification.
4. **Feature Engineering**: 
   - Image paths are stored as strings.
   - Labels are mapped to indices using `ClassLabel` and `Sequence` from Hugging Face's `datasets`.

---

## Model Architecture and Configuration

### Model Details:
- **Base Model**: `Qwen2-VL-7B-Instruct`  
- **Parameter Efficient Fine-Tuning**: LoRA configuration with the following:
  - `lora_alpha=16`
  - `lora_dropout=0.05`
  - `r=8`
- **Quantization**: 4-bit quantization with `BitsAndBytesConfig`.

---

## Dependancies
- Hugging Face Transformers, Datasets, Accelerate, Evaluate  
- Tensorboard, Pillow, bitsandbytes

## Training Details

### Data Preparation
- Input Data: Image paths and their labels are loaded into a pandas DataFrame and converted into a Hugging Face Dataset.
- Preprocessed Data: The dataset is tokenized and processed to align with `Qwen2-VL-7B-Instruct` specifications.

### Training Process
- **Fine-Tuning**: Using Hugging Face's `SFTTrainer` for supervised fine-tuning.
- **Data Collation**: Custom collator ensures proper handling of multi-modal data (text and images).

### Training Configurations:
- **Optimizer**: Fused AdamW (`adamw_torch_fused`)  
- **Scheduler**: Constant Learning Rate  
- **Precision**: bfloat16  
- **Warmup Ratio**: 0.03  
- **Epochs**: 2  

---



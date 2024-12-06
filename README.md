# Team53_Adobe_InterIIT_13.0

# **Abstract**

Identifying fake versus real images is crucial in combating misinformation and ensuring the integrity of digital content in today’s
AI-driven world. This report provides a comprehensive overview of the approach, experiments, and results for the mid-preparation phase of the Adobe problem statement in Inter IIT Tech 13.0. The problem statement encompassed two tasks:
**Task 1 - Detection of AI-Generated Images**, and **Task 2 - Artifact Identification and Explanation Generation**. For Task 2, the objective was to generate explanations detailing why an image might be considered fake if classified as such. The report is structured to first address Task 1, followed by Task 2.


## **Task 1: Detection of AI-Generated Images**

*Objective*:
Build a model that accurately identifies AI-generated images, focusing on those generated by diffusion and other advanced techniques. With the growing prevalence of AI-generated imagery, challenges such as Deepfakes and fabricated visuals are increasingly common. Effective detection is essential for applications in news verification, e-commerce, and personal identification, ensuring integrity and trust in digital media.

### **Challenges**

1. One of the primary challenges in this task was the dataset’s low image quality (32x32). At such a small resolution, distinguishing between fake and real images becomes significantly harder, as the features that could reliably indicate authenticity or forgery are often minimal or indistinct.
2. Additionally, the problem constraints on model size and inference time further complicated the task, requiring the use of simpler, lightweight architectures and restricting reliance on complex or computationally intensive models.

### **Training**

**Dataset creation**

1. Due to complex nature of the problem coupled with generalizablity issue and latency constraints, we created a more diverse and challenging dataset to complement the provided CIFAKE dataset. These dataset included- PixArt, GigaGAN, Abode Firefly and Diffusion V2 generated images.
This generated dataset was used to test and gauage the robustness of our models.
2. Adversarial Datasets were generated to check model security against such attacks. FGSM and PGD based adversarial images were respectively compiled into a dataset. Another dataset of adversarial examples generated using a resnet backbone was also used.
3. Other than these, Genimage and Artifact datasets for AI generated images were also used. (links in the training folder)

**Experimentation**

After rigorous experimentation with augmenations, adversarial training and several models of varying sizes, the best performance was exhibited by models trained on genimage, artifact and cifake datasets while keeping the practical constraints in mind.


### **Inference Pipeline**

The inference pipeline employed an ensemble of three models:

• **DenseNet-121**: A compact CNN architecture that uses densely connected layers to enhance feature reuse and gradient flow, making it efficient for extracting fine-grained visual features in low-resolution images.

• **ViT-Tiny**: A transformer-based model that processes images as patch embeddings, leveraging self-attention to capture global context and inter-patch relationships for effective image classification.

• **PatchCraft**: A texture-based classification approach that focuses on detecting inter-pixel correlation contrasts, which serve as a universal fingerprint for AI-generated images.
(Details in the Inference Folder)

We ensemble these using an 'OR gate' strategy for fake image prediction which proves to be practical as well as efficient within the given constraints.

### Results

We carefully considered the efficiency-accuracy trade-off and greatly prioiritised making an accessible solution with small model sizes and speedy detection.
**Final File Size : 52 MB**
**Overall Inferenec Time : 92 ms**

## **Task 2:: Artifact Identification & Explanation Generation**

*Objective:*
Develop a model that not only identifies distinguishing artifacts within images but also provides interpretable explanations for its classifications of real vs. AI-generated images. Many AI models are opaque "black boxes," making it difficult to trace the reasoning behind their outputs. To address this, participants should design a model that interprets and highl ights identifiable features in real and synthetic images.

### **Challenges**

1. *Low-Resolution Dataset*: Working with 32x32 images, as provided in the dataset, severely limits the amount of information available for models to identify and explain artifacts. For certain types of artifacts, the resolution made accurate detection nearly impossible.
2. *Artifact Detection Complexity*: Subtle, fine-grained artifacts often require an intricate understanding of model imperfections, image context, and domain-specific nuances. Many current models struggle to achieve this level of preci-
sion.
3. *Model Limitations*: Pre-trained models often lack the precision needed for nuanced artifact detection and require extensive fine-tuning to adapt to new datasets. Additionally,they struggle to provide detailed, context-aware explanations.
4. *Model Hallucinations*: The limited information in low-resolution images often leads to hallucinations, where models mistakenly identify artifacts that do not exist. Addressing this issue required crafting innovative prompts to guide the models toward more reliable results.

### **Training and Dataset Generation**

1. Initially, our approach primarily relied on pre-trained vision-language models. Instead of explicit training, we employed adaptive prompting strategies and artifact-specific categorization frameworks to enhance the models’ performance. To enhance detection accuracy, we manually annotated a subset of the CIFAKE dataset, categorizing
512px images into the six artifact groups. This annotation process enabled targeted fine-tuning, aligning the models with task-specific needs and improving their explanation generation. These images were then downscaled to 32x32 images and finetuned upon.
2. Experimentation with finetuning VLMs was done extensively.

### **Artifact Sub-classification**

To enable nuanced detection and explanation generation, artifacts were categorized into six groups:
1. AI Defects: Floating parts, noise on flat areas, weird perspectives, blurred details, ghosting, and repeated patterns
inherent to generative models.
2. Biological Defects: Misaligned or deformed features, fur errors, unrealistic eyes, asymmetry, and irregular facial
proportions.
3. Overprocessing: Artifacts caused by grid artifacts, cinematic looks, over-sharpening, dramatic lighting, and scale
issues due to excessive post-processing.
4. Scene Oddities: Logical inconsistencies such as metallic artifacts, distorted reflections, specular issues, shadow in-
consistencies, and glossy surfaces.
5. Reality Breaks: Implausible elements like non-manifold structures, asymmetric or disproportionate forms, impossi-
ble joints, and jagged edges.
6. Texture Defects: Depth anomalies, blurred edges, aliasing, texture bleeding, fake depth, synthetic appearances, and
color breaks.
These classes were used in the further pipelines to reduce inference time.

### **Inference Time Experimentation**

After experimenting with higher order question, multiple vision models and a multi-step artifact classifiaction scheme, Qwen2-VL-7B-Instruct was used. 
This comprehensive framework effectively combines vision-language models, adaptive prompting, and domain-specific artifact classification to distinguish real from AI-generated images. By focusing on interpretability and transparency, it sets a foundation for broader applications, including digital content verification and forensic
analysis. Future work will focus on integrating additional models, expanding artifact categories, and extending the framework to video and 3D content.

### **JSON Parsing**

All outputs were parsed into a standardized JSON format to enable seamless integration into analysis pipelines. This approach offered several key advantages:

• Easy Retrieval of Artifact-Specific Insights: The structured format allowed quick and efficient access to detailed
information about detected artifacts, categorized according
to the artifact taxonomy.

• Consistency in Workflows: Standardized outputs ensured uniformity across visualization tools and downstream
applications, simplifying integration and facilitating automation of analysis processes.


## Report 
A comprehensive and detailed report has been aadded to the repsitory with all the accounts of experimentation and a proper compilation of all results and observations. Refer to '53_m3_adobe.pdf'

## Final Results
Find our final results in '53_task1.json' and '53_task2.json' files in the repository.

## Repository Structure

**Task 1**

Folder contains codes for-

1. *Training*
2. *Inference*

for task 1, along with workflow and methodology explanations.

**Task 2**

Folder contains files for-

1. *Finetuning*
2. *Inference*

for task 2, complete with details regarding implementation










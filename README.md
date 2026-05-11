**Multi-Disease Medical Deepfake Detection System** 😱😱😱😱👨‍⚕️

An advanced, multi-tiered deep learning pipeline engineered to detect Generative AI (GAN) manipulation and synthetic anomalies in both Chest X-Rays (Pneumonia/Lung pathologies) and Brain MRI scans (Tumor imaging). This system provides real-time forensic verification to ensure the mathematical authenticity of clinical imaging.

🎯 Project Overview:

This project implements a complete, end-to-end forensic detection system for medical imaging. The pipeline achieves 99.96% detection accuracy on lung imaging through custom spatial domain analysis and utilizes a dynamic routing architecture to analyze multiple organ types seamlessly. By targeting both X-Ray and MRI modalities, it directly addresses the critical vulnerability of deepfake injection in diagnostic workflows and tumor detection systems.

Note on Intellectual Property: This repository serves as a technical portfolio demonstration. To protect pending intellectual property and the proprietary mathematical weights of the models, the .pth files and raw medical datasets are not publicly distributed.

✨ Key Features:

Dual-Organ Routing Engine: Dynamically routes preprocessed image tensors to highly specialized, organ-specific AI architectures based on the user's clinical selection.

Lung Specialist Engine: A custom-built, Heavyweight 4-block CNN (256-filter capacity) explicitly engineered to catch microscopic GAN checkerboard artifacts and algorithmic upscaling in Chest X-Rays.

Brain MRI Specialist: Leverages an EfficientNet-B0 architecture optimized for identifying synthetic manipulation, frequency domain anomalies, and synthetic texture mapping in neuroimaging (specifically T1/FLAIR tumor scans).

Real-time Web Interface: An enterprise-grade Gradio dashboard providing clinical simulations, exact Softmax confidence percentages, and dynamic visual reporting.

🏗️ System Architecture:

<img width="1347" height="347" alt="image" src="https://github.com/user-attachments/assets/76097f42-2b71-4ab9-93a0-6255ca0c3f0b" />






📁 Repository Structure:


          medical-deepfake-forensics/
          │
          ├── README.md                           # Project documentation and architecture details
          ├── final_multi_disease_dashboard.py    # Master Gradio UI deployment & Routing Engine
          ├── lungdetectiongantrainer.py          # Training loop for Custom Lung CNN
          ├── copy_of_test.py                     # Standalone inference and testing script
          ├── requirements.txt                    # Python dependencies
          │
          ├── data/                               # Dataset architecture (Raw files withheld for IP/Privacy)
          │   ├── lung_xray_data/                 # Lung forensics dataset
          │   │   ├── REAL/                       # Authentic Chest X-Rays
          │   │   └── FAKE/                       # Synthetic GAN-generated X-Rays
          │   └── brain_mri_data/                 # Neuroimaging dataset
          │       ├── REAL/                       # Authentic T1/FLAIR MRIs
          │       └── FAKE/                       # Synthetic DCGAN-generated MRIs
          │
          |└── saved_models/                       # Model Weights (Withheld for IP Protection)
          |    ├── custom_lung_detector.pth        # Custom 4-Layer CNN weights
          |    └── deepfake_detector_efficientnet.pth # EfficientNet-B0 weights
          ├── requirements.txt            # Python dependencies (torch, torchvision, gradio)
          ├── .gitignore                  # Git ignore rules




🔬 Technical Details:

Brain MRI Specialist (EfficientNet-B0):

      Input:224×224×3 RGB tensor (Standardized ImageNet formatting)
      
      Backbone: Pre-trained `EfficientNet-B0` (Utilizing Mobile Inverted Bottleneck Convolution and Squeeze-and-Excitation optimization)
      
      Modified Classifier Head:
      
             ├── AdaptiveAvgPool2d
             ├── Dropout (p=0.2)
             └── Linear (in_features=1280, out_features=2) 
        
      Output: [REAL, FAKE] probability
      
      Detection Method: Transfer learning explicitly fine-tuned to isolate synthetic DCGAN texture mapping, frequency domain anomalies,         and FLAIR/T1 intensity inconsistencies.


Custom Lung CNN Architecture (custom_lung_detector):

       Input: 224×224×3 RGB tensor

       ├── Conv2D (32 filters, 3×3) + BatchNorm2d + ReLU + MaxPool

       ├── Conv2D (64 filters, 3×3) + BatchNorm2d + ReLU + MaxPool

       ├── Conv2D (128 filters, 3×3) + BatchNorm2d + ReLU + MaxPool

       ├── Conv2D (256 filters, 3×3) + BatchNorm2d + ReLU + MaxPool
      
       ├── Flatten
      
       ├── Dense (512) + ReLU + Dropout (0.5)
      
       └── Dense (2) + Softmax

       Output: [REAL, FAKE] probability:

       Detection Accuracy
      
       Custom Lung CNN: 99.96% blind test validation accuracy
      
       Detection Method: Identifies GAN-generated upscaling artifacts and anomalous pixel gradients.



🎓 Academic Context:

Institution: VIT Bhopal University

Student: Kushagra Singh

Research Objectives:

      Engineer robust deepfake detection mechanisms for clinical data.

      Solve Out-of-Distribution (OOD) vulnerabilities in standard AI pipelines.

      Develop multi-tier, dynamically routed model architectures.




🔒 Medical Ethics & Privacy:

Dataset: Uses publicly available de-identified medical scans and internally generated synthetic data.

Compliance: Follows standard data anonymization guidelines.

Purpose: Academic research and educational demonstration.

Disclaimer: Not approved for clinical diagnostic use.



🛠️ Technologies Used:

Deep Learning: PyTorch 2.0+, TorchVision, Transfer Learning (EfficientNet-B0, MobileNetV2)

Architecture Design: Custom Convolutional Neural Networks (CNN)

Web Framework: Gradio

Development: Google Colab, Git/GitHub, CUDA/cuDNN GPU Acceleration


<img width="1366" height="768" alt="Screenshot (1062)" src="https://github.com/user-attachments/assets/91080b8e-cff0-4212-85b7-6468ba7dd4d6" />



🛑 Copyright & Licensing

© 2026 Kushagra Singh. All Rights Reserved.

This repository is provided strictly for academic portfolio demonstration. The proprietary code, model architectures, triage logic, and concepts herein may not be copied, reproduced, distributed, or utilized for commercial purposes without explicit written permission from the author. Patent Pending / IP Protected.

⚠️ Academic Use Only | Not for Clinical Diagnosis | Research Demonstration

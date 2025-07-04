# 🌐 Point Cloud Classification of Propeller Geometry Using DGCNN

## 🧾 Project Overview

This project implements a pipeline for classifying point cloud representations of propeller geometries using the **Dynamic Graph Convolutional Neural Network (DGCNN)**. The input data is sourced from the **APC Propeller Dataset**, which contains propeller geometry in `.peo` format. The workflow involves converting these files to point clouds, labeling ground truth, and applying a fine-tuned DGCNN model for classification.

The current implementation achieves high training accuracy but suffers from overfitting due to limited dataset diversity. Future work focuses on automating preprocessing steps and expanding the dataset for improved generalization.

---

## 🎯 Objectives

- 🔄 Convert propeller geometry from `.peo` to point cloud format  
- 🏷️ Annotate point clouds with ground truth labels  
- 🧠 Train and evaluate a DGCNN model for point cloud classification  
- 🧪 Address overfitting through dataset expansion and automation of preprocessing  

---

## 📂 Dataset

The project uses the **APC Propeller Dataset**, publicly available online. Each `.peo` file contains detailed geometric information about the propeller blades and hubs, which are processed to create point clouds suitable for machine learning.

---

## 🔧 Workflow

### 1. Data Acquisition
- Obtain `.peo` files from the APC Propeller Dataset

### 2. File Conversion
- `.peo ➝ .bem` using Julia script:  
  `julia peo_to_bem.jl input.peo output.bem`
- `.bem ➝ .stl` using **OpenVSP**
- ⚠️ Manual attachment of blades and hubs is required (automation planned)

### 3. Point Cloud Generation
- Use **CloudCompare** to convert `.stl` to point cloud format

### 4. Ground Truth Labeling
- Manually annotate point clouds in **CloudCompare**

### 5. DGCNN Model Application
- Preprocess point cloud for DGCNN input  
- Fine-tune the DGCNN model  
- Train and evaluate  

---

## 📈 Current Results

- ✅ **Training Accuracy:** High accuracy achieved with fine-tuned DGCNN  
- ⚠️ **Overfitting:** Small dataset leads to overfitting on training data  
- 🔍 **Validation:** Poor generalization on unseen data confirms the need for dataset expansion  

---

## 🔮 Future Improvements

### 🚀 Preprocessing Automation
- Develop a **Julia/Python script** to automate blade and hub attachment

### 📦 Dataset Expansion
- Add more diverse `.peo` files

### 🛠️ Model Optimization
- Use regularization, dropout, and better hyperparameter tuning

### 📊 Scalability
- Improve pipeline performance for large-scale datasets  

---

## 📋 Prerequisites

- **Julia** (v1.8 or later): `.peo ➝ .bem` conversion  
- **OpenVSP** (v3.30 or later): `.bem ➝ .stl` conversion  
- **CloudCompare** (v2.12 or later): Point cloud generation and labeling  
- **Python** (v3.8 or later)  
- **Libraries**: PyTorch or TensorFlow, NumPy, etc.  
- `requirements.txt` provided  
- DGCNN source: [https://github.com/WangYueFt/dgcnn](https://github.com/WangYueFt/dgcnn)

---

## ⚙️ Installation

### 1. Install Dependencies

```bash
# Julia
Download from https://julialang.org/

# OpenVSP
Download from https://openvsp.org/

# CloudCompare
Download from https://www.cloudcompare.org/

# Python Libraries
pip install -r requirements.txt

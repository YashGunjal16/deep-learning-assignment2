# 🌿 Plant Species Classification Using VGG-19

## 📌 Project Overview
This project implements **plant species classification** using **transfer learning with the VGG-19 model** on the **Swedish Leaf Dataset**. The model is fine-tuned for **high accuracy classification of 15 plant species** based on their leaf images.

---

## 🚀 Features
- ✅ **Pre-trained VGG-19 Model** with transfer learning  
- ✅ **Image Preprocessing & Augmentation** (resizing, rescaling, rotation, zoom)  
- ✅ **Fine-tuning of VGG-19** for improved classification  
- ✅ **Feature Map Visualization** to analyze model learning  
- ✅ **Performance Evaluation** (Accuracy, Precision, Recall, Confusion Matrix)  

---

## 📂 Dataset  
**Dataset:** [Swedish Leaf Dataset](https://www.cvl.isy.liu.se/en/research/datasets/swedish-leaf/)  

- **15 Plant Classes**  
- **Total Images:** 1125 (75 per class)  
- **Split:** 70% Training, 30% Testing  

---

## ⚙️ Methodology

This project follows a **transfer learning-based approach** using **VGG-19** for plant species classification. The methodology consists of the following steps:

### **1️⃣ Data Preprocessing & Augmentation**
- **Image Resizing:** 256×256×3 pixels  
- **Rescaling:** Normalize pixel values by dividing by 255  
- **Data Augmentation:**
  - Random **rotation** (±30°)
  - **Zoom** (range 0.1)
  - Ensuring variation in training data  

### **2️⃣ Model Selection & Modification**
- **Pre-trained VGG-19 Model (ImageNet weights)**
  - Used as a **feature extractor**
  - Top layers removed  
- **Custom Classifier Head Added:**
  - `GlobalAveragePooling2D()`
  - `Dense(512, activation='relu')`
  - `Dropout(0.5)`
  - `Dense(15, activation='softmax')`  

### **3️⃣ Model Training & Fine-Tuning**
- **Phase 1:**  
  - **Freeze VGG-19 layers** and train **only the custom head**  
  - **Optimizer:** Adam (learning rate **1e-4**)  
  - **Epochs:** 30  
- **Phase 2:**  
  - **Unfreeze top layers of VGG-19** for fine-tuning  
  - **Lower learning rate (1e-5)** for stability  
  - **Epochs:** Additional 20  

### **4️⃣ Model Evaluation & Visualization**
- **Performance Metrics:**
  - Accuracy, Loss, Precision, Recall, F1-score  
  - Confusion Matrix  
- **Feature Map Visualization**
  - Extracts leaf features to confirm model learning  

---

## 📊 Results Summary

| Metric               | Before Fine-Tuning | After Fine-Tuning |
|----------------------|-------------------|-------------------|
| **Training Accuracy** | 83.28%            | 99.85%            |
| **Validation Accuracy** | 96.14%        | **100%**          |
| **Test Accuracy**     | -                 | **100%**          |
| **Test Loss**        | -                  | **0.0068**        |

**🔍 Feature Map Visualization:**  
The model successfully extracts **leaf patterns and textures**, ensuring **accurate classification**.

---

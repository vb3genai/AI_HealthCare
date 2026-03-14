#  Alzheimer’s detection Using MONAI framework
A deep‑learning pipeline for classifying cognitive impairment levels from MRI images using **PyTorch** and **MONAI** (https://project-monai.github.io/). 
This project provides a full workflow from dataset preparation to model training, evaluation, and single‑image inference. This project is done locally on Windows 11 Pro laptop. To replicate the project download Alzheimer_Prediction.ipynb and run it locally or on google Collab Pro. 

**Note**: Due to image processing, model training takes bit time on locally and sometimes on Google Collab Pro though google collab pro is fast.

---

##  Project Overview  
This project builds a 2D convolutional neural network (ResNet‑18 - https://huggingface.co/microsoft/resnet-18 ) to classify MRI images into four below cognitive impairment categories:

- **No Impairment**  
- **Very Mild Impairment**  
- **Mild Impairment**  
- **Moderate Impairment**

The workflow includes preprocessing, augmentation, caching, training, validation, test evaluation, confusion matrices, and single‑image prediction.

---

##  Dataset Structure  
Download dataset from Kaggle - https://www.kaggle.com/datasets/lukechugh/best-alzheimer-mri-dataset-99-accuracy?resource=download 

Downloaded dataset follow this directory layout:

```
DataSet/
   train/
      No Impairment/
      Very Mild Impairment/
      Mild Impairment/
      Moderate Impairment/
   test/
      No Impairment/
      Very Mild Impairment/
      Mild Impairment/
      Moderate Impairment/
```

**Note** - test/ used as a validation set during training and evaluation

Each folder contains `.jpg` MRI images. Sample for each category is as below:

Mild Impairment

![Mild Impairment](https://github.com/vb3genai/AI_HealthCare/blob/main/sample_dataset/MildImpairment%20(1).jpg)


Moderate Impairment

![Moderate Impairment](https://github.com/vb3genai/AI_HealthCare/blob/main/sample_dataset/ModerateImpairment%20(1).jpg)


No Impairment

![No Impairment](https://github.com/vb3genai/AI_HealthCare/blob/main/sample_dataset/NoImpairment%20(1).jpg)


VeryMildImpairment

![VeryMildImpairment](https://github.com/vb3genai/AI_HealthCare/blob/main/sample_dataset/VeryMildImpairment%20(1).jpg)



---

##  Installation  
Install required libraries:

```bash
pip install monai nibabel matplotlib seaborn scikit-learn torch torchvision
```

---

##  Key Dependencies  (for information)
- **MONAI** – medical imaging deep learning framework  
- **PyTorch** – model training backend  
- **Nibabel** – MRI/NIfTI handling  
- **Matplotlib & Seaborn** – visualization  
- **Scikit‑learn** – evaluation metrics  

---

##  Preprocessing Pipeline  
The project uses MONAI framework to transforms for:

- Loading images  
- Ensuring channel-first format  
- Resizing to 96×96  
- Intensity scaling  
- Random flips (training only)  
- Tensor conversion  

Caching is used to speed up training.

---

##  Model Architecture  
**ResNet‑18** is used:

- Input channels: **1** (grayscale MRI)  
- Output classes: **4**  
- Loss: **CrossEntropyLoss**  
- Optimizer: **Adam (1e‑4)**  

---

##  Training  
The training loop includes:

- Forward pass  
- Loss computation  
- Backpropagation  
- Weight updates  
- Epoch‑level loss tracking  

Validation accuracy is computed after each epoch. 
**Note** A separate validation split is not created. Instead, the test/ folder is used for validation accuracy during training.

---

##  Evaluation  
The test set evaluation includes:

- Accuracy  
- Classification report  
- Confusion matrix (raw + normalized)  

---

##  Testing time - A Single‑Image Prediction  
A minimal inference example is included to load a single MRI slice, preprocess it, run the model, and display the predicted class using Matplotlib.

![alt text](https://github.com/vb3genai/AI_HealthCare/blob/main/sample_dataset/Test_A_Prediction/test_pred.png)
---

##  Visualizations  
The notebook generates:

- Training loss curve  
- Validation accuracy curve  
- Confusion matrices  
- Test image prediction plot  

---

##  Results Summary  
The model demonstrates the ability to distinguish between four levels of cognitive impairment using 2D MRI slices. Performance varies by class, with confusion matrices highlighting where misclassification occurs.

---

##  Future Enhancements  
Potential extensions include:

- 3D MRI modeling (full volumetric networks)  
- Grad‑CAM interpretability  
- Hyperparameter tuning  
---

## Conclusion  
This project provides a complete, reproducible deep‑learning pipeline for MRI‑based cognitive impairment classification using MONAI enabling anyone to build upon a solid foundation for clinical AI experimentation.

---

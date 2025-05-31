<p align="center">
  <img src="invisibility_cloak.jpg" alt="Invisibility Cloak" width="300"/>
</p>

# Adversarial Examples as Privacy Defenses

This project investigates how adversarial examples can serve as a form of resistance against facial recognition AI in public surveillance contexts. 
We examine Invisibility Cloak, which is designed to protect individuals from identification by subtly altering facial features in images using adverserial attack techniques. 
The audit focuses on evaluating the tool's technical effectiveness, transparency, and compliance with privacy and consumer protection standards.

---
## 📜 Setup
Invisibility Cloak, an Adversarial Image Perturbation tool, markets itself as a privacy shield. The primary output is a visually similar but adversarially perturbed version of an input image. This perturbed image is crafted so that it looks normal to the human eye but causes face recognition systems to fail, misidentify the person, or reject the image altogether.


## ⚙️ Key Features

- FaceNet (InceptionResnetV1) used to extract face embeddings from a subset of Labeled Faces in the Wild (LFW) dataset
- Invisibility Cloak based on PGD-based adversarial cloaking
- SVM classifier trained on original and cloaked training sets 
- Side-by-side comparison of predictions before and after cloaking
- Comparison dataframes (`df_before`, `df_after`) contain:
  - Name  
  - Race
  - Gender
  - Image  
  - True Label  
  - Predicted Label  

---

## How It Works

**📊 Data:**
1. **Load and Filter Data**  
   Images and labels are filtered based on a race mapping dictionary.

2. **Generate Embeddings**  
   Preprocessed images are passed through FaceNet to extract 512-D vectors.

3. **Train/Test Split**  
   A stratified split ensures fair representation of each class (person).



**🛡️ Invisible Cloak:**

**Cloaking (PGD Attack)**  
The adversarial system requires a dataset of facial images in order to train the perturbation. Specifically, the training process optimizes a universal perturbation vector that, when added to input images, disrupts the embeddings. Perturbations are trained on and applied only to White individuals in the training set. Here we 'implant' the issue into the system. 



**🤖 Face Recognition Models:** 
1.  **Train and Evaluate Classifier on original data**
    An SVM classifier is trained first on the original data, then evaluated on the untouched test set.
2.  **Train and Evaluate Classifier on cloaked data**
    An SVM classifier is trained on the cloaked data, then evaluated on the untouched test set.



**Build Comparison Tables:**  
Two Pandas DataFrames (`df_before`, `df_after`) are created to analyze how predictions change due to cloaking.

---

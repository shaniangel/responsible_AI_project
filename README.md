# 🛡️ Adversarial Examples as Privacy Defenses

This project investigates how adversarial examples can serve as a form of resistance against facial recognition AI in public surveillance contexts. 
We examine Invisibility Cloak, which is designed to protect individuals from identification by subtly altering facial features in images using adverserial attack techniques. 
The audit focuses on evaluating the tool's technical effectiveness, transparency, and compliance with privacy and consumer protection standards.

---
## 📁 Setup
•	Invisibility Cloak markets itself as a privacy shield, claiming “full invisibility” from facial recognition.

•	The company showcases: 100% evasion success — but the audit reveals these results were achieved only on commercial, open-source models in ideal conditions.

• Disproportionate failure on dark-skinned faces — audit reveals adversarial filters were less effective on Black users, but this was neither tested nor disclosed.


## 📌 Key Features

- FaceNet (InceptionResnetV1) used to extract face embeddings
- Invisibility Cloak based on PGD-based adversarial cloaking
- SVM classifier trained on original and cloaked training sets 
- Side-by-side comparison of predictions before and after cloaking
- Comparison dataframes (`df_before`, `df_after`) contain:
  - Name  
  - Race  
  - Image  
  - True Label  
  - Predicted Label  

---

## 🚀 How It Works

**Data:**
1. **Load and Filter Data**  
   Images and labels are filtered based on a race mapping dictionary.

2. **Generate Embeddings**  
   Preprocessed images are passed through FaceNet to extract 512-D vectors.

3. **Train/Test Split**  
   A stratified split ensures fair representation of each class (person).



**Invisible Cloak:**

**Cloaking (PGD Attack)**  
Perturbations are applied only to White individuals in the training set. Here we 'implant' the issue into the system. 



**Face Recognition Models:** 
1.  **Train and Evaluate Classifier on original data**
    An SVM classifier is trained first on the original data, then evaluated on the untouched test set.
2.  **Train and Evaluate Classifier on cloaked data**
    An SVM classifier is trained on the cloaked data, then evaluated on the untouched test set.



**Build Comparison Tables:**  
Two Pandas DataFrames (`df_before`, `df_after`) are created to analyze how predictions change due to cloaking.

---

# update_readme.py
import os

# === Configuration ===
# Folder where your images are stored (relative to README)
IMAGE_DIR = "images"

# Paths for images
confusion_matrices = [
    "confusion_matrix_1.png",
    "confusion_matrix_2.png",
    "confusion_matrix_3.png",
    "confusion_matrix_4.png"
]

loss_curves = [
    "loss_curve_train.png",
    "loss_curve_val.png",
    "accuracy_curve.png"
]

roc_curves = [
    "roc_curve_1.png",
    "roc_curve_2.png",
    "roc_curve_3.png",
    "roc_curve_4.png"
]

# === Read the original README ===
with open("README.md", "r", encoding="utf-8") as f:
    content = f.read()

# === Append the visualization section ===
visual_section = f"""
---

## 📊 Results and Visualizations

### 🔹 Confusion Matrices
Below are the confusion matrices for the four evaluated models:

| Model 1 | Model 2 |
|----------|----------|
| ![Confusion Matrix 1]({os.path.join(IMAGE_DIR, confusion_matrices[0])}) | ![Confusion Matrix 2]({os.path.join(IMAGE_DIR, confusion_matrices[1])}) |

| Model 3 | Model 4 |
|----------|----------|
| ![Confusion Matrix 3]({os.path.join(IMAGE_DIR, confusion_matrices[2])}) | ![Confusion Matrix 4]({os.path.join(IMAGE_DIR, confusion_matrices[3])}) |

---

### 📈 Training and Validation Curves

| Training Loss | Validation Loss | Accuracy |
|----------------|-----------------|-----------|
| ![Loss Curve 1]({os.path.join(IMAGE_DIR, loss_curves[0])}) | ![Loss Curve 2]({os.path.join(IMAGE_DIR, loss_curves[1])}) | ![Accuracy Curve]({os.path.join(IMAGE_DIR, loss_curves[2])}) |

---

### 🧠 ROC Curves

| Model 1 | Model 2 |
|----------|----------|
| ![ROC Curve 1]({os.path.join(IMAGE_DIR, roc_curves[0])}) | ![ROC Curve 2]({os.path.join(IMAGE_DIR, roc_curves[1])}) |

| Model 3 | Model 4 |
|----------|----------|
| ![ROC Curve 3]({os.path.join(IMAGE_DIR, roc_curves[2])}) | ![ROC Curve 4]({os.path.join(IMAGE_DIR, roc_curves[3])}) |

---
"""

# === Insert visual section before citation (if present) ===
if "## If you like this work" in content:
    parts = content.split("## If you like this work")
    updated_content = parts[0] + visual_section + "\n## If you like this work" + parts[1]
else:
    updated_content = content + visual_section

# === Write updated README ===
with open("README.md", "w", encoding="utf-8") as f:
    f.write(updated_content)

print("✅ README.md updated successfully with image sections!")

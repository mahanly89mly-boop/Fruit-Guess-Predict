# 🍌🍎🍊 Fruit Guess Predict

A lightweight machine learning project that classifies fruit images (**Banana, Apple, Orange**) using **color histograms** and a **Multi-Layer Perceptron (MLP) classifier**.


---

## 📑 Table of Contents

- [Overview](#-overview)
- [How It Works](#-how-it-works)
- [Project Structure](#-project-structure)
- [Requirements](#-requirements)
- [Installation](#-installation)
- [Usage](#-usage)
- [Model Details](#-model-details)
- [Results](#-results)
- [Future Improvements](#-future-improvements)
- [License](#-license)

---

## 🔎 Overview

**Fruit Guess Predict** is a simple, educational computer-vision pipeline that:

1. Reads fruit images from disk (Banana, Apple, Orange).
2. Extracts a **3D color histogram** as a feature vector for each image.
3. Trains an **MLPClassifier** (neural network) on these histogram features.
4. Evaluates the model with accuracy scores and a confusion matrix.
5. Predicts the fruit class of a new, unseen image.

This project is a great starting point for understanding classic feature-based image classification before moving on to deep learning (CNNs).

---

## ⚙️ How It Works

```
Image (.jpg)
     │
     ▼
Resize to 256x256
     │
     ▼
Compute 3D Color Histogram (8x8x8 bins, BGR channels)
     │
     ▼
Flatten + Normalize (sum = 1)
     │
     ▼
Feature Vector (512 values)
     │
     ▼
MLPClassifier (hidden_layer_sizes=512, activation="relu", solver="adam")
     │
     ▼
Predicted Label → Banana (0) / Apple (1) / Orange (2)
```

The core idea: each fruit has a distinctive color distribution, so a histogram of pixel colors — rather than raw pixels — is often enough to tell them apart.

---

## 📁 Project Structure

The notebook expects the following folder layout (relative to the notebook):

```
Fruit_Guess_Predict/
├── Fruit_Guess_Predict.ipynb
├── Banana/
│   ├── Banana.jpg
│   └── Banana2.jpg
├── Apple/
│   └── Apple.jpg
├── Orange/
│   └── Orange.jpg
└── Predict.jpg          # the image you want to classify
```

> ⚠️ Image paths in the notebook use Windows-style backslashes (`.\\Banana\\Banana.jpg`). On macOS/Linux, update these to forward slashes (`./Banana/Banana.jpg`).

---

## 🧰 Requirements

- Python 3.x
- Jupyter Notebook / JupyterLab
- numpy
- pandas
- opencv-python
- scikit-learn
- matplotlib
- seaborn

---

## 🚀 Installation

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/Fruit-Guess-Predict.git
cd Fruit-Guess-Predict

# 2. (Optional) Create a virtual environment
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install numpy pandas opencv-python scikit-learn matplotlib seaborn
```

---

## ▶️ Usage

1. Place your training images in the `Banana/`, `Apple/`, and `Orange/` folders.
2. Add the image you want to classify as `Predict.jpg` in the root folder.
3. Open the notebook:

   ```bash
   jupyter notebook Fruit_Guess_Predict.ipynb
   ```

4. Run all cells in order. The notebook will:
   - Load and preprocess the training images
   - Train the MLP classifier
   - Display accuracy scores and a confusion matrix
   - Predict and print the class of `Predict.jpg` (e.g. `Banana`, `Apple`, or `Orange`)

---

## 🧠 Model Details

| Component            | Detail                                   |
|-----------------------|-------------------------------------------|
| **Feature extraction** | 3D color histogram, 8×8×8 bins (BGR)      |
| **Feature vector size**| 512 (normalized to sum to 1)              |
| **Model**              | `MLPClassifier` (scikit-learn)            |
| **Hidden layer size**  | 512                                        |
| **Activation**         | ReLU                                       |
| **Solver**             | Adam                                       |
| **Train/Test split**   | 80% / 20%                                  |
| **Labels**              | `0 = Banana`, `1 = Apple`, `2 = Orange`   |

---

## 📊 Results

The notebook reports:

- **Training Accuracy** and **Test Accuracy** (printed as text)
- A **Confusion Matrix** heatmap (via `seaborn`)
- A **bar chart** comparing train vs. test accuracy

**Achieved Accuracy:**

| Metric            | Score |
|--------------------|-------|
| Train Accuracy     | 1.0   |
| Test Accuracy      | 1.0   |

**Confusion Matrix:**

![Confusion Matrix](Confusion_Matrix.png)

---

## 🔮 Future Improvements

- Expand the dataset with many more images per fruit class.
- Add data augmentation (rotation, brightness, flipping).
- Use `train_test_split` with `stratify=y` for balanced splits.
- Replace the handcrafted histogram features with a CNN-based feature extractor (e.g., transfer learning with MobileNet/ResNet).
- Save/load the trained model with `joblib` for reuse without retraining.
- Add a simple web or CLI interface for uploading and predicting new images.

---

## 📄 License

This project is released under the [MIT License](LICENSE). Feel free to use, modify, and distribute it for learning purposes.

---

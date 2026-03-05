# 👗 Fashion MNIST CNN Classifier

A Convolutional Neural Network (CNN) trained on the **Fashion MNIST** dataset to classify clothing items into 10 categories, achieving **~92% test accuracy**.

---

## 📋 Dataset Overview

The [Fashion MNIST](https://github.com/zalandoresearch/fashion-mnist) dataset is a drop-in replacement for the classic MNIST handwritten digits dataset. It contains:

| Property    | Value                    |
|-------------|--------------------------|
| Images      | 70,000 (60k train / 10k test) |
| Image Size  | 28 × 28 grayscale        |
| Classes     | 10 clothing categories   |

### Class Labels

| Label | Description |
|-------|-------------|
| 0     | T-shirt/top |
| 1     | Trouser     |
| 2     | Pullover    |
| 3     | Dress       |
| 4     | Coat        |
| 5     | Sandal      |
| 6     | Shirt       |
| 7     | Sneaker     |
| 8     | Bag         |
| 9     | Ankle boot  |

---

## 🏗️ Model Architecture

A Sequential CNN with the following layers:

```
Input         → (28, 28, 1)
Conv2D(32)    → ReLU, padding="same"    → (28, 28, 32)
MaxPooling2D  → (2, 2)                  → (14, 14, 32)
Conv2D(64)    → ReLU, padding="same"    → (14, 14, 64)
MaxPooling2D  → (2, 2)                  → (7, 7, 64)
Conv2D(128)   → ReLU, padding="same"    → (7, 7, 128)
MaxPooling2D  → (2, 2)                  → (3, 3, 128)
Flatten       →                          → (1152)
Dense(128)    → ReLU                     → (128)
Dropout(0.5)  →                          → (128)
Dense(10)     → Softmax                  → (10)
```

**Total Parameters:** 241,546

---

## 📊 Training Details

| Hyperparameter     | Value                    |
|--------------------|--------------------------|
| Optimizer          | Adam                     |
| Loss Function      | Categorical Crossentropy |
| Batch Size         | 128                      |
| Epochs             | 20 (with EarlyStopping)  |
| Validation Split   | 10%                      |
| Dropout Rate       | 0.5                      |

### Callbacks Used
- **EarlyStopping** — Monitors `val_loss`, patience=3, restores best weights
- **ModelCheckpoint** — Saves best model based on `val_accuracy`

---

## 📈 Results

| Metric         | Value  |
|----------------|--------|
| Test Accuracy  | 92.08% |
| Test Loss      | 0.2392 |

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/fashion-mnist-classifier.git
cd fashion-mnist-classifier
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the notebook
```bash
jupyter notebook notebooks/fashion_mnist.ipynb
```

The notebook includes:
- Data loading and preprocessing
- Model building, compilation, and training
- Evaluation on the test set
- Visualization of accuracy/loss curves
- Sample predictions with true vs predicted labels

---

## 📁 Project Structure

```
fashion-mnist-classifier/
├── README.md                          # Project documentation
├── .gitignore                         # Git ignore rules
├── requirements.txt                   # Python dependencies
├── notebooks/
│   └── fashion_mnist.ipynb            # Training & evaluation notebook
└── models/
    ├── fashion_mnist_cnn_final.keras  # Trained Keras model
    └── fashion_mnist_edge_model.tflite # TFLite edge model
```

---

## 🛠️ Requirements

- Python 3.10+
- TensorFlow 2.x
- NumPy
- Matplotlib

---

## 📄 License

This project is open-source and available for educational purposes.

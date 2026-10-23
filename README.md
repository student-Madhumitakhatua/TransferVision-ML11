# 🐱 TransferVision-ML11: Transfer Learning vs Fine-Tuning

A deep learning project comparing **Transfer Learning, Fine-Tuning, and CNN training from scratch** for three-class image classification using PyTorch and a pretrained ResNet18 model.

## 📌 Project Overview

This project investigates how ImageNet-pretrained models perform compared with a CNN trained from scratch.

Three experiments are conducted:

1. **Feature Extraction:** Freeze the pretrained ResNet18 backbone and train only the final classification layer.
2. **Fine-Tuning:** Unfreeze the final ResNet18 block (`layer4`) and classification layer to adapt pretrained features to the target dataset.
3. **CNN from Scratch:** Train a custom CNN without pretrained weights as a baseline.

The models classify images into three cat breeds from the Oxford-IIIT Pet dataset.

## 🎯 Objectives

* Implement transfer learning using pretrained ResNet18.
* Compare feature extraction and fine-tuning strategies.
* Train a CNN from scratch as a baseline.
* Apply image preprocessing and data augmentation.
* Evaluate models using test accuracy, precision, recall, and F1-score.
* Compare training time and model performance.
* Visualize training and validation loss and accuracy.

## 🗂️ Dataset

**Dataset:** Oxford-IIIT Pet Dataset

**Selected classes:**

* Abyssinian
* Bengal
* Birman

The selected subset contains **600 images**, with 200 images per class.

| Dataset Split |  Images |
| ------------- | ------: |
| Training      |     420 |
| Validation    |      90 |
| Testing       |      90 |
| **Total**     | **600** |

The dataset was split into training, validation, and testing sets using stratified sampling.

Images were resized to `224 × 224` pixels. ImageNet mean and standard deviation were used to normalize the inputs for the pretrained ResNet18 models.

Training images used random horizontal flipping, random rotation, and light color augmentation.

## 🛠️ Technologies Used

* Python
* PyTorch
* Torchvision
* NumPy
* Pandas
* Matplotlib
* Pillow
* Scikit-learn
* Jupyter Notebook
* Google Colab

## 🧠 Model Architectures

### 1. ResNet18 — Feature Extraction

* Uses pretrained ImageNet weights.
* Freezes the backbone parameters.
* Replaces the final fully connected layer with a three-class classifier.
* Trains only the classification head.

### 2. ResNet18 — Fine-Tuning

* Starts with pretrained ImageNet weights.
* Freezes most of the backbone.
* Unfreezes `layer4` and the final classifier.
* Uses lower learning rates for fine-tuning.

### 3. CNN from Scratch

* Uses a custom convolutional neural network.
* Starts with randomly initialized weights.
* Includes convolutional layers, batch normalization, ReLU activation, max pooling, and dropout.
* Trains without pretrained ImageNet features.

## 📊 Experimental Results

The following results were obtained from the completed three-epoch experiments.

| Model                         | Test Accuracy |     Training Time | Best Validation Accuracy |
| ----------------------------- | ------------: | ----------------: | -----------------------: |
| ResNet18 — Feature Extraction |    **97.78%** | **47.06 seconds** |                   95.56% |
| ResNet18 — Fine-Tuning        |        94.44% |     65.67 seconds |               **96.67%** |
| CNN from Scratch              |        60.00% |     87.57 seconds |                   61.11% |

### Key Findings

* **Feature Extraction achieved the highest test accuracy**, at 97.78%.
* Feature Extraction was also the fastest experiment, taking 47.06 seconds.
* Fine-Tuning achieved the highest validation accuracy, at 96.67%, but its test accuracy was lower than Feature Extraction's.
* The CNN trained from scratch achieved 60.00% test accuracy after three epochs.
* In these experiments, using pretrained ImageNet features provided a substantial advantage over training the small CNN from scratch.

These results describe this particular dataset split and training configuration. They do not guarantee the same performance on other datasets or splits.

## 📈 Visualizations

The notebook generates the following figures:

* Feature Extraction training and validation curves
* Fine-Tuning training and validation curves
* CNN from Scratch training and validation curves
* Test Accuracy Comparison
* Training Time Comparison

The figures are saved in:

`reports/figures/`

Add the generated PNG files to your repository to make the visual results available to readers.

## 📁 Project Structure

```text
TransferVision-ML11/
│
├── notebooks/
│   └── 01_transfer_learning.ipynb
│
├── data/
│   └── oxford-iiit-pet/
│
├── models/
│   ├── resnet18_feature_extraction.pth
│   ├── resnet18_finetuned.pth
│   └── scratch_cnn.pth
│
├── reports/
│   ├── comparison_results.csv
│   ├── experiment_summary.json
│   └── figures/
│       ├── feature_extraction_curves.png
│       ├── fine_tuning_curves.png
│       ├── scratch_cnn_curves.png
│       ├── test_accuracy_comparison.png
│       └── training_time_comparison.png
│
├── requirements.txt
├── .gitignore
└── README.md
```

Generated files may be absent from the repository until the notebook is run and those files are uploaded.

## ⚙️ Installation and Setup

### 1. Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd TransferVision-ML11
```

Replace `YOUR_GITHUB_REPOSITORY_URL` with your actual public repository URL.

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Run the notebook

Open the following notebook in VS Code Jupyter or Google Colab:

`notebooks/01_transfer_learning.ipynb`

Run the cells in order. The notebook downloads and prepares the dataset, trains all three models, evaluates test performance, generates plots, and saves experiment results.

**Note:** The first dataset download requires a stable internet connection and downloads an image archive of approximately 792 MB.

## 💾 Generated Outputs

After successful execution, the notebook creates:

* `reports/comparison_results.csv`
* `reports/experiment_summary.json`
* Training and validation curves
* Test accuracy comparison plot
* Training time comparison plot
* Saved model weights in `models/`

## 🔮 Future Improvements

* Train for more epochs and tune hyperparameters.
* Use learning-rate scheduling and early stopping.
* Evaluate additional pretrained architectures, such as EfficientNet.
* Add a confusion matrix and per-class performance plots.
* Test the models on additional image datasets.
* Improve experiment reproducibility with multiple random seeds.
* Add a prediction interface for new images.

## 👩‍💻 Author

**Madhumita Khatua**

BCA — Computer Science

Brainware University

## 📄 Conclusion

This project demonstrates the practical benefits of transfer learning for image classification. In the completed experiments, ResNet18 feature extraction achieved the best test accuracy and shortest training time, while fine-tuning achieved the highest validation accuracy. The CNN trained from scratch performed less effectively under the same three-epoch training budget.

The comparison highlights the value of pretrained representations when training data and computational resources are limited.

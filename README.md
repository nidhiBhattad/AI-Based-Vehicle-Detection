# Part 1: Historical Structure Image Classification Using CNN

## Project Overview

This project is part of the AIML Capstone work. The objective of Part 1 was to build a deep learning model for image-based object recognition.

The original problem statement expected an object detection model with bounding box localization. However, the provided dataset did not contain bounding box annotation files. The dataset contained only class-wise image folders. Therefore, this implementation was completed as a multi-class image classification project using a CNN-based transfer learning model.

## Dataset

The dataset contains historical architectural structure images arranged into class folders.

Total classes: 11

Classes used:

1. altar
2. apse
3. bell_tower
4. column
5. dome(inner)
6. dome(outer)
7. flying_buttress
8. gargoyle
9. portal
10. stained_glass
11. vault

## Dataset Summary

Initial dataset inspection:

* Total image files: 12,020
* Training images before split: 10,543
* Test images: 1,477
* Annotation files found: 0

Processed dataset:

* Training images: 8,440
* Validation images: 2,103
* Test images after cleaning: 1,474

Note: Three corrupted test images were detected and removed before final evaluation.

## Project Folder Structure

```text
Part1_Historical_Structure_CNN/
│
├── data/
│   ├── dataset_hist_structures 2 .zip
│   ├── extracted/
│   └── processed/
│       ├── train/
│       ├── val/
│       └── test/
│
├── models/
│   ├── historical_structure_cnn.keras
│   └── class_names.json
│
├── outputs/
│   ├── training_history.png
│   ├── classification_report.txt
│   ├── confusion_matrix.png
│   ├── test_metrics.json
│   ├── sample_predictions.png
│   └── sample_predictions.txt
│
└── src/
    ├── 01_dataset_inspection.py
    ├── 02_prepare_dataset.py
    ├── 03_fix_test_classes.py
    ├── 04_train_model.py
    ├── 05a_clean_corrupt_images.py
    ├── 05_evaluate_model.py
    └── 06_predict_sample_images.py
```

## Technologies Used

* Python
* TensorFlow
* Keras
* MobileNetV2
* Matplotlib
* Scikit-learn
* Pillow
* NumPy

## Model Architecture

The model uses MobileNetV2 transfer learning.

Architecture:

* Input image size: 224 x 224 x 3
* Data augmentation layer
* MobileNetV2 base model with ImageNet weights
* Global Average Pooling layer
* Dropout layer
* Dense output layer with softmax activation

Model details:

* Total parameters: 2,272,075
* Trainable parameters: 14,091
* Non-trainable parameters: 2,257,984

## Training Configuration

* Image size: 224 x 224
* Batch size: 32
* Epochs: 10
* Optimizer: Adam
* Learning rate: 0.0005
* Loss function: Categorical Crossentropy
* Metric: Accuracy

Callbacks used:

* ModelCheckpoint
* EarlyStopping
* ReduceLROnPlateau

## Training Result

Best validation accuracy:

```text
94.29%
```

Best epoch:

```text
Epoch 9
```

Model saved at:

```text
models/historical_structure_cnn.keras
```

## Test Evaluation Result

Final test result:

```text
Test Accuracy: 93.21%
Test Loss: 0.2077
```

The model was evaluated on 1,474 valid test images after corrupted images were removed.

## Sample Inference Result

Sample inference was performed on 12 randomly selected test images.

Result:

```text
Correct predictions: 11 / 12
Approximate sample inference accuracy: 91.67%
```

One gargoyle image was misclassified as bell_tower with 57.18% confidence. This is acceptable because some architectural classes have similar shapes, textures, and visual patterns.

## Important Limitation

The dataset did not contain bounding box annotation files such as XML, JSON, CSV, or TXT files. Because of this, true object detection and rectangular bounding box localization could not be implemented.

The original task expected object localization, but object detection requires labeled bounding boxes for each image. Since the provided dataset had only class-wise image folders, this project was implemented as a multi-class image classification solution.

If bounding box annotations are provided in the future, this project can be extended using object detection models such as:

* YOLO
* Faster R-CNN
* SSD
* RetinaNet

## How to Run the Project

### 1. Inspect Dataset

```powershell
& "C:\ProgramData\anaconda3\python.exe" "E:\nidhi\simplilearn\capstone\project2\Part1_Historical_Structure_CNN\src\01_dataset_inspection.py"
```

### 2. Prepare Dataset

```powershell
& "C:\ProgramData\anaconda3\python.exe" "E:\nidhi\simplilearn\capstone\project2\Part1_Historical_Structure_CNN\src\02_prepare_dataset.py"
```

### 3. Fix Class Folder Consistency

```powershell
& "C:\ProgramData\anaconda3\python.exe" "E:\nidhi\simplilearn\capstone\project2\Part1_Historical_Structure_CNN\src\03_fix_test_classes.py"
```

### 4. Train Model

```powershell
& "C:\ProgramData\anaconda3\python.exe" "E:\nidhi\simplilearn\capstone\project2\Part1_Historical_Structure_CNN\src\04_train_model.py"
```

### 5. Clean Corrupted Images

```powershell
& "C:\ProgramData\anaconda3\python.exe" "E:\nidhi\simplilearn\capstone\project2\Part1_Historical_Structure_CNN\src\05a_clean_corrupt_images.py"
```

### 6. Evaluate Model

```powershell
& "C:\ProgramData\anaconda3\python.exe" "E:\nidhi\simplilearn\capstone\project2\Part1_Historical_Structure_CNN\src\05_evaluate_model.py"
```

### 7. Run Sample Predictions

```powershell
& "C:\ProgramData\anaconda3\python.exe" "E:\nidhi\simplilearn\capstone\project2\Part1_Historical_Structure_CNN\src\06_predict_sample_images.py"
```

## Output Files

The project generates the following output files:

```text
outputs/training_history.png
outputs/classification_report.txt
outputs/confusion_matrix.png
outputs/test_metrics.json
outputs/sample_predictions.png
outputs/sample_predictions.txt
```

## Conclusion

A CNN-based transfer learning model using MobileNetV2 was successfully trained to classify historical structure images into 11 categories.

The final model achieved:

```text
Best Validation Accuracy: 94.29%
Test Accuracy: 93.21%
Sample Inference Accuracy: 91.67%
```

The result shows that the model performs well on unseen architectural structure images. However, due to the absence of bounding box annotation files, object localization using rectangular bounding boxes could not be implemented.

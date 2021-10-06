# Breast cancer classification with Keras and Deep Learning

## [The breast cancer histology image dataset](https://www.kaggle.com/paultimothymooney/breast-histopathology-images)

The original dataset consisted of 162 whole mount slide images of Breast Cancer (BCa) specimens scanned at 40x. From that, 277,524 patches of size 50 x 50 were extracted (198,738 IDC negative and 78,786 IDC positive). Each patch’s file name is of the format: uxXyYclassC.png — > example 10253idx5x1351y1101class0.png . Where u is the patient ID (10253idx5), X is the x-coordinate of where this patch was cropped from, Y is the y-coordinate of where this patch was cropped from, and C indicates the class where 0 is non-IDC and 1 is IDC.


![Dataset Sample](https://github.com/walae-br/breast-cancer-classification/blob/main/images/breast_cancer_classification_dataset.jpg?raw=true)



##### Project structure

```
.
├── datasets
│   ├── icd
│   ├── idc
│   │   ├── testing
│   │   │   ├── 0 [39720 entries exceeds filelimit, not opening dir]
│   │   │   └── 1 [15785 entries exceeds filelimit, not opening dir]
│   │   ├── training
│   │   │   ├── 0 [143082 entries exceeds filelimit, not opening dir]
│   │   │   └── 1 [56736 entries exceeds filelimit, not opening dir]
│   │   └── validation
│   │       ├── 0 [15936 entries exceeds filelimit, not opening dir]
│   │       └── 1 [6265 entries exceeds filelimit, not opening dir]
│   ├── IDC_regular_ps50_idx5 [279 entries exceeds filelimit, not opening dir]
│   └── orig [279 entries exceeds filelimit, not opening dir]
├── images
│   └── breast_cancer_classification_dataset.jpg
├── pipeline
│   │  
│   ├── cancernet.py
│   ├── config.py
│   └── __init__.py
├── build_dataset.py
├── README.md
└── train_model.py

```

Clone the repository:
```
git clone git@github.com:walae-br/breast-cancer-classification.git
```

Download the dataset [The breast cancer histology image dataset](https://www.kaggle.com/paultimothymooney/breast-histopathology-images)

create a dataset folder, orig and idc
```
mkdir datasets
mkdir datasets/orig
mkdir datasets/icd
```

Unzip the dataset file into datasets/orig
```
unzip breast-cancer-dataset.zip -x "IDC_regular_ps50_idx5/*"
```

Go ahead and create the training, testing, and validation split directory structure by executing the following command:

```
python build_dataset.py
```

Go ahead and train CancerNet on our breast cancer dataset.

```
python train_model.py
```

Results:
```
[INFO] evaluating network...
              precision    recall  f1-score   support

           0       0.89      0.90      0.90     39720
           1       0.75      0.73      0.74     15785

    accuracy                           0.85     55505
   macro avg       0.82      0.82      0.82     55505
weighted avg       0.85      0.85      0.85     55505

[[35867  3853]
 [ 4272 11513]]
acc: 0.8536
sensitivity: 0.9030
specificity: 0.7294
```
![Accuracy/Loss Plot](https://github.com/walae-br/breast-cancer-classification/blob/main/plot.png?raw=true)

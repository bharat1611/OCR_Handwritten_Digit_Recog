## Optical Character Recognition: ##
OCR stands for "Optical Character Recognition." It is a technology that recognizes text within a digital image. It is commonly used to recognize text in scanned documents and images.

## MNIST Dataset: ##
The MNIST database of handwritten digits with 784 features, raw data available at: http://yann.lecun.com/exdb/mnist/. It can be split in a training set of the first 60,000 examples, and a test set of 10,000 examples. It is a subset of a larger set available from NIST. The digits have been size-normalized and centered in a fixed-size image. It is a good database for people who want to try learning techniques and pattern recognition methods on real-world data while spending minimal efforts on preprocessing and formatting. The original black and white (bilevel) images from NIST were size normalized to fit in a 20x20 pixel box while preserving their aspect ratio. The resulting images contain grey levels as a result of the anti-aliasing technique used by the normalization algorithm. the images were centered in a 28x28 image by computing the center of mass of the pixels, and translating the image so as to position this point at the center of the 28x28 field.

The dataset was fetched using fetch_openml library:
```
from sklearn.datasets import fetch_openml
mnist = fetch_openml("mnist_784")
```

## About the model: ##
Here. we have created a detector that detects 2 correctly. We can easily do so for other digits too.

We have used a Logistric Regression model with a tolerance of 0.1. The model was fitted quite easily.
```
from sklearn.linear_model import LogisticRegression
clf = LogisticRegression(tol = 0.1)
#specify solver = "lbfgs"
clf.fit(x_train, y_train_2)
```
The **cross-val-score** of the model was calculated with cv=3 and scoring accuracy. 
```
from sklearn.model_selection import cross_val_score
a = cross_val_score(clf, x_train, y_train_2, cv=3, scoring="accuracy")
print(a)
```
The output for the segment was : [0.9778  0.97745 0.97975].

The mean score of cross_val_score:
```
a.mean()
```
_0.9783333333333334_

This wraps up the project. Thank you.


# terrain-detection

## Introduction

Individuals with lower limb amputations usually depend on prosthetic devices to restore the basic walking function. Lower-limb robotic prosthetics can benefit from context awareness to provide enhanced comfort and safety to the amputee. In this study, a terrain identification system based on inertial measurement units \(IMU\) streams collected from the lower limb is developed. The system for a prosthetic leg uses visual and inertial sensors though, and in this study, the viability of terrain identification without the visual data is tested. With such information, the control of a robotized prosthetic leg can be adapted to changes in its surrounding.

Hence, this is a classification task to find different terrains from time series data. The idea is to train a neural network using given data to classify which terrain an unknown data represents.

## Dataset Description

- "_x" files contain the xyz accelerometers and xyz gyroscope measures from the lower limb.
- "_x_time" files contain the time stamps for the accelerometer and gyroscope measures. The units are in seconds and the sampling rate is 40 Hz.
- "_y" files contain the labels. (0) indicates standing or walking in solid ground, (1) indicates going down the stairs, (2) indicates going up the stairs, and (3) indicates walking on grass.
- "_y_time" files contain the time stamps for the labels. The units are in seconds and the sampling rates is 10 Hz.

## Code

- ### Data pre-processing:
  In order to match the frequency of x data, the labels are upsampled. The data is then scaled and split into train-test-valid sets. Label weights are calculated to address class imbalance in the dataset. Further, the labels are One-Hot encoded.

- ### Model Training:
  Bidirectional LSTM is used to perform predictive analysis. The model is fit on the training data and run for 5 epochs and standard classification metrics of Accuracy, Precision, Recall and F1 scores are reported. The model generated training accuracy of 0.9705 and training F1 score of 0.9705, and a validation accuracy of 0.6274 and a validation F1 of 0.6259.
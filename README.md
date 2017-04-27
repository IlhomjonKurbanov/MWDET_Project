## Introduction

In this project, we focus on mind-wandering detection during watching lecture videos. Since lecture videos are one of the main conponent in MOOCs and mind-wandering may have negative effects on learning performance in video watching. Previous work shows some relations between learners' mind-wandering and their gaze movements. However, all of these studies are based on professional but expensive eye tracking device. It is not applicable for average MOOC learners. Therefore, we investigate to what extent we can detect learners' mind-wandering based on webcam-based eye tracking in our project.

In this page, we first introduce a Web application which is used to collect participants' gaze data and reports of mind-wandering during watching lecture videos. Then we release the data about mind-wandering reports and the raw gaze data collected by both [Tobii](https://www.tobii.com/) and [WebGazer.js](http://webgazer.cs.brown.edu/)[1]. After a brief introduction of the dataset, the experiment results and classifier parameters, which are not included in our papers due to the space limitation, are introduced concretely. In the last part, we introduce the scripts leveraged in our work for data processing and mind-wandering detection.

## Web Application for Experiments

During the experiments, participants are asked to watch two lecture videos (i.e. [solar energy](https://www.youtube.com/watch?v=SNmKom56HqE) and [nuclear energy](https://www.youtube.com/watch?v=BW4Q9YQ2gAQ)). Before each video, there is a webcam setup and a calibration for WebGazer.js. In the webcam setup, participants are asked to make sure their faces are fully detected before the calibataion. In the calibration, participants are asked to click 40 dots randomly appearing in the screen.
The calibration of Tobii is conducted before the participants start interacting with the Web application.

In our experiments, Tobii studio runs in the background while participants are interacting with this Web application. When participants are watching lecture videos, their gaze data is recorded by both Tobii and the Web application at the same time. Their reports of mind-wandering are recorded by the Web application.

If you are interested in this Web application, the detail information and setup can be found in [this repository]().

## Dataset

There are three folders for the following 3 kinds of data in the dataset. In each folder, a file contains the data of a participant.
1. Tobii Data (.csv files)
  - Coordinates (X, Y), timestamps, and durations of fixations
  - Angles of saccades
  - Coordinates (X, Y) and timestamps of gaze point

2. WebGazer Data (.csv files)
  - Raw data: coordinates (X, Y) and timestamp of gaze point 
  - Prcossed data: coordinates (X, Y) and timestamp of gaze point; coordinates (X, Y), timestamps, and durations of fixations; angles of saccades

3. Event Data (.json files)
  - Participants' report about their mind-wandering
  - The bell rings
  - Video playing status

The timestamps leveraged in this experiments are based on [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) (e.g. 2017-04-26T14:38:29.235Z) with UTC+0 timezone.

The video information (i.e. video playing time and video length) can be found from the event data. The lengths of the videos about [solar energy](https://www.youtube.com/watch?v=SNmKom56HqE) and [nuclear energy](https://www.youtube.com/watch?v=BW4Q9YQ2gAQ) are about 468 seconds and about 400 seconds respectively.

## Detection Results for Mind-Wandering

In the following table, we first list classifiers with parameters leveraged in our experiments. All of them are based on modules in scikit-learn.

| Classifier | Parameters | module |
| ---------- | ---------- | ------ |
| L1-Logistic Regression | Default Setting with penalty='l1', tol=0.01 | [sklearn.linear_model.LogisticRegression](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html) |
| L2-Logistic Regression | Default Setting with penalty='l2', tol=0.01 | [sklearn.linear_model.LogisticRegression](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html) |
| SVM | Default Setting with tol=0.01 | [sklearn.svm.SVC](http://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html#sklearn.svm.SVC) |
| Decision Tree | Default Setting | [sklearn.tree.DecisionTreeClassifier](http://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html)|
| GaussianNB | Default Setting| [sklearn.naive_bayes.GaussianNB](http://scikit-learn.org/stable/modules/generated/sklearn.naive_bayes.GaussianNB.html) |

Then we list all the results generated by each classifier in the following.

The experiment results with Tobii Data are following.

| Data | Classifier | Feature | SMOTE | Precision | Recall | F1-measure |
| ---- | ---------- | ------- | ----- | ---------:| ------:| ----------:|
| Tobii Data | L1-Logistic Regression | Global | No | 000 | 000 | 000 |
| Tobii Data | L1-Logistic Regression | Global | Yes | 000 | 000 | 000 |
| Tobii Data | L1-Logistic Regression | Local | No | 000 | 000 | 000 |
| Tobii Data | L1-Logistic Regression | Local | Yes | 000 | 000 | 000 |
| Tobii Data | L1-Logistic Regression | Global+Local | No | 000 | 000 | 000 |
| Tobii Data | L1-Logistic Regression | Global+Local| Yes | 000 | 000 | 000 |

| Data | Classifier | Feature | SMOTE | Precision | Recall | F1-measure |
| ---- | ---------- | ------- | ----- | ---------:| ------:| ----------:|
| Tobii Data | L2-Logistic Regression | Global | No | 000 | 000 | 000 |
| Tobii Data | L2-Logistic Regression | Global | Yes | 000 | 000 | 000 |
| Tobii Data | L2-Logistic Regression | Local | No | 000 | 000 | 000 |
| Tobii Data | L2-Logistic Regression | Local | Yes | 000 | 000 | 000 |
| Tobii Data | L2-Logistic Regression | Global+Local | No | 000 | 000 | 000 |
| Tobii Data | L2-Logistic Regression | Global+Local| Yes | 000 | 000 | 000 |

| Data | Classifier | Feature | SMOTE | Precision | Recall | F1-measure |
| ---- | ---------- | ------- | ----- | ---------:| ------:| ----------:|
| Tobii Data | SVM | Global | No | 000 | 000 | 000 |
| Tobii Data | SVM | Global | Yes | 000 | 000 | 000 |
| Tobii Data | SVM | Local | No | 000 | 000 | 000 |
| Tobii Data | SVM | Local | Yes | 000 | 000 | 000 |
| Tobii Data | SVM | Global+Local | No | 000 | 000 | 000 |
| Tobii Data | SVM | Global+Local | Yes | 000 | 000 | 000 |

| Data | Classifier | Feature | SMOTE | Precision | Recall | F1-measure |
| ---- | ---------- | ------- | ----- | ---------:| ------:| ----------:|
| Tobii Data | Decision Tree | Global | No | 000 | 000 | 000 |
| Tobii Data | Decision Tree | Global | Yes | 000 | 000 | 000 |
| Tobii Data | Decision Tree | Local | No | 000 | 000 | 000 |
| Tobii Data | Decision Tree | Local | Yes | 000 | 000 | 000 |
| Tobii Data | Decision Tree | Global+Local | No | 000 | 000 | 000 |
| Tobii Data | Decision Tree | Global+Local | Yes | 000 | 000 | 000 |

| Data | Classifier | Feature | SMOTE | Precision | Recall | F1-measure |
| ---- | ---------- | ------- | ----- | ---------:| ------:| ----------:|
| Tobii Data | GaussianNB | Global | No | 000 | 000 | 000 |
| Tobii Data | GaussianNB | Global | Yes | 000 | 000 | 000 |
| Tobii Data | GaussianNB | Local | No | 000 | 000 | 000 |
| Tobii Data | GaussianNB | Local | Yes | 000 | 000 | 000 |
| Tobii Data | GaussianNB | Global+Local | No | 000 | 000 | 000 |
| Tobii Data | GaussianNB | Global+Local | Yes | 000 | 000 | 000 |

The experiment results with WebGazer Data are following.

| Data | Classifier | Feature | SMOTE | Precision | Recall | F1-measure |
| ---- | ---------- | ------- | ----- | ---------:| ------:| ----------:|
| WebGazer Data | L1-Logistic Regression | Global | No | 000 | 000 | 000 |
| WebGazer Data | L1-Logistic Regression | Global | Yes | 000 | 000 | 000 |
| WebGazer Data | L1-Logistic Regression | Local | No | 000 | 000 | 000 |
| WebGazer Data | L1-Logistic Regression | Local | Yes | 000 | 000 | 000 |
| WebGazer Data | L1-Logistic Regression | Global+Local | No | 000 | 000 | 000 |
| WebGazer Data | L1-Logistic Regression | Global+Local| Yes | 000 | 000 | 000 |

| Data | Classifier | Feature | SMOTE | Precision | Recall | F1-measure |
| ---- | ---------- | ------- | ----- | ---------:| ------:| ----------:|
| WebGazer Data | L2-Logistic Regression | Global | No | 000 | 000 | 000 |
| WebGazer Data | L2-Logistic Regression | Global | Yes | 000 | 000 | 000 |
| WebGazer Data | L2-Logistic Regression | Local | No | 000 | 000 | 000 |
| WebGazer Data | L2-Logistic Regression | Local | Yes | 000 | 000 | 000 |
| WebGazer Data | L2-Logistic Regression | Global+Local | No | 000 | 000 | 000 |
| WebGazer Data | L2-Logistic Regression | Global+Local| Yes | 000 | 000 | 000 |

| Data | Classifier | Feature | SMOTE | Precision | Recall | F1-measure |
| ---- | ---------- | ------- | ----- | ---------:| ------:| ----------:|
| WebGazer Data | SVM | Global | No | 000 | 000 | 000 |
| WebGazer Data | SVM | Global | Yes | 000 | 000 | 000 |
| WebGazer Data | SVM | Local | No | 000 | 000 | 000 |
| WebGazer Data | SVM | Local | Yes | 000 | 000 | 000 |
| WebGazer Data | SVM | Global+Local | No | 000 | 000 | 000 |
| WebGazer Data | SVM | Global+Local | Yes | 000 | 000 | 000 |

| Data | Classifier | Feature | SMOTE | Precision | Recall | F1-measure |
| ---- | ---------- | ------- | ----- | ---------:| ------:| ----------:|
| WebGazer Data | Decision Tree | Global | No | 000 | 000 | 000 |
| WebGazer Data | Decision Tree | Global | Yes | 000 | 000 | 000 |
| WebGazer Data | Decision Tree | Local | No | 000 | 000 | 000 |
| WebGazer Data | Decision Tree | Local | Yes | 000 | 000 | 000 |
| WebGazer Data | Decision Tree | Global+Local | No | 000 | 000 | 000 |
| WebGazer Data | Decision Tree | Global+Local | Yes | 000 | 000 | 000 |

| Data | Classifier | Feature | SMOTE | Precision | Recall | F1-measure |
| ---- | ---------- | ------- | ----- | ---------:| ------:| ----------:|
| WebGazer Data | GaussianNB | Global | No | 000 | 000 | 000 |
| WebGazer Data | GaussianNB | Global | Yes | 000 | 000 | 000 |
| WebGazer Data | GaussianNB | Local | No | 000 | 000 | 000 |
| WebGazer Data | GaussianNB | Local | Yes | 000 | 000 | 000 |
| WebGazer Data | GaussianNB | Global+Local | No | 000 | 000 | 000 |
| WebGazer Data | GaussianNB | Global+Local | Yes | 000 | 000 | 000 |

## Scripts

For the data processing and mind-wandering prediction, we have 3 main scripts which are written as Jupyter notebooks.

1. Scripts 01 (in Python) for feature extraction and mind-wandering prediction based on Tobii data.
2. Scripts 02 (in R) for saccade detection based on WebGazer data (detection algorithm is based on [2])
3. Scripts 03 (in Python) for feature extraction and mind-wandering prediction based on WebGazer data preprocessed in 2.

Due to the randomazation of the techniques SMOTE [3], which is leveraged in our scripts for unbalanced data, the prediction results might be slightly different in each runs.

## Reference
[1] Papoutsaki, Alexandra, et al. "WebGazer: scalable webcam eye tracking using user interactions." IJCAI, 2016.

[2] Engbert, Ralf, and Reinhold Kliegl. "Microsaccades uncover the orientation of covert attention." Vision research 43.9 (2003): 1035-1045.

[3] Chawla, Nitesh V., et al. "SMOTE: synthetic minority over-sampling technique." Journal of artificial intelligence research 16 (2002): 321-357.

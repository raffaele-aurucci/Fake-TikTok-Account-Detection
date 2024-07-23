# Fake TikTok Account Detection

Project of course **Fondamenti di Data Science & Machine Learning** - University of Salerno.

# Contributors
<a href="https://github.com/raffaele-aurucci/Fake-TikTok-Account-Detection/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=raffaele-aurucci/FakeAccountDetection" />
</a>

# Table of Contents

1. [Introduction](#introduction)
2. [Methodology](#methodology)
3. [Experimental Results](#experimental-results)
4. [Installation Guide](#installation-guide)
   - [Installing Python](#installing-python)
   - [Cloning the Repository](#cloning-the-repository)
   - [Creating the Virtual Environment](#creating-the-virtual-environment)
   - [Installing Requirements](#installing-requirements)
5. [Citation](#citation)

# Introduction
The issue of fake accounts on social networks remains widespread, representing a significant threat to the security and integrity of online platforms. This project focuses on detecting fake accounts on the emerging social platform TikTok, which has experienced exponential growth in recent years.

# Methodology
This work presents a Machine Learning (ML) pipeline for detecting fake TikTok accounts. We used a dataset created with [TikAPI](https://tikapi.io/) containing 10.043 accounts (5.029 fake and 5.014 real). The dataset includes information such as *diggCount*, *heartCount*, *followerCount*, *followingCount*, *videoCount*, *signature*, etc., and label *fake* (True or Real).  
In the preprocessing step, we transformed all textual and boolean features in numerical features and then scaled the data using *z-score normalization*.  
Afterwards, we trained different ML models: Support Vector Machine (SVM), K-Nearest-Neighbor (KNN), Logistic Regression, Decision Tree and Random Forest, and then evaluated the algorithm performance under three conditions:
1. training with default hyperparameters (defined in [Scikit-Learn](https://scikit-learn.org/stable/index.html));
2. training with hyperparameters tuning using Grid Search and K-Fold Cross Validation;
3. training using two different feature sets after discovering Relaxed Functional Dependencies (RFDs), following the feature engineering strategy proposed in this [research work](https://doi.org/10.1145/3625097):
   - Only RFDs: training using only the added features identified through the RFD process, excluding the original dataset features.
   - Baseline + RFDs: training with the original dataset features along with the added features identified through the RFD process.

# Experimental Results
The table below shows the performance of the algorithms after training with the default hyperparameters (see point 1 of the previous section).

| **Classifier**      | **Accuracy** | **F1-Score** | **Precision** | **Recall** |
|---------------------|--------------|--------------|---------------|------------|
| Logistic Regression | 0.935        | 0.938        | 0.899         | 0.980      |
| SVM                 | 0.965        | 0.966        | 0.954         | 0.978      |
| KNN                 | 0.981        | 0.981        | 0.974         | 0.989      |
| Decision Tree       | 0.998        | 0.998        | 0.997         | 0.999      |
| Random Forest       | 0.999        | 0.999        | 0.998         | 1.000      |

In the following table, we present the performance of the algorithms after the Hyperparameter Tuning step (see point 2 of the previous section).

| **Classifier**     | **Accuracy** | **F1-Score** | **Precision** | **Recall** |
|--------------------|--------------|--------------|---------------|------------|
| Logistic Regression | 0.997        | 0.997        | 0.997         | 0.997      |
| SVM                | 0.981        | 0.981        | 0.976         | 0.987      |
| KNN                | 0.986        | 0.986        | 0.979         | 0.993      |
| Decision Tree      | 0.998        | 0.998        | 0.997         | 0.999      |
| Random Forest      | 0.998        | 0.998        | 0.998         | 0.999      |

In the following table, we present the mean performance of the algorithms after considering Only RFDs (see point 3 of the previous section).

| **Classifier**      | **Accuracy** | **F1-Score** | **Precision** | **Recall** |
|---------------------|--------------|--------------|---------------|------------|
| Logistic Regression | 0.491        | 0.383        | 0.629         | 0.490      |
| SVM                 | 0.600        | 0.522        | 0.778         | 0.600      |
| KNN                 | 0.763        | 0.735        | 0.829         | 0.763      |
| Decision Tree       | 0.763        | 0.735        | 0.829         | 0.763      |
| Random Forest       | 0.763        | 0.735        | 0.829         | 0.763      |

Finally, in the table below, we present the mean performance of the algorithms after considering Baseline + RFDs (see point 3 of the previous section).

| **Classifier**      | **Accuracy** | **F1-Score** | **Precision** | **Recall** |
|---------------------|--------------|--------------|---------------|------------|
| Logistic Regression | 0.946        | 0.928        | 0.930         | 0.928      |
| SVM                 | 0.987        | 0.987        | 0.982         | 0.987      |
| KNN                 | 0.990        | 0.986        | 0.986         | 0.986      |
| Decision Tree       | 0.974        | 0.996        | 0.996         | 0.996      |
| Random Forest       | 0.994        | 0.998        | 0.998         | 0.998      |


# Installation Guide
To install the necessary requirements for the project, please follow the steps below.

## Installing Python
Verify you have Python installed on your machine. The project is compatible with Python `3.10.1`.

If you do not have Python installed, please refer to the official [Python Guide](https://www.python.org/downloads/).

## Cloning the Repository 
To clone this repository, download and extract the `.zip` project files using the `<Code>` button on the top-right or run the following command in your terminal:
```shell 
git clone https://github.com/raffaele-aurucci/Fake-TikTok-Account-Detection.git
```

## Creating the Virtual Environment 
It's strongly recommended to create a virtual environment for the project and activate it before proceeding. 
Feel free to use any Python package manager to create the virtual environment. However, for a smooth installation of the requirements we recommend you use `pip`. Please refer to [Creating a virtual environment](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/#creating-a-virtual-environment).

You may skip this step, but please keep in mind that doing so could potentially lead to conflicts if you have other projects on your machine. 
## Installing Requirements
To install the requirements, please: 
1. Make sure you have **activated the virtual environment where you installed the project's requirements**. If activated, your terminal, assuming you are using **bash**, should look like the following: ``(name-of-your-virtual-environment) user@user path``

2. Install the project requirements using `pip`:
```shell 
pip install -r requirements.txt
```

## Citation 

If you have have found this work useful and have decided to include it in your work, please consider citing
```BibTeX
@online{aurucci-miglino2024:fake-tiktok-account-detection,
    author={Raffaele Aurucci, Annalaura Miglino}, 
    title = {Fake TikTok Account Detection},
    url={https://github.com/raffaele-aurucci/Fake-TikTok-Account-Detection},
    year={2024}
}
```


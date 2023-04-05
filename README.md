# NLP-Project - Exploring BERT and VADER ensamble methods for sentiment analysis

## Description

This project will investigate possibilities of fine-tuning existing techniques of NLP sentiment analysis through ensemble methods. The project takes inspiration from the work of [Wang et al.](https://aclanthology.org/2022.ltedi-1.15/) but proposes two simplified methods which focus on combining BERT with VAD score from VADER to increase performance in the task of classifying the sentiment of IMDb reviews.

---

## Dataset

The dataset used consist of 50k labeled IMDb movie reviews. Due to hardware constraints, we slim down the dataset into reviews of length 128 or lower. We then split the data into 75% train and 25% test.

<center>

|           | Train | Valid | Test  |
| :-------: | :---: | :---: | :---: |
| Positive  | 4,849 | 1,033 | 1,013 |
| Negative  | 4,442 |  958  |  979  |
| **Total** | 9,291 | 1,991 | 1,992 |

</center>

## Evaluation

To evaluate the effectiveness of the model, and later do comparisons between the baseline and the other implemented models, 4 performance evaluation metrics will be used.

1. Accuracy, which measures proportion of correctly classified instances by the model.
2. Precision, which measures proportion of predicted positives correctly classified by the model.
3. Recall, which measures proportion of true positives correctly classified by the model.
4. F1-score, which takes both precision and recall into account and gives a weighted avarage.

Performance will mostly be judged on accuracy. However, in order to get additional insights and a full understanding of
our model, precision, recall and f1-score will serve as a complementary to the accuracy.

## Baseline

As baseline for this project, a regular BERT model has been implemented and fine tuned on the task of classifying the sentiment of IMDb reviews.

Training our baseline model for 1 epoch using a batch size of 32 yielded the following average results:

<center>

| Accuracy | Precision | Recall | F1-score |
| :------: | :-------: | :----: | :------: |
|   87.7   |   86.3    |  90.4  |   88.3   |

</center>

## Results

### Method 1

Method 1 implements a multi layer perceptron to combine the fine-tuned BERT model from our baseline with VAD-scores from VADER. Training the MLP implementation yielded average results as follows:

<center>

| Accuracy | Precision | Recall | F1-score |
| :------: | :-------: | :----: | :------: |
|   88.5   |   88.2    |  89.6  |   88.9   |

</center>

### Method 2

Method 2 assigns weights to the individual results from the fine-tuned BERT and VADER and combines the models with different weight-combinations. The best combination of weights yielded the following average results:

<center>

| Accuracy | Precision | Recall | F1-score |
| :------: | :-------: | :----: | :------: |
|   88.6   |   87.2    |  91.2  |   89.1   |

</center>

# Tweet COVID-19 Sentiment Analysis

Sentiment analysis was used to analyze tweets from netizens on the Twitter platform related to COVID-19.

Face mask detection is used to detect the use of masks during the COVID-19 pandemic. This project is a personal experiment to implement the FastText algorithm as word embedding as well as the Long Short-Term Memory Neural Network algorithm to classify tweets about COVID-19 based on positive and negative sentiments.

## About Dataset

The face mask dataset used in this experiment can be downloaded [here](https://www.kaggle.com/datasets/datatattle/covid-19-nlp-text-classification).
The following is a summary of the dataset.

| Number of Classes | 5                                                             |
| :---------------- | :------------------------------------------------------------ |
| Class Details     | Extremely Negative, Negative, Neutral, Positive, Extremely Positive                |
| Amount of data    | 41157 Train, 3798 Test |

## Model Architecture

The model architecture used in this experiment is as follows.

`Model: Sequential`
| Layer Type | Output Shape | Params # |
| :-------- | :------- | :-------|
| lstm (LSTM) | (None, 200) | 400800 |
| dense (Dense) | (None, 2) | 402 |
| Total params: 401,202 |
| Trainable params: 401,202 |
| Non-trainable params: 0 |

## Model Evaluation

Pelatihan model dilakukan dengan `epochs = 10` dan menggunakan ModelCheckpoint Callback yang mana akan menyimpan model ketika pada epoch tertentu mengalami kenaikan pada metrik yang dimonitor, dalam hal ini `val_accuracy`. Berdasarkan hasil training, didapatkan metrik evaluasi terbaik

Model training is performed with `epoch = 10` and uses an Early Stopping and ModelCheckPoint callback which will stop model training if `val_accuracy` has converged to a value.
From the results of the training, the evaluation of the model in the last epoch (epochs = 9) was obtained as follows.
| Metrics | Value |
| :-------- | :------- |
| Accuracy | 0.8168 |
| Loss | 0.3960 |
| Val Accuracy | 0.74361 |
| Val Loss | 0.5266 |

In addition, the model is also evaluated with test data that has never been seen at all and produces `Accuracy: 0.729` and `Loss: 0.549` with the following confusion matrix results.

![Confusion Matrix](https://raw.githubusercontent.com/taqiyyaghazi/lstm-fasttext-covid19-sentiment-analysis/main/img/confusion_matrix.png)

### Accuracy Plot per Epoch

![Accuracy Plot](https://raw.githubusercontent.com/taqiyyaghazi/lstm-fasttext-covid19-sentiment-analysis/main/img/accuracy.png)

### Loss Plot per Epoch

![Loss Plot](https://raw.githubusercontent.com/taqiyyaghazi/lstm-fasttext-covid19-sentiment-analysis/main/img/loss.png)

## Acknowledgements

- [Data Resource](https://www.kaggle.com/datasets/datatattle/covid-19-nlp-text-classification)

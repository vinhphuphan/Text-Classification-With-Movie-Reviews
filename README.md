<h1 align="center"> </a> Text Classification With Movie Reviews Using TensorFlow<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2d/Tensorflow_logo.svg/173px-Tensorflow_logo.svg.png?20170429160244" alt="tensorflow" width="55" height="40"/> </a> </h1>

## 1. Introduction
This notebook classifies movie reviews as *positive* or *negative* using the text of the review. This is an example of *binary*—or two-class—classification, an important and widely applicable kind of machine learning problem. 

We'll use the [IMDB dataset](https://www.tensorflow.org/api_docs/python/tf/keras/datasets/imdb) that contains the text of 50,000 movie reviews from the [Internet Movie Database](https://www.imdb.com/). These are split into 25,000 reviews for training and 25,000 reviews for testing. The training and testing sets are *balanced*, meaning they contain an equal number of positive and negative reviews. 

This notebook uses [tf.keras](https://www.tensorflow.org/api_docs/python/tf/keras), a high-level API to build and train models in TensorFlow, and [TensorFlow Hub](https://www.tensorflow.org/hub), a library and platform for transfer learning. For a more advanced text classification tutorial using `tf.keras`, see the [MLCC Text Classification Guide](https://developers.google.com/machine-learning/guides/text-classification/).

Example :

[**positive**] A wonderful little production. The filming technique is very unassuming-very old-time-BBC fashion and gives a comforting, and sometimes discomforting, sense of realism to the entire piece. . . .

[**negative**] Encouraged by the positive comments about this film on here I was looking forward to watching this film. Bad mistake. I’ve seen 950+ films and this is truly one of the worst of them - it’s awful in almost every way ....


## 2. Method
The neural network is created by stacking layers—this requires three main architectural decisions:

* How to represent the text?
* How many layers to use in the model?
* How many *hidden units* to use for each layer?

In this scenario, the input data consists of sentences. The labels to predict are either 0 or 1. I have tried multiple approach to build the models with different architecture to explore the result.

I have used two models for this project and then compare them. 

The first model uses a pre-trained Saved Model from [TensorFlow Hub](https://www.tensorflow.org/hub) called [google/nnlm-en-dim50/2](https://tfhub.dev/google/nnlm-en-dim50/2) to embed the sentences. 

The second one is the model I built from sratch which is that I standardize, tokenize, and vectorize the data using the helpful <code translate="no" dir="ltr">tf.keras.layers.TextVectorization</code> layer.

#### 🛠 Technologies and Tools 🛠

[![My Skills](https://skillicons.dev/icons?i=py,tensorflow,numpy)](https://skillicons.dev)
<br>

## 3. Results 
<p align="center"><img style="align: center;" src="https://github.com/vinhphuphan/Text-Classification-With-Movie-Reviews/edit/main/images/Accuracy_plot.png?raw=true" width=400></p>
<h4 align="center">Figure 2. Training and validation loss of two models</h4>


### Related Projects:question: 👨‍💻 🛰️
<code>[Olympic-Weightlifting-Data-Analysis](https://github.com/vinhphuphan/Olympic-Weightlifting-Data-Analysis)</code> 📊

<code>[Titanic - Machine Learning from Disaster using Python](https://github.com/vinhphuphan/Titanic-Machine-Learning-from-Disaster)</code> 📊

<code>[Living Species Image Classification using Python](https://github.com/vinhphuphan/ImageClassification)</code> 📊


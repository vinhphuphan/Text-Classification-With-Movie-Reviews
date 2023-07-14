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

## 3. Result
I have used the best model to classify the sentiments of some reviews

[**positive**] "This is one of Bruce's most underrated films in my opinion, its an awesome heartwarming film, with a neat story and an amazing performance from Bruce Willis!. All the characters are great, and I thought Willis and Spencer Breslin were just awesome together, plus Bruce Willis is simply amazing in this!...."
Sentiment Score: [17.677164]

[**positive**] "This wonderful movie captures so many elements of what makes a family comedy funny, entertaining, sweet and memorable, it\'s difficult to decide where to start.From the opening number, "Rainbow Connection," Paul Williams\'s excellent score sung with gusto by Kermit D. Frog .... Highly recommended.'
Sentiment Score: [14.733066]

[**positive**] "This is a great German slasher, that's often quite suspenseful, and creative, with a fun story and solid performances. All the characters are cool, and Benno F\xc3\xbcrmann is great as the psycho killer, plus Franka Potente gives a fantastic performance as the main lead....."
Sentiment Score: [14.462514]

[**negative**] "Hollywood has churned out yet another garbage that\'s wildly overhyped and underwhelming on a first-time viewing basis. Hannibal is bad, terrible, inept, lame, droll, idiotic, contrived, laughable and utterly atrocious (no pun intended). Minor spoilers follow...This movie has huge logic holes - more than any Bruckheimer/Bay movie - or for that matter - any movie that exemplify the indulgence of Hollywood exaggeration..."
Sentiment Score: [-16.826437]

[**negative**] "This is just the same old crap that is spewed from amateur idiots who have no clue how to make a movie--gee maybe that's why it is a straight-to-video wanna-be movie! I guess it is my fault for actually spending money to see it (one of the worst decisions I have ever made). What a waste..."
Sentiment Score: [-16.771723]

[**negative**] As you can tell from the other comments, this movie is just about the WORST film ever made. Let me see how many different words I can use to describe it: Boring, Unbearable, Laughable, Lousy, Stupid, Horrible.....I could go on with such descriptions but you probably get the point.I would have given this a 0, if possible--bad acting, bad directing, bad production, bad plot.
Sentiment Score: [-16.768122]

## 4. Conclusion
<p align="center"><img style="align: center;" src="https://raw.githubusercontent.com/vinhphuphan/Text-Classification-With-Movie-Reviews/main/images/Accuracy_plot.png" width=600></p>
<h4 align="center">Figure 1. Training and validation accuracy of two models</h4>

<p align="center"><img style="align: center;" src="https://raw.githubusercontent.com/vinhphuphan/Text-Classification-With-Movie-Reviews/main/images/Loss.png" width=600></p>
<h4 align="center">Figure 2. Training and validation loss of two models</h4>

- **The trainning and validation loss graphs** shows that there is **the overfitting problem** which occurs with pretrained embeddings model. While the training loss goes down over time, the validation loss goes down until a turning point is found, and there it starts going up again. That point represents the beginning of overfitting. Sratch model has this problem but **the gap between trainning loss and validation is not as big as pretrained embeddings model.**

<br>

- Regards of the accuracy when predicting test dataset, **the accuracy of Origin model** is `84.56%` and that of **Sratch model** is `84.92%`. It can be concluded that there is no clear difference between two model's test accuracy. The reason for this might be that the **Sratch model** with embeddings defined from scratch allows for adaptation to the specific training data and can perform well when there is sufficient labeled data available.

<br>

In summary, the model with pretrained embeddings benefits from prelearned semantic representations, which can be useful when the pretrained embeddings align well with the target task or when data is limited.
<br>On the other hand, the model with embeddings from scratch allows for adaptation to the specific training data and can perform well when there is sufficient labeled data available.

### Related Projects:question: 👨‍💻 🛰️
<code>[Olympic-Weightlifting-Data-Analysis](https://github.com/vinhphuphan/Olympic-Weightlifting-Data-Analysis)</code> 📊

<code>[Titanic - Machine Learning from Disaster using Python](https://github.com/vinhphuphan/Titanic-Machine-Learning-from-Disaster)</code> 📊

<code>[Living Species Image Classification using Python](https://github.com/vinhphuphan/ImageClassification)</code> 📊


# Diverse Mini-Batch Active Learning

This experiment is based on [paper](https://arxiv.org/pdf/1901.05954.pdf) name Fedor Zhdanov 2019, "Diverse mini-batch Active Learning"

### Packages
- pytorch
- numpy

### Datasets

- Korean movie review data
  - training : (150000, 2)
  - testing : (50000, 2)
- English movie review data
  - training : (40000,2)
  - testing : (10000,2)

Please check this path if you want more detail about preprocessing.
- [Korean data preprocessing](https://github.com/hskimim/active-learning-tutorial/blob/master/Diverse_minibatch_Active_Learning/Korean_MR_Preprocessing.ipynb)
- [English data preprocessing](https://github.com/hskimim/active-learning-tutorial/blob/master/Diverse_minibatch_Active_Learning/English_MV_Preprocessing.ipynb)


### Experiments

First of all, I did four different experiments.
- [English_K-means Active Learning(paper replicate)](https://github.com/hskimim/active-learning-tutorial/blob/master/Diverse_minibatch_Active_Learning/Diverse%20mini-batch%20Acitve%20Learning(paper%20replicate).ipynb)
- [Random Sampling](https://github.com/hskimim/active-learning-tutorial/blob/master/Diverse_minibatch_Active_Learning/ENG_experiments/random_sampling_with_embedding.ipynb)
- [Margin Sampling](https://github.com/hskimim/active-learning-tutorial/blob/master/Diverse_minibatch_Active_Learning/ENG_experiments/uncertainty_sampling_with_embedding.ipynb)
- [K-means with embedding(sum and mean)](https://github.com/hskimim/active-learning-tutorial/blob/master/Diverse_minibatch_Active_Learning/ENG_experiments/k%3D1000%2Cbeta%3D10_with_embedding(ENG).ipynb)

Operating mini-batch Active Learning by using weighted K-means algorithm. Comparison methodology is "random sampling", "margin sampling"(vanilla active learning)

The number of initial training dataset is 10,000. And add the 1,000 training set under each methodology (random or uncertainty or k-means).

I trained the model for 3 times (3 epoch) and estimated the validation datasets and measured the uncertainty. The reason why I trained model 3 times is it is better to multiple training could contribute to robust performance such as learning curve.

### Korean Movie review data performance (Validation Accuracy)
- random : random sampling
- no_embedding : K-means active learning(paper)
- us : Uncertainty sampling (Margin sampling)
- sum : K-means active learning with embedding(sum)
- mean : K-means active learning with embedding(mean)

<img src = 'assets/markdown-img-paste-20190614160248702.png'>

### English Movie review data performance (Validation Accuracy)
- random : random sampling
- no_embedding : K-means active learning(paper)
- us : Uncertainty sampling (Margin sampling)
- sum : K-means active learning with embedding(sum)
- mean : K-means active learning with embedding(mean)

<img src ="assets/markdown-img-paste-20190614160255840.png">

### Conclusion and Further works

In case of Korean, K-means active learning with embeeding(sum) had the highest performance. And In case of English, K-means active learning with embedding(mean) had the highest performance. There was not big difference between paper's performance. But sightly better than paper's in both case. I thought that if the length of sentence is long, then embedding with mean is more proper than sum. (English's max length : 100, Korean's max length : 25)

I guess that the gap between the performance is getting larger if experiments is more difficult task such as multi-class classification (ex. yelp)

### Issue
```
The hyperparameter I applied is k = 1000, beta = 10.
Other hyperparameter can change the result for sure.   
```
```
I don't know why random sampling's validation accuracy is so high.
Im gonna search why it is so high.
And try to fix it or find the reason as soon as possible if I can
```

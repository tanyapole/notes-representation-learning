# My notes on representation learning
Self-supervised learning is a method of utilizing unsupervised data as supervised by extracting supervision from the data itself.


### Semi-supervised learning
Semi-supervised learning is the type of machine learning that uses a small amount of labelled data (LD) and a larger amount of unlabelled data (UD).
2 main strategies:
1. self-training: LD -> UD
train a model on LD; use it to create labels for UD; train a new model on LD and UD with fake labels <sup>1</sup>, <sup>2</sup>
2. self-supervised learning: UD -> LD
use UD to extract useful features; then train a model, utilizing those features, on LD

<sup>1</sup> more sophisticated options: use only mose confident UD labels in the third step

<sup>2</sup> EfficientNet was trained that way according to [[1]](#1) (sec 4.3)


## References
<a id="1">[1]</a> 
Liu et al. 2020
Self-supervised Learning: Generative or Contrastive
[arxiv](https://arxiv.org/abs/2006.08218)

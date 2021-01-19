# My notes on representation learning
Self-supervised learning is a method of utilizing unsupervised data as supervised by extracting supervision from the data itself. 

2 tasks:
* Pretext task == self-supervised task: artificial task for learning representation.
* Downstream task: main task

We don't really care about performance on pretext task

<span style="color:orange">Any studies on how performance on the pretext task affects performance on doewnstream task</span>

Difference to generative models is in their goals^
* generative: generate well, representative
* self-supervised: find useful features




### Semi-supervised learning
Semi-supervised learning is the type of machine learning that uses a small amount of labelled data (LD) and a larger amount of unlabelled data (UD).
2 main strategies:
1. self-training: LD -> UD
train a model on LD; use it to create labels for UD; train a new model on LD and UD with fake labels <sup>1</sup>, <sup>2</sup>
2. self-supervised learning: UD -> LD
use UD to extract useful features; then train a model, utilizing those features, on LD

<sup>1</sup> more sophisticated options: use only mose confident UD labels in the third step

<sup>2</sup> EfficientNet was trained that way according to [[1]](#1) (sec 4.3)

### Types of self-supervised models [[1]](#1) (sec 3)
1. Generative models (autoencoders, flow-based, auto-regressive)
2. Contrastive models (i.e. discriminative models)
3. Generative-contrastive (= adversarial) models

[Further](self_supervised_types.md)

### Contrastive learning
[Further](contrastive_learning.md)

### Specific results
[Further](specific.md)





## References
<a id="1">[1]</a> 
Liu et al. 2020
Self-supervised Learning: Generative or Contrastive
[arxiv](https://arxiv.org/abs/2006.08218) [pdf](papers/selfsupervised_learning:_generative_or_contrastive.pdf)
 

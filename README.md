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

### Types of self-supervised models
1. Generative models
    * AE (autoencoders)  [[1]](#1) (sec 3.3): reconstruct (part of) inputs from (corrupted) inputs
        * AEs
        * Denoising AEs
        * Variational AEs
    * Flow-based models  [[1]](#1) (sec 3.2): estimate high-dimensional densities p(x) from data
    * AR (auto-regressive) models  [[1]](#1) (sec 3.1): model images pixel by pixel, examples
        * PixelRNN
        * PixelCNN
2. Contrastive models (i.e. discriminative models)
    * Context-instance contrast == global-local contrast  [[1]](#1) (sec 4.1): focus on modeling the belonging relationship between local feature of a sample and its global context representation
        * PRP (Predict Relative Position): learn relative postiions between components
            * predict relative postitions of 2 patches from a sample
            * recover positions of shuffled segments of the image (sove jigsaw)
            * predict rotation angle
        * MI (Maximize Mutual Information): learn the explicit belonging relationships between local parts and global context
            * Deep InfoMax - 1st one to explicitly model mutual information through a contrastive learning task, maximizing the MI btwn a local pathc and its global context
            * Contrastive Predictinve Coding
            * AMDIM - similar to Deep InfoMax
    * Context-context contrast  [[1]](#1) (sec 4.2)
        * Cluster-based Discrimination
        * Instance Discrimination
            * InstDisc - prototype
            * CMC
            * MoCo
              use momentum contrast to substantially increacse the amount of negative samples
              however uses a too simple positive sample strategy (a pair of positives comes from the same sample without transformation or augmentation
3. Generative-contrastive (= adversarial) models



## References
<a id="1">[1]</a> 
Liu et al. 2020
Self-supervised Learning: Generative or Contrastive
[arxiv](https://arxiv.org/abs/2006.08218)
 

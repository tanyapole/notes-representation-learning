## SSL for Semantic Segmentation
### Contrastive Learning for Label-Efficient Semantic Segmentation
Zhao et al.

__Note:__ they use SSL pretraining using masks (i.e. labels)

How the use SSL:
* Fully-supervised mode <br/>
Algo:
    1. take images & masks
    2. train UNet-like NN in SSL manner (with SSL loss, using masks)
    3. replace projection head (top layer) with softmax
    4. tune for segmentation task using BCE
    
* Semi-supervised mode <br/>
Algo:
    1. train a model in fully-supervised mode with labelled data
    2. use this model to create labels for the unlabelled data
    3. train a model in fully-supervised mode with labelled a& pseudo-labelled data
    
Pixel-wise label-based contrastive loss (their SSL loss):
Image I, distorted version I^, |I|=N <br/>
Mask Y={yi}, yi \in 1..C, |I=c| = Nc <br/>
F, F^ - representations of I, I^ <br/>
tau - temperature parameter
![Alt text](segm_zhao.png "segm_zhao") <br/>

Note: they computer SSL loss separately for each image. 
They tried to to computer per-batch, but that worsened the performance.

Note: It is crucial to train the entire network in the fine-tuning stage,
as there is no interaction between pixels from different images during contrastive pretraining. 
While contrastive pretraining encourages pixels within an image to cluster according to their class labels, softmax fine-tuning rearranges
these clusters so that they fall on the correct side of the appropriate decision boundary.

### Self-supervised learning for segmentation
A. Dhere, J. Sivaswamy

Downstream task: segment kidneys

Method: use SSL to pretrain the encoder, that is later used in segmentation model <br/>
Segmentation model is shares the encoder with a autoencoder, trained simultaneously.

Pretext task: split all CT scan images of kidneys into left and right halves 
-> given 2 halves predict if they are from the same side

SSL Loss: 
![Alt text](segm_dhere.png "segm_dhere") <br/>
y - label: y= \mathbb{1}_{a & b from the same side}

### Medical Image Segmentation via Unsupervised Convolutional Neural Network 
Chen, Frey

<span style="color:orange"> сложный лосс, пока нафиг </span>

### Self-supervision with Superpixels: Training Few-shot Medical Image Segmentation without Annotation
Ouyang et al.

They use superpixels in pretext task, but their tasks are totally different 
(few-shot learning tasks, with queries & supports)

### Self-Supervised Depth Learning Improves Semantic Segmentation
Irrelevant: pretext task specific for videos - depth prediction

### Self-Supervised Feature Learning for Semantic Segmentation of Overhead Imagery
Pretext task: inpainting <br/>
How they use: pretrain Unet-like NN on pretext, the adapt by removing top layer 
and tune for segmentation <br/>
Specialty: they train a special coach NN in parallel with the main NN.
The coach NN learns to generate difficult occluding masks (difficult for the main NN)

### Instance-aware Self-supervised Learning for Nuclei Segmentation
Xie et al.

Downstream task: segmenting nuclei <br/>
Difficulty: images of different scale => nuclei of different sizes & differen count of nuclei in an image <br/>
Notation: A (anchor), P (positive sample), N (negative sample) <br/>
For sampling technique see picture <br/>
![Alt text](segm_nuclei.png "nuclei segmentation") <br/>
Note: S(I) - size of nuclei in img I, C(I) - count of nuclei in img I <br/>
2 pretext tasks: <br/>
Task #1: triplet loss learning of A, P, N <br/>
This tasks addresses primarily different nuclei sizes problem <br/>
Task #2: Loss(P,N) = max(0, f(N)-f(P)+m), where f-NN, m-margin <br/>
This task addresses different nuclei count problem (count in N should be less than in P by a margin m) <br/>

### Fine-Grained Segmentation Networks: Self-Supervised Segmentation for Improved Long-Term Visual Localization
Larsson et al.

They use k-means clustering, but they have reference images and target images 
(with different view angle, different season of the year etc.)





### SeSe-Net: Self-Supervised deep learning for segmentation
Zeng et al.

Используют обучение с учителем (есть сетка основная и сетка учитель, оценивающая основную) <br/>
<span style="color:orange"> Пока не стала вчитываться, но можно будет перечитать </span>




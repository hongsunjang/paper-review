# BossNAS: Exploring Hybrid CNN-transformers with Block-wisely Self-supervised Neural Architecture Search


## Main questions

> Ensemble bootstrapping?

> HyTra?

> Population center?

> Spearman correlation?


## Abstract
NAS -> reducing human effort to find good architcture

$But,$ diversified search space using   CNNs and transformers is still open question.

> Problem?
>
> 1. Large weight sharing search space -> blockwise distill
> 2. Biased supervision in previous method -> teacher dependency

> Solution?
>
> Ensemble bootstrapping: Train each block separately before searching them as  whole towards the population center.
> 
> HyTra: fagbric-like hybrid CNN-transformer search space with searchable down-sampling position

> Result?
>
> 1. surpassing EfficientNet by 2.4% with comparable compute time
> 2. superior architecture rating accuracy with 0.78 and 0.76 Spearman correlation on the canonical MBConv search space with ImageNet and NATS-Bench(CIFAR-100) 

## Intro
ViT and diverse design of neural network architecture requires heavy human works for choice.

Representative success in NAS on manually designed building block is MobileNetV3, EfficientNet by $multi-trial NAS$ => computationally heavy

Main culprit of inaccurate architecture rating of one-shot NAS is large search space

block-wise supervision successfully shrink search space => highly correlated with the teacher's architecture

Unsupervised NAS has emerged and have been proven capable of achieving comparable performance

> Ensemble bootstrapping
> 
> - Train: predict the prob. ensemble of all the sampled ones in the target network
> - Search: unsupervised evaluation metric


> Generalization = three different search spaces and datasets
> 
> 1. Search space: HyTra =>  outperforms DNA, surpassing EfficientNet
> 2. Spearman correlation: 0.78(MBConv, imageNet), 
> 3. Spearman correlation: 0.76 (NATS-Bench, CIFAR-100)

## Methodology

- Siamese supernet을 활용하여
- Teacher network는 EMA(exponential moving average) weight를 가지는 supernet랑 똑같은 구조로 한다.
- 일단 똑같이 Teacher network와 student network의 MSE loss를 minimize하는데 data aug의 pixel difference를 최소화 하기위해 항상 downsample or FC layer 다음 optimization을 수행한다.
- uniform sampling, fair sampling 같이 기존의 방법을 통해 optimization을 수행하면 당연히 EMA weight를 가지는 동일한 supernet에 가까워질텐데 이는 convergence만 느리게 할 뿐 의미없는 수행이 된다.
- 이런 문제를 해결하기 위한 방법이 ensemble bootstrapping이다.

> Ensemble distillation
>  MEAL, MEALV2 참고






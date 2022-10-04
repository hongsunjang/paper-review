# MEAL: Multi-Model Ensemble via Adversarial Learning

## Abstract

SOTA 방법들은 ensemble of multiple base-level network이다.
하지만 이는 test-time, memory requirement 때문에 제약사항이 많다.

=> $따라서$, complex trained ensembles을 single network로 압축하는 방법을 제시한다.

그 방법은 adversarial-based learning strategy이다.
1. block-wise training loss를 사용해, teacher guide feature를 사용해 predefined student network를 optimize한다.
2. discriminator network를 사용하여 teacher, student features를 구별하게 한다.

이 방법을 $MEAL$이라 하고 이 방법의 장점은
1. student network가 discriminator를 함ㄲ 사용되어 distilled student network는 original model보다 최적화가 더 잘된다.
2. fast inference is done by single model. + performance is better!
3. teacher network의 구조와 상관없이 distill을 할 수 있다.



## methodology
Teacher feature map 여러개를 adaptive pooling을 통해 student feature map에 맞춰 준 다음 두개의 Loss를 최적화 하는 방향으로 student network를 학습시킨다.
1. Similarity loss: L1, L2, KL-divergence 를 사용 가능(L2, KL-div가 좋았다)
2. GAN loss: 3 fc layer를 discriminator로 사용하고 이를 fool 시키기 위해 최적화한다.

> original model보다 더 좋다고????응?
> 
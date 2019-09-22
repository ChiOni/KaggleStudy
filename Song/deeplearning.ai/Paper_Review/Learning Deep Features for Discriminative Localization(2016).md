# Learning Deep Features for Discriminative Localization(2016)

#### 해당 논문의 Novelty( Cited by 1330 )

- GAP(global average pooling)을 single FC-layer 전, 마지막 Conv layer에 적용하는 것. 

- 효과:

  한 번의 전파를 통해 이산적인 이미지 구역을 효과적으로 찾을 수 있다.

  GAP를 통해 CAM(class activation maps)를 자동으로 일반화할 수 있다.

  	- class activation maps: 이미지의 어느 부분이 분류에 사용될 수 있는지 찾는 기술.
  	- CAM을 통해 특정 구역의 importance를 찾고 역전파시 가중할 수 있다.

  (https://glassboxmedicine.com/2019/06/11/cnn-heat-maps-class-activation-mapping-cam/)



#### Abstract

- 고전적인 GAP 기법이 CNN에서 효과적인 이미지 구역화를 가능하게  한다는 것을 제안한다.
- 정규화 기법으로 사용됬던 GAP이 localizable deep representation을 가능하게 한다는 것을 발견했다.
- 고전적인 bounding box annotation을 사용하지 않고도 높은 분류력을 가짐을 실험으로 확인했다.



#### Introduction

- 연구를 통해  CNN이 구역에 대한 정보없이도 효율적으로 Object detection이 가능하다는 것을 발견했다.

- 그러나 이런 구역화(Object detection(?)) 성능이 최종의 FC layer를 지나며 소멸되는 것을 발견했다.

- NIN/GoogLeNet 등과 같은 최신의 모델은 FC Layer의 파라미터를 최소화하면서도 높은 성능을 보이고 있다.

- 그리고 그것을 가능하게 하는 것은 정규화 기법인 GAP이 과적합을 예방해주기 때문이다.

- 해당 연구에서 GAP이 정규화뿐 아니라 구역화 정보를 전파함에도 효과적임을 발견했다.

  ![image2_1](C:\Users\littl\kaggle\Song\deeplearning.ai\Paper_Review\image\image2_1.JPG)

- 해당 방법론을 통해 weekly supervised 로도 기존의 supervised 모델과 유사한 성능을 가질 수 있다.



#### Related Works

- Weekly-Supervised object localization:
  - 기존의 방법론들은 여러 층의 전파를 통해 구역의 정보를 전달했다.
  - GMP를 사용했던 방법도 있지만 이것은 구역이 아닌 특정 Point를 찾는것이 한계였다.



#### Class Activation Mapping


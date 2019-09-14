# Continuous Video to Simple Signals for Swimming Stroke Detection with Convolutional Neural Networks
Continuous Video to Simple Signals for Swimming Stroke Detection with
Convolutional Neural Networks - Brandon Victor(2017) 을 리뷰합니다.



#### Abstract

- CNN 을 통해 연속성을 가진 4차원 비디오에서 이산적인 이벤트를 추출하는 것을 목표로 합니다.
- 기존의 연구들은 특정 시점의 행동을 분류하는 action recognition을 위해 CNN을 사용합니다.
- 해당 논문에서는 이미지를 시그널로 정사영하기 위해 CNN을 사용합니다.



#### Introduction

해당 연구에서는 개인의 수영 영상 속에서 팔 저음 횟수를 count 하는 것을 과제로 선정했습니다.

그러나 해당 모델의 방법론은, 수영 도메인 뿐 아니라 연속적인 비디오 데이터에서 

반복적인 행위의 횟수를 산출하는 모든 니즈에 적용할 수 있습니다.

- 해당 과제를 discrete event detection( 기존의 event detection과 다름)으로 정의합니다.
- 기존에는 특정 이미지 프레임에 1/0의 hard labelling을 통해 전체 비디오를 분류하고 학습했습니다.
- 그러나 hard labelling은 true point가 neighbor의 이미지들과 너무 적은 차이를 갖음에서 문제가 있습니다.
-  개략적인 모델링 과정
  1. 시계열에 Point로 된 라벨을 smooth signal 로 변환합니다.(피크 =  True point)
  2. 이미지 <-> Smooth Signal로 CNN 모델을 학습합니다.
  3. 모델을 통해 생성한 Signal을 다시 이산화된 포인트로 변환합니다.
- 주어진 과제
  1. Action recognition
  2. Action localisation
  3. discrete event detection



#### Related works

이미지 분류와 수영 비디오 데이터에 관한 기존의 연구들에 대해 소개합니다.

- 이미지를 Signal로 만들어 연속적인 비디오 데이터의 이미지를 분류하는 것이 해당 논문의 novel point입니다.



#### Modified problem description

![1_1](C:\Users\littl\kaggle\Song\deeplearning.ai\Paper_Review\image\1_1.JPG)

- Smoothing
  - 1/0 2분류의 raw label data를 연속적인 signal data로 변환
- Regression
  - CNN 모델을 통해 비디오 -> Signal 학습
  - mean-squared error loss를 최소화하도록 최적화합니다.
- Discretisation
  - Regression의 output인 시그널에서 이산의 점들을 추출합니다.



#### Our solution

- Regression
  - VGG-B를 기반으로하여 CNN 모델을 구현합니다.
  - 두 번의 conv layer과 하나의 pooling, 3번의 fc layer로 구성됩니다.
- Discretisation
  1. exponential smoothing 기법을 통해 output signal을 더욱 smooth하게 조정합니다.
  2. 적절한 threshold를 설정하여 broken chain으로 변환합니다.
  3. 각 구간의 중간 지점을 predict stroke 로 출력합니다.
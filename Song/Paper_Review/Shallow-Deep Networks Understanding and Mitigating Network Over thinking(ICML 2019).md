# Shallow-Deep Networks: Understanding and Mitigating Network Over thinking(ICML 2019)

#### The Over thinking Problem

- 초기 레이어에서 이미 정답을 알게 되는 문제들에 더 깊은 네트워크를 사용하는 것은 낭비
- 또한, 더 깊게 생각하는 것은 결과에 악영향을 준다.



#### Shallow - Deep Networks

- 네트워크 끝까지 가기전에, 네트워크 중간 중간에 결정을 내리자
  - Auxiliary classifier in GoogLeNet의 컨셉과 유사하다.
    - Gradient vanishing 문제를 완화
    - 결과 예측에 사용하지 않음.
  - Internal classifier in SDN



- 예측 방법

  - 중간 중간 예측을 하는 건 좋은데, 어떤 예측이 맞는지 어떻게 알지?

    = <b>Confidence-Based early exits</b>

    너무 나이브하지만, 직관적이고 효과적인 방법

- 실험
  - VGG16, ResNet56, Wide ResNet, MobileNets (vs) SDN
  - Data: CIFAR 10, CIFAR 100, Tiny ImageNet
  - 소모 비용을 25%, 50%, 75% 100% 로 제한해가면서 실험 진행



- Back dooring attack

  - 학습된 네트워크를 의도적으로 속이기 위한 데이터를 생성, 공격하는 행위

  - Image + noise -> 육안으로는 똑같지만 모델은 완전히 다른 결과를 내놓는다

    = VGG with SDN -> 잘못 분류되는 비율을 98%에서 17%까지 낮출 수 있다.




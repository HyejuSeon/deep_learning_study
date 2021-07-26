# lec02: Image Classification pipline

14

- 고양이 인식을 위해 corner를 찾는 방식으로 '명시적인 규칙 집합'을 쓰는 방법은 잘 동작하지 않는다.

1. 알고리즘이 강인하지 못함

2. 다른 객체를 인식하는 경우, 그 객체에 대해서도 별도로 만들어야 하기 때문에 처음부터 다시 시작해야 함.

<br>

25

- Nearest Neighbor: fast at training; slow at prediction

- CNN: fast at prediction; slow at training

<br>

27

- K가 증가할수록 노이즈에 강해짐

<br>

30

- 왼쪽 그림은 L1의 관점에서 원이다. -> 모든 점에서 (x-0) + (y-0)이 동일함

- 축을 회전시키면 L1 distance는 변하지만 L2는 변하지 않음

- 따라서 features가 개별적인 의미를 가지고 있으면(ex. 키, 몸무게) L1, 일반적이고 각 features간의 실질적인 의미를 잘 모르면 L2

<br>

31

- L1의 decision boundary는 좌표 축에 영향을 받지만, L2는 더 자연스러움

<br>

53

- bias는 특정 클래스에 우선권을 부여함 ex. 데이터셋이 불균형한 경우, 고양이 데이터가 개 데이터 보다 많다면 고양이 클래스에 해당하는 bias값이 더 커짐

- 테스트할 때 W값만 있으면 되기 때문에 속도가 빨라짐

<br>

54

- 가중치 행렬 W의 각 행은 각 이미지에 대한 템플릿으로 볼 수 있음

- W의 행 벡터와 이미지의 열 벡터 간의 내적 계산은 클래스 간 템플릿의 유사도를 측정하는 것과 유사함

- bias는 데이터와 독립적으로 각 클래스에 scailing offsets을 더해주는 것

<br>

56

- 아래 그림은 템플릿 매칭 관점에서 linear classification을 해석해보기 위해 W의 행 벡터를 시각화 시킨 것

- plane의 경우 linear classifier가 비행기를 분류할 때 푸른 것을 찾는 것이 도움이 된다고 볼 수 있음

- linear classifier의 문제는 각 클래스에 대해서 하나의 템플릿만 학습한다는 것 -> 한 클래스 내에서 다양한 특징들이 존재할 수 있지만 평균화하기 때문에

- 특히 말 템플릿은 말이 보통 풀밭에 있기 때문에 바닥이 초록빛이고 말의 머리가 앞뒤로 두 개가 달려있음

<br>

57

- 이미지가 고차원 공간의 한 점이라는 관점에서 linear classification이 해결할 수 없는 경우들이 있음

<br>

58

- 왼쪽 그림의 경우 두 개의 클래스를 선 하나로 분류할 수 없음

- 오른쪽 그림의 경우 파란 원 중 어떤 것이든 말의 머리가 될 수 있음

<br>

59

- linear classifier는 단순히 행렬과 벡터 곱의 형태이고, 템플릿 매칭과 관련이 있으며 각 카테고리 당 하나의 템플릿을 학습함을 알 수 있다.
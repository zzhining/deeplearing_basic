# CNN

**Contents**

[TOC]

## Computer Vision Task

![image-20220902201614719](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902201614719.png)

- Image Classification(Single object)
- Localization(Single object)
- Object Detection(Multiple object)

![image-20220902201633653](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902201633653.png)

- Image Segmentation(Multiple object)
- Image Generation
- Automated Colorization

![image-20220902202012580](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902202012580.png)

- Translation

![image-20220902201952357](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902201952357.png)

- Automatic Image Caption Generation([출처](http://cs.stanford.edu/people/karpathy/deepimagesent/))

![image-20220902201822278](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902201822278.png)



이미지도 숫자다

![image-20220902202941516](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902202941516.png)



![image-20220902202711392](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902202711392.png)







## CNN

- Convolutional Neural Network

- 배경

  - 일반적 신경망은 다양한 형태의 입력에 대한 확장성이 떨어짐 
  - 가운데 위치한 사과 이미지로 학습한 모델: 이미지의 가운데 부분을 집중하여 분석
  - ![image-20220902202902372](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902202902372.png)
  - 사과의 위치가 바뀌게(한쪽으로 치우치도록) 되면 성능 저하
  - 사물이 조금만 치우쳐도 인식하지 못하는 문제를 이미지 전체를 필터링하는 방식으로 해결

- Convolution Layer로 구성된 이미지 처리에 좋은 성능을 가지는 인공 신경망
  
  - 이미지 처리에만 사용되는 것은 아니지만, 이미지처럼 고차원 데이터에서 탁월한 성능을 보이기때문에 이미지 데이터를 활용한 태스크에 많이 활용됨

- 구성

  - Convolutional layer → pooling layer(subsampling) → Convolutional layer → pooling layer… → fully connected layer로 구성
  - 각 layer를 단순히 교차해서 조합하는 것은 아니고, 목적에 따라 조합하는 방법은 무궁무진함. 또한 Pooling layer가 항상 존재하는 것은 아님

  ![image-20220901174515827](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220901174515827.png)

  

### CNN의 주요 연산

(CNN의 입력으로 이미지만 가능한 것은 아니지만, 일반적으로 이미지를 많이 사용하므로 이미지 기준으로 작성함)

- 컨볼루션(Convolution)
  - 특징 추출 위해 단계별 다양한 필터 적용하고, 필터 적용시 마다 이미지 왼쪽 위에서 오른쪽 아래까지 밀면서 곱하고 더하는 작업
  - 이미지의 특징점을 효과적으로 찾는데 활용
  - 필터(Filter), 커널(Kernel)
    - 이미지에 겹치는 작은 필터 3x3 또는 5x5 사용
    - 학습을 통해 자동으로 적합한 필터 생성: 이미지의 특징을 추출하는 필터 학습
  - 컨볼루션 연산을 통해 여러 개의 작은 필터가 이미지 위를 돌아다니면서 특징점들을 찾아 그 합성곱 결과를 다음 계층으로 보냄
    - 적은 수의 가중치로 이미지 처리를 효율적으로 할 수 있음
- 패딩(Padding)
  - 입력 이미지 주변을 0으로 감싸서, 이미지 크기가 줄어드는 것을 보완
- 스트라이드(Stride)
  - 필터를 몇 칸 씩 건너뛰며 적용할 지 조절하는 값
- 특징 맵(feature map)
  - 컨볼루션 거쳐 나온 새로운 이미지유형 
- 풀링(Pooling)
  - 필터를 거친 여러 특징 중 가장 중요한 특징 하나 골라냄 (Sub sampling)
  - 평균값이나 최대값 선택(max-pooling, average-pooling)
  - 학습해야할 매개변수가 없고, 채널 수가 변하지 않음
- 완전연결(Fully connected)
  - 이전 레이어의 모든 처리 결과를 하나로 연결
  - 찾은 특징점을 기반으로 이미지를 분류(Classification)하는데 주로 활용



### 컨볼루션 연산

![](https://miro.medium.com/max/630/1*32zCSTBi3giSApz1oQV-zA.gif)



**기본**

![image-20220901175847569](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220901175847569.png)



**여러 개의 kernel이 존재할 때**

![image-20220901175859590](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220901175859590.png)



**Padding이 적용된 경우**

![image-20220901175911929](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220901175911929.png)





### 입출력 크기 계산 방법



![image-20220902203206717](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902203206717.png)



![image-20220902203213671](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902203213671.png)





### CNN의 차원 축소 방법

- Pooling
- Stride



## 실습

- MNIST 숫자 인식 모델
- CIFAR 객체 인식 모델
- VGGNet 구현하기(TensorFlow2.X ver.)
- VGGNet 구현하기(Torch ver.)
- ResNet Transfer learning
- 블랙핑크 멤버 분류 모델







------

## 주요 CNN 모델

### [ILSVRC](http://image-net.org/challenges/LSVRC/)

- 이미지 넷(Image Net)의 사물 인식 대회(Large Scale Visual Recognition Challenge)
- ILSVRC 대회 역대 우승 알고리즘
- ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FqTosh%2FbtqEcHOWtQ9%2FrJH68q6vDvsxgqMAFj9Br1%2Fimg.png)



-----

### [VGGNet](https://arxiv.org/pdf/1409.1556.pdf)

- 2014년 이미지 사물인식 대회에서 2위(1위는 GoogLeNet)

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FsK2Yt%2FbtqzklXMZZH%2FdSNDrxQKe8S5t9nkUpmL2K%2Fimg.png)





-----

### GoogLeNet

- 2014년 LSVRC 1위

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FIq9NO%2FbtqyPWk5PBX%2FK2JicGjIjj5w0eFIbhx4bK%2Fimg.png)

- 22층짜리 딥러닝 구조, 인셉션 모듈
- 잘 정리된 [블로그](https://bskyvision.com/539)



-----

### ResNet

- 2015년 LSVRC 1위
- layer의 입력을 layer의 출력에 바로 연결(skip connection)
  - skip-connection
    - H(x) = F(x) + x
- 깊은 층을 가지고 있지만 학습이 잘됨: Residual 구조 = gradient vanishing을 방지하는 방법

- 기존 NN: H(x)를 얻기 위한 학습
- Resnet
  - F(x)가 0이 되는 방향으로 학습, F(x) = H(x) – x
  - F(x)를 학습한다는 것은 나머지(residual)를 학습하는 것임

![](https://gaussian37.github.io/assets/img/dl/concept/resnet/2.png)

- 잘 정리된 [블로그](https://gaussian37.github.io/dl-concept-resnet/)
- [He et al., 2015] [Deep Residual Learning for Image Recognition](https://arxiv.org/pdf/1512.03385.pdf)
- [He et al., 2016] [Identity Mappings in Deep Residual Networks](https://arxiv.org/pdf/1603.05027.pdf)





## EfficientNet

- depth, width, resolution을 동시에 고려한 compound scaling을 통해 ConvNet기반 이미지 분류 성능을 개선한 모델

- 목적: 이미지 분류

- 개선방향 : depth, width, resolution 동시에 키워서 성능 개선
  - width(필터의 개수 늘림), depth(레이어 수 늘림), resolution(이미지 해상도 키움)
- 성과: 연산은 줄이고, 정확도는 높임

![image-20220902200713864](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902200713864.png)







## Transfer Learning

- 기존의 만들어진 모델을 사용하여 새로운 모델을 만드는 방법
- 학습을 빠르게 하며 예측 성능을 더 높임
- 이미 잘 훈련된 모델이 있고, 특히 해당 모델과 유사한 문제를 해결 시 transfer learning을 사용



## CNN 적용 사례


# GAN

- Generative Adversarial Networks, 생성적 적대 신경망
- 대립하는 두 시스템 생성자(Generator)와 판별자(Discriminator)가 서로 경쟁하는 방식으로 학습을 진행하는 비지도 학습 알고리즘 (준지도학습, Semi-supervised learning)
- 비교 학습 방식으로 실제와 비슷한 가상의 데이터(예: 이미지 또는 음성 등) 생성
  - GAN을 활용하여 유명 화풍을 반영한 이미지 생성, 웹툰 제작 등 다양한 컨텐츠를 제작가능
- GAN의 구성
  - 생성자(Generator)
    - ‘데이터의 형태' 를 만들어냄: ‘데이터의 형태’라는 것은 데이터의 분포 혹은 분산을 의미함
    - 각 클래스의 분포를 모델링: 원본 데이터의 확률분포를 분석하고, 원본 데이터의 확률분포를 따르는 새로운 데이터 인스턴스 생성
    - 판별자로부터 피드백(비지도학습)
  - 판별자(Discriminator)
    - 데이터 진위평가
- GAN의 한계
  - 결과가 불안정
  - 생성자(Generator) 모델의 평가방법이 주관적임
  - 새로운 샘플이 기존 샘플과 얼마나 유사한지 확인할 수 있는 정량적인 척도가 없음









# DCGAN

- GAN알고리즘을 구성하는 Generator와 Discriminator 의 Fully connected layer를 CNN(Convolutional Neural Network) 구조로 대체한 알고리즘
- 생성자(Generator)가 단순 기억으로 생성하지 않고, z의 미세변동에 따른 생성(generate)결과가 연속적으로 부드럽게 이루어지도록 보완
  - 생성자: 매개변수에서 원래 이미지를 찾아 처리하는 디컨볼루션 네트워크(De-Convolution Network)로 구성되며, 입력된 노이즈(랜덤 신호)로부터 이미지를 생성
  - 판별자: 매개변수를 응축처리하는 컨볼루션 네트워크로 구성되며, 여기에 위조 이미지 또는 실제 이미지를 입력
- 특징
  - 데이터 불균형(abnormal 데이터 부족) 해결
  - labeling 시간 및 리소스 단축
  - 기존에 알지 못했던 anormal event detect
- 방법
  - G: 정상 데이터의 주요 특징을 사용해서 정상 이미지 생성
  - D: Fake normal과 Real normal의 잔차(residual)계산
  - G와 D의 weight는 고정시키고, latent vector를 total loss가 최소화되도록 조절
- 의의
  - inverse mapping(data space를 latent space로 변환)
- 한계
  - large dataset, real time app에 적용 불가능
- DCGAN으로 생성한 MNIST 이미지 

![image-20220902210017976](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902210017976.png)







# Examples

- [BEGAN](https://arxiv.org/pdf/1703.10717.pdf)
- [Progressive Growing GAN](https://arxiv.org/pdf/1710.10196.pdf)
- Everybody Dance Now: [paper](https://arxiv.org/pdf/1808.07371.pdf), [youtube](https://www.youtube.com/watch?v=PCBTZh41Ris)
- [DeepVoice2](https://carpedm20.github.io/tacotron/)
- [DeepVoice3 paper](https://arxiv.org/pdf/1710.07654.pdf)
- [Meitu](https://www.meitu.com/en/media/305)
- [네이버 웹툰 '마주쳤다'에 적용된 GAN (generative adversarial networks) 기술](https://www.naverlabs.com/storyDetail/44)

![img](https://www.naverlabs.com/naverlabs_/story/201712/1513822603755_%EB%8F%84%EC%8B%9D2.jpg)




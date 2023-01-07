# AutoEncoder
![image-20220902212114574](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902212114574.png)
- 입력한 데이터를 부호화한 후 복호화하는 신경망
- 입력데이터의 특징점을 추출


----

## AutoEncoder 구조

![image-20220902212120686](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902212120686.png)
- 인코더와 디코더로 구성
- 입력층과 출력층의 노드 수가 동일



----


## AutoEncoder로 생성한 이미지
![image-20220902212128682](https://github.com/zzhining/deeplearing_basic/blob/main/images/image-20220902212128682.png)



----


## 특징
  - Data-specific : 훈련된 데이터와 비슷한 데이터로만 압축
    - 예) 얼굴 사진에 대해 학습된 AE는 나무의 사진 압축에 성능 (X)  → 얼굴 특징 학습
  - 손실 발생 :  압축 해제된 결과물은 원본 보다 좋지 않음



----


## 활용
  - 데이터압축, 저차원화를 통한 데이터 관계 관찰, 배경잡음억제(denosing)



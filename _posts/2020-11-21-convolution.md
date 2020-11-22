---
layout: post
title:  "[Tensorflow] 기본적인 CNN의 적용"
date:   2020-11-21T14:25:52-15:00
author: Cho Kwanheum
categories: AI
---

coursera 강의 'Convolutional Neural Networks in TensorFlow' by Laurence Moroney 를 수강한 후 자체 환경에서 수정, 적용한 내용입니다.

---


# CNN의 적용
기본적인 CNN을 만들고, 실제 데이터를 이용하여 적용해보자.<br>
먼저 기본적인 라이브러리들을 사용하기 위해 다음과 같이 구성해줬다.<br>
![sreensh](/assets/cnn1/ss1.png)

### 데이터
데이터는 Kaggle에 존재하는 개&고양이 이미지를 로컬저장소 'Kaggle'폴더에  저장후 진행했다.<br>
[데이터 출처](https://www.kaggle.com/chetankv/dogs-cats-images)<br>

![sreensh2](/assets/cnn1/ss2.png)
원하는 위치의 하위에 /dataset폴더가 만들어졌고 그 하위에 각각 training_set과 test_set이 존재한다. 각각 데이터의 크기는 4000개 1000개이다.
추가적으로 각 이미지마다의 label값이 따로 주어져 있지는 않지만, 각각의 폴더에 사진이 모여있으므로 ImageGenerator를 사용하여 간편하게 데이터를 사용할 수 있다.
![sreensh5](/assets/cnn1/ss5.png)
rescale을 이용해 픽셀값이 0~1의 값을 가지도록 범위를 조정해주고, batch_size , class_mode, target_size를 설정해준다. ImageGenerator의 장점은 상위 디렉토리의 이름대로 label을 설정해준다는 것이다.<br>
예를 들어, cats 폴더 밑에 있는 사진들은 모두 cat 의 class로 묶는다.<br>
위에서 보이듯이 8000개의 training image , 2000개의 test image가 2 class로 분류되었음을 볼 수 있다.

### 모델
모델은 3개의 Convolution layer와 MaxPooling layer를 쌓고, 그 이후 Flatten과 Dense layer를 쌓아 구성했다.<br>
optimizer는 RMSprop을 사용했고 개 or 고양이 두가지의 분류이기 때문에 loss는 binary crossentropy를 사용했다.<br>
![sreensh3](/assets/cnn1/ss3.png)
model. summary()를 이용하여 모델의 형태를 살펴보면 전체적인 구성을 알 수 있다. <br>
![sreensh4](/assets/cnn1/ss4.png)
(300, 300, 3)의 입력 값이 Convolution layer를 지나면 필터의 크기로 인해 (298, 298, channel=8)의 결과 값이 나오게 되고 Pooling layer를 거쳐 절반의 크기인 (149, 149, channel=8)로 변하게 됨을 알 수있다. 마찬가지의 작용이 두 번 더 일어나게 된다. <br>
Image Generator를 사용했기 때문에 fit_generator를 사용하여 훈련을 시켜주게되면 다음과 같은 결과를 얻을 수 있다.
![sreensh6](/assets/cnn1/ss6.png)
training acc는 계속해서 증가하나, validation_acc는 큰차이 없이 유지됨을 볼 수 있다.
좀 더 살펴보기 위해 loss 와 accuray에 관한 그래프로 살펴보자.<br>
![sreensh7](/assets/cnn1/ss7.png)
파란색이 Validation인데, 전체적으로 acc는 변하지 않으며 일정시점을 기준으로 loss는 오히려 증가함을 볼 수있다.<br>
원인은 4000개라는 한정된 훈련데이터 양으로 인한 overfitting을 예상해 볼 수 있다.<br>
해당 부분에 대한 개선사항은 추후 더 알아보겠다.

---

추가 학습 필요
Q. fit 과 fit_Generator의 차이점?<br>
Q. Overfit을 막을 수 있는 방법?<br>
Q. 성능을 향상 시킬 수 있는 parameter 설정 방향성?<br>

---


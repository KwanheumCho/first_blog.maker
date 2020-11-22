---
layout: post
title:  "[TensorFlow] Tutorial1 - Keras를 이용한 기본 분류"
date:   2020-11-14T14:25:52-15:00
author: Cho Kwanheum
categories: AI
---

원본 출처 : https://github.com/tensorflow/docs/blob/master/site/en/r1/tutorials/keras/basic_classification.ipynb 

---


# 뉴럴넷의 시작 : 분류 
keras에서 제공하는 fashion_mnist 데이터를 이용해 텐서플로를 경험해볼 것입니다.  필요한 라이브러리들을 세팅했습니다. 제 텐서플로우 버전은 1.15.0입니다.
![screensh](/assets/tutorial1_img/ss1.png)
<br>  
<br>

### Data
Fashion Mnist dataset은 10가지 종류의 70000개의 흑백이미지를 제공합니다. 이미지는 흑백이미지이기 때문에 하나의 채널을 가지며 28X28의 numpy array의 형태로 각 픽셀의 값은 0~255입니다(RGB). 그리고 각각 이미지의 종류는 다음과 같습니다. ![screensh2](/assets/tutorial1_img/ss2.png){: width="250" height="400"}
60000개의 이미지가 훈련데이터이고, 10000개의 이미지가 실험데이터입니다.

각 픽셀의 값은 0~1의 값을 가지도록 normalization 해줄 필요가 있습니다.
![screensh3](/assets/tutorial1_img/ss3.png)
<br>
<br>
### Build the Model
뉴럴넷 모델을 구축하는 과정은 필요한 layer를 쌓고 컴파일 하는 과정을 거칩니다.
<br>
####   Setup layers
![screensh4](/assets/tutorial1_img/ss4.png)
여기서는  keras의 선형결합을 이용해 Flatten , Dense layer를 결합하여 모델을 만듭니다.
첫번째 Flatten layer는 2차원 배열형태의 input값을 1차원 배열 형태 (28*28 = 784pixels)로 바꿔줍니다. ( 파라미터는 존재하지 않고, 단순히 데이터의 형태를 바꿔주기 위한 층입니다.)
두번째 Dense layer는 Fully-Connected layer로 완전 연결형태를 띄며 layer의 노드 수를 설정해줄 수 있습니다. 각각 128, 10으로 설정했습니다. layer에 존재하는 activation function은 따로 정리해서 올리겠습니다. 
간단하게 설명하면 relu는 선형적인 연결을 비선형적인 결과로 표현해주기 위함이고, softmax는 출력 값들을 0~1사이의 확률로 정규화하며 모든 값의 합이 1이 되도록 만들어 줍니다.

<br>
####   Compile model
![screensh5](/assets/tutorial1_img/ss5.png)
layer를 쌓았으면 이제 모델의 세부사항을 설정해야합니다. 대표적으로 Loss function, Optimizer, Metrics 들이 있습니다.
<br>
<br>
### Train & Evaluate
모델에 훈련 데이터와 훈련 라벨을 넣어주고 반복횟수(epochs)를 정하여 훈련을 시켜줍니다. 결국 훈련이란 우리가 설정한 layer로 구성된 모델에 훈련용 데이터셋을 넣어서 반복하며 데이터의 관계를 파악하는 과정입니다.
훈련이 완료된 모델을 이용해  실험 데이터와 실험 라벨을 넣어서  정확도를 평가해줍니다.
![screensh6](/assets/tutorial1_img/ss6.png)
<br>

## Prediction
훈련이 완료된 모델을 이용해서 어떤 이미지의 종류를  예측 해볼 수 있습니다. 
![screensh7](/assets/tutorial1_img/ss7.png)
예측해 볼 데이터가 현재는 없는 관계로 실험용 이미지를 다시 사용해 보겠습니다.<br>
predictions[5]는 6번째 이미지의 예측 결과 값으로, 길이가 10인 확률의 배열을 확인할 수 있습니다.<br>
이 확률 값들 중 가장 큰 값을 가지는인 1번 index가 해당 이미지의 종류임을 예측해 볼 수 있고, 실제로 6번째 이미지의 라벨 값이 1임을 알 수 있습니다.
<br>




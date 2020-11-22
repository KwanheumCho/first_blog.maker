---
layout: post
title:  "[TensorFlow] Tutorial2 - Keras를 이용한 기본 텍스트분류"
date:   2020-11-16T14:25:52-15:00
author: Cho Kwanheum
categories: AI
---

원본 출처 :  https://github.com/tensorflow/docs/blob/master/site/en/r1/tutorials/keras/basic_text_classification.ipynb

---


# 뉴럴넷의 시작 : 분류 
keras에서 제공하는 IMDB 데이터를 이용해 텐서플로를 경험해볼 것입니다.  필요한 라이브러리들을 세팅했습니다. 제 텐서플로우 버전은 1.15.0입니다.
![screensh](/assets/tutorial1_img/ss1.png)
<br>  
<br>

### Data
![scrrensh2](/assets/tutorial2_img/ss2.png)
IMDB데이터는 이미 전처리과정을 거쳐서 단어들이 정수의 인덱스로 변환이 되어있습니다.<br>
num_words=10000을 통해 빈도수가 높은 상위 10000개의 단어들만 저장했습니다.
<br>
정수의 인덱스로 표현된 데이터들을 뉴럴넷에서 사용하기 위해서 벡터화 시켜줄 필요가 있고 여기서는 Embedding 방법을 사용할 것입니다. [Embedding 참고](https://kwanheumcho.github.io/ai/2020/11/16/embedding.html)<br>
Embedding을 위해선 사용할 데이터들의 길이를 맞춰줄 필요가 있고 다음과 같이 패딩을 진행합니다.
![scrrensh3](/assets/tutorial2_img/ss3.png)
데이터가 maxlen보다 짧다면  뒷쪽(post)에 값(0)을 길이(256)이 되도록 추가해줍니다. 길다면 오히려 잘라줍니다.
<br>


### Build the Model
뉴럴넷 모델을 구축하는 과정은 필요한 layer를 쌓고 컴파일 하는 과정을 거칩니다.
<br>
####   Setup layers
![screensh4](/assets/tutorial2_img/ss4.png)
여기서는  keras의 선형결합을 이용해 Embedding, Pooling, Dense layer를 결합하여 모델을 만듭니다.
첫번째 Embedding layer에서는 상위 10000개의 단어를 가져왔으니 vocab_size를 10000으로 설정해주고 16차원의 벡터를 만듭니다. shape : (batch_size * 10000 * 16)<br>
두번째 Pooling layer에서는 단어 차원의 평균을 내는 작업을 수행합니다. shape: (batch_size * 16)<br>
마지막 Dense layer에서는 완전 결합으로 결과값을 도출합니다. 각각의 활성함수는 추후에 자세하게 설명하겠습니다.

<br>
####   Compile model
![screensh5](/assets/tutorial2_img/ss5.png)
layer를 쌓았으면 이제 모델의 세부사항을 설정해야합니다. 대표적으로 Loss function, Optimizer, Metrics 들이 있습니다.
<br>
<br>
### Train & Evaluate
모델에 훈련 데이터와 훈련 라벨을 넣어주고 반복횟수(epochs)를 정하여 훈련을 시켜줍니다. 결국 훈련이란 우리가 설정한 layer로 구성된 모델에 훈련용 데이터셋을 넣어서 반복하며 데이터의 관계를 파악하는 과정입니다. 여기서는 훈련데이터의 일부를 검증데이터로 만들었습니다. verbose=1을 넣어줌으로써 진행상황을 확인할 수 있습니다.
![screensh6](/assets/tutorial2_img/ss6.png)
훈련이 완료된 모델을 이용해  실험 데이터와 실험 라벨을 넣어서  정확도를 평가해줍니다.
![screensh7](/assets/tutorial2_img/ss7.png)
<br>

이번 튜토리얼을 통해 자연어 처리의 과정을 간단하게 경험할 수 있었습니다.

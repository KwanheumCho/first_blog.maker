---
layout: post
title:  "기본 개념 : Embedding이란"
date:   2020-11-15T14:25:52-15:00
author: Cho Kwanheum
sitemap:
   changefreq: daily
   priority: 1.0
categories: AI
---

---


# Embedding이란 
Embedding을 간단하게 설명하면 텍스트 데이터를 컴퓨터가 이해할 수 있도록 수치화 해주는 것이라고 할 수 있다.<br>
가장 기본적인 방법은 One-hot encoding이다. 예를 들어 '사과, 바나나, 토마토'라는 단어 집합이  있을 때 각각의 단어를 [1,0,0] [0,1,0] [0,0,1]로 만들어 주는 것이다. 단어의 수가 많아질수록 0이 굉장히 많이 들어가게 되고 이를 '희소 표현'이라고도 부른다. 간단하지만 공간이 많이 필요하기 때문에 비효율적이고, 단어간의 관계를 표현하지 못한다는 단점이 있다.<br>
이를 해결하기 위한  방법으로 word embedding이 있다. '밀집 표현'의 형태로, 단어의 수에 상관없이 설정해주는 특정 차원의 벡터로 단어를 표현하는 것이다. 예를 들어2차원으로 벡터를 만든다고 한다면  사과 : [0.5, 0.3], 바나나 : [0.1, 0.2], 토마토: [0.8, 0.1] 와 같이 만드는 것이다. <br>

### Keras Embedding layer
Word embedding을 하기 위한 여러 방법들(TF-IDF , Word2vec, ... etc)등이 있으나 기본적으로 Keras에서 어떻게 작동하는지를 살펴보자.
![screensh](/assets/concept/embedding1.png)
작동원리를 확인하기 위해 임의로 입력값을 만들었다.<br>
input_array는 10개의 단어집합에서 각각 5개의 단어를 가지는 2개의 문장이라고 볼 수 있다.<br>
Embedding layer에는 (전체 단어집합의크기 , 임베딩벡터의 차원)을 넣어줬다. <br>
간단하게 구현한 모델에 input값을 넣고 output의 형태와 값을 보면, (2, 5, 2) = ( input_shape, 임베딩벡터의차원)의 형태를 가짐을 알 수 있고 각각의 단어들이 2차원 벡터로 표현되었음을 알 수 있다.<br>
input의 0 -> [-0.00266911 0.02828922]<br>
input의 4 -> [0.0131993 -0.01541017]<br>
<br>  
<br>

---
layout: post
title:  "TensorFlow Tutorial1 - 텐서플로를 이용한 기본 분류"
date:   2020-11-10T14:25:52-15:00
author: Cho Kwanheum
categories: AI
---

원본 출처 : https://github.com/tensorflow/docs/blob/master/site/en/r1/tutorials/keras/basic_classification.ipynb 

---


# 뉴럴넷의 시작 : 분류 
keras에서 제공하는 fashion_mnist 데이터를 이용해 텐서플로를 경험해볼 것입니다.  필요한 라이브러리들을 세팅했습니다. 제 텐서플로우 버전은 1.15.0입니다.
![screensh](/_posts/tutorial1_img/ss1.png)
<br>  
<br>

## Data set
Fashion Mnist dataset은 10가지 종류의 70000개의 흑백이미지를 제공합니다. 이미지는 흑백이미지이기 때문에 하나의 채널을 가지며 28X28의 numpy array의 형태로 각 픽셀의 값은 0~255입니다(RGB). 그리고 각각 이미지의 종류는 다음과 같습니다. ![screensh2](/_posts/tutorial1_img/ss2.png)
<br>60000개의 이미지가 훈련데이터이고, 10000개의 이미지가 실험데이터입니다. 각 픽셀의 값은 0~1의 값을 가지도록 normalization을 해줄 필요가 있습니다.



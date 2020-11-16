---
layout: post
title:  "TensorFlow Tutorial1 - 텐서플로를 이용한 기본 분류"
date:   2020-11-16T14:25:52-15:00
author: Cho Kwanheum
categories: AI
---
<p> https://github.com/tensorflow/docs/blob/master/site/en/r1/tutorials/keras/basic_classification.ipynb를 참조했습니다.</p>
<hr>

<h1> 뉴럴넷의 시작 : 분류 </h1>
<p> keras에서 제공하는 fashion_mnist 데이터를 이용해 텐서플로를 경험해볼 것입니다.</p>
<hr>

<h2> Data set </h2>
<p> Fashion Mnist dataset은 10가지 종류의 70000개의 흑백이미지를 제공합니다. 이미지는 흑백이미지이기 때문에 하나의 채널을 가지며 28X28의 numpy array의 형태로 각 픽셀의 값은 0~255입니다(RGB). 그리고 각각 이미지의 종류는 다음과 같습니다. (사진) 
60000개의 이미지가 훈련데이터이고, 10000개의 이미지가 실험데이터입니다. 각 픽셀의 값은 0~1의 값을 가지도록 normalization을 해줄 필요가 있습니다. </p>




---
layout: post
title:  "TensorFlow Tutorial3 - 케라스와 텐서플로 허브를 사용한 영화 리뷰텍스트 분류하기"
date:   2020-11-16T14:25:52-15:30
author: Cho Kwanheum
categories: AI
---
<p> https://www.tensorflow.org/tutorials/keras/text_classification_with_hub를 참조했습니다.</p>
<hr>

<h1> Transfer Learning(전이학습)이란? </h1>
<p>전이학습이란 풍부한 학습데이터를 바탕으로 이미 훈련된 모델(pre-trained model)을 활용하는 것을 의미합니다.</p>
<p>만약 우리가 검증하고자 하는 데이터와 유사한 특징을 가진 데이터로 훈련된 모델이 존재한다면 처음부터 시작하는 것 보다는 전이학습을 이용할 때 쉽고 빠르게 결과를 얻을 수 있을 것입니다. 또한 데이터가부족할 때 이 방법은  유의미하게  사용될 것입니다.
<hr>

<p>이번 튜토리얼에서는 영화 리뷰 텍스트를 감성분석하여 긍정/부정으로 분류합니다. 고수준 파이썬 API인 keras와 전이학습 라이브러리이자 플랫폼인 TF hub를 이용합니다.</p>



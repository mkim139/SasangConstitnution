# 사상체질 분석 모델


사진을 찍으면 얼굴을 Detect -> process 후 사상체질을 분석 해주는 모델 개발하여, Fun 건강 컨텐츠 제공 및 식단 등의 연계 서비스 확장

![image](https://user-images.githubusercontent.com/32697109/173339697-3f881038-1dff-48e0-a3cf-83cd984581b3.png)
http://pointsofhealthacupuncture.com/acupuncture-and-oriental-medicine/

## Project 기간 6개월:  
* 데이터 수집 2개월: Crowd Sourcing을 통하여 Age/Gender Demographic 골고루 얼굴 사진 및 사상체질 설문(간소화된 QSCC) 내용 수집
* 얼굴 Detection model 훈련 1개월: 얼굴 Detection에 Specialize된 YOLOv3 구성 및 훈련
* 얼굴 Processing을 위한 XceptionNet 기반 Landmark detection 모델 개발 1개월
* Process된 얼굴의 사상체질을 Classify 하는 모델 개발 1개월
* 최종 Pipeline 구성 1개월


## 모델 구성

이 모델은, 아이 얼굴 사진으로 유전질환 여부를 확인하는 모델인 DeepGestalt 모델을 Motive로 구성되었습니다.
https://arxiv.org/pdf/1801.07637.pdf

![image](https://user-images.githubusercontent.com/32697109/173341143-f68c6542-352e-4bc7-9809-fce058b630e2.png)

1. Input 이미지를 YOLO 모델을 활용하여 얼굴 부분만 가져옵니다. 
2. XceptionNet-Landmark은 얼굴의 주요 landmark를 예측한 후, 알맞는 부분들로 나눕니다.
3. 부분별로 나뉜 얼굴은 각 분석 모델의 input으로 들어가 사상체질 결과값을 받고, Voting을 하게 됩니다.

## Model performance
 
 Classification Accuracy: ~74%
 
 비교 모델 : 얼굴 정보와 혈액 성분수치를 활용한 모델의 정확도가 ~80% 정도  
 https://www.hellodd.com/news/articleView.html?idxno=28027
 
 ## 개선점
 
 사람들의 설문의 성실도가 떨어질 수 있다는 점과, QSCC 설문 또한 사상체질 진단에 참고용으로만 사용되어, 완벽한 Label이 되기 어려움.  
 가능하다면 다음에는 사상체질 전문 한의사의 도움을 얻어 사람들의 정확한 체질 label을 얻는 것이 필요할 것으로 보임

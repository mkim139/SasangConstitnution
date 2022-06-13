# 사상체질 분석 모델


사진을 찍으면 얼굴을 Detect -> process 후 사상체질을 분석 해주는 모델 개발

![image](https://user-images.githubusercontent.com/32697109/173339697-3f881038-1dff-48e0-a3cf-83cd984581b3.png)
http://pointsofhealthacupuncture.com/acupuncture-and-oriental-medicine/

Project 기간 6개월:  
* 데이터 수집 2개월: Crowd Sourcing을 통하여 Age/Gender Demographic 골고루 얼굴 사진 및 사상체질 설문 내용 수집
* 얼굴 Detection model 훈련 1개월: 얼굴 Detection에 Specialize된 YOLOv3 구성 및 훈련
* 얼굴 Processing을 위한 XceptionNet 기반 Landmark detection 모델 개발 1개월
* Process된 얼굴의 사상체질을 Classify 하는 모델 개발 1개월
* 최종 Pipeline 구성 1개월


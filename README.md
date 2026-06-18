# ABIDE 데이터셋 기반 자페 스펙트럼 장애 분류

## 1. 프로젝트 배경 및 동기 

### 1) 자페 스펙트럼 장애 (ASD) 원인:
* 뇌 영역 간의 기능적 과잉 연결(Functional Over-connectivity) 또는 저연결(Functional Under-connectivity)로 인해 발생.

### 2)진단의 필요성: 
* 정확한 진단을 위해 뇌의 특정 활동 패턴을 식별하는 객관적 지표가 필요.

## 2. 데이터

### 1) ABIDE 데이터
* ABIDE는 자폐증 뇌 영상 데이터 교환(Autism Brain Imaging Data Exchange)의 약자.
* 전 세계의 여러 병원과 연구 기관들이 협력하여, 자폐 스펙트럼 장애를 가진 사람들과 일반 대조군의 뇌 영상 및 임상 데이터를 하나로 모아 2012년에 공개한 대규모 데이터베이스 프로젝트
* 수집 기관(Sites): 전 세계 17개 서로 다른 연구 기관

### 2) ABIDE 종류

|Atlas|분할 기준|총 영역 수|특징 및 장단점|
|--|--|--|--|
|AAL|해부학적 구조 (고랑, 이랑)|116개|가장 고전적이고 직관적이지만, 기능적 분석(fMRI)에는 구역이 너무 넓어 정밀도가 떨어질 수 있음|
|CC200|데이터 기반 기능적 군집화|200개|ABIDE 논문 및 AI 분류 모델에서 가장 대중적으로 쓰이는 벤치마크 기준. 신호의 동질성이 잘 유지됨|
|Schaefer|대규모 네트워크 기능적 연결성|100 ~ 1,000개 (가변적)|최신 연구에서 선호됨. 뇌의 7대/17대 인지 네트워크(Yeo Atlas)와 완벽히 연동되어 고차원 분석에 유리|


## 3. 전처리 
* 데이터 전처리 : 18세 이하(Adolescent) 와 18세 이상(Adult)으로 2개의 데이터 그룹으로 전처리함


## 4. 모델
<img width="903" height="369" alt="제목 없음" src="https://github.com/user-attachments/assets/48b83ee5-f13c-4b0c-8ad1-bb136d05d232" />

* 자폐 데이터에 적합한 7가지 모델을 선정
* 다른 모델에 비해 GAT 모델과 TransformerGNN이 성능적으로 뛰어남 

## 5. 결과
<img width="1324" height="791" alt="그림2" src="https://github.com/user-attachments/assets/6477721b-811e-46a3-8147-551c573202a3" />

* 최종적으로 CC200, 청소년, GAT 조합이 가장 높은 성능으로 학습됨



||AgeGroup|Model|Acc|F1|AUC Best|
|--|--|--|--|--|--|
|ALL (fusion)|        all| 	     CrossAtlasFusion|    0.5212±0.0308|    0.3424|     0.5000±0.0000|   
|ALL (fusion)| 	adolescent|   CrossAtlasFusion|    0.4937±0.0290|    0.3303|     0.5000±0.0000|   
|ALL (fusion)|      	adult|          CrossAtlasFusion|    0.5311±0.0353|     0.3465|    0.5000±0.0000|   



# 머신러닝을 위한 학습 데이터 전처리 DataOps 기술 개발

경희대학교 컴퓨터공학과 김서현

## Abstract

머신러닝 학습을 통해 유의미한 결과를 도출하기 위하여 우수한 알고리즘을 설계하는 것만큼이나 정제된 데이터를 보유하는 것이 중요하다. 이를 위하여 데이터 전처리 과정은 필수적이지만 전처리 작업을 수행하는 데 많은 노력과 시간이 소요된다. 따라서 본 문서에서는 학습 데이터 전처리 작업의 편의성을 증진하는 DataOps 기술을 제안한다. 학습 데이터셋 관리부터 데이터 시각화 및 통계 작업, 그리고 다양한 전처리 기법 적용까지 머신러닝 학습을 위한 데이터 준비 과정을 웹 인터페이스 기반으로 간편하게 수행할 수 있는 기술을 구현한다. 특히 본 기술에서는 시계열 데이터를 중심으로 하여, 시계열 데이터의 특성을 바탕으로 효율적으로 수행할 수 있는 전처리 기능을 제공한다.

## Tech Stack

- Spring Boot
- FastAPI
- Vue.js
- MySQL

## Project

### Dataset API

https://github.com/seoh02h/khu-data-studio-dataset-api

### Preprocessing API

https://github.com/seoh02h/khu-data-studio-preprocessing-api

### API Gateway

https://github.com/seoh02h/khu-data-studio-api-gateway

### Service Discovery

https://github.com/seoh02h/khu-data-studio-service-discovery

### UI

https://github.com/seoh02h/khu-data-studio-ui

## VAR 모델 기반 예측값 대체 프로세스

### 전체 프로세스 요약

1. 지수 이동 평균 EMA 방식을 이용한 노이즈 제거
2. 피어슨 상관 계수를 계산하여 상관 관계를 가지는 컬럼 선택
3. VAR 모델을 이용하여 복합 데이터 학습
4. 결측치 예측

### 1. 지수 이동 평균 EMA 방식을 이용한 노이즈 제거

- 지수 이동 평균(Exponential Moving Average)
- 가중변수를 이용하여 최근 수치의 영향력은 높이고 과거 수치의 영향력은 낮추는 기법

```
EMA(i) = k * price(i) + (1-k) * EMA(i-1)
```

<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205540910-f0887d56-815a-4c83-a43c-8033209cd2aa.png">

### 2. 피어슨 상관 계수를 계산하여 상관 관계를 가지는 컬럼 선택

- 노이즈 제거를 먼저 수행하는 이유는 노이즈 제거 후 피어슨 상관 계수 계산 시 절댓값이 향상
- 노이즈 제거 후 피어슨 상관 계수 계산 결과 시 상관 관계가 존재하는 컬럼에 대하여 계산 결과 절댓값이 증가하는 경향을 확인할 수 있다

<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205540972-6a3dfa93-caa7-4f46-8a31-2ac228445d40.png">

### 3. VAR 모델을 이용하여 복합 데이터 학습

- Vector Auto Regression 벡터 자동 회귀 모델을 통해 복합 데이터 예측을 위한 학습을 수행
- VAR은 예측할 변수의 과거 값 뿐만 아니라 예측할 변수와 의존성이 있는 변수까지 고려하여 선형 함수로 나타내는 확률적 과정
- 성능평가 데이터 : ‘스마트 플랜트 이상상태 조기감지를 위한 머신러닝 기반 저대역 영상/통신 Edge Computing 시스템’ 과제에서 발전설비 이상 상태 조기 감지를 위해 센서로 수집된 데이터
- p 차 VAR 모델

<img width="376" alt="image" src="https://user-images.githubusercontent.com/68395698/205542006-2f5f9b9b-3e88-4a89-930e-5dd930ad0b68.png">
변수 c는 모델의 절편 역할을 하는 상수의 k 벡터, A i는 시불변 ( k × k )-행렬 및 e t는 오류 항의 k- 벡터

### 4. 결측치 예측

<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205541040-37686275-5216-4244-add6-e1201baa09ad.png">

## KHU Data Studio

### 데이터셋 관리

#### 데이터셋 리스트

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/68395698/205538854-47d4754c-6a2b-4fab-ac17-6065683d0c0a.png">

- 데이터베이스 테이블을 통한 데이터셋 등록

<img width="1438" alt="image" src="https://user-images.githubusercontent.com/68395698/205538896-6d0facbd-2912-4074-ae56-dace12a9f36a.png">

- 정보 입력 후 프리뷰

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/68395698/205538930-6d38d736-a5ec-4290-b426-7b4f476a934d.png">

- CSV 파일을 통한 데이터셋 등록

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/68395698/205539006-f3d03172-e221-46cf-a2c6-74563946bf0b.png">

### 데이터 현황

#### 데이터셋 선택

- 메뉴 클릭 시 먼저 데이터셋을 선택할 수 있는 모달이 나타난다
- 모달을 통해 원하는 데이터셋을 선택하여 시각화/통계를 수행한다

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/68395698/205539122-b91aa8a8-3d62-443a-9888-88441b1de9fb.png">

#### 데이터 시각화

- 상단의 컬럼 라벨을 클릭하여 해당 컬럼 데이터의 디스플레이 여부를 결정할 수 있다
- 우측 상단 기간 선택 기능을 통해 날짜별 필터링을 수행할 수 있다

<img width="1438" alt="image" src="https://user-images.githubusercontent.com/68395698/205539240-b047b89f-259a-4d3a-a61e-511bf7fd55fa.png">

<img width="409" alt="image" src="https://user-images.githubusercontent.com/68395698/205539506-8ef05e38-7db2-4e12-8da7-e15337a153db.png">

#### 데이터 통계

- 표본표준편차, 평균, 피어슨 상관계수 계산 결과를 보여준다
- 피어슨 상관계수의 경우 임계값 입력을 통해 특정 임계값을 넘는 데이터에 하이라이트를 수행할 수 있다

<img width="1435" alt="image" src="https://user-images.githubusercontent.com/68395698/205539288-6e3224d2-30c0-4f79-ae9c-82517ce5eefe.png">

### 데이터 전처리

#### 결측치 처리

- 결측치 처리 방법은 3가지가 존재한다

1. VAR모델 기반 예측값 대체
2. 전,후 데이터 평균값으로 대체
3. 결측치 포함 행 제거

<img width="1437" alt="image" src="https://user-images.githubusercontent.com/68395698/205542745-9e568ad1-ed65-4d57-b152-1a989b6d2649.png">

#### 노이즈 제거

- 가중치와 노이즈 제거를 원하는 컬럼을 선택하여 노이즈 제거를 수행할 수 있다

<img width="1438" alt="image" src="https://user-images.githubusercontent.com/68395698/205542856-7dd5902b-b200-4ee5-83be-cc7b66f5572e.png">

#### 전처리 이력

- 데이터 현황 및 데이터 전처리 메뉴 클릭시 나타나는 데이터셋 선택 모달에서 최근 데이터 전처리 이력을 확인할 수 있다

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/68395698/205542503-69f369ee-ceaa-4c95-92f9-07f4d27ce798.png">

- 전처리 이력 메뉴를 통해 전처리 전체 이력 및 세부 정보를 확인할 수 있다
- 좌측 상단 선택 박스를 통해 특정 데이터셋의 전처리 이력만 확인할 수 있다

<img width="1440" alt="image" src="https://user-images.githubusercontent.com/68395698/205542619-9545a838-f3fe-448b-ba8c-f0e3c5973b59.png">

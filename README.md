# 머신러닝을 위한 학습 데이터 전처리 DataOps 기술 개발

경희대학교 컴퓨터공학과 김서현

## Abstract
머신러닝 학습을 통해 유의미한 결과를 도출하기 위하여 우수한 알고리즘을 설계하는 것만큼이나 정제된 데이터를 보유하는 것이 중요하다. 이를 위하여 데이터 전처리 과정은 필수적이지만 전처리 작업을 수행하는 데 많은 노력과 시간이 소요된다. 따라서 본 문서에서는 학습 데이터 전처리 작업의 편의성을 증진하는 DataOps 기술을 제안한다. 학습 데이터셋 관리부터 데이터 시각화 및 통계 작업, 그리고 다양한 전처리 기법 적용까지 머신러닝 학습을 위한 데이터 준비 과정을 웹 인터페이스 기반으로 간편하게 수행할 수 있는 기술을 구현한다. 특히 본 기술에서는 시계열 데이터를 중심으로 하여, 시계열 데이터의 특성을 바탕으로 효율적으로 수행할 수 있는 전처리 기능을 제공한다.


## System Architecture
<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205537286-e66ca81d-1e4b-4a99-b834-67a972bfdabf.png">

## Package Design

<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205538268-026c5588-e8bc-4fb6-9059-3a39b8df61cd.png">

## How to Run

### khu-data-studio-service-discovery
```
cd khu-data-studio-service-discovery
./gradlew build
java -jar ./build/libs/khu-data-studio-service-discovery-0.0.1-SNAPSHOT.jar
```
### khu-data-studio-api-gateway

```
cd ./khu-data-studio-api-gateway
./gradlew build
java -jar ./build/libs/khu-data-studio-api-gateway-0.0.1-SNAPSHOT.jar
```
### khu-data-studio-dataset-ui

```
cd ./khu-data-studio-dataset-ui
npm i
npm run serve
```

### khu-data-studio-preprocessing-api

```
cd ./khu-data-studio-preprocessing-api
uvicorn main:app --reload --port=8083
```

### khu-data-studio-dataset-api

```
cd ./khu-data-studio-dataset-api
./gradlew build
java -jar ./build/libs/khu-data-studio-dataset-api-0.0.1-SNAPSHOT.jar
```

## KHU Data Studio

### 데이터셋 관리

#### 데이터셋 리스트

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/68395698/205538854-47d4754c-6a2b-4fab-ac17-6065683d0c0a.png">

* 데이터베이스 테이블을 통한 데이터셋 등록 

<img width="1438" alt="image" src="https://user-images.githubusercontent.com/68395698/205538896-6d0facbd-2912-4074-ae56-dace12a9f36a.png">

* 정보 입력 후 프리뷰

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/68395698/205538930-6d38d736-a5ec-4290-b426-7b4f476a934d.png">

* CSV 파일을 통한 데이터셋 등록

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/68395698/205539006-f3d03172-e221-46cf-a2c6-74563946bf0b.png">

### 데이터 현황

* 데이터셋 선택

메뉴 클릭 시 먼저 데이터셋을 선택할 수 있는 모달이 나타난다. 모달을 통해 원하는 데이터셋을 선택하여 시각화/통계를 수행한다.

<img width="1439" alt="image" src="https://user-images.githubusercontent.com/68395698/205539122-b91aa8a8-3d62-443a-9888-88441b1de9fb.png">


* 데이터 시각화

<img width="1438" alt="image" src="https://user-images.githubusercontent.com/68395698/205539240-b047b89f-259a-4d3a-a61e-511bf7fd55fa.png">

상단의 컬럼 라벨을 클릭하여 해당 컬럼 데이터의 디스플레이 여부를 결정할 수 있다.
우측 상단 기간 선택 기능을 통해 날짜별 필터링을 수행할 수 있다. 날짜 선택 컴포넌트의 경우 아래 이미지와 같이 일별, 주별, 월별, 계절별로 원하는 기간을 선택할 수 있다.


<img width="409" alt="image" src="https://user-images.githubusercontent.com/68395698/205539506-8ef05e38-7db2-4e12-8da7-e15337a153db.png">


* 데이터 통계

통계 메뉴 클릭 시 마찬가지로 데이터셋 선택 모달이 나타나며 데이터셋 선택 시 해당하는 데이터셋에 대한 표본표준편차, 평균, 피어슨 상관계수 계산 결과를 보여준다. 우측 상단의 기간 선택 기능을 통하여 날짜별 필터링을 수행할 수 있다. 피어슨 상관계수의 경우 임계값 입력을 통해 특정 임계값을 넘는 데이터에 하이라이트를 수행할 수 있다.

<img width="1435" alt="image" src="https://user-images.githubusercontent.com/68395698/205539288-6e3224d2-30c0-4f79-ae9c-82517ce5eefe.png">



# 머신러닝을 위한 학습 데이터 전처리 DataOps 기술 개발

경희대학교 컴퓨터공학과 김서현

## Abstract
머신러닝 학습을 통해 유의미한 결과를 도출하기 위하여 우수한 알고리즘을 설계하는 것만큼이나 정제된 데이터를 보유하는 것이 중요하다. 이를 위하여 데이터 전처리 과정은 필수적이지만 전처리 작업을 수행하는 데 많은 노력과 시간이 소요된다. 따라서 본 문서에서는 학습 데이터 전처리 작업의 편의성을 증진하는 DataOps 기술을 제안한다. 학습 데이터셋 관리부터 데이터 시각화 및 통계 작업, 그리고 다양한 전처리 기법 적용까지 머신러닝 학습을 위한 데이터 준비 과정을 웹 인터페이스 기반으로 간편하게 수행할 수 있는 기술을 구현한다. 특히 본 기술에서는 시계열 데이터를 중심으로 하여, 시계열 데이터의 특성을 바탕으로 효율적으로 수행할 수 있는 전처리 기능을 제공한다.


## System Architecture
<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205537286-e66ca81d-1e4b-4a99-b834-67a972bfdabf.png">

## ERD
<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205537482-073a1792-7dd8-4d30-8ffc-c9e83e4490d2.png">

## Package Design

<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205537731-f81da900-dd4c-4527-9f5a-fbc400827169.png">

## KHU Data Studio

### 데이터셋 관리

* 데이터셋 리스트

<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205537877-7b5b1763-ff82-4dc0-8cdb-e252a7d83358.png">

* 데이터베이스 테이블을 통한 데이터셋 등록 

<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205537900-8e2becbd-f247-4bb4-96f9-ee6d9f27ddca.png">

* 정보 입력 후 프리뷰

<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205537946-50596efb-1081-4b16-a330-b9f812e9a024.png">

* CSV 파일을 통한 데이터셋 등록

<img width="800" alt="image" src="https://user-images.githubusercontent.com/68395698/205538051-20b40307-3e37-44d3-b22b-6d0e89f6b7e7.png">





# 21-1_DataMining

## 2021 1st semester Datamining class project 


## 1. Classification - Prediction of diabetes using pima indian diabetes dataset
#### pima 원주민들의 의료기록 데이터를 기반으로 한 당뇨병 예측 문제 (Binary Classification)

#### EDA 결과 이슈사항
1) 결측치 처리 
- '인슐린','피하지방' 변수에서 결측치가 다수 존재함
- KNN을 활용해 결측치가 존재하는 행의 데이터와 유사한 이웃들의 데이터를 활용해 결측치 처리
  : 'feature similarity'를 이용해 가장 닮은(근접한) 데이터를 K개를 찾는 방식
2) 상관관계 분석
- '혈당수치'와 당뇨병과의 상관관계가 높았음
- 이에 따라, '혈당수치'를 제거한 모델을 함께 만들어서 결과를 비교 분석


#### 사용한 모델 
- Logistic Regression
- Decision Tree
- Gradient Boosting
- Random Forest

## 2. Regression - Prediction of insurance premiums using US health insurance dataset
#### US 건강 보험 데이터를 활용한 보험료 예측 문제 

#### EDA 결과 이슈사항
1) 종속변수 값인 '보험료'를 정규분포에 근사하도록 정규화시킴
2) IQR 기반 결측치 처리 

#### 사용한 모델 
- Linear Regression
- Regression Tree
![image](https://user-images.githubusercontent.com/60679596/146880673-e4465d19-f1e9-4050-9180-b3e29b379e14.png)



- Gradient Boosting
- Random Forest
-

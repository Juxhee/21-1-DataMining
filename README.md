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

#### EDA 
1) 종속변수 값인 '보험료'를 정규분포에 근사하도록 정규화
![image](https://user-images.githubusercontent.com/60679596/146880897-42afdbe4-eb45-4658-ad70-76695d256c71.png)



2) 흡연 여부와 보험료 관계 확인
![image](https://user-images.githubusercontent.com/60679596/146880979-9d1f2af8-3231-4cb5-9a1b-2780d4ada2fd.png)
- 흡연자의 보험료가 비흡연자보다 상대적으로 높은 편
- 흡연 여부는 보험료에 중요한 영향을 미칠 것이라 판단하여 흡연 여부 포함 / 미포함 모델링 과정 비교 



#### 사용한 모델 
- Linear Regression
![image](https://user-images.githubusercontent.com/60679596/146880831-e56690c5-6217-41b4-bec2-edd9029cccd1.png)

- Regression Tree
![image](https://user-images.githubusercontent.com/60679596/146880673-e4465d19-f1e9-4050-9180-b3e29b379e14.png)


- Gradient Boosting
![image](https://user-images.githubusercontent.com/60679596/146880795-6d1c638e-ec4f-4bdc-b0cf-6df1a957aad4.png)

- Random Forest
![image](https://user-images.githubusercontent.com/60679596/146880750-fbe17cae-9ce7-4a1c-a05e-348e490a93d4.png)


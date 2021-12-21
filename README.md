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
### US 건강 보험 데이터를 활용한 보험료 예측 문제 
### - 보험계약자의 나이, 성별, 자녀수 등 데이터를 기반으로 한 보험료 예측 

### DataSet
#### US health Insurance Dataset
#### 설명변수 6개 
- Region 거주지역
- Smoker 흡연여부
- Children 자녀수
- BMI 체질량지수
- Sex 성별
- Age 나이

#### 종속변수 
- Charges 보험료


### EDA 
#### 1) 종속변수 값인 '보험료'를 정규분포에 근사하도록 정규화

![image](https://user-images.githubusercontent.com/60679596/146881400-a0e5db7c-f833-4500-874c-e8b8a8382f3a.png)




#### 2) 흡연 여부와 보험료 관계 확인

![image](https://user-images.githubusercontent.com/60679596/146881370-68e4a34b-3f76-4179-bbff-316654f4e329.png)


- 흡연자의 보험료가 비흡연자보다 상대적으로 높은 편
- 흡연 여부는 보험료에 중요한 영향을 미칠 것이라 판단하여 흡연 여부 포함 / 미포함 모델링 과정 비교 



### 사용한 모델 
#### 1) Linear Regression

![image](https://user-images.githubusercontent.com/60679596/146881350-a8a8917f-92bc-4e7d-9f83-df31c6a35e52.png)


#### 2) Regression Tree

![image](https://user-images.githubusercontent.com/60679596/146881282-8511cd38-065f-4dfc-921d-6b387f508399.png)

#### 3) Gradient Boosting

![image](https://user-images.githubusercontent.com/60679596/146881230-264ceb54-650a-40b0-abe4-b68b4324311e.png)

#### 4) Random Forest

![image](https://user-images.githubusercontent.com/60679596/146881250-ad5c15de-cb64-410c-8952-e960a30e301c.png)


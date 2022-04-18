## 데이터 마이닝 수업 프로젝트

## 1. Classification - Prediction of diabetes using pima indian diabetes dataset
#### pima 인디언 여성들의 의료기록 데이터를 기반으로 한 당뇨병 예측 문제 (Binary Classification)

`classification-pima.ipynb`

#### 데이터셋 : US health Insurance Dataset
#### 설명변수 8개 
- Pregnancies 임신 횟수
- Glucose 혈당 수치
- BloodPressure 혈압
- SkinThickness 팔 삼두근 뒤쪽 피하지방 값
- Insulin 인슐린
- BMI 비만도를 나타내는 체질량지수
- DiabetesPedigreeFunction 당뇨 내력가중치


#### 종속변수 
- Outcome 당뇨 여부 (0/1)


#### 1.2 EDA 


#### 1) 혈당 수치와 당뇨병 여부와의 관계 확인 

![image](https://user-images.githubusercontent.com/60679596/146881974-4cb1a83c-6aad-4b6d-9123-8846f15920ff.png)
- 혈당 수치가 당뇨병 여부 분류에 중요한 영향을 미칠 것이라 판단
- 혈당 수치 포함 모델/미포함 모델링 진행 


#### 2) KNN을 활용한 결측치 처리 
- '인슐린','피하지방' 변수에서 결측치가 다수 존재함
- KNN을 활용해 결측치가 존재하는 행의 데이터와 유사한 이웃들의 데이터를 활용해 결측치 처리
  : 'feature similarity'를 이용해 가장 닮은(근접한) 데이터를 K개를 찾는 방식
  
  ![image](https://user-images.githubusercontent.com/60679596/146882174-76ccc1e0-c5ef-4f09-b329-4777eebcc289.png)

  


#### 1.3 모델링 및 결과
#### 1) Logistic Regression

```python
from sklearn.linear_model import LogisticRegression

lr_clf = LogisticRegression()
lr_clf.fit(X_train , y_train)
pred = lr_clf.predict(X_test)
pred_proba = lr_clf.predict_proba(X_test)[:, 1]
get_clf_eval(y_test , pred, pred_proba)

```

</br>

![image](https://user-images.githubusercontent.com/60679596/146882202-63e71bcf-31b3-4a0c-b47f-e27684a5c6b2.png)


#### 2) Decision Tree

```python
from sklearn.tree import DecisionTreeClassifier

dtc = DecisionTreeClassifier(criterion='entropy',max_depth=5)
dtc.fit(X_train, Y_train)
dtc_acc= accuracy_score(Y_test,dtc.predict(X_test))

```

</br>

![image](https://user-images.githubusercontent.com/60679596/146882467-9153f7a2-d5a7-4cbc-bc55-65b5aff203dc.png)


#### 3) Gradient Boosting

```python
from sklearn.model_selection import GridSearchCV

parameters = {
    "learning_rate": [0.01, 0.025, 0.05, 0.075, 0.1],
    "max_depth":[2,3,4,5,6],
    "criterion": ["mse"],
    "n_estimators":[10,20,30,40,50,60,70,80,90,100]
    }

clf = GridSearchCV(GradientBoostingClassifier(), parameters, cv=5, n_jobs=-1)
clf.fit(X_train, y_train)
```

</br>


![image](https://user-images.githubusercontent.com/60679596/146882262-125d95be-ff28-4a79-ac80-898e11bcfb1e.png)


#### 4) Random Forest

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report

rf = RandomForestClassifier(n_estimators=100, random_state=0).fit(X_train,y_train)

```

</br>

![image](https://user-images.githubusercontent.com/60679596/146882533-a7739375-fc1f-439f-b18a-4891c60f95ca.png)





## 2. Regression - Prediction of insurance premiums using US health insurance dataset
#### US 건강 보험 데이터를 활용한 보험료 예측 문제 
#### - 보험계약자의 나이, 성별, 자녀수 등 데이터를 기반으로 한 보험료 예측 

`Regression-insurance.ipynb`

#### 2.1 DataSet
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


#### 2.2 EDA 
#### 1) 종속변수 값인 '보험료'를 정규분포에 근사하도록 정규화

![image](https://user-images.githubusercontent.com/60679596/146881400-a0e5db7c-f833-4500-874c-e8b8a8382f3a.png)




#### 2) 흡연 여부와 보험료 관계 확인

![image](https://user-images.githubusercontent.com/60679596/146881370-68e4a34b-3f76-4179-bbff-316654f4e329.png)


- 흡연자의 보험료가 비흡연자보다 상대적으로 높은 편
- 흡연 여부는 보험료에 중요한 영향을 미칠 것이라 판단하여 흡연 여부 포함 / 미포함 모델링 과정 비교 



#### 2.3 사용한 모델 
#### 1) Linear Regression



```python
from sklearn.linear_model import LinearRegression

line_fitter = LinearRegression()
line_fitter.fit(X_train, Y_train)
y_predicted = line_fitter.predict(X)

```

</br>


![image](https://user-images.githubusercontent.com/60679596/146881350-a8a8917f-92bc-4e7d-9f83-df31c6a35e52.png)


#### 2) Regression Tree

```python
from sklearn.tree import DecisionTreeRegressor as dtr
from sklearn.model_selection import GridSearchCV

param_grid = {'criterion':['mse','friedman_mse','mae'], 'max_depth':[None,2,3,4,5,6], 'max_leaf_nodes':[None,2,3,4,5,6,7], 'min_samples_split':[2,3,4,5,6], 'min_samples_leaf':[1,2,3]}
reg_tree = GridSearchCV(dtr(), param_grid, cv=5, n_jobs=-1)
reg_tree.fit(X_train, y_train)

```

</br>

![image](https://user-images.githubusercontent.com/60679596/146881282-8511cd38-065f-4dfc-921d-6b387f508399.png)

#### 3) Gradient Boosting

```python
import xgboost 

xgb_fitter = xgboost.XGBRegressor(colsample_bytree = 0.4603, learning_rate = 0.01, min_child_weight = 1.8, 
                                                max_depth= 3, subsample = 0.52, n_estimators = 2000, 
                                                random_state= 7, ntrhead = -1) 
xgb_fitter.fit(X_train,Y_train)
```

</br>

![image](https://user-images.githubusercontent.com/60679596/146881230-264ceb54-650a-40b0-abe4-b68b4324311e.png)

#### 4) Random Forest


```python
from sklearn.ensemble import RandomForestRegressor
param_grid = {'criterion':['mse','mae'], 
              'max_depth':[2,3,4,5,], 
              'max_leaf_nodes':[2,3,4,5,6], 
              'max_features':[3,4,5,6]}
              
clf_rf = GridSearchCV(RandomForestRegressor(), param_grid,  n_jobs=-1)

clf_rf.fit(X_train, y_train)

```

</br>

![image](https://user-images.githubusercontent.com/60679596/146881250-ad5c15de-cb64-410c-8952-e960a30e301c.png)


# CarPricePrediction

Trying to build a model that could predict the price of the used car in U.S. using Kaggle dataset

Kaggle: https://www.kaggle.com/datasets/deepcontractor/car-price-prediction-challenge/data

# 프로젝트 시행 배경:
- 미국에서 생활 할 당시, 중고차 구매가 매우 스트레스가 심한 과정이었음을 기억
- 각 딜러마다, 상황마다, 지역마다, 시기마다 가격이 너무 천차만별로 다르고, 잘 모르는 외국인의 경우 정당한 거래를 하기 쉽지 않음
- 중고차 가격을 제공하는 사이트들도 개인정보를 요구하는 경우가 많아, 개인정보 유출에 대한 피로감이 심각함

# 프로젝트 Process:
1. Dataset preparation (데이터셋 준비)
2. Feature Engineering (특징 엔지니어링)
3. EDA(Exploratory Data Analysis)
4. Selecting Model (모델선택)
5. Model Training (모델 학습)
6. Model Evaluation (모델 평가)

# Ensemble Model :

Base Model과 LightGBM 모델 비교 <br>
LightGBM과 Stacking model 비교



# Results:

Base Model scores (Linear Regression, Decision Tree Regressor, SVR) <br>
<img width="385" alt="image" src="https://github.com/user-attachments/assets/b7dce405-caa1-4266-b75f-94abe1338b08" />


LightGBM Model and Base Model for stacking (Using 3 base learners): <br>
<img width="468" alt="image" src="https://github.com/user-attachments/assets/1512c202-1a04-4682-bd79-bccdf3d845e0" />


Base Model for Stacking (Using 4 base learners):<br>
<img width="608" alt="image" src="https://github.com/user-attachments/assets/313bdd82-34ec-467a-a18d-0ca03a832b87" />
![image](https://github.com/user-attachments/assets/1a722ee7-0cfc-4f05-b05a-6ae67c51cd80) <br>

Graphical Result for LightGBM model: <br>
<img width="914" alt="image" src="https://github.com/user-attachments/assets/18088189-c084-404c-a4b7-6a79834b96f8" /> <br>

- Meta learner에서 ridge 와 linear regression는 같은 모델 스코어를 준다.
- 단순 base model을 사용하는 것 보다 LightGBM model을 사용하는 것이 최대 60퍼센트 이상의 성능 개선을 보여준다.
- Stacking을 사용할 시, 3퍼센트의 성능 개선을 보인다.
- 하지만 모델링에 걸리는 시간이 상당하게 증가한다.
- Meta learner를 3개에서 4개로 증가시키면, 0.2퍼센트 성능 향상을 보여준다. 하지만 걸리는 시간이 5분가량 증가한다.
- base learner중 3가지가 boosting 기법이기 때문에, stacking의 층을 늘려도 큰 효과를 보여주지 못하는 것으로 추정된다.

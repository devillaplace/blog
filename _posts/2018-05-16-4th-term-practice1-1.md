##4학기 1번 실습 첫 번째 시간 (정리중)
---
- 데이터를 chart로 그려보면서 어떤 feature가 class를 잘 나눌 수 있는지 살펴보기
  - 잘 working하는 feature는 나의 생각과는 다를 수도 있다 : 다 보고 눈으로 살펴보는게 좋다.
  
- 여러 모델을 사용하기
  - Elastic net (Linear Model)
  - Random forest : Ensemble Model
  - SVM
  - Neural Network
  
- Competition 1등 팀에서는 Feature를 엄청나게 많이 쓰고 (수백개), 많은 수의 모델로 Ensemble 진행

- Churn prediction of Casual Games
  - 모델별로 가장 좋은 성능을 내는 Feature의 조합이 다를 수도 있다.
  - Gradient boosting 이 DL 모델들보다 더 좋은 성능을 거뒀음 : Data가 부족했던 것으로 보임. (많지는 않았다고)
  - 또한 해석이 필요한 상황이었기 때문에...(근데 그럼 DL모델을 쓴 이유가 뭔지;)
  
---
Feature Preprocessing & Feature generation for models (Ref. : Coursera course "How to win a data science competition")
 - 다 해야 하는 것은 아니고 필요한 것을 선택 (메뉴판이라고 생각)

1. Numeric
Preprocessing
scaling :
Tree들은 Feature를 한 번에 하나씩만 보기 때문에, scaling효과는 거의 드러나지 않는다.
Non-tree based 모델들은 scaling에 민감성을 어느 정도 가질 수 밖에 없다.
KNN 같은 local model이 특히 더 scaling에 민감하다. (전체를 둘러보기 때문에)
PCA도 반드시 scaling이 필요하다.
중간점에 있는 애들은 아주 잘 구분해줘야 하고,분포 양 끝에 있는 애들은 큰 관심 없다면, Min-Max 같은 방법 적용
- 설명 놓쳤다.. 물어봐야겠다.

Rank transformation : 
10, 8, 7, 6, 1
1,2,3,4,5
순서 정보만 중요하고 사이사이 간격은 별로 안 중요할 때
또는 1번 리스트에서 맨 위에 100 같은 애가 쑥 들어왔는데, 값의 크기는 신경쓰지 않되 사용은 하고 싶을 때
근데 이런 outlier를 끌어안고 싶지 않을 때는 버려야 하는 경우도 있다.

Log transform
선형으로 잘 나눠지지 않는 데이터 셋에 대해, log를 취해주면 선형으로 잘 나눠질 수 있도록 만들어질 수 있다.
비선형 모델에서는 필요 없을 수도 있는데, 선형으로 된 모델은 좀 쉽게 풀리는 경향이 있어서 해보는 경우도 있다.
이걸 적용해야 할지 말지는 그려보고 결정
Square root 도 마찬가지인건가..?

Feature generation
Domain knowledge, EDA (Squared area, fractional part 등)
fractional part : 
예: 제품 가격에서 소수점 아래만 취해서 만든 feature
1.39 -> .39
1.0 -> .0
2.47 -> .47
-> 소수점
이걸 찾은 방법 : Domain knowledge 로 유추해보거나, 이것 저것 생각해서 데이터 그려보거나 (둘 다 눈으로 확인은 필요)


2. Categorical, ordinal
Ordinal features
 - 순서가 있는 경우는 순서도 중요한 정보이므로 사용해야 함
Label encoding
 - Categories -> numbers
 - 어떻게든 숫자로 바꿔야 알고리즘에서 처리 가능
 - dummy variable 함수 사용 (get_dummies()같은거) 할 수도 있고 자기가 직접 할 수도 있고..
Frequency encoding
 - 빈도로 구분하여 비율화 시키는게 좋은 방법일 수 있다.
 - ex : [A, C, B] -> [0.5, 0.3, 0.2]
One-hot encoding
 - Categories -> several binary features
 - linear 문제에 잘 된다.
 - 차원이 높아지는 trade-off 는 있다.
Interactions between categorical features
 - categorical feature x categorical feature -> new feature
   (ex : 성별 x 좌석 등급 -> 성별/좌석등급별 나타나는 feature)

3. Date and time
 - Periodicity : 주어진 Datetime을 나눠서 연도/달/계절 등으로 만들기 (주말/계절/휴일 등)
 - Time since : 가입한지 얼마나.. 최근 접속한지 얼마나.. 입사한지 얼마나..
 - Different between dates : 첫 구매와 두 번째 구매의 간격 등
 - Regularity : 주기적으로 발생하는 이벤트인지 등
 
 - Coordinates
 - Rotation : Linear model을 위한 것. 45도 정도의 선으로 나눌 걸 rotate해서 수직선으로 나누도록 만들 수도 있음 : 이렇게 되면 한 축만 써도 됨
 - Aggregate features
 
4. Missing values
 - NA, -1, 999, 0, ... 
 - 이런걸 어떻게 처리할 것인지 : 버릴 것인지, 채워 넣을 것인지
 - 보통은 버릴 수 있으면 버리는게 좋다 : 불필요한 추정을 안해도 되니까..
 - 데이터가 아주 소중한 경우일 때
   -999, mean, median : -999는 모델이 알아서 학습하게 하거나, 분포에 적당한 값으로 넣거나, outlier에 덜 민감하게 median을 넣거나..
   - 잘되면 다행인데 안되는 경우도 많다.
 - Trick 중에 isnull 이라는 binary feature 를 추가하는 방법도 있다고 함.
   - missing value 를 median 으로 임의로 채워 넣은 거라면, 내가 임의로 넣었다고 표시를 해주는 것
   - 이렇게 하고 모델이 잘 학습하기를 기대하는 것
 - Reconstruction
   - 가능한 경우에 하는 것
   - 차트 그려서 앞/뒤 사정을 봤을 때, 누가봐도 저기엔 저 값이다 싶은게 있은게 있으면 채워 넣는게 큰 문제가 안될 수 있다.
 - 주의사항
  - Do not fill NAs before feature generation : 임의로 넣은 값을 기반으로 feature를 만들어내면, 문제아를 만들 가능성이 높다.

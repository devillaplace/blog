EDA
데이터 탐색하기

CDA : 
뭘 알고 들어가는거
데이터의 성격 또는 수집한 목적이 명확한 경우가 대부분
MBTI 같은 걸 만들 때 사용한 방법

EDA : 
뭣도 모르고 들어가는거
ART 의 영역 (정답을 말하기 어려움)
start from EDA, not modeling!

histogram
scatter plot
statistics

tSNE
높은 차원의 데이터를 낮은 차원으로 우겨넣기
하나의 관측값이 다른 관측값과 가지는 거리 (Euclidian 또는 KL Divergence, Manhattan 등 선택 가능)를 이용
점들을 큰 차원에 뿌렸다가, Gradient Descent 를 반복해서 가깝게 이동시켜나감
잘 되긴 하는데, 튜닝이 필요함. unsupervised clustering 알고리즘이기 때문에, 항상 최적 결과를 내지 않음.
요즘은 tree-based t-SNE를 사용함 (빠름)


Bagging
bootstrapping 을 통해 여러 개의 백을 만들고 그것들의 앙상블을 취함

Boosting
이전 모델이 잘못했던 부분을 바로잡는 방향으로 학습시킨 후 앙상블을 취함 (점진적인 앙상블이라고 보면 됨)

Bosch Data 소개



추가 Data 소개
보험사

Fraud Detction Cheat Sheet
EDA
PCA 로 bi plot 그려봄

Histogram / Density / Scatter Plot

NN
Tensor flow
Visualizing
t-SNE

EDA
- Any other unsupervised method? PCA, tSNE (파라미터 바꿔가면서)
- no Date-time features(ex, the off-peak pattern)

Feature selection
- By 'eyes' with visualization (histograms) <- 이건 예제 코드에서..
- Other or better way to find the exact value? 겹치는 부분을 숫자로 뱉어내도록 만들기 등
- Can we consider the evaluation matrix, cost-sensitively?

Dataset setting
 - Down sampling? -> Up sampling 해서 결과가 좋은지 확인 필요
 - Train:Test = 80:20... Other ratio? -> Train Sample 늘리기 사용
 
Frauds weight
 - Uniform weight... more clever way?
Input scaling for all features
 - Scaling 말고 Frequency 기반으로 바꿔서 generation 해보면 어떨지?
Network tuning
 - Layer tuning (지금은 37-18-27-40 으로 지금은 구성되어 있음)
 - Sigmoid 대신 Relu






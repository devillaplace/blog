군집화를 먼저 하고, k-means -> decision tree
k-means 만 사용하면 cluster 의 의미를 알기 힘들다. 각각의 군집의 성격을 보기 위해 decision tree 를 이용
입력 변수
 - 사고 발생 환경 변수
 - 충돌 상황 변수
출력 변수
 - 교통사고의 유형 코드
 
 각 행이 운전자 한 명에 대한 정보
  - 사고 상황 관련 변수
   - 충돌 상황 변수
   - 인적 변수
   - 차량 변수
   
   1. report no 기준으로 inner join - join 방식은 달라질 수 있음
   2. 위 테이블에 vihicle 테이블을 left join
   
   변수 선택
   분석 목적과 부합하는 변수
   결측치가 적은 변수
   다양한 정보를 포함하는 변수 (성별같은건 전체 데이터가 카테고리 2개로 나뉘는거라 별로)
   
   date 와 time 을 합쳐서 하나의 time 컬럼
   
   date of birth = age 로 변경
   
   결측치 핸들링
    - 평균으로 채워넣거나.. 근데 이러면 code 정보가 사라질 수 있음
    - 그냥 지워버리는 것도 방법
   
   의미를 알 수 없는 변수 제거
    - Not Applicable, Other, Unknown 등..
    
   명세서에 없는 code 값 제거 (ex : 11.04)
   
   변수 값들은 알 수 있는 형태로 변환한 다음, 실제 분석할 땐 dummy coding 해서 쓰는 방식 사용
   
   47401 개의 record로 변경

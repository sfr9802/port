# 2차프로젝트 고객 분류 분석
## 팀 구성원 & 역할
-	구자운 : 고객 분류 분석
-	이승수 : 고객 분류 분석
-	최병찬 : 고객 분류 분석
-	강수연 : 구매 트렌드 분석
-	정성훈 : 구매 트렌드 분석

## 활용 데이터 
[Kaggle Customer Shopping Trends Dataset](https://www.kaggle.com/datasets/iamsouravbanerjee/customer-shopping-trends-dataset)

## 고객 분류 분석

### 분석 목적
고객은 우수고객, 휴면고객, 신규고객 등 고유한 구매패턴과 선호도를 나타내는 집단으로 구분할 수 있다. 이에 맞는 제품, 서비스, 마케잉을 맞춤화 하여 고객 만족도를 높이고 매출에 긍정적인 영향을 끼치며 마케팅 효율성을 향상시킬 수 있다.  
분류기준 고객 분류를 위해 얼마나 최근에 구매했는지, 자주 구매했는지, 많은 금액을 지출했는지에 따라 분류하는 RFM 분석기법을 사용하였다. 최근 구매점수(Recency)는 변수 Frequency Purchases를 사 용하였고 다음과 같은 기준을 적용하여 점수를 계산했다.  
- Weekly : 1주에 한번꼴로 구매 -> 5점  
- Bi-Weekly, Fortnightly : 격주에 한번꼴로 구매 ->  4점  
- Monthly : 1개월에 한번꼴로 구매 -> 3점  
- Quarterly, Every 3 Months : 3개월에 한번꼴로 구매 -> 2점  
- Annually : 1년에 한번꼴로 구매 -> 1점  

자주 구매했는지에 대한 점수(Frequency)점수는 변수 Previous Purchases(과거 구매 횟수)를 사용 하였고 분위수를 기준으로 5점제로 계산하였다.  
지출금액에 대한 점수(Monetary)는 (과거구매횟수 + 1) * 최근 구매액으로 계산한 후 분위수를 기준으로 5점제로 계산하였다. 3종류의 점수를 모두 더해 Total Score 변수를 생성한 후 분포를 기반으로 다음과 같은 기준으로 5집단으로 분류하였다.  

| 고객 분류| 고객 수| 기준|
|-------------|------------|---------------|
| New Customer| 신규 고객 (244)| 6개월 이내에 가입한 고객, (주/격주/1개월에 한번 구매하며 구매횟수가 5회 이하인 고객)|
| Inactive Customer| 비활성 고객 (54)| 구매주기가 1년이고 구매횟수가 5회 이하인 고객|
| Loyal Customer| 우수 고객 (505)| Total Score가 13점 이상인 고객|
| Light Customer| 비활성 위험고객 (412)| Total Score가 5점 이하인 고객|
| Regular Customer| 일반 고객 (2685)| 위 4개 집단에 속하지 않는 고객|

### 집단별 계절에 따른 구매 비율
사계절 중 집단과 item 구매와 유의미한 차이를 보인 계절은 통계검정결과 여름으로 확인되었다. 여름의 경우 우수고객과 신규고객의 집단간 차이가 존재한다는 통계검정결과에 따라 여름 선호 item을 확인했다.  
우수고객, 전체 데이터의 트렌드와 비교할 때 shirt, socks, T-shirt, Hat의 구매량이 높음을 볼 수 있다.

### 집단, 계절별 item 구매건수
![image](https://github.com/sfr9802/port/assets/55042043/ca992a5e-6b3d-48d0-b8ac-bb23177ab8ea)

### 집단별 계절에 따른 지역별 구매건수
![image](https://github.com/sfr9802/port/assets/55042043/8f3506ef-b981-4a3f-8721-66e1495285df)


지역별, 계절별로 그룹화하여 비교했지만 유의미한 차이가 보이지 않는다.  
이에 집단과 item 변수간 유의미한 관계를 갖는 계절은 여름이었기 때문에 여름으로 통제하여 시각화하였다.

### 여름의 집단별 item 구매율
![image](https://github.com/sfr9802/port/assets/55042043/f4bad088-890f-43ed-b053-78d83edb9179)

 
구매율이 낮은 outers를 제외한 나머지 상품에서 신규고객과 우수고객의 선호도 차이가 극명하게 드러났다.  
이는 신규고객의 구매가 봄, 여름에 집중되었지만 우수고객은 겨울에 집중되어있고 여름에 구매하지 않는 경향을 보이기 때문이다.



### 집단별 지역과 계절의 관련성 heatmap
![image](https://github.com/sfr9802/port/assets/55042043/912342b8-a0c2-4df3-b238-079a35be1561)

우수고객의 경우 전체적으로 서부에 집중되었고 겨울에 많이 구매하는 경향을 보인다.  
신규 고객의 경우 봄, 여름에 활발하게 구매하며 특히 북동부, 남서부 지역의 고객수가 많다.

## 집단 별 계절에 따른 분석 결론
우수고객의 여름 구매량은 적으나 외투류에 대해 기온이 높은 지역과 계절에 많이 소비됨을 확인 하였다.  
두껍고 보온성을 강조한 종류가 아닌 가볍게 걸칠 수 있는 외투류를 준비해 아우터 준비를 제안하고 트렌드를 확인할 수 있다.
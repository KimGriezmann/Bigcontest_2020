# **2020 Big Contest**
![1page](https://user-images.githubusercontent.com/80115212/135368169-186a0f21-6c94-41ab-96ff-51774509ecca.PNG)


<br/>
<br/>

## **1. 프로젝트 소개**
### **1-(1) 대회 소개**
2020 빅콘테스트 데이터 분석분야 퓨처스리그 

: KBO 잔여시즌 팀별 승률, 타율 및 방어율 예측

<br/>


### **1-(2) 팀원 소개** 
- 김재홍([@KimGriezmann])
- 김동우([zxcvbnm1997@hanmail.net])
- 김시현([tlgus626@hanmail.net])
- 박준근([pjg2755@naver.com])
- 황재원([dch222@naver.com])

<br/>


### **1-(3) 수상** 
- 우수상 [빅데이터포럼의장상](https://www.bigcontest.or.kr/introduce/history2020.php) 

<br/>


## **2. 프로젝트 내용**
### **2-(1) 문제 정의**

- KBO 잔여시즌 팀별 승률 예측
- KBO 잔여시즌 팀 타율 예측
- KBO 잔여시즌 팀 방어율 예측

<br/>


### **2-(2) 분석 목표**
![분석목표](https://user-images.githubusercontent.com/80115212/135368122-ac0ebf36-980a-4a94-a63b-e23fc41525bf.PNG)

- 각 시즌의 1 ~ 115경기의 누적합 지표를 이용하여 115 ~ 144경기의 성적을 예측   
- 이때, home/away(홈/원정)로 나누어 각각 예측하여 가중 평균

<br/>


### **2-(3) 데이터 수집 및 전처리**
- 스탯티즈에서 2020년의 65~115경기의 데이터를 크롤링
- EDA
- 홈/원정간 편차를 반영하는 지표 추가
- 타율/방어율/승률에 영향을 미치는 파생 변수 추가

<br/>


### **2-(4) 분석 방향**
- 타율 예측
    * 변수의 유의성 t-test : coefficient <= 0.01 변수 제거
    * PCA : 다중 공선성 해결
    * WLS : Sample Weight를 부여하여 최적의 주성분 개수
    * Outlier 제거 : Residual Analysis
    
![타율](https://user-images.githubusercontent.com/80115212/135368450-2477d2d6-4aaa-41a5-9d53-ef51528d099b.PNG)

<br/>

- 방어율 예측
    * 변수의 유의성 t-test : coefficient <= 2 변수 제거
    * PCA : 다중 공선성 해결
    * WLS : Sample Weight를 부여하여 최적의 주성분 개수
    * Outlier 제거 : Residual Analysis
    
![방어율](https://user-images.githubusercontent.com/80115212/135368656-452636f7-ef12-4009-ba42-269ab110df48.PNG)

<br/>

- 승률 예측
    * 분석 방향 재설정 : 과거 누적 데이터 사용 -> 동일 시점 데이터 사용 
    * 앞서 수행한 타율, 방어율 예측값을 사용하여 독립 변수로 사용
    * 상대팀 별 타율, 방어율 지표 추가
    
![승률](https://user-images.githubusercontent.com/80115212/135369165-7e008644-69cc-4076-a159-821191f4ab4a.PNG)

<br/>

- 모델 선정 및 Hyper Parameter 설정
   * Ridge Regression
   * Lasso Regression
   * Random Forest
   * XGBoost
   
cf. MSE를 통해 모델 성능 비교

<br/>


## **3. 분석 결과**
### **3-(1) 타율 예측**
![타율예측](https://user-images.githubusercontent.com/80115212/135369337-de64856f-5826-4e5a-a9c5-ae1eb72908f1.PNG)


### **3-(2) 방어율 예측**
![방어율예측](https://user-images.githubusercontent.com/80115212/135369418-7088e755-0657-4920-857c-9953b4911bc9.PNG)


### **3-(3) 승률 예측**
![승률예측](https://user-images.githubusercontent.com/80115212/135369427-15c1b0ed-6b2d-475a-9923-9bdbf821d540.PNG)

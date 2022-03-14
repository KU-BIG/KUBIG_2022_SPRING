# KUBIG NLP CONTEST
<b>분반원:</b> 쿠빅 12기 원윤정, 14기 제갈예빈, 이연정, 15기 김진수

## 대회 소개
### DACON 뉴스 토픽 분류 AI 경진대회

![initial](https://user-images.githubusercontent.com/81248507/158175477-0f50a7c6-923e-47ac-ab69-95db23dc8e26.png)

- **Task**: 연합 뉴스 헤드라인을 데이터 세트로 활용해 뉴스의 주제를 분류하는 text classification
- **Data**: index, title, topic_idx의 3개의 컬럼으로 이루어짐 (학습 데이터 총 45,654건)

## 대회 진행방식
### 1. EDA
- target값 분포 확인 결과, 카테고리 간의 분포가 전체적으로 고르진 않지만 test label을 알 수 없어 stratified k-fold을 이용한 훈련
- 한자어 데이터 확인 결과, 뉴스 제목의 특성상 한자를 포함한 데이터가 많음.

### 2. 데이터 전처리
- 한자어 데이터 번역: 등장 빈도가 10 이상인 한자어에 대해서는 번역 진행함.
- **Back Translation** 기반의 데이터 증강

### 3. 학습
- 사용 모델: **RoBERTa** 모델
- 학습 진행방식:
  - 학습시 한글 데이터와 1차 가공된 영어 데이터 함께 사용해 학습함.
  - 팀을 나눠 영어 데이터/한글(기존+BT) 데이터를 각각 학습함.
  - 학습결과를 ensemble하여 최종 결과 도출함. 각각 학습된 모델을 제출해 얻은 public 점수를 가중치로 활용해 가중합 실시함.


### 4. 최종 결과
- public score: 0.870009 (17위)
  - 한글(원본+BT) 데이터에 RoBERTa-base로 사용
- **private score: 0.83552 (8위)**
  - 한글(원본+BT) 데이터에 RoBERTa-base, RoBERTa-small, 영어 데이터에 BERT-base 3가지 모델 앙상블해 사용
 
 ### 5. 결론
 : Back Translation에서 최종적으로 역번역된 결과뿐만 아니라 1차 번역된 영어 데이터 역시 성능 향상에 기여함.

---
title: 데이터 알아가기 실전 실습
---

🇰🇷 **한국어** · 🇺🇸 [English](README.en.md) · 🇯🇵 [日本語](README.ja.md)

<style>
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:16px;margin:16px 0}
.card{border:1px solid #d0d7de;border-radius:10px;padding:16px;background:#fff}
.card h3{margin:0 0 4px;font-size:1.1em}.tag{color:#57606a;font-size:.85em;margin-bottom:8px}
.card ul{padding-left:18px;margin:8px 0;font-size:.92em}.links a{display:inline-block;margin:2px 6px 2px 0;font-size:.85em;
padding:2px 8px;border-radius:12px;background:#eef3fb;text-decoration:none}.links a.new{background:#dafbe1}
.series td{vertical-align:top}</style>

# 데이터 알아가기 실전 실습

Kaggle·공공 데이터로 해 보는 데이터 분석 실습 모음입니다. 각 분석은 **기본 분석**과, 결과를 다시 점검하고 한 단계 더 들어간 **추가 분석**으로 구성되어 있습니다.

전체 목록과 데이터 출처는 [GitHub 저장소 README](https://github.com/LDJWJ/dataAnalysis#readme)에서 볼 수 있습니다.

## 추가 분석 시리즈

<table class="series"><tr><th>시리즈</th><th>배우는 것</th><th>분석</th></tr>
<tr><td><b>정확도의 함정</b></td><td>불균형 데이터에서 정확도만 보면 생기는 착시</td><td>03 뇌졸중 예측, 11 심장병</td></tr>
<tr><td><b>너무 좋은 성능 의심하기</b></td><td>데이터 누수와 합성 데이터 찾기</td><td>08 수면 스트레스, 09 브라질 주식(ibovespa), 10 체지방 예측</td></tr>
<tr><td><b>평균의 함정 · 혼재 변수</b></td><td>표본 수와 제3의 변수 확인하기</td><td>17 Data Science Salaries 2023</td></tr>
<tr><td><b>교차검증 + Pipeline</b></td><td>한 번의 split보다 믿을 수 있는 평가</td><td>07 와인 품질, 01 캘리포니아 집값, 17 Data Science Salaries 2023</td></tr>
<tr><td><b>지도 · 인터랙티브 차트</b></td><td>plotly · folium으로 확대하고 마우스를 올려 보기</td><td>01 캘리포니아 집값, 06 태풍 찬투(2021), 12 MCU 박스오피스, 15 주민등록 인구 (2023.10), 17 Data Science Salaries 2023</td></tr>
</table>

## 분석 목록

<div class="grid">
<div class="card"><h3>01 · 캘리포니아 집값</h3><div class="tag">부동산 · 지도 · 회귀</div>
<ul><li>해안 10km 이내 집값 중앙값 25.1만 달러, 100~200km는 9.3만 달러로 약 2.7배. 소득을 맞춰도 대도시 거리 효과는 남는다.</li><li>집값 500,001달러는 상한값(814블록, 4.8%). 새로 만든 해안 거리(r = -0.49)가 위도·경도보다 훨씬 강한 변수.</li><li>그래디언트 부스팅 + 파생 변수 교차검증 RMSE 44,191달러(R² 0.855). 가장 중요한 변수는 해안 거리, 그다음 소득.</li></ul>
<div class="links"><a class="" href="01_01_california.html">기본 EDA</a><a class="new" href="01_01B_California_Housing_Map.html">추가 1편 · 집값 지도</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_01B_California_Housing_Map.ipynb">코드</a><a class="new" href="01_01C_California_Housing_Model.html">추가 2편 · 예측 모델</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_01C_California_Housing_Model.ipynb">코드</a></div></div>
<div class="card"><h3>03 · 뇌졸중 예측</h3><div class="tag">의료 · 불균형 분류 · 정확도의 함정 ①</div>
<ul><li>원본 모델의 정확도 95.04%는 전부 &quot;없음&quot;으로 찍는 기준선과 같고, 환자를 한 명도 예측하지 못했다.</li><li>class_weight·오버샘플링·임계값 조정으로 재현율 0.00 → 약 0.76~0.79 (테스트 환자 75명 중 57~59명 발견).</li><li>오버샘플링을 분할 전에 하면 교차검증 재현율이 0.95로 부풀려진다(누수). 가장 강한 위험 요인은 나이(80세 이상 21.5%).</li></ul>
<div class="links"><a class="" href="01_02_Stroke_Prediction_Analysis_01.html">기본 분석</a><a class="new" href="01_02B_Stroke_Accuracy_Trap_Metrics.html">추가 1편 · 평가 지표</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_02B_Stroke_Accuracy_Trap_Metrics.ipynb">코드</a><a class="new" href="01_02C_Stroke_Imbalance_Handling_RiskFactors.html">추가 2편 · 불균형 처리·위험 요인</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_02C_Stroke_Imbalance_Handling_RiskFactors.ipynb">코드</a></div></div>
<div class="card"><h3>04 · 은행 파산 위기</h3><div class="tag">금융 · 분류 · Kaggle</div>
<div class="links"><a class="" href="01_03_Bankruptcy_Risk_Prediction01_v10_220518.html">1 시작</a><a class="" href="01_03_Bankruptcy_Risk_Prediction02.html">2 피처 변환</a><a class="" href="01_03_Bankruptcy_Risk_Prediction04_withkaggle_V10.html">3 탐색~모델 구축</a></div></div>
<div class="card"><h3>05 · Spaceship Titanic</h3><div class="tag">분류 · Kaggle</div>
<div class="links"><a class="" href="01_04A_Spaceship_Titanic_2209.html">기본 탐색·첫 모델</a></div></div>
<div class="card"><h3>06 · 태풍 찬투(2021)</h3><div class="tag">기상 · 지도 · 시계열</div>
<ul><li>11일 동안 약 4,748km 이동. 가장 강했던 때는 09/09 15시, 중심기압 915hPa·최대풍속 55m/s.</li><li>이동속도: 북상기 평균 20.3 → 상하이 앞바다 정체기 8.7 → 가속기 25.7km/h.</li><li>기압과 풍속의 상관은 -0.991. 예측 R²는 분할에 따라 -0.65~0.60으로 흔들리고, 직전 값만 써도 MAE 6.7 → 4.0.</li></ul>
<div class="links"><a class="" href="01_05_Typhoon_analysis.html">기본 분석</a><a class="new" href="01_05B_Typhoon_Track_Map.html">추가 · 경로 지도</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_05B_Typhoon_Track_Map.ipynb">코드</a></div></div>
<div class="card"><h3>07 · 와인 품질</h3><div class="tag">분류 · 교차검증 · Pipeline</div>
<ul><li>같은 모델도 split만 바꾸면 정확도가 0.598~0.729로 달라지지만, 5-fold 평균은 0.661~0.675로 안정적이다.</li><li>전체 11개 변수 랜덤포레스트 0.670 (기준선 0.423). 원본 4개 변수 모델은 교차검증 0.549.</li><li>3등급 분류 정확도 0.703. 가장 중요한 변수는 알코올 &gt; 황산염 &gt; 휘발산.</li></ul>
<div class="links"><a class="" href="01_06_WindQT_DataAnalysis.html">기본 분석</a><a class="new" href="01_06B_WineQT_CrossValidation_Pipeline.html">추가 · 교차검증 + Pipeline</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_06B_WineQT_CrossValidation_Pipeline.ipynb">코드</a></div></div>
<div class="card"><h3>08 · 수면 스트레스</h3><div class="tag">헬스케어 · 성능 의심하기</div>
<ul><li>8개 변수 중 아무거나 하나만 써도 교차검증 정확도 0.98 이상.</li><li>인접 스트레스 수준끼리 값 범위가 전혀 겹치지 않고, 수준별 정확히 126행, 수준 안에서 변수끼리 |r| = 1.0 → 합성 데이터.</li><li>라벨을 섞으면 0.23(코드 누수 아님). 1표준편차 잡음을 넣으면 0.66~0.71로 떨어진다.</li></ul>
<div class="links"><a class="" href="01_07_Human_Stress_Detection.html">기본 분석</a><a class="new" href="01_07B_Human_Stress_Too_Good_Performance.html">추가 · 너무 좋은 성능 의심하기</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_07B_Human_Stress_Too_Good_Performance.ipynb">코드</a></div></div>
<div class="card"><h3>09 · 브라질 주식(ibovespa)</h3><div class="tag">경제 · 시계열 · 누수 점검</div>
<ul><li>월별 주가 수익률과 환율(USD/BRL) 변화의 상관은 같은 달 -0.61. 시차 상관은 우연 범위 안.</li><li>위기 구간 변동성 36.2% (평상시 23.7%). 2008년 -52.5%, 2020년 -31.0%.</li><li>원본 정확도 97.2%는 정답 누수(시가·종가 동시 입력). 장 시작 정보만 쓰면 55.6%로 기준선 61.5%보다 낮다.</li></ul>
<div class="links"><a class="" href="01_08_ivospa_stock.html">기본 분석</a><a class="" href="01_08B_ivospa_stock_Prophet.html">Prophet</a><a class="new" href="01_08D_ibovespa_Rates_FX_Stock.html">추가 · 금리·환율과 주가</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_08D_ibovespa_Rates_FX_Stock.ipynb">코드</a></div></div>
<div class="card"><h3>10 · 체지방 예측</h3><div class="tag">헬스케어 · 회귀 · 누수 점검</div>
<ul><li>체지방은 Density로 계산한 값(Siri 공식, r = -0.988)이라 Density는 누수 → 제외.</li><li>복부 둘레 하나로 MAE 3.93. 체중 + 복부 식(MAE 3.65)이 13개 변수 모델(3.73)보다 정확하다.</li><li>체지방(%) = -45.26 − 0.323 × 체중(kg) + 0.979 × 복부(cm). 원본 6개 변수 랜덤포레스트는 MAE 4.69.</li></ul>
<div class="links"><a class="" href="01_09_bodyFatPredict.html">기본 분석</a><a class="new" href="01_09B_bodyFat_Simple_Tape_Model.html">추가 · 줄자 변수 모델</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_09B_bodyFat_Simple_Tape_Model.ipynb">코드</a></div></div>
<div class="card"><h3>11 · 심장병</h3><div class="tag">의료 · 불균형 분류 · 정확도의 함정 ②</div>
<ul><li>원본 정확도 0.9144 = &quot;No&quot; 비율 0.9144. 테스트 95,939명 중 &quot;Yes&quot; 예측은 0명.</li><li>class_weight로 재현율 0.775, 놓친 환자 1,367명 → 347명. 전체 변수 ROC-AUC 0.838.</li><li>오즈비: 건강 자가평가 Poor 6.57, 뇌졸중 2.83, 남성 2.04. 연령은 21→82세 약 26.9배로 가장 강한 요인.</li></ul>
<div class="links"><a class="" href="01_10_Heart_Disease.html">기본 분석</a><a class="new" href="01_10B_Heart_Disease_Accuracy_Trap_Modeling.html">추가 1편 · 모델링</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_10B_Heart_Disease_Accuracy_Trap_Modeling.ipynb">코드</a><a class="new" href="01_10C_Heart_Disease_Risk_Factors.html">추가 2편 · 위험 요인</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_10C_Heart_Disease_Risk_Factors.ipynb">코드</a></div></div>
<div class="card"><h3>12 · MCU 박스오피스</h3><div class="tag">영화 · 비중 분석 · 인터랙티브</div>
<ul><li>영화 27편 회귀는 학습 R² 0.86 vs 테스트 -0.72로 과적합 (LOOCV 0.30).</li><li>지역 비중 북미 43.3% &gt; 아시아태평양 31.1% &gt; 유럽 17.0%. 2019년에는 아시아태평양이 북미를 추월.</li><li>해외 1위 시장은 중국(11.8%), 한국은 4.1%로 3위. 흥행배수 1위는 No Way Home 9.46배.</li></ul>
<div class="links"><a class="" href="01_11_MCU_MOVIE_INFO.html">기본 모델</a><a class="" href="01_11_MCU_MOVIE_INFO_02.html">데이터 탐색</a><a class="new" href="01_11B_MCU_Regional_Box_Office_Patterns.html">추가 · 지역별 흥행 패턴</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_11B_MCU_Regional_Box_Office_Patterns.ipynb">코드</a></div></div>
<div class="card"><h3>13 · 인구 예측 및 국가 기반 시설</h3><div class="tag">인구 · EDA</div>
<div class="links"><a class="" href="01_12_Population_Analysis01_EDA.html">EDA</a><a class="" href="01_12_Population_Analysis02.html">분석 2</a></div></div>
<div class="card"><h3>14 · 문화 예술인 현황</h3><div class="tag">문화 · EDA</div>
<div class="links"><a class="" href="01_14_Artist_Kor_analysis01_EDA.html">EDA</a></div></div>
<div class="card"><h3>15 · 주민등록 인구 (2023.10)</h3><div class="tag">공공 데이터 · 인터랙티브</div>
<ul><li>수도권에 인구의 50.7%(약 2,602만 명). 읍면동 상위 20%에 인구의 50.0%가 산다.</li><li>시군구 1위 수원시 약 119.7만 명, 최하위 울릉군 9,090명. 인구 10만 미만 93곳이 인구의 8.8%.</li><li>전국 성비 0.993. 남초는 섬·접경·산업단지(옹진군 1.333), 세대당 인구 최고는 과천시 2.76.</li></ul>
<div class="links"><a class="" href="01_15_Population_Data.html">기본 탐색</a><a class="new" href="01_15B_Population_Data_Analysis.html">추가 · 인구 분석</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_15B_Population_Data_Analysis.ipynb">코드</a></div></div>
<div class="card"><h3>17 · Data Science Salaries 2023</h3><div class="tag">취업 · 연봉 · 혼재 변수</div>
<ul><li>경력별 연봉 중앙값: 신입 70 → 중급 100 → 시니어 146 → 임원 196 (천 달러).</li><li>&quot;중기업 &gt; 대기업&quot;, &quot;하이브리드가 가장 낮다&quot;는 회사 위치(미국 비율) 때문에 생긴 착시. 통제하면 -2~-3% 수준.</li><li>예측 모델의 영향 요인 순위는 회사 위치 &gt; 경력 &gt; 직무 그룹. 교차검증 MAE 약 36~37천 달러.</li></ul>
<div class="links"><a class="" href="01_19_DataScienceSalaries_Analysis_2305.html">기본 EDA</a><a class="new" href="01_19B_DataScienceSalaries_Analysis_Advanced.html">추가 1편 · 연봉 결정 요인</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_19B_DataScienceSalaries_Analysis_Advanced.ipynb">코드</a><a class="new" href="01_19C_DataScienceSalaries_Prediction_Model.html">추가 2편 · 예측 모델·지도</a><a href="https://github.com/LDJWJ/dataAnalysis/blob/main/01_19C_DataScienceSalaries_Prediction_Model.ipynb">코드</a></div></div>
</div>

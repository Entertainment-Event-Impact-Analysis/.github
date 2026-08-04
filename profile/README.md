# 🎬 Entertainment Investment Signal Engine

> **81,348건의 뉴스 데이터를 Event-Driven Investment Analytics로 변환하여 투자 의사결정을 지원하는 엔터테인먼트 투자 시그널 엔진**

자연어 처리(NLP)와 시계열 분석을 결합하여 HYBE, SM, JYP의 주요 이벤트와 주가 반응을 정량적으로 분석하고, 투자자가 이벤트 기반 투자 전략을 수립할 수 있도록 지원하는 프로젝트

---

# 🚀 Project Highlights

- 📰 **81,348건** 뉴스 데이터 분석
- 📅 **2,094일** 시계열 데이터 구축
- 🎯 **39건** 주요 이벤트 자동 추출
- 📰 **대표 기사 선정률 100%** 달성
- 🏷️ **10개 Event Taxonomy** 구축
- 📊 **Event Reaction Score (ERS)** 자체 설계
- 📈 **Tableau Public** 기반 인터랙티브 투자 대시보드 구현

---

# 📌 프로젝트 개요

| 항목 | 내용 |
|------|------|
| **프로젝트 유형** | 개인 프로젝트 (기여도 100%) |
| **개발 기간** | 2026.07.13 ~ 2026.08.10 |
| **분석 기업** | HYBE · SM · JYP |
| **분석 기간** | 2020.10.15 ~ 2026.07.13 (총 2,094일) |
| **프로젝트 목표** | 뉴스 이벤트와 주가 데이터를 결합하여 이벤트 기반 투자 의사결정을 지원하는 분석 프레임워크 구축 |

---

# 🚨 문제 정의 (Problem)

기존 주가 예측은 가격 데이터 중심으로 이루어져 **기업 이벤트가 시장에 미치는 영향을 정량적으로 설명하기 어렵다**는 한계.

또한 투자자는 수많은 뉴스 기사 중에서 실제 주가를 움직이는 핵심 이벤트를 직접 선별해야 하므로 정보 탐색 비용이 높음.

EDA 결과,

- 기업마다 주가 반응 패턴이 다르고
- 이벤트 유형마다 Return, MDD, Recovery Rate가 다르며
- 시장 반응 시점(Lag) 또한 서로 다르다는 점을 확인.

이에 따라 **기업별 이벤트 특성과 시장 반응을 함께 고려하는 Event-Driven Investment Analytics Framework**를 설계.

---

# 💡 해결 방법 (Solution)

뉴스 데이터와 주가 데이터를 하나의 분석 파이프라인으로 통합하여,

- Event Detection
- Representative News Selection
- Event Taxonomy
- Event Study
- Investment Signal

까지 하나의 프로세스로 자동화하였습니다.

---

# ⚙️ 분석 프로세스

```text
News (81,348건)
      │
      ▼
데이터 전처리 및 Query Expansion
      │
      ▼
Feature Engineering
      │
      ▼
ARIMA 기반 이상 이벤트 탐지
      │
      ▼
Representative News Selection
      │
      ▼
Event Taxonomy 분류
      │
      ▼
Event Study
      │
      ▼
Event Reaction Score (ERS)
      │
      ▼
Tableau Dashboard
```

---

# 🛠️ 주요 분석 방법론

### ① Event Detection

주가, 뉴스, 거시경제 데이터를 통합한 **Data Mart**를 구축하고,

**Auto ARIMA**를 이용하여 기대수익률을 추정한 뒤 잔차(Residual) 상위 5%를 **Abnormal Event**로 탐지.

---

### ② Representative News Selection

대표 기사는 다음과 같은 Hybrid Scoring으로 선정.

```text
Rep_FinalScore = 0.5 × Keyword + 0.3 × Semantic Similarity (SBERT) + 0.2 × Information Density
```

이를 통해 **39건의 주요 이벤트**와 대표 기사를 자동 매핑.

---

### ③ Event Taxonomy

대표 기사를 의미 기반으로 분류하기 위해

- Rule-based Keyword Matching
- SBERT Semantic Similarity

를 결합하여 **10개 Event Taxonomy**를 구축.

예)

- Album Launch
- Concert / Tour
- Chart Performance
- Award
- TV / Drama
- Corporate Earnings
- Lawsuit
- Investment / M&A

---

### ④ Event Study

이벤트 발생 이후 **20거래일** 동안

- Return
- MDD
- Recovery Rate
- Peak CAR
- Persistence

를 계산하여 시장 반응을 정량적으로 분석.

---

### ⑤ Custom KPI 설계

기존 Event Study가 **CAR만으로 이벤트 효과를 평가하는 한계**를 보완하기 위해

**Peak CAR**와 **Persistence**를 결합한 Event Reaction Score (ERS)를 직접 설계.

ERS를 통해

- 이벤트 반응 강도
- 반응 지속성

을 동시에 평가하여 기업별 이벤트 품질을 비교.

---

# 📈 주요 성과 (Results)

### 정량적 성과

| KPI | 결과 |
|------|------:|
| 뉴스 기사 | **81,348건** |
| 분석 기간 | **2,094일** |
| 주요 이벤트 | **39건** |
| 대표 기사 선정률 | **100%** |
| Event Taxonomy | **10개** |
| 이상 이벤트 탐지율 | **29.64%** |

---

### 기업별 주요 인사이트

#### HYBE
- 초기 주가 반응은 강하지만 약 10거래일 이후 모멘텀이 빠르게 약화
- 단기 이벤트 대응 전략에 적합

#### SM
- 이벤트 직후 일시적 반응 이후 장기적으로 모멘텀 감소
- 보수적인 접근이 유효

#### JYP
- 대부분 이벤트에서 안정적인 양(+)의 수익률과 회복력 유지
- 중장기 Hold 전략에 적합

---

# 📊 Tableau Dashboard

<img width="2159" height="1535" alt="OVERVIEW (1) (1)" src="https://github.com/user-attachments/assets/da5360cb-9a16-4f94-bb70-3ab371cfeb27" />


최종 결과는 **Tableau Public**을 활용하여 인터랙티브 대시보드로 구현

### 주요 기능

- Executive KPI
- Response Curve
- Category Performance
- Event Fingerprint
- Event Reaction Score (ERS)
- Investment Insight

🔗 [**Tableau Public Dashboard**](https://public.tableau.com/views/ENTERTAINMENTEVENTIMPACT/OVERVIEW?:language=ko-KR&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

---

# 🧰 Tech Stack

| Category | Technology |
|----------|------------|
| **Programming** | Python |
| **Data Analysis** | Pandas, NumPy |
| **Machine Learning** | Scikit-learn |
| **Time Series Analysis** | Statsmodels (Auto ARIMA) |
| **Natural Language Processing** | KR-FinBERT, SBERT |
| **Data Visualization** | Tableau Public, Matplotlib, Seaborn |
| **Data Collection** | Naver News API, Yahoo Finance |
| **Version Control** | Git, GitHub |

---

# 📁 Repository Structure

```text
📦 Entertainment-Investment-Signal-Engine
 ┣ 📂 data/             # Raw & Processed Data
 ┃   ┣ 📂 raw/          # Stock, News, Macro Raw Data
 ┃   ┣ 📂 processed/    # Cleaned & Merged Data Mart
 ┃   ┣ 📂 insight/      # Event Analysis & Signal Outputs
 ┃   ┗ 📂 tableau/      # Tableau Export & Visual Assets
 ┣ 📂 src/              # Data Pipeline & Signal Engine
 ┃   ┣ 📂 crawling/     # Naver API & Yahoo Finance Collectors
 ┃   ┣ 📂 preprocessing/# Text Cleaning & Feature Engineering
 ┃   ┣ 📂 modeling/     # ARIMA Anomaly Detection & SBERT Scoring
 ┃   ┗ 📂 insight/      # Signal Rule & Decision Logic
 ┣ 📂 dashboard/        # Tableau Workbook Assets
 ┗ README.md            # Project Documentation
```

---

# ⭐ 프로젝트 핵심 기여

- **81,348건의 뉴스 데이터**와 주가·거시경제 데이터를 통합한 **End-to-End Event-Driven Analytics Pipeline**을 구축
- **ARIMA + SBERT + Event Taxonomy**를 결합하여 주요 이벤트를 자동 탐지하고 의미 기반으로 분류하는 프레임워크 설계
- Peak CAR와 Persistence를 결합한 Event Reaction Score (ERS)를 직접 설계하여 이벤트 반응의 강도와 지속성을 함께 평가할 수 있는 **KPI 제안**
- **Tableau Public**을 활용해 투자자가 기업별 이벤트 반응을 비교하고 투자 의사결정을 지원할 수 있는 인터랙티브 대시보드 구현

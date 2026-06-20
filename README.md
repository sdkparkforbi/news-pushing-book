# 기사 밀어내기(Churnalism) 검정

이슈가 발생하면 거의 똑같은 기사가 공장처럼 대량 생산되는 현상을 **두 지표**로 통계 검정합니다.

| 지표 | 의미 | 검정 |
|---|---|---|
| **N** (기사 수) | 평소보다 많아졌나 | 음이항 회귀 (요일·시간대 통제, post 더미 β₁>0) |
| **S** (평균 코사인 유사도) | 평소보다 닮았나 | Permutation test + 무작위 배정 영모형(z) |

두 조건이 **모두** 충족될 때 churnalism으로 판정합니다.
("풀리는지(평균회귀)"는 보지 않음 — 큰 클러스터의 발생 자체가 관심.)

## 파일
- **`churnalism_test.ipynb`** — Colab/로컬 공용 분석 노트북 (데모 데이터 내장, 바로 실행 가능)
- **`index.html`** — 개념을 설명하는 어린이용 그림책 → https://sdkparkforbi.github.io/news-pushing-book/

## 빠른 시작 (Colab)
1. `churnalism_test.ipynb`를 Colab에서 열기
2. 상단 **설정 셀**에서 `EVENT_TIME`, `TIME_UNIT`, `EMB_MODEL` 지정
3. 실제 데이터는 2번 셀의 `pd.read_csv(...)`로 교체 (컬럼: `published_at`, `text`)
4. 전체 실행 → 그래프 + 검정 결과 + 종합 판정 출력

## 임베딩
기본 `jhgan/ko-sroberta-multitask` (한국어 SBERT). 대안: `snunlp/KR-SBERT-V40K-klueNLI-augSTS`

## 한국어 폰트
`koreanize_matplotlib` 사용 (apt nanum 설치 불필요, 세션 재시작 없음).

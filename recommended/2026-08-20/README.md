# 일일 논문 추천 — 2026-08-20

## 검색 개요

- **연구 기준일**: 2026-08-20 (Asia/Seoul 기준 요청일 전날)
- **실제 검색창**: 단일일(2026-08-20)과 7일(2026-08-14~2026-08-20) 창에서는 관련 논문이 없어,
  30일 창(2026-07-22~2026-08-20)으로 확대하여 검색했습니다.
- **검색 쿼리**: `chest X-ray deep learning multi-institution generalization` (1차) 및
  보완 쿼리 `chest radiograph classification thoracic pathology external validation` (2차, 동일 30일 창)

## 코호트 개요 (llm.hospital, cohort-level)

- 총 272건의 흉부 X-ray 스터디, 환자 153명
- 성별: 남 136 / 여 136 (거의 균등)
- 연령: 평균 51.5세 (범위 9–87세)
- 촬영 체위: PA 184건, AP 88건
- 5개 기관(INST01–05, 48–62건씩), 9개 촬영 장비(DEV01–09)
- 소견 라벨: 'No Finding' 145건(과반), 그 외 Infiltration(21), Atelectasis(16), Nodule(7),
  Fibrosis(6), Effusion(6), Cardiomegaly(5), 다중 소견 조합 다수 — 희귀 소견의 표본 수가
  매우 적어 라벨 불균형이 뚜렷함
- 모든 레코드가 `is_synthetic = true`로 표시된 합성/벤치마크 유래 데이터셋으로 보임

## 채택된 논문 (3편)

축(axes): **기관 간 일반화**, **보고서-영상 연계**, **라벨 불균형/데이터 증강**

### 1. CLEAR: an auditable foundation model for radiology grounded in clinical concepts
- Nature Biomedical Engineering, 2026-07-22, OpenAlex
- 축: 기관 간 일반화, 모델 해석가능성
- 왜 관련 있는가: 우리 코호트는 5개 기관·9개 장비·PA/AP 혼재라는 다기관 이질성을 가지고 있어,
  CLEAR가 검증한 미국·유럽·아시아 4개 외부 코호트 기반의 개념 해석 가능 분류 접근이
  기관 간 일반화 문제와 직접 맞닿아 있습니다.
- 우리 데이터가 뒷받침하는 것: 다기관·다장비 구성이라는 점.
- 확인해 줄 수 없는 것: 우리 데이터는 단일 소스 벤치마크로 보여, CLEAR류 모델의 실제
  기관 간 confounder 분석이나 전향적 리더 스터디는 재현할 수 없습니다.
- 링크: https://doi.org/10.1038/s41551-026-01741-4

### 2. Grounding Radiology Report Findings into Medical Image Segmentation (CF2Seg)
- npj Digital Medicine, 2026-07-28, OpenAlex
- 축: 기관 간 일반화, 보고서-영상 연계
- 왜 관련 있는가: 우리 데이터는 판독문(report_text)과 소견 라벨(findings_label)을 함께
  보유하고 있어, 자유 텍스트 보고서만으로 병변을 분할하는 CF2Seg의 접근을 그대로 적용해 볼
  여지가 있습니다.
- 우리 데이터가 뒷받침하는 것: 판독문·소견 라벨이 함께 존재하고 다기관 구성이라는 점.
- 확인해 줄 수 없는 것: 픽셀 단위 전문가 주석이 없어 분할 정확도나 병변 부담 일치도는
  검증 불가.
- 링크: https://doi.org/10.1038/s41746-026-03051-0

### 3. UniMedDiff: a knowledge-enhanced diffusion model for medical image generation from clinical reports
- npj Digital Medicine, 2026-08-13, OpenAlex
- 축: 라벨 불균형/데이터 증강, 보고서-영상 연계
- 왜 관련 있는가: 우리 코호트는 'No Finding'이 과반(145/272)이고 다수 소견이 10건 미만인
  심한 라벨 불균형을 보여, 판독문 기반 합성 흉부 X-ray 증강이 실질적 대안이 될 수 있습니다.
- 우리 데이터가 뒷받침하는 것: 극심한 라벨 불균형(희귀 소견 표본 부족)이라는 점.
- 확인해 줄 수 없는 것: 합성 영상의 병리학적 사실성이나 실제 분류기 성능 개선 효과는
  별도 실험 없이는 검증 불가.
- 링크: https://doi.org/10.1038/s41746-026-03135-x

## 검토 안내

**본 추천은 자동 생성된 초안이며, 임상적 판단과 최종 채택 여부는 반드시 담당 의료진의
검토를 거쳐야 합니다.** 각 논문의 `relevance`는 코호트 수준 통계에 근거하며, 환자 개별
정보는 포함하지 않았습니다.

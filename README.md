# 🎾 Tennis Serve Analyzer

딥러닝 기반 테니스 서브 분석 프로젝트입니다.  
서브 결과(에이스, 폴트, 리턴 성공 여부)를 예측하고 시각적으로 분석합니다.

---

## 📌 프로젝트 개요

- 원본 기반 프로젝트: [Capstone Project - Serve Optimization for Tennis Players](https://github.com/lance41/Capstone_Project-Serve-Optimization-for-Tennis_Players)
- 리디자인 및 확장: [RowanSkye](https://github.com/RowanSkye)
- 주요 모델: 3D-CNN, ConvLSTM
- 입력: 테니스 서브 영상에서 추출된 프레임 이미지
- 확장 기능: **사용자 훈련 세션 기반 서브 결과 시각화 기능**

---

## ✨ 주요 수정 및 개선 사항

### 1) 프레임 추출 안정성 개선
✅ 중복 처리 방지 로직을 추가하여,  
정상 처리된 영상이 재실행 시 삭제되는 문제 해결

### 2) 전처리 효율화 및 재사용성 강화
✅ 전처리 결과를 `.npy` 파일로 저장하여 반복 실행 방지  
→ 실행 속도 향상, 실험 재현성 확보

### 3) 데이터 품질 관리 강화
✅ 프레임 누락 시 관련 폴더 삭제 및  
원본 영상은 `failed_videos/`로 자동 이동  
→ 오류 데이터 자동 정리 및 학습 데이터 품질 향상

### 4) 사용자별 서브 결과 시각화 기능 추가
✅ 개인 훈련 데이터를 기반으로  
- 에이스/폴트/정상 서브 비율  
- 리턴 성공률/미리턴 비율  
을 직관적으로 파악할 수 있는 시각화 기능 제공

---

## 📁 디렉토리 구조

```plaintext
tennis-serve-analyzer/
│
├── code/                           # 코드 파일
│   ├── 01_Predicting_Tennis_Serve.ipynb
│   └── 02_Tennis_Data_Visualization.ipynb
│
├── assets/                         # 모델 시각화 이미지
│   └── model_plot.png
│
├── analysis/                       # 사용자 훈련 기록 데이터
│   └── 테니스_세션_데이터_v03.xlsx
│
├── data/                           # 수동 다운로드한 원본 영상 저장 폴더
│   ├── 01_ace/
│   ├── 02_faults/
│   └── ...
│
├── frames/                         # 추출된 프레임 이미지 (자동 생성)
├── frames_data/                    # 프레임 경로 및 레이블 (자동 생성)
│   ├── X.npy
│   └── y.npy
├── preprocessed_data_3d/           # 3D-CNN 전처리 데이터 (자동 생성)
│   ├── X_3d.npy
│   └── y_3d.npy
├── failed_videos/                  # 프레임 추출 실패 시 이동된 원본 영상
├── README.md

```
---

## 📁 주요 코드 파일

파일명	설명

01_Predicting_Tennis_Serve.ipynb	테니스 서브 예측 모델 (3D-CNN, ConvLSTM) 구현 및 평가

02_Tennis_Data_Visualization.ipynb	사용자 서브 기록을 기반으로 분석 및 시각화 수행 (개인 기능 확장)

---

## 💾 경로 설명

| 경로 | 설명 |
|------|------|
| `./frames/` | 추출된 프레임 이미지 저장 (7장씩) |
| `./frames_data/X.npy` | 프레임 이미지 경로 배열 (학습용) |
| `./frames_data/y.npy` | 프레임 레이블 배열 |
| `./preprocessed_data_3d/X_3d.npy` | 전처리된 이미지 데이터 (3D-CNN 입력용) |
| `./preprocessed_data_3d/y_3d.npy` | 전처리된 레이블 |
| `./failed_videos/` | 프레임 추출 실패 시 이동된 영상 |
| `./assets/model_plot.png` | 모델 구조 시각화 이미지 |
| `./analysis/테니스_세션_데이터_v03.xlsx` | 사용자 훈련 기록 엑셀 (시각화 입력 데이터) |

---
  
## 📦 영상 데이터 다운로드 안내

⚠️ GitHub 저장 용량 제한으로 인해, 영상 데이터는 직접 다운로드해야 합니다.  
👉 아래 링크를 통해 원본 데이터를 받아주세요:

📂 [Google Drive 영상 데이터 다운로드](https://drive.google.com/drive/folders/1-rfgudMgdzlRARMM11O5Pwyv5OCMrSbN)

> 📥 받은 영상 파일은 `./data/` 폴더 안에 넣어주세요.

---

## 🙌 기여자
- 원작자: Ngan Han Kiong  
- 리디자인 및 코드 수정: RowanSkye
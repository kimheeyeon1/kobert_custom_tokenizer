# KoBERT Custom Tokenizer Experiment

본 실험에서는 KoBERT를 감정 분류 task에 fine-tuning하면서  
직접 구현한 Custom tokenizer와 기존 KoBERT tokenizer를 각각 적용하여 모델을 학습했습니다.

Custom tokenizer는 다음과 같이 구성되었습니다:

- Okt 형태소 분석기로 텍스트 토큰화  
- 학습 데이터에서 빈도 기반 vocabulary 학습
- `[PAD]`, `[CLS]`, `[SEP]`, `[UNK]` 스페셜 토큰 포함
- HuggingFace tokenizer 인터페이스와 호환되도록 구현 (`encode`, `__call__` 등)

각 토크나이저를 적용한 모델의 정확도를 비교하여 tokenization 방식에 따라 감정 분류 모델의 성능 차이가 발생하는지 확인했습니다.

---

## 파일 구조
```bash
kobert_custom_tokenizer
│
├ baseline_kobert.ipynb          # 기본 KoBERT tokenizer 사용
├ custom_tokenizer_kobert.ipynb  # Custom tokenizer 사용
│
├ data
│   └ dataset.csv
│
├ requirements.txt
└ README.md
```
---
## 실험 파이프라인
1. Seed 설정
2. 데이터 로드
3. Label Encoding
4. Train / Validation / Test Split
5. Tokenizer 적용
    - KoBERT 기본 tokenizer (pretrained vocabulary)
    - Custom tokenizer      (vocabulary 학습)
6. Dataset & DataLoader 구성
7. KoBERT Fine-tuning
8. Validation Accuracy 평가
---
## 실험 결과 (Accuracy)

KoBERT Tokenizer | 0.58

Custom Tokenizer | 0.87

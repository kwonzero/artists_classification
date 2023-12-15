# artists_classification
* 대회 정보
  - 월간 데이콘 예술 작품 화가 분류 AI 경진대회
  - 링크 : https://dacon.io/competitions/official/236006/overview/description
* 훈련 데이터 구조
  - data 폴더 밑에 다운 받은 압축 파일을 풀면 아래와 같은 구조가 나옴
  - data 폴더 밑에 gan folder 추가
  ```
  - data
    + gan
    + test
    + train
    - artists_info.csv
    - sample_submission.csv
    - submit.csv
    - test.csv
    - train.csv
  ```
* 진행 사항
  - 12/8(금)
    - Baseline 코드 학습
    - EfficientNet-B0
    - https://dacon.io/competitions/official/236006/codeshare/6675
  - 12/11(월)
    - 공유된 코드 학습
    - private 4위 노트
      - 앙상블
        - EfficientNet-V2-M
        - ViT_B_16
        - ViT_L_16
        - ViT_B_16 + 장르 정보
        - ViT_L_16 + 장르 정보
      - weighted random sampling 사용
      - Cutmix, FMix, MixUp 사용(loss function 주의)
      - get_cosine_schedule_with_warmup 사용
      - 결과 도출을 위한 Stacking 모델 적용
        - 5개 모델의 결과를 열로 묶은 후(250열) layernorm 적용 후 linear로 50개 도출
        - 이 모델에 대해서 별도의 훈련을 진행
      - https://dacon.io/competitions/official/236006/codeshare/7077
    - private 10위 노트
      - Pytorch로 EfficientNet B1~B6 앙상블
      - TensorFlow로 EfficientNet B1~B6 앙상블
      - 12개의 모델의 결과를 softmax 돌린 후 합산하고 argmax로 작가 선정 
      - https://dacon.io/competitions/official/236006/codeshare/7073
    - private 15위 노트
      - EfficientNet-B4
      - Cutmix 사용
      - https://dacon.io/competitions/official/236006/codeshare/7062
    - private 20위 노트
      - EfficientNet B4, EfficientNEt B7 앙상블 
      - MixUp 사용
      - StepLR 사용
      - https://dacon.io/competitions/official/236006/codeshare/7056
  - 12/12(화)
    - private 1위 노트
      - tf_efficientnet_b7_ns(Noisy Student)
      - weighted random sampling 사용
      - StepLR 사용
      - StratifiedKFold(10) 사용
      - 10개의 모델의 결과를 softmax 돌린 후 합산하고 argmax로 작가 선정 
      - https://dacon.io/competitions/official/236006/codeshare/7080
    - private 2위 노트
      - TinyVit384 모델
      - CutMix, CutOut 사용
      - Custom CosineAnnealingWarmUpRestarts
      - StratifiedKFold 사용
      - TinyVit384 모델로 2개의 모델을 구성
        - 다른 설정값으로 훈련시켜 2개의 결과를 만들고 softmax 돌린 후 합산하고 argmax로 작가 선정 
      - https://dacon.io/competitions/official/236006/codeshare/7040
    - private 5위 노트
      - Convnext_large 모델(https://arxiv.org/pdf/2201.03545.pdf)
      - CutMix, CutOut 사용
      - CosineAnnealingLR
      - SAM Optimizer 사용
      - https://dacon.io/competitions/official/236006/codeshare/7039
    - private 6위 노트
      - 7개의 모델 앙상블(세부 모델 분석 못함)
        - Swin-T
        - MultiModal(푸리에 변환)
        - MultiModal(RGB 히스토그램)
        - MultiModal(horizontal flip)
        - MultiModal(vertical flip)
        - MultiModal(장르)
      - EfficientNet B0, Swin Transformer(https://arxiv.org/abs/2103.14030)
      - 데이터셋을 9분할하여 데이터를 제공
      - LambdaLR
      - tta 적용(VerticalFlip, HorizontalFlip)
  - 12/13(수)
    - 베이스라인 모델 만들기
      - EfficientNet B2
      - Image size : 384
      - augmentation 
        - resize, centercrop 
        - normalization 
      - early stopping
  - 12/14(목)
    - 대이터 증강 기법
      - CutMix
    - lr-scheduler
      - Custom CosineAnnealingWarmUpRestarts
    - vit 모델로 변경하여 테스트
      - tiny_vit_21m_384.dist_in22k_ft_in1k
    - 앙상블 기법 적용
  - 12/15(금)
    - StratifiedKFold(5)
    - metric adjust
      - Focal Loss
    - 앙상블(2)
  - 12/18(월)
  - 12/19(화)
- 남은 TodoList
  - 모델 변경 테스트
  - SAM
  - sampler
  - 물리적 데이터 증강
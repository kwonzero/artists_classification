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
      - weighted random sampling 기법 사용
      - Cutmix, FMix, MixUp 기법 사용(loss function 주의)
      - https://dacon.io/competitions/official/236006/codeshare/7077
    - private 10위 노트
      - Pytorch로 EfficientNet B1~B6 앙상블
      - TensorFlow로 EfficientNet B1~B6 앙상블
      - 12개의 모델의 결과를 softmax 돌린 후 더해준 후 argmax로 작가 선정 
      - https://dacon.io/competitions/official/236006/codeshare/7073
    - private 15위 노트
      - EfficientNet-B4
      - Cutmix 기법 사용
      - https://dacon.io/competitions/official/236006/codeshare/7062
    - private 20위 노트
      - EfficientNet B4, EfficientNEt B7 앙상블 
      - MixUp 기법 사용
      - StepLR 사용
      - https://dacon.io/competitions/official/236006/codeshare/7056
  - 12/12(화)
  - 12/13(수)
  - 12/14(목)
  - 12/15(금)
  - 12/18(월)
  - 12/19(화)
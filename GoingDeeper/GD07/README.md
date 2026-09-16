# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 강지수
- 리뷰어 : 박희지


# PRT(Peer Review Template)
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    1) MLM, NSP task의 특징이 잘 반영된 pretrain용 데이터셋 생성과정이 체계적으로 진행되었다.
       - MLM+NSP 128,000 sample을 JSONL → np.memmap 이진 포맷으로 변환하였다.
      
         <img width="586" height="900" alt="image" src="https://github.com/user-attachments/assets/96f8ef2f-d656-490c-971c-c784019f811e" />

    2) 구현한 BERT 모델의 학습이 안정적으로 진행됨을 확인하였다.
       - Total Loss 8.65 → 7.04(−18.6%), MLM Loss 8.02 → 6.56(−18.2%), NSP Loss 0.63 → 0.48(−24.4%)로 세 지표 모두 발산 없이 감소했다.
      
         <img width="1089" height="651" alt="image" src="https://github.com/user-attachments/assets/cd7e7949-9968-4bb6-8396-df98b6edb4e9" />

    3) 1M짜리 mini BERT 모델의 제작과 학습이 정상적으로 진행되었다.
       - `Trainable Parameters = 1,014,528` (STEP 6-12), 10 epoch 학습하였다.

        <img width="573" height="927" alt="image" src="https://github.com/user-attachments/assets/ffd15782-dd7e-4c63-bf7c-5136a94e3458" />

    
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 노트북 전체에서 가장 핵심적인 부분은 STEP 6의 `SharedEmbedding` → `PositionEmbedding` → `ScaleDotProductAttention` → `MultiHeadAttention` → `EncoderLayer` → `BERT` → `PreTrainModel`로 이어지는 모델 구현부라고 판단했다.
    - 이 구간은 6~7개의 클래스가 서로를 호출하며 쌓이는 구조(embedding 3종 → attention → FFN → encoder layer × 2 → NSP/MLM head)로, 클래스 간 조립을 이해해야 전체 흐름이 보이기 때문이다.
    - shape 변화 자체를 주석에 그대로 써놓아서, 두 함수의 코드를 오가며 shape를 직접 추적하지 않아도 "지금 몇 차원이 늘었는지"가 바로 확인된다.
    - weight tying 설계 의도를 주석으로 작성하여 "embedding table을 MLM head projection과 공유해서 parameter 수를 줄이는 BERT의 표준 기법"이라는 것을 알 수 있었다.
     
      <img width="373" height="583" alt="image" src="https://github.com/user-attachments/assets/cfbb3215-7596-4a59-a723-c395aace8c53" />

        
- [x]  **3. 에러가 난 부분을 디버깅하여 문제를 해결한 기록을 남겼거나
새로운 시도 또는 추가 실험을 수행해봤나요?**
    - Batch Size Benchmark 실험 및 데이터 기반 의사결정을 진행하였다. batch=256을 최종 채택한 근거를 수치로 제시했다. 이는 실측 없이 임의로 하이퍼파라미터를 정한 것이 아니라, 실제 forward/backward/optimizer step을 포함한 벤치마크를 직접 설계해 실행한 추가 실험이다.
     
      <img width="860" height="319" alt="image" src="https://github.com/user-attachments/assets/e2e85ccf-b749-4e6f-83e6-2ba5ce9d6214" />

        
- [x]  **4. 회고를 잘 작성했나요?**
    - STEP 8 이후 배운 점, 결과 해석, 한계까지 구조적으로 정리되어 있다.
      - parameter 수, loss 감소율, accuracy 상승, learning rate/후반부 수렴 관계까지 수치 기반으로 서술하여 결과 해석을 작성하였다.
      - corpus → tokenizer → dataset → model → training → 결과까지 ASCII 다이어그램으로 시각화되어 있어 전체 파이프라인을 한눈에 파악할 수 있었다.

        <img width="367" height="1007" alt="image" src="https://github.com/user-attachments/assets/9342c890-dc82-47e4-a140-88543fdf40aa" />

        
- [x]  **5. 코드가 간결하고 효율적인가요?**
    - `SharedEmbedding.forward`에서 `mode="embedding"/"linear"` 분기로 하나의 클래스가 embedding lookup과 MLM output projection을 모두 처리하도록 모듈화한 점은 잘 설계되었다.
    - 전체 코드가 STEP n-m 단위로 명확히 구획되어 있어 어느 코드가 어떤 단계에 속하는지 추적하기 쉽다.
    - 줄바꿈이 세분화되어 있다. PEP8  위반은 아니지만 코드 길이와 스크롤 양이 늘어나 가독성이 떨어진다.


# 회고(참고 링크 및 코드 개선)
```
파이프라인이 체계적으로 잘 구현되어 있어서 많이 배웠습니다.
또한, 주석과 markdown으로 기법을 사용하는 이유나 개념이 정리되어 있어서 개념을 다시 확인할 수 있었습니다.
```

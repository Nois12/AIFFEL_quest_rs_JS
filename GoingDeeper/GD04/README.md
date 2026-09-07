# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 강지수
- 리뷰어 : 김나연


# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 두 모델의 pose estimation 테스트결과 이미지 및 학습진행상황 등을 체계적으로 비교분석하였다.
        - <img width="1336" height="665" alt="image" src="https://github.com/user-attachments/assets/5d0f1752-c377-4432-895e-945558e11ae2" />
        - <img width="1712" height="583" alt="image" src="https://github.com/user-attachments/assets/1d194de0-6257-46fe-8d9e-459d1a50ad6c" />
    - simplebaseline 모델을 구현하여 실습코드의 모델을 대체하여 정상적으로 학습이 진행되었다.
        - <img width="1192" height="537" alt="image" src="https://github.com/user-attachments/assets/74a1e7c1-d6fa-4233-95b4-b6a6865fc436" />
    - MPII 데이터셋을 기반으로 1epoch에 30분 이내에 학습가능한 베이스라인을 구축하였다.
        - <img width="750" height="536" alt="image" src="https://github.com/user-attachments/assets/7ac3ce3a-eb5e-4d40-b789-4d45c22a94cd" />
    
- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 코드의 흐름이 바뀌거나 이해가 어려운 부분을 텍스트를 통해 잘 설명하고 있다.
        - <img width="481" height="662" alt="image" src="https://github.com/user-attachments/assets/1448d66a-c4ea-4f27-9487-ba6f89981e85" />
        - <img width="1253" height="737" alt="image" src="https://github.com/user-attachments/assets/84d2d690-1972-4a22-835b-1e27338f3ba4" />
        
- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 해결한 기록을 남겼거나
새로운 시도 또는 추가 실험을 수행해봤나요?**
    - 런타임 종료에 따라 삭제된 실행 내역을 복구하기 위해 구글 드라이브를 이용하였다.
        - <img width="1527" height="731" alt="image" src="https://github.com/user-attachments/assets/6f46bc28-b4f6-4aaf-9ae7-87c1afa360d5" />
        
- [x]  **4. 회고를 잘 작성했나요?**
    - 학습 결과를 시각화하고 에폭에 따른 loss 값을 그래프로 나타내고 있다.
        - <img width="908" height="583" alt="image" src="https://github.com/user-attachments/assets/e0478c5f-4ddc-4fbb-8a58-9f37180b9480" />
        - <img width="780" height="657" alt="image" src="https://github.com/user-attachments/assets/d6a76416-4b08-4c4d-8bee-1186c6a6379a" />
    - <img width="1697" height="742" alt="image" src="https://github.com/user-attachments/assets/c0777e5e-4626-43f2-b3ee-0008e872cf00" />
        
- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 모델 구조가 클래스 단위로 적절히 분리되어 있다.
        - `BottleneckBlock`, `HourglassModule`, `StackedHourglassNetwork`, `DeconvBlock`, `SimpleBaseline`

# 회고(참고 링크 및 코드 개선)
```
지수님의 프로젝트는 항상 한 편의 이야기를 읽는 것 같아요!
회고가 가장 기억에 남는데 개인적인 생각이지만 최신 기술에 많은 신경을 쓰기 보다는 가장 많이 쓰이는 기술을 확실하게 알고 익힌 기술을 적재적소에 사용하는 능력이 제일 중요하다고 생각합니다.
현재 AI의 판도를 뒤집어 놓을 만한 신기술이 나오기 전까지는요...
어찌되었든 현재의 AI는 결국엔 loss를 최소화한다는 동일한 개념이 바탕이 되기 때문에 이 개념에서 벗어나지 못하면 현재 기술을 개선하는 수준을 넘어서기는 어렵다고 생각합니다.
물론 제 개인적인 생각일 뿐이지만 저도 AI의 미래에 대해 생각 해본 적이 많아서 한 번 적어 봤습니다 ㅎㅎ

이번 프로젝트도 수고하셨습니다~
```

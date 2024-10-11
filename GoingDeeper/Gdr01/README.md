# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 담안용
- 리뷰어 : 유지희


# PRT(Peer Review Template)
- [X]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
        - 중요! 해당 조건을 만족하는 부분을 캡쳐해 근거로 첨부  
    - 1. SentencePiece를 사용하여 accuracy 80% 이상을 성공적으로 도출하고, 2. mecab을 사용한 모델을 만들어서 성능을 비교함
 ![image](https://github.com/user-attachments/assets/3a0c7653-65f0-4641-9b5e-3cef19a5f371)
 ![image](https://github.com/user-attachments/assets/04dec503-7412-4f27-87d6-02c4f7d29038)


- [X]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭을 왜 핵심적이라고 생각하는지 확인
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드의 기능, 존재 이유, 작동 원리 등을 기술했는지 확인
    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
        - 이번 프로젝트 핵심인 sentencePiece 모델 학습 부분에 대하여 자세한 주석을 첨부함
        ![image](https://github.com/user-attachments/assets/7439339d-5528-46ba-8bef-d7f4a3789cfb)

- [X]  **3. 에러가 난 부분을 디버깅하여 문제를 해결한 기록을 남겼거나
새로운 시도 또는 추가 실험을 수행해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 프로젝트 평가 기준에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
        - 전처리 시 문장 길이를 끊는 기준에 대하여 다양한 실험을 시도해본 후 근거를 마련하여 전처리 함
          ![image](https://github.com/user-attachments/assets/4621036c-e154-4b4d-b513-8bc67cee7083)
      ![image](https://github.com/user-attachments/assets/d8807cc0-6f4c-4c63-aa16-1aab1ccee5e1)
 
        
- [X]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
        - 배운점, 아쉬운점, 느낀점 모두 적힘
        ![image](https://github.com/user-attachments/assets/83ad75b8-bfcf-4bc5-a089-77c71e7cb6d6)

- [X]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화/모듈화했는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
        - 토크나이저 함수 정의를 잘 했음
![image](https://github.com/user-attachments/assets/6a1a211d-8aa8-4876-8ba4-f4edff56276c)


# 회고(참고 링크 및 코드 개선)
```
# 전처리를 공들여서 하신 부분이 인상깊었습니다, 데이터를 하나하나 확인해보면서 어디서부터 어디까지 잘라야 좋을지 고민한 흔적과 짧은 시간 내 성능을 비교하신 추가 실험까지 진행하신 부분이 대단하다고 생각됩니다ㅎㅎ
train데이터와 validation 데이터를 한 번 더 나누어서 꼼꼼하게 실험 하신 것도 인상깊었습니다. 고생 많으셨습니다!
```

# chatbot_kullm
[Customizing Chatbot]

개요 특정 산업 혹은 업무에 특화된 챗봇을 개발하기 위해 기 개발된 모델을 Fine-tuning 하여 결과 확인 원래 정상 모델을 사용하려고 하였으나, 현재 진행하는 서버에서 메모리 문제로 돌아가지 않아 경량화 모델을 사용함. kullm, koalpaca, KoreanLM, Koat 4가지 모델로 테스트하였으며, 가장 성능이 괜찮은 모델이 kullm임. 데이터는 AI-hub의 질의응답 형식의 데이터를 가져와 진행함.

과정 서버 연결은 MobaXterm을 활용함. AI-hub에서 6가지 분야의 질의응답 형식의 데이터를 Json 형태로 받아와 학습에 사용함. 특수 문자 혹은 의미를 파악할 수 없는 문자들을 제거한 후 학습에 맞는 형태로 전처리를 진행함. 학습 시 kullm의 하이퍼파라미터 튜닝을 진행하여 미리 준비한 질문을 던져 결과를 확인함.

결론 속도 측면에서는 다른 모델에 비해 10~20sec 정도 떨여졌으나, 정확도 측면에서 다른 모델에 비해 좋다고 판단함.

## korean-LLM-quantize
autoGPTQ를 활용한 koalpaca &amp; kullm 모델 양자화 및 테스트

## 실행

#### KoAlpaca
```bash
python quant_with_LLM.py --pretrained_model_dir beomi/KoAlpaca-Polyglot-12.8B --quantized_model_dir ./model/koalpaca-8bit
```

#### Kullm
```bash
python quant_with_LLM.py --pretrained_model_dir nlpai-lab/kullm-polyglot-12.8b-v2 --quantized_model_dir ./model/kullm-8bit
```

### 2019-01-10
- seq2seq GRU 예제를 보며 확인한 결과 학습시 loss값과 optimizer 선언을 다 잘하고 optimizer 를 zero_grad()로 초기화를 안 하고 학습시킨게 문제였다. 그 후 LSTM으로도 모델을 변경하여 확인한 결과 loss값이 제대로 떨어지는 것을 확인하였다. LSTM의 경우 GRU 보다 loss 값이 덜 떨어져서 learning_rate를 조금 조절한 결과 GRU 보다 loss가 훨씬 더 떨어졌다. 데이터 구성이 아주 쉬우므로 별 의미는 없다.
![](https://github.com/JeongMyeong/pytorch-example/blob/master/seq2seq/fig/loss.png)


### 2020-01-09
- LabelEncoding 방식으로 변경하여 데이터를 구성.
- Encoder에서 입력값으로 토큰 하나를 입력받아 Embedding Layer를 통과 후 LSTM Layer를 거쳐 output, hidden 값을 반환
- Decoder는  Teacher forcing 방식을 사용하여 예측할 토큰의 그 전 토큰을 넣과 Encoder에서 나온 hidden state를 Decoder에 입력한다. Decoder에서도 마찬가지고 Embedding Layer를 통과 후 LSTM Layer를 거친 output 값을 Softmax Layer에 넣기 전에 차원을 맞추어 주기 위해 Linear Layer를 vocab size에 맞게 만들어 통과시켜준다. 
- 모델이 이상한 것인지 loss값은 떨어지지만 정확히 학습이 되는것 같지 않음.
- LSTM의 output값 중 hidden state 중 hn과 cn 을 둘 다 넣었는데 하나만 넣는것인지 잘 모르겠음.
- 일단 GRU로 다시 해보기로 ...

### 2020-01-08
- seq2seq 구현 중 문장의 단어들을 one-hot-encoding을 했지만 이것보단 label-encoding 방식으로 하는것이 나아보임
- [OneHotEncoding](https://wikidocs.net/22647)
- [LabelEncoding](https://pinkwink.kr/1247)
- OneHotEncoding(OHE)으로 seq2seq2 을 구현하면서 Encoder에 OHE된 데이터를 입력하여 (output state, hidden state) 값을 반환, 반환한 값을
![](https://github.com/JeongMyeong/pytorch-example/blob/master/seq2seq/fig/seq2seq flow.png)
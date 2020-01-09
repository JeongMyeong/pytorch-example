### 2020-01-09
- LabelEncoding 방식으로 변경하여 데이터를 구성.
- Encoder에서 입력값으로 토큰 하나를 입력받아 Embedding Layer를 통과 후 LSTM Layer를 거쳐 output, hidden 값을 반환
- Decoder는  Teacher forcing 방식을 사용하여 예측할 토큰의 그 전 토큰을 넣과 Encoder에서 나온 hidden state를 Decoder에 입력한다. Decoder에서도 마찬가지고 Embedding Layer를 통과 후 LSTM Layer를 거친 output 값을 Softmax Layer에 넣기 전에 차원을 맞추어 주기 위해 Linear Layer를 vocab size에 맞게 만들어 통과시켜준다. 

### 2020-01-08
- seq2seq 구현 중 문장의 단어들을 one-hot-encoding을 했지만 이것보단 label-encoding 방식으로 하는것이 나아보임
- [OneHotEncoding](https://wikidocs.net/22647)
- [LabelEncoding](https://pinkwink.kr/1247)
- OneHotEncoding(OHE)으로 seq2seq2 을 구현하면서 Encoder에 OHE된 데이터를 입력하여 (output state, hidden state) 값을 반환, 반환한 값을
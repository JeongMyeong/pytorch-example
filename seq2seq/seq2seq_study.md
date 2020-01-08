# seq2seq 구현 중 문장의 단어들을 one-hot-encoding을 했지만 이것보단 label-encoding 방식으로 하는것이 나아보임
- [OneHotEncoding](https://wikidocs.net/22647)
- [LabelEncoding](https://pinkwink.kr/1247)
- OneHotEncoding(OHE)으로 seq2seq2 을 구현하면서 Encoder에 OHE된 데이터를 입력하여 (output state, hidden state) 값을 반환, 반환한 값을
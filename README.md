# compare_encoder_output-bert-
단순히 호기심에서 시작함.

Bert에서 evaluation할 떄,
어텐션 계산 -> Add Residual&NL -> FFNN -> ADD Residual&NL -> Next encoder의 순서를 따른다.

이 때, 각 인코더의 아웃풋의 형태는 N개의 평가 데이터가 존재하고, batch size가 1이라 가정한다면
[N/batch_size * layer_num * batch_size * seq_num * max_token] 이다.

이를 레이어별 아웃풋으로 살펴보면
[layer_num * seq_num * max_token]으로 볼 수 있고,
어텐션 계산에 쓰인 헤드의 개수로 토큰을 나누고
이를 다시 행렬로 표시한다면,
12(layer_num) x 12(token_head)로 나타낼 수 있다.

이것을 히트맵으로 찍어보고 버트에서 인코더가 깊어질 수록 어떤 특징을 학습하는지 알아보자.

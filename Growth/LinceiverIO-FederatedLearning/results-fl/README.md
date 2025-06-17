# Linceiver IO - FederatedLearning 실험 결과

실험 수행시 `fed_linceiverio_report_{local_ep}_{k}_{test_no}.txt ` 이름으로 결과 파일이 생성됩니다. <br><br>
* `local_ep` : 로컬 에폭 수
* `k` : 연합학습에서 사용된 projection 차원
* `test_no` : 반복 실험의 경우 몇 번째 test 인지 표시함

결과 파일의 첫 번째 라인에는 실험을 진행할 때 사용한 명령어가 저장됩니다. <br><br>

```bash
federated_main_per.py --model=perceiver-io-linstyle --dataset=fmnist --iid=1 --epochs=10 --optimizer=adam --lr=5e-4 --frac=1.0 --num_users=10 --local_bs=64 --local_ep=5 --test_no=1 --k=128
```

이를 통해 설정한 실험 환경을 알 수 있습니다. 관련 파라미터는 `../README.md`를 참고 해주세요.

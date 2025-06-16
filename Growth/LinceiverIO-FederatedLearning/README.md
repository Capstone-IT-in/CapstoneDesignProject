# Federated Linceiver IO Test

## Source Code

| 파일명                        | 설명                                  |
| -------------------------- | ----------------------------------- |
| `federated_main_per.py`    | Federated 학습을 수행하는 메인 스크립트          |
| `federated_batch.sh`       | 다양한 하이퍼파라미터 조합에 대해 반복 실험 실행         |
| `options.py`               | 명령줄 인자 파서 정의                        |
| `sampling.py`              | IID 및 Non-IID 데이터 분할 방식 정의          |
| `test_with_sharing_lat.py` | Shared Latent 기반 Perceiver IO 모델 정의 |
| `utils.py`                 | 데이터 로딩 및 기타 보조 함수 정의                |
| `save/`                    | 실험 결과 저장 폴더 (자동 생성)                 |

---

## ⚙️ How to Build

빌드 과정은 없습니다. 모든 파일은 Python 스크립트로 구성되어 있으며 바로 실행할 수 있습니다.

---

## 📦 How to Install

필요한 라이브러리 설치:

```bash
pip install torch==1.10.2 torchvision==0.11.3 einops==0.8.0 tensorboardX==2.1
```

**필수 환경:**

* Python 3.8.20
* PyTorch 1.10.2
* torchvision 0.11.3
* einops 0.8.0
* tensorboardX 2.1

---

## 🧪 How to Test

### 1. 단일 실험 실행

```bash
python federated_main_per.py --epochs 50 --num_users 100 --frac 0.1 --local_ep 10 --local_bs 10 --lr 0.01 --k 128 --test_no 0 --dataset fmnist --iid 1
```

### 2. 여러 실험 자동 실행

```bash
bash federated_batch.sh
```

* 다양한 `k`, `test_no`, `local_ep` 등의 조합으로 반복 실험을 실행합니다.

---

## ⚙️ Arguments 설명

| 옵션명           | 설명                             | 기본값                   |
| ------------- | ------------------------------ | --------------------- |
| `--epochs`    | 전체 라운드 수                       | 10                    |
| `--num_users` | 클라이언트 수                        | 100                   |
| `--frac`      | 매 라운드 참여 클라이언트 비율              | 0.1                   |
| `--local_ep`  | 클라이언트별 로컬 학습 epoch 수           | 10                    |
| `--local_bs`  | 로컬 배치 크기                       | 10                    |
| `--lr`        | 학습률                            | 0.01                  |
| `--momentum`  | SGD momentum (현재 사용 안함)        | 0.5                   |
| `--test_no`   | 실험 번호 (결과 폴더 구분용)              | 0                     |
| `--model`     | 모델 이름                          | perceiver-io-linstyle |
| `--dataset`   | 사용 데이터셋 (mnist, fmnist, cifar) | fmnist                |
| `--iid`       | IID 여부 (1: IID, 0: Non-IID)    | 1                     |
| `--unequal`   | Non-IID 데이터 불균등 여부             | 0                     |
| `--k`         | Linformer projection dimension | 128                   |

---

## 📁 Sample Data

* `torchvision.datasets`를 통해 Fashion-MNIST가 자동 다운로드됩니다.

---

## 📚 Used Open Source Libraries

* [PyTorch](https://pytorch.org/) - 딥러닝 프레임워크 (BSD)
* [Torchvision](https://github.com/pytorch/vision) - 데이터 및 이미지 전처리 도구 (BSD)
* [einops](https://github.com/arogozhnikov/einops) - 텐서 구조 조작 유틸리티 (MIT)
* [tensorboardX](https://github.com/lanpa/tensorboardX) - 시각화 및 로그 기록 도구 (MIT)

---

## 🧠 Project Overview

본 프로젝트는 **Federated Learning** 환경에서 **Linceiver IO** 모델을 적용하여 효율적이고 확장 가능한 분산 학습을 실현하는 것을 목표로 합니다.

### 특징:

* 클라이언트 간 데이터 불균형을 고려한 IID/Non-IID 샘플링
* Adaptive k 기반 Attention으로 통신량 절감 및 연산 효율 향상
* Shared Latent 구조를 통한 전역 표현 공유

---

## 📈 실험 결과물 및 해석 예시

(추가)

---

## ▶️ 실행 스크립트 예시

```bash
#!/bin/bash
echo "Running federated experiments..."
bash federated_batch.sh

echo "All results saved under ./save/fmnist/"
```

---

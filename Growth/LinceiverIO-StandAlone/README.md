# Adaptive K Test

## Source Code

| 파일명                        | 설명                                       |
| -------------------------- | ---------------------------------------- |
| `main.py`                  | 단일 실험 실행 스크립트 (모델 학습 및 평가)               |
| `perceiver_io_linstyle.py` | Linformer 기반 Perceiver IO 모델 정의 파일       |
| `run_batch.sh`             | 다양한 설정의 실험을 자동 반복 실행하는 배치 스크립트           |
| `report_batch.sh`          | 실행된 실험 결과들을 평균내어 `report.txt`로 정리하는 스크립트 |
| `results/`| 실험 결과 저장 폴더 (자동 생성)                      |
| `results-standalone/`| 실제 실험 결과 예시                      |

---

## ⚙️ How to Build

별도의 빌드 과정은 필요하지 않습니다. Python 스크립트 실행만으로 모든 기능이 동작합니다.

---

## 📦 How to Install

다음 명령어로 필수 라이브러리를 설치하세요:

```bash
pip install torch==1.10.2 torchvision==0.11.3 einops==0.8.0
```

**필수 환경:**

* Python 3.8.20
* PyTorch 1.10.2
* torchvision 0.11.3
* einops 0.8.0

---

## 🧪 How to Test

### 1. 단일 실험 실행

```bash
python main.py --model perceiver-io-linstyle --epochs=10 --batch_size=64 --lr=5e-4 --weight_decay=1e-4 --k=128 --test_no=1
```

### 2. 여러 실험 자동 실행

```bash
bash run_batch.sh
```

* 다양한 `k` 및 `test_no` 조합으로 실험이 자동 실행되며, 각 조합별 결과 폴더가 자동 생성됩니다.

### 3. 결과 보고서 생성

```bash
bash report_batch.sh
```

* 각 실험의 `result.txt` 파일을 평균내어 하나의 `report.txt`로 생성합니다.

---
## ⚙️ Arguments 설명

| 인자               | 설명                                                      | 기본값            |
| :--------------- | :------------------------------------------------------ | :------------- |
| `--model`        | 사용할 모델 종류. `perceiver-io` 또는 `perceiver-io-linstyle` 선택 | `perceiver-io` |
| `--epochs`       | 학습할 에폭 수                                                | `10`           |
| `--batch_size`   | 배치 크기                                                   | `64`           |
| `--lr`           | 학습률                                                     | `5e-4`         |
| `--weight_decay` | Weight decay 값                                          | `1e-4`         |
| `--k`            | Linformer 압축 차원                                         | `128`          |
| `--test_no`      | 실험 번호 (결과 폴더 구분용)                                       | 없음             |
---

## 📁 Sample Data

* Fashion-MNIST 데이터셋은 `torchvision.datasets`를 통해 **자동 다운로드**됩니다.
* 별도 수동 다운로드는 필요하지 않습니다.

---

## 📚 Used Open Source Libraries

본 프로젝트는 다음의 오픈소스를 활용합니다:

* [PyTorch](https://pytorch.org/) - 딥러닝 프레임워크 (BSD)
* [Torchvision](https://github.com/pytorch/vision) - 데이터셋 및 이미지 처리 도구 (BSD)
* [einops](https://github.com/arogozhnikov/einops) - 텐서 구조 조작 유틸리티 (MIT)

---

## 🧠 Project Overview

이 프로젝트는 Perceiver IO에 Linformer 기반 Adaptive Attention을 통합한 **Linceiver IO** 모델을 구현합니다. `k` 값을 입력 복잡도에 따라 동적으로 조절하여 효율성과 성능을 동시에 추구합니다.

### 특징:

* Adaptive k 기법을 적용한 압축 Attention
* 다양한 `k` 값에 대한 반복 실험 및 자동 보고서 생성
* Perceiver IO와 Linceiver IO 모델 비교 가능

---

## 📈 실험 결과물 및 해석 예시

(추가)

---

## ▶️ 실행 스크립트 예시

```bash
#!/bin/bash
echo "Running batch experiments..."
bash run_batch.sh

echo "Generating final report..."
bash report_batch.sh

echo "Done. Results saved in ./results/ or ./results-pio/"
```

---

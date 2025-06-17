# Linceiver IO - StandAlone 실험 결과

실험 수행시 `results/{k}/{test_no}` 안에 실험 결과가 저장됩니다. 또한  `bash report_batch.sh`를 수행하여 각 k에 대한 반복 실험의 평균 결과인 `report_{k}.txt`를 얻을 수 있습니다. <br>
* `k` : Linceiver IO의 projection 차원
* `test_no` : 반복 실험의 경우 몇 번째 test 인지 표시함 <br>
`makeplots.ipynb`는 `report_{k}.txt`들을 바탕으로 그래프를 그리는 코드입니다. 이를 통해 아래와 같은 이미지를 생성할 수 있습니다. <br>
<img src="https://github.com/Capstone-IT-in/CapstoneDesignProject/blob/main/Growth/LinceiverIO-StandAlone/results-standalone/epoch_accuracy_plot_new.png?raw=true" alt="정확도" width="600"/> <br>
<img src="https://github.com/Capstone-IT-in/CapstoneDesignProject/blob/main/Growth/LinceiverIO-StandAlone/results-standalone/training_time_and_model_size_new.png?raw=true" alt="시간및사이즈" width="600"/> <br>

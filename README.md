# Editing
# Easy training program of Yolov5 Deep Sort with PyTorch
- This repository is folked from https://github.com/mikel-brostrom/Yolov5_DeepSort_Pytorch

### Prerequisites
- Already installed Docker

### How to use
- create environment (common step)
  - execute following script in command line
    ```
    # clone this repository
    git clone --recurse-submodules https://github.com/tmfi-analytics/Yolov5_DeepSort_Pytorch.git
    
    # build Docker container using Dockerfile
    cd Yolov5_DeepSort_Pytorch
    docker build -t [YOUR CONTAINER NAME] .
    ```

### 3 ways to use
  - Just execute human tracking demo
    - edit config.sh as following
      ```
      #!/bin/sh
      
      # YOLOV5実行時の設定を記載
      YOLOV5_BATCH_SIZE=8
      YOLOV5_EPOCHS=40
      YOLOV5_WEIGHTS=yolov5s.pt

      # 訓練済みのモデルで物体追跡をする場合はここを1に設定
      JUST_PREDICTION=1

      # YOLOV5の訓練に自前のデータセットを使用する場合はここを1に設定
      USE_CUSTOM_DATASET=0
      ```
    - execute docker run command
      ```
      cd Yolov5_DeepSort_Pytorch
      docker run -it --env-file=config.sh -v `pwd`/data:/app/data --shm-size=2048m [YOUR CONTAINER NAME] bash
      ```
    - watch the output video
      ```
      ls data/result
      ```


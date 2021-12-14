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
      
  - train the human detection model and track using prepared dataset
    - edit config.sh as following
      ```
      # 訓練済みのモデルで物体追跡をする場合はここを1に設定
      JUST_PREDICTION=0

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
      
      **The movies for train/val are downloaded by open image dataset v6**  
      https://storage.googleapis.com/openimages/web/index.html  
      **The movie for test is downloaded by following link**  
      https://www.motionelements.com/ja/stock-video-12530972-shopping-mall-in-japan?query_id=solr_40d80e54990840ae85da7fcfb8008d67&position=5
      
  - train the human detection model and track using custom dataset
    - put train and val dataset as following  
    　 <img width="110" alt="スクリーンショット 2021-12-14 23 36 52" src="https://user-images.githubusercontent.com/25993195/146018927-d881a2e5-8385-4730-a1d4-6d8567c79bcf.png">  
      **put image files in images directory and label files in labels directory.
        the pair of image file and label file must be same file name**  
      **please refer the following link about label format**  
        https://github.com/ultralytics/yolov5/wiki/Train-Custom-Data
    - put mp4 file for test as data/test/test.mp4
    - edit config.sh as following
      ```
      # 訓練済みのモデルで物体追跡をする場合はここを1に設定
      JUST_PREDICTION=0

      # YOLOV5の訓練に自前のデータセットを使用する場合はここを1に設定
      USE_CUSTOM_DATASET=1
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
      


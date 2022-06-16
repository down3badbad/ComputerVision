Light-Weight Facial Landmark Prediction Challenge
Read me (Group 22, Chibaku Tensei)

environment:
- 所需的套件如requirements.txt所寫，我們是使用python3.8.10來執行
- pip3 install -r requirements.txt

Handle dataset path:
- 我們會在B07901122的directory底下開一個叫dataset的directory
- 此directory會有兩個subdirectories： train_data/ 和 aflw_test/
- 請助教在處理dataset的時候注意：
  - 所有的test data (1790張)都會放在aflw_test/底下
  - train_data/這個directory底下會有兩個subdirectories: synthetics_train/ 和 aflw_val/
    - 所有的training data都會在synthetics_train/底下 (包括annot.pkl)
    - 所有的validation data都會在aflw_val/底下 (包括annot.pkl)

如果處理好dataset的話，最終的submission format會是如下：
B07901122/
|
+-- utils/
|   +-- train_tool.py
|   +-- testing.py
|   +-- test_tool.py
|   +-- model.py
|   +-- mobilenetv3.py
|   +-- download_data.py
|   +-- data_preprocess.py
|
+-- dataset/
|   +-- train_data/
|   |   +-- synthetics_train/
|   |   |    +-- annot.pkl
|   |   |   +-- 099999.jpg
|   |   |   +-- (all other training image...)
|   |
|   |   +-- aflw_val/
|   |   |   +-- annot.pkl
|   |   |   +-- image04358.jpg
|   |   |   +-- (all other validation image...)
|   |
|   +-- aflw_test/
|   |   +-- image04375.jpg
|   |   +-- (all other test image...)
|   |
|   +-- bestmodel/
|   |   +-- pretrained_model.pt
|   |   +-- (any other checkpoint, such as best_model.pt)
|
+-- cfg.py
|
+-- main.py
|
+-- requirements.txt
|
+-- readme.txt

reproducing our result:
1. training
- 在B07901122的directory底下執行"python3 main.py --mode training"，即可開始training的過程
- 當training完成後，程式會自動執行testing set的1790張image
- 最後會在bestmodel/best_model.pt生成最後的model parameter file
- 最後的solution.txt在B07901122/這個directory底下產生

2. testing
- 若想要跳過training的部分，直接使用我們附上的pretrained model (即為另外繳交的pretrained_model.pt)，
在B07901122的directory底下執行"python3 main.py --mode pretrained"
- 最後會在的solution.txt在B07901122/這個directory底下產生


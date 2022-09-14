## Darknet架構-超參數設置(yolov4)
* epoch：loss不往下降就行了，再下去會過擬和
* max-batches：classes * 2000 (最好至少4000，且不要少於訓練圖片數)
* steps：max_batches * 0.8 / max_batches * 0.9
* network size：width 與 height 為 32 的倍數 (預設為 416*416)
* filters：(1)每個[yolo]前的[convolutional]：filters = (classes + 5) * 3；(2)[Gaussian-yolo]：filters = (claseese + 9) * 3
* batch：每個 batch 學習採用多少的樣本資料 (64)
* subdivisions：在一個 batch 學習中，要拆成幾個 mini-batch (4.16.32.64，數字越大代表記憶體越小)

## 混淆矩陣(Confusion Matrix)
<img src=https://user-images.githubusercontent.com/46515944/190164532-77e9ebcb-bef8-49f7-9078-7e2190892872.png width=50% height=50% />

* Accuracy = (tp+tn)/ (tp+fp+tn+fn) 
* Precision = tp / (tp+fp)
* Recall = tp / (tp+fn)
* F1 = 2 * [(Precivion*Recall)/(Precivio+*Recall)]

## 衡量單位
| 單位縮寫|  英語全名 | 中文全名 | 意思 | 結論 |
| ---- | ---- | ---- | ---- | ---- |
| FLOPS | FLoating point Operations Per Second | 每秒浮點數運算 | 衡量速度 | 越大越好 |
| FLOPs | FLoating point Operations | 浮點數運算|指計算量 | 越小越好 |
| FPS | Frames Per Second | 每秒處理幀數 | 評價執行速度 | 越大越好 |

## 比較： Yolo vs. dlib
| 比較 | Yolo|  dlib | 
| ---- | ---- | ---- |
| 組態檔 | .cfg | X | 
| 標記檔 | .txt | .xml |
| 存放各種資訊 |.data | X | 
| 預訓練檔 | darknet53.conv4 | X |
| 標記工具 | Labelimg | Imglab |
| 輸出 | 權重檔 .weight | 特徵模型檔 .dat (SVM模型檔.svm)

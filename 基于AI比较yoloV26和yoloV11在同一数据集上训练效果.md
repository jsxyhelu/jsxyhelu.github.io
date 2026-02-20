# 基于AI比较yoloV26和yoloV11在同一数据集上训练效果

今天在modelscop中看到了yoloV26的相关消息，作为一名图像处理工程师，我在过往对yolo系列的还是非常情有独钟的，这里对同样的数据集做同样的实验，验证模型能力。

## 一、数据背景

采用开源的飞机数据集"mar20"：这个数据集不仅提供了正框(HBB)而且提供了倾斜框(OBB)的标注结果，方便同步开展实验。

## 二、正框实验

### 1. yolov11_mar20_hbb （正框 HBB）

主要结论：

大模型进行归纳：

This notebook demonstrates training a YOLOv11 object detection model on the mar20 dataset:

1. Environment Setup:
   a. GPU: Tesla T4 (16GB)
   b. Framework: Ultralytics YOLOv11
   c. Python: 3.10.14
   d. PyTorch: 2.4.02

2. Dataset:
   a. Name: mar20
   b. Classes: 20 (A1-A20)
   c. Training images: 24,90
   d. Total instances: 14,348
   e. Format: YOLO annotation format

3. Model Configuration:
   a. Model: YOLOv11s (Small version)
   b. Input size: 640x640
   c. Training epochs: 100 (interrupted at 95)
   d. Batch size: 8
   e. Multi-GPU: Enabled (GPU 0,1)

4. Training Results:
   a. Final mAP@0.5: 0.903 (90.3%)
   b. Final mAP@0.5: 0.95 (70.8%)
   c. Precision: 0.871
   d. Recall: 0.875

5. Data Augmentation:
   a. Mosaic augmentation (disabled after epoch 90)
   b. Albumentations: Blur, MedianBlur, ToGray, CLAHE

### 2. yolov26-mar20_obb

这里尝试，基于trae+GLM4.7直接生成结果。这里我指明了需要参考的对象，并且生成了思维步骤。这里应该是得益于yolo系列在命令操作上的统一性，所以没有遇到太大的问题。生成的结果同样上传大模型预估的结果：

【这里从数据结果上，并没有增量】

## 三、倾斜框实验

为什么我要区分两个实验了，是因为我想把第2部分修改的过程，保存为一个skill，让第3部分直接来抄。

1. yolov11_mar20_obb (倾斜框）
2. yolov26-mar20_obb

采用的方法就是直接评估后形成skill，然后直接复制思路。

大模型给的判断是：

生成结果：

## 四、初步小结

①目前直接kaggle命令行上传还有格式问题，还需要手动上传，这个需要进一步研究；

②首先给我的启发，就是如果可以基于OpenClaw把这个过程自动化，那么是否可以提高解决Kaggle题目的效率？因为很多时候，解题的思路都可以从别人那里学到，而且对于Kaggle的这样比赛而言，它是有边界的；

③其次给我联想的，就是GLM4.7这样的大规模模型在解决前面的一些问题中效果很好，但是如果我只有上一个阶段的模型，那么是否仍然可以复用一些思路想法；

④最后，yolo仍然在持续的发展。那么在这个AI技术发展非常迅速的今天，我们是否能够拿出新的使用方法？无论何时，算力、能够拿到手里的算力都是开展下一步创造的基础，而这需要长期规划准备，这一点毋庸置疑。

---

**原文链接**：https://www.modelscope.cn/learn/5632

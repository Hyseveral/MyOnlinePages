# 阅读笔记
# Gate-Shift Networks for Video Action Recognition

## Abstract

- 深度3D卷积网络是为了同时学习视频中的时空特征，但是由于存在大量的参数，所以实际运用中不 使用大量的数据集训练的话，效果不理想。
- 本论文 在3D kernels的时空特征分解中 引入了空间控制(spatial gating)。通过GSM(Gate-shift Module) 门转换模块实现这个概念。
- GSM是轻量级的，它将一个2DCNN变成了一个高效的时空特征提取器。
- 插入GSM后，2D-CNN学会了通过时间自适应地路由特征并将它们结合起来，几乎不需要额外的参数和计算开销。







## 5. Conclusion
- 我们提出了一种新的时间交互模块——门转换模块(GSM)，它将2D-CNN变成了一个高度高效的时空特征提取器。
- GSM引入了空间门控来决定是否与相邻帧交换信息。
- 实验结果中，在Something SomethingV1和Diving48数据集上获得了最先进(state-of-the-art)的效果。同时在 EPIC-Kitchens 上也获得了有竞争力的的效果。然而，模型的复杂性小了很多。

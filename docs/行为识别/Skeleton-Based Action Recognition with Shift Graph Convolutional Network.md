
# 论文阅读笔记

# Skeleton-Based Action Recognition with Shift Graph Convolutional Network


## Abstract
- 图卷积网络(GCNs) 将将人体骨骼作为时空图形进行建模，取得了显著的效果。
- 但是基于GCN-based的方法的计算复杂度相当大，一个动作示例通常超过15 GFLOPs. 最近的一些甚至达到了 ~ 100 GFLOPs。

- 另一个缺点是空间图和时间图的感受野都不灵活。
- 虽然有些 方法使用引入空间自适应模块来 增强空间图的可表达性。

- 本文中，我们提出了一种新的移位图卷积网络(shift - gcn)来克服这两个缺点。
- 该方法由 新的位移图操作(novel shift graph operations) 和轻量级的 逐点卷积(lightweght point-wise convolution)组成。
- 移位图操作 为空间图和时间图 提供了灵活的感受野。

- 在基于骨架的动作识别的三个数据集上，我们提出的 shift-GCN 超过了目前最好的方法，并且计算复杂度小了10倍。





## 5. Conclusion
- 本文中提出了一个 新的 shift-图卷积网络，用于 基于骨架特征的动作识别。
- 它是由 空间位移图卷积(spatial shift graph convolusion) 和时间位移图卷积(temporal shift graph convolusion)组成。
- 该 非局部的空间位移图卷积明显优于 常规的图卷积网络，并且使用更少的计算成本。
- 我们的 自适应时移图卷积 可以 自适应地调整感受野，并且具有很高的效率。
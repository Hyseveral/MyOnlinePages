# 阅读笔记
# Disentangling and Unifying Graph Convolutions for Skeleton-Based Action Recognition


## Abstract
- 时空图 广泛的用在基于骨架的动作识别算法中，用来对人的动作行为进行建模。
- 为了从这些图中获取鲁棒的运动模式，长范围(long-range)和多尺度上下文聚合(multi-scale context aggregation)还有时空相关性建模 是一个好的特征提取器的关键所在。
- 但是，现存的方法存在一些局限性。

- 本文中，提出了一个简单的方法用来 解开多尺度的图卷积(disentangle multi-scale graph convolutions), 然后提出了一个统一的时空图卷积操作，命名为G3D。

- 我们提出的多尺度的聚集方案 阐明了不同邻域节点对有效的 long-range建模的重要性。
- G3D模块利用密集的跨时空边 作为跳跃连接，以便在时空图中直接传播信息。

- 基于以上内容，开发了一个 强大的特征提取器 MS-G3D。在此基础上，我们的模型在三个大规模数据集上达到了目前最优的效果（NTU RGB+D 60,
NTU RGB+D 120, and Kinetics Skeleton 400）。





## 5.Conclusion
- 我们提出了两个 基于骨架的动作识别的 改进方法。
- 一种用于图卷积的解纠缠多尺度聚合方案，消除了不同邻域之间的冗余依赖关系。
- 二是一个统一的时空图卷积算子，可以直接从骨架图序列 对时空相关性 进行建模。

- 通过这些方法，得到了MS-G3D，即一个强大的特征提取器，用来捕获 之前被 被分解的模型所忽略的 多尺度的时空特征。
- 实验表明，在三个大数据集上 相比现有的方法有很大的优势。
# 论文阅读笔记

# GFNET: A LIGHTWEIGHT GROUP FRAME NETWORK FOR EFFICIENT HUMAN ACTION RECOGNITION


## Abstruct
- 最近的一些 two-stream 和C3D方法 达到了很高的识别精度，但是 是以巨大的计算复杂度、内存占用和参数 为代价。
- 本文中，提出了一种轻量级的 神经网络————群框架网络（Group Frame Network）GFNet，通过一种简单有效的方法 在空间维度上 强加帧内的空间稀疏信息。
- 受益于两个核心部件，Group Temporal Module (GTM) and Group Spatial Module (GSM), 即组空间模块和组时间模块。
- GFNet减少了帧内的不相关运动和帧间的重复纹理特征，可以以极低的代价提取帧的时空信息。

- 在NTU RGB+D数据集和Varying-view RGB-D动作数据集上的实验结果表明，我们的方法在不需要任何预训练策略的情况下，在计算复杂度、参数和性能之间取得了合理的平衡，比现有的方法具有更高的性价比。



## 4. Conclusion
- 本文中，提出了一个轻量级的 Group Fame Network(GFNet)。 
- 该方法主要由连个组件构成：GTM 和 GSM。
- GTM的设计目的是提供时间信息和提高帧间相关性。
- GSM获得不同的帧内信息，同时利用 图像空间冗余 来减少参数的数量。
- 通过这两个模块，GFNet 可以减少 帧间的无关信息。
- 实验结果表明：GFNet不仅实现了准确的识别结果，而且减轻了资源利用的负担.
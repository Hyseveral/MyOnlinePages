# 论文阅读笔记

# Something-Else: Compositional Action Recognition with Spatial-Temporal Interaction Networks

## Abstract

- 在本文中，我们通过观察 主体-客体 相互作用的 动力学来研究 行为的组合性。
- 我们提出了一个新的模型可以明确地 推理构成对象 和执行动作 的主体之间的几何关系。
- 为了训练该模型，我们再 something-something 数据集上手机了密集的对象框注释。
- 我们提出了一个新的组合动作识别任务，其中动词和名词的组合训练不与测试集重叠。

- 我们的模型 适用于 具有适用于具有突出的对象交互动力学的活动(prominent object interaction dynamics), 以及可以用最先进的方法追踪的物体.

- 对于没有明确定义空间 object-agent 交互的活动,我们依赖于baseline 场景级(scene-level)的时空特征(spatio-temporal)表示.

- 我们的方法不仅适用于提出的组合动作识别任务，而且适用于较少拍摄的组合场景(a few-shot compositional setting)，这需要模型对物体的外观和动作进行概括.


## 6. Conclusion
- 受当前动作识别模型中 的外表偏差(appearance bias) 所影响，我们提出了一种 基于稀疏语义基础的 主体-客体对象图表示的动作识别模型。
- 我们在SomethingElse数据集中 验证了我们的 新的组合和少数镜头设置(novel compositional and few shot settings)的方法。
- 我们的模型是用 新的组成对象 接地标注训练的，我们的STIN方法 建模了一个动作中组成的对象的交互动力学，并且优于所有的基线。

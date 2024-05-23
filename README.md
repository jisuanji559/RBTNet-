# 景点便民设施RBTNet冗余检测
## 1 背景介绍
由于部分便民设施属于后天改建或扩建，且相关地区旅游业的落后，导致景区地图中便民设施位置无法及时更新，再加上大部分游客并不熟悉景点中的便民设施，导致游客无法享受便民设施带来的便利，而现存对旅游景点便民设施进行标注的技术仍有很大不足。目前主流的旅游景点便民设施标注方式是群智协同标注，群智协同标注主要是通过个人上传旅游景点便民设施的位置信息、图像信息和文字描述信息等，进行旅游景点便民设施的标注。但由于地理定位精度不足、人群密度分布不均衡等因素的影响，旅游景点便民设施标注的数据存在冗余问题，即多人对同一旅游景点便民设施进行标注，影响标注数据集的质量。

故针对上述问题，本项目拟采用以Transformer、Bert、ResNet-152为主干网络的RBTNET模型对旅游景点便民设施标注的多模态数据进行分析，更好地捕获位置、图片和文本中所蕴含的信息，对目前旅游景点便民设施标注中存在的冗余标注进行检测，去除其中冗余标注的信息，对现有的旅游景点便民设施标注信息进行优化，提高旅游景点便民设施标注信息的质量。并根据优化后的数据制作**旅游景点便民设施地图平台**方便游客的出行，提高旅游服务的便利度，以科技创新提升旅游业的发展水平。
## 2 相关工作
### 2.1冗余标注检测
冗余标注是指：由于手工标注的过程中可能出现多人对同一旅游景点设备进行标注或者用于标注设备的精度不足而造成冗余标注。同时在旅游景点便民设施群智协同标注的过程中，受到地理定位精度不足、人群密度分布不均衡等因素的影响，而形成的冗余标注，影响了标注的效率和质量。而冗余标注检测就是检测出这些影响标注效率和质量的数据。
### 2.2基于Transformer的表征学习
基于深度学习的地图匹配模型相当于构建了一个用于序列到序列学习的模型，这个模型最初被用于机器翻译这个任务中。在Graves等人的研究中，提出了递归神经网络这种可以处理序列的输入并且有选择地在顺序阶段传递信息的网络结构也成为编码器-解码器结构。然而这种结构往往会受到长依赖性的影响。

在2017年，谷歌团队的Vaswan等人引入了Transformer模型用于解决受到长依赖性的问题。Transformer中的完全依赖注意力机制用于获取输入和输出之间的全局依赖关系。相比于递归神经网络，Transformer不仅可以预防循环神经网络中存在的梯度消失的问题，而且能高度训练并行，减少了长句子中丢失重要信息的风险，在一定程度上解决了长依赖性的问题。
### 2.3基于Bert文字特征学习
在自然语言处理领域，预训练模型一直是一个难点。Turian提出了预先训练词嵌入模式，从而打开了自然语言处理领域预训练的大门，从此以后又有Mnih等人提出的从左到右的语言建模目标，以及左右语境中区分正确或者错位的单词目标(Mikolov)。Vaswan提出Transformer之后，Devlin受到启发提出了一种名为Bert的预训练模型。

Bert首先通过在所有层中联合调节左右上下文，从未标记文本中预训练深度双向表示，然后增加一个输出层，对预训练的Bert模型进行微调，从而应用于问答和语言推理等下游任务，而无需对特定于任务的架构进行修改。Bert在机器阅读理解顶级水平测试SQuAD1.1中表现出惊人的成绩:全部两个衡量指标上全面超越人类，并且在11种不同NLP测试中表现十分亮眼，从此Bert成为了自然语言处理领域的里程碑式的模型成就。
### 2.4残差网络
在计算机视觉中，深度CNN网络达到一定深度后会面临着深度神经网络“退化”的问题,即深度CNN在达到一定深度后，再一味地增加层数并不能带来进一步的分类性能的提高，反而会招致网络收敛速度变得更慢，并且测试级的分类准确率也会变得更差。针对这个问题，Razavian等人提出了ResNet网络这一概念，该框架能够简化那些非常深的网络的训练，使得层能根据其输入来 学习残差函数而非原始函数，这样的残差网络的优化更简单，而且能由更深的层来获得更高的准确率。因为这种残差结构可以优化梯度退化的问题，ResNet网络目前常被用于目标识别(Xu)，图片分类等领域。
## 3 前端效果图
首页
![Uploading image.png…]()



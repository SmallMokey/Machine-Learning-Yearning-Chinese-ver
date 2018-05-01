## 15. 在误差分析中并行评估多个想法

你的团队有几个改进猫检测器的想法。

- 修正算法中将狗识别为猫的问题；
- 修正算法中将大型猫科动物(Great Cat)（狮子，豹）识别为家猫的问题；
- 提升系统在模糊图像(Blurry Images)上的性能表现。
- ……

你可以同时有效地评估所有的这些想法。我通常会列一张表，并在开发集上检查错误分类的100张图像的时候填写它。我同时也会写下可能帮助我分析具体例子的备注。为了说明这个过程。我们来看下面的一张表，它是一个由四个样本组成的小开发集：

图片(Image)|狗(Dog)|大型猫科动物(Great Cat)|模糊图像(Blurry)|备注(Comments)
---|---|---|---|---
1|√|||不寻常颜色的斗牛犬
2|||√|
3||√|√|狮子；照片是在雨天的动物园拍摄
4||√||豹子在树后面
占总数百分比|25%|50%|50%|

在上表中，图片3在“Great Cat”和“Blurry”两列都被勾选了。一个示例可能与多个类别关联，所以底部的百分比总值并不一定等于100%。

尽管你可能会制定一些类别（狗，大型猫科动物，模糊图像等等），然后将开发集的误分类图像进行归类，但在实践中，一旦你开始浏览这些样本，你可能会受到启发，发现其他的错误类别。比如在浏览了一些样例之后，你发现许多图片分类错误是因为Instagram的滤镜造成的，你可以回到表格中，添加“Instagram”列。手动查看算法错误分类的示例，并思考“如果是人的话，能否/如何正确标记图片”，通常这能激发你提出新的错误类别和解决方案。

你有办法去改进的错误类别才是最有帮助的错误类别。例如，如果你有“撤销Instagram滤镜并将其恢复为原始图像”的好办法的话，那么添加Instagram类别则是最有用的。不过，你不必局限在那些你知道如何去改进的错误类别上。这个过程的目的是建立你最希望关注的领域的直觉。

误差分析是一个迭代的过程。如果你开始没有想到任何的错误类别也不用担心。看过几组图片之后，你可能就能想出一些错误类别了。在对一些图片进行手动分类之后，你可能考虑到一些新的类别，此时就要根据新的类别对图片重新检查。

假设你完成了对开发集上那100张误分类图片的分类，并得到下列的结果：

图片(Image)|狗(Dog)|大型猫科动物(Great Cat)|模糊图像(Blurry)|备注(Comments)
---|---|---|---|---
1|√|||不寻常颜色的斗牛犬
2|||√|
3||√|√|狮子；照片是在雨天的动物园拍摄
4||√||豹子在树后面
……|……|……|……|……
占总数百分比|8%|43%|61%|

从上表你发现，处理分类为狗的这个问题最多只能消除8%的错误。而处理“Great Cat”和“Blurry”的问题却可以消除更多错误。因此，你可以挑选后两个之一来继续努力。当然，如果你的团队人手足够，也可以并行地同时开展多个方向的工作，你可以分派一些工程师负责“Great Cat”方向，分派另一些在“Blurry”方向。

“误差分析”不会产生一个严格的数学公式来告诉你最优先的任务是什么。你还必须考虑你想在不同的错误类别上取得多少的进展，以及处理每个类别所需要的工作量。
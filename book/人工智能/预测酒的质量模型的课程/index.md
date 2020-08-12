# Python机器学习教程,Scikit-Learn: 构建预测酒的质量模型

## 大体内容：
  搭建环境、导入相关工具包，然后加载数据、拆分数据、对数据预处理(转换、缩放、包装等)、

## 完成该课程的必备技能
1.吸收了大量理论
2.有一定的Python编程功底

## 该课程中构建随机森林模型的步骤

1.搭建环境。
  必须安装下面的包：
    Python 2.7+：基础运行平台
    NumPy：为数值计算提供支持
    Pandas：支持数据框架的库

    Scikit-Learn：机器学习中一个广泛使用的开源框架，需要前面两个包的支持。其提供了分类，回归，聚类，数据降维，模型选择和数据预处理六大功能。

  注：可以通过Anaconda安装，其包含上面所有的包。

2.导入相应的库和模块.
  numpy：计算
  pandas：数据框架

  sklearn.model_selection的train_test_split: 拆分训练数据和测试数据
  sklearn的preprocessing：预处理数据，对数据进行缩放、转换和包装

  sklearn.ensemble：算法
  sklearn.pipeline：十字交叉验证
  sklearn.metrics: 评估方模式
  sklearn.externals：留存模型

3.加载红酒数据。
4.把数据拆分成训练数据和测试数据。
5.确定数据预处理步骤.
 标准化：从每一个特征里面扣除一部分，然后通过特征的偏差进行划分。
  一般经验：许多算法假设所有特征以0为中小，几乎有相同的方差。

6.确定优化调整的超参数.

7.用十字交叉验证方法调整优化模型
8.在完整的训练数据集中修正.
9.在测试数据上评估哪种模型可靠。

10.为更广泛的应用保存模型。



详情：
  https://elitedatascience.com/python-machine-learning-tutorial-scikit-learn
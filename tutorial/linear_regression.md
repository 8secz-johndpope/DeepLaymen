# 线性回归（Linear Regression）

机器学习（尤其是监督学习），主要围绕[分类](https://github.com/kebiao/deeplearning/blob/master/tutorial/logistics_regression.md)和回归两类问题展开，而线性回归模型作为最简单的回归模型，与大多数监督学习算法具有相同的建模思路，包括建立损失函数、优化参数、模型评估。

### 什么是线性回归：

线性回归输出是一个连续值，因此线性回归适合如预测房屋价格、气温、销售额等连续值的回归问题。
分类问题则不同，输出是一个离散值，适合用来例如做：物体分类、疾病检测等。

一个简单的小例子：

    import numpy as np
    from numpy import random
    import matplotlib.pyplot as plt

    # 随机生成在[0,30]区间内服从均匀分布的100个数
    X = random.uniform(0, 30, 100)

    # 对X乘以固定系数后加上随机扰动
    y = 1.85 * X + random.normal(2, 5, 100)

    plt.scatter(X, y)
    plt.xlabel('X')
    plt.ylabel('y')
    plt.show()

输出结果：

<p align="center">
  <img src="https://github.com/kebiao/deeplearning/blob/master/screenshots/tutorial/linear_regression_1.png">
</p>

**以上代码随机生成一组样本X和y，现在给定一组X值，需要预测其对应的y值。**


解决这个问题的思路如下：

- 假设X和y之间存在线性关系，即***y = w ∗ X + b***
- ***ŷ = wX + b***，其中***ŷ***表示根据线性方程计算得到的***y***值（称为估计值），为尽可能准确的表达样本中***X***和***y***之间的关系，我们需要找到最优的***w∗***和***b∗***，使得***y***的实际值和估计值之间的误差|***y*** − ***ŷ***|最小化。


**以上问题中X称为自变量，y称为因变量，找到最优直线方程y = w∗X + b∗，使得因变量的估计值与实际值之间的误差最小的过程，称为线性回归。**
### 获取数组中最大的前N个数字
```python
import numpy as np
数组 = np.random.randint(1, 100, 10)

# 数组.argsort()会返回排序后的下标
# 取最大值对应的三个下标，因为默认升序，所以要用【-3:】表示倒数第三到最后一个
下表 = 数组.argsort()[-3:]
最大 = 数组【下标】
print(f'最大的三个数是{最大}')
```

### random
- rand 返回[0,1]之间， 从均匀分布中抽取样本
- randn 返回标准正态分布随机数(浮点数)平均数0， 方差1
- randint 返回随机整数： 随机1至20之间取24个元素组成三维数组
```python
np.random.randint(1,20,size=(2,3,4))
```
- random 生成0.0至1.0的随机数
- normal 生成正态分布数字： np.random.normal(1,10,10) # 平均值1，方差10， 10个数
```
高斯分布重要量的性质
1. 密度函数关于平均值对称
2. 平均值是它的众数(statistical mode)以及中位数(median)
3. 函数曲线下68.268949%的面积在平均值左右的一个标准差范围内
4. 95.449974%的面积在平均值左右两个标准差的范围内
5. 99.730020%的面积在平均值左右三个标准差的范围内
其中第3-5条称为68-95-99.7法则
```
- uniform 均匀分布 ： np.random.uniform(1,10,10) # 在1到10之间生成10个随机数
- choice 从一维数组中生成随机数
```python
np.random.choice(第一参数，第二参数）
# 第一参数是一个1维数组，如果只有一个数字那就看成range(5)
# 第二参数是维度和元素个数
```
- shuffle(数组) 把一个数进行随机排列，多维数组的情况只按最高维度随机，其他不变
- permutation(数组) 把一个数组随机排列或者数字全排列: 和shuffle一样，但**原来数组不发生改变**
```python
排列 = np.random.permutation(10) # 这里的10就看成是range(10)
```

### 数据标准化
- 对于机器学习、神经网络来说，不同列的量纲是相同的，收敛更快。
- 有两个特征，一个是商品单价1元至50元，另一个是销售数量3千个至一万个，这两个数字不可比，所以需要都做标准化。
- 比如在Excel里，单价一个列，销售数量一个列，不同列代表不同特征，所以用axis=0做计算
- 标准化一般使用： 通过均值和方差实现
  - 数组 = (数组- mean(数组, axis=0)) / std(数组,axis=0)


# 机器学习
## 机器学习的误区
- 很强的数学背景, 他认为有一定门槛, 但并没有想象中但那么恐怖
    - 一些看到的公式比较复杂, 但我们常用但就那几套
- AI算法很深奥
    - 对于不熟悉的领域我们望而却步, 但是实际了解一下会发现没有那么夸张
- 作为程序员, 以后不打算转型算法工程师, 所以不需要懂AI
    - 可能未来参与AI开发的主流人群将会是开发工程师
    - 随着数据量的加大, 一些AI算法开始融入公司的项目中
    - 随着一些工具的出现, AI开发的门槛变得很低
- 学好AI不难
    - 想学的很精通是很难的
    - 入门比较简单, 做使用者是容易的, 想做研发者是需要大量付出的

## 什么是人工智能
- AI is the field that studies the synthesis and analysis of computational agents that act intelligently.
- AI are systems that ...
    - Think like humans
    - Act like humans
    - Think rationally
    - Act rationally

## 限制领域AI和通用AI
- 限制领域AI (Narrow AI)
    - 限定某一个特定的领域, 然后去解决该领域的问题
    - 电商推荐系统, 医疗智能问答
- 通用AI (General AI)
    - 让AI做任何事情
    - 现在做不到, 这是未来的方向

## 人工智能AI和商业智能BI
- BI更多提供数据的支撑, 由人来做决策
- AI会包含决策部分


- 我们所有人都可以使用简单的AI工具来提示工作效率, AI算法工程师参与AI的开发和推荐, 更高层的研究员科学家做模型改造或创造

## 什么是机器学习
- Field of study that gives computers the ability to learn without being explicitly programmed.
- 从数据中自动学出规律
    - 训练数据, 打label
    - 比如给一些训练数据是苹果和香蕉的图片, 打上相应的label, 训练出一个系统, 传给它一个图片, 计算出是苹果的概率是多少, 是香蕉的概率是多少, 给出一个分类结果

## 什么是深度学习
- Deep Learning is a subfield of machine learning concerned with algorithms inspired by the structure and function of the brain called artificial neural networks.
- 机器学习的一种
- 借鉴人脑的神经网络

- 浅层模型vs.深度学习模型
    - 深度学习不是特指某一类模型, 是一种框架/方法论, 是对浅层模型的纵向叠加

## 人工智能vs.机器学习vs.深度学习
人工智能是目标, 机器学习是方法, 深度学习是发展较好的方法的一种

## 常用的工具
- mapplotlib, 可视化
- NumPy, 
- Pandas, 提供数据处理的便捷性

- scikit learn
- spark MLlib, 分布式环境
- 深度学习的框架
    - PyTorch, 最近几年发展的很快, 上手难度低一点
    - Keras, 
    - TensorFlow, 上手门槛比较高, 谷歌维护

## 深度学习的常见模型
- 深度神经网络 Deep Neural Networks
- 卷积神经网络 Convolutional Neural Networks
- 循环神经网络 Recurrent Neural Networks
- 递归神经网络 Recursive Neural Networks
- 生成式对抗网络 Generative Adversarial Networks, GAN
    - 让AI画画, 

## 监督学习vs.无监督学习
- 监督学习
    - D = (X, y), 数据中包含label y, 学习x->y的关系
- 无监督学习
    - D = (X), 寻找X中的特征或规律
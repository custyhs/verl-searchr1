1. 把retriever开在不同服务器
2. 用bm25的retriever
3. 只训练前一些token：
    3.1. format规定训练的部分<plan> </plan>
        训练部分的reward的修改
    3.2. 更粗暴一点：250个token


修改Format部分，加入一个制定计划的要求，比如：
    Please fitst make a plan for answering the question inside <plan> </plan> tags.

计算loss的时候，mask只保留<plan> </plan> 之前的token, 参考怎么mask工具返回的部分。


--------- 6.15 ---------

1. 实现
   1. response_mask添加plan_mask
   2. system prompt修改
2. 问题
   1. format reward没定义？
   2. 直接改掉response_mask会不会有问题
3. 想法
   1. 直接训练这个针对plan的优化算法，结果会如何？
   2. 猜想：plan起很大作用？
OWL 在 
      1. 相同计算资源，模型只训练plan比全训练效果更好
      2. 小模型训练plan用大模型rollout效果比单纯用大模型rollout效果好
      3. 制定plan很重要的数据集？
      4. prefix-tuning with reinforment learning
4. 接下来要做什么
   1. 跑起来

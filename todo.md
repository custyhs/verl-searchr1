1. 把retriever开在不同服务器
2. 用bm25的retriever
3. 只训练前一些token：
    3.1. format规定训练的部分<plan> </plan>
        训练部分的reward的修改
    3.2. 更粗暴一点：250个token


修改Format部分，加入一个制定计划的要求，比如：
    Please fitst make a plan for answering the question inside <plan> </plan> tags.

计算loss的时候，mask只保留<plan> </plan> 之前的token, 参考怎么mask工具返回的部分。

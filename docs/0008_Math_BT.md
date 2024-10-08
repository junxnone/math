---
Title | Math BT
-- | --
Created @ | `2020-07-14T06:08:46Z`
Updated @| `2024-09-16T17:28:30Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/8)

---
# 贝叶斯定理


- **先验/Prior** - 原因 ==> 结果, 事情发生之前, 根据以往经验和分析得到的
  - **先验概率/Prior Probability**
    - `e.g. 抛硬币正面向上的概率`
  - **先验分布/Prior Distribution** - 已知结果, 估计分布
- **后验/Posterior** - 结果 ==> 原因 事情发生, 在相关结果或者背景给定并纳入考虑之后的
  - **后验概率/Posterior Probability**
  - **后验分布/Posterior Distribution** - 已知历史, 估计分布
- **似然估计/Likelihood ** - 已知原因, 估计分布

Name | Details
-- | --
贝叶斯推断 | ![image](https://user-images.githubusercontent.com/2216970/112805871-be819180-90a8-11eb-92ba-bf688842fd79.png)
x |  结果 - 观察得到的数据
θ | 原因 - 决定数据分布的参数
后验/Posterior | ![image](https://user-images.githubusercontent.com/2216970/112806034-ec66d600-90a8-11eb-8fd0-3353767d2923.png)
先验/Prior | ![image](https://user-images.githubusercontent.com/2216970/112806042-eec93000-90a8-11eb-8664-a374e26fd27f.png)
似然估计/Likelihood | ![image](https://user-images.githubusercontent.com/2216970/112806053-f1c42080-90a8-11eb-8a9e-c1eeb4af4512.png)
证据因子/边缘似然/Evidence | ![image](https://user-images.githubusercontent.com/2216970/112806058-f4267a80-90a8-11eb-857c-e9113cec67c4.png)

## 贝叶斯公式

推理 | 
-- | 
![image](https://user-images.githubusercontent.com/2216970/87391783-f362bc80-c5dd-11ea-9e27-f33ccbab2125.png)
![image](https://user-images.githubusercontent.com/2216970/87391784-f65dad00-c5dd-11ea-91ac-0b4b5d0506fd.png)


- P(A|B) - 事件 B 发生后 A 发生的概率 - 条件概率 - 后验概率
- P(B|A) - 事件 A 发生后 B 发生的概率
- P(A) / P(B) - A/B 发生的概率 - 先验概率


## Reference
- [一个例子搞清楚（先验分布/后验分布/似然估计）](https://blog.csdn.net/qq_23947237/article/details/78265026)
- [贝叶斯定理](https://blog.csdn.net/qq_41529692/article/details/84105315)





---
Title | Math SA
-- | --
Created @ | `2021-03-30T08:34:59Z`
Updated @| `2024-09-16T17:27:38Z`
Labels | ``
Edit @| [here](https://github.com/junxnone/math/issues/14)

---
# Simulated annealing 模拟退火


## Hill climbing

- 爬山算法是一种简单的贪心搜索算法，该算法每次从当前解的临近解空间中选择一个最优解作为当前解,直到达到一个局部最优解
- 如图， 有局部最优解 B/E, 如果初始点在 A - G之前的谷底，则只可能达到局部最优点 B/E

![image](https://user-images.githubusercontent.com/2216970/216500266-5a38f235-cae3-4040-a054-6431ecef705c.png)

## Simulated Annealing

- SA - Simulated annealing -  来源于固体退火原理
- `Hill Climbing` + `Random Walk`
- 搜索过程中以一定概率接受比当前解较差的解，以跳出局部最优
  - 概率随着时间推移逐渐降低

自然界退火 | ![image](https://user-images.githubusercontent.com/2216970/112960271-d45d8800-9176-11eb-98fb-4d0f7cd3d505.png)
-- | --

> 将固体加温至充分高，再让其徐徐冷却（退火），加温时，固体内部粒子随温升变为无序状，内能增大，而徐徐冷却时粒子渐趋有序，在每个温度都达到平衡态，最后在常温时达到基态，内能减为最小


![image](https://user-images.githubusercontent.com/2216970/112960664-35855b80-9177-11eb-8885-4764e5f97145.png)

![image](https://user-images.githubusercontent.com/2216970/112964300-c90c5b80-917a-11eb-95b6-aa6262a74da0.png)

## UseCase



## Reference
- [模拟退火算法](https://ustccoder.github.io/2019/05/20/optimization_SA/)
- [模拟退火算法 Simulated Annealing](https://www.jianshu.com/p/57678cfe8553)
- [SA - 数独- Visualizer](https://jeremypflipsen.github.io/Sudoku-Visualizer/#0)
- [SA - demo](http://aimacode.github.io/aima-javascript/4-Beyond-Classical-Search/)
- [SA - 路径规划 demo](https://harmonc.github.io/sketches/simulated_annealing/index.html)


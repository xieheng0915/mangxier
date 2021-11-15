##### OLS Regression Model OLS回归模型
OLS的 linregress(线性回归) func输出项： slope, intercept, P-value, R-value, std-err, intercept stderr

- slope: 线性回归直线的斜率
- intercept: 线性回归直线的截距
- P value: P越小越好，表示假设可信，P代表发生事件A和A相反事件的比例，如果P过大，可能是样本不够，或者样本参考意义不足（假设可能错了）P代表贝叶斯的条件概率
- R value: R 相关系数
- R value ^2: R^2
  __小的P值/高的R2的组合表明预测量的变化和因变量的变化有关，并且您的模型解释了一些反应变异性。__  
  
- std-err: 预测的斜率的标准差
- intercept std-err: 预测的截距的标准差



- ref:
  + [线性回归分析中的P值是什么，P值太高如何解决](https://www.zhihu.com/question/391345581)
  + [Python Statsmodels 统计包之 OLS 回归](https://zhuanlan.zhihu.com/p/22692029)
  + [机器学习初步（简书）](https://www.jianshu.com/p/b53d654bf264)
  + [python统计函数库scipy.stats的用法解析](https://www.jb51.net/article/181315.htm)
  + [scipy.stats的用法——常见的分布和函数](https://www.cxyzjd.com/article/baby_superman/83749803) 
  + [理解概率密度函数](https://zhuanlan.zhihu.com/p/48140593)
  + [如何解释R2低值和P值较小的回归模型](https://zhuanlan.zhihu.com/p/37940501)
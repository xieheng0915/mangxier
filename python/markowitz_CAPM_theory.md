- MPT(Modern Portfolio Theory), 又称为 Markowitz portfolio theory,
着重于风险和回报的计算, portfolio voladility vs. Portfolio return
Portfolio Voladility: standard variation ^ 2

  - 下图为P&G和标普指数的MPT图
    + ![P&G和标普指数的MPT图](resource/MPT_sample.jpg)

- CAPM：Capital Asset Price Model 
  如下MPT图的切线为CAPM线，截距为risk-free return 
    + ![CAPM 和 MPT图的关系](resource/MPT&CAPM.jpg)
  CAPM 假定有risk-free 的资产存在（通常债券可以认为是risk free)
  从MPT图可以得出，风险越高回报越高，风险越底回报越低。
    + 当把某只股票和市场指数比较（比如S&P指数）Beta值表示了该股票和市场表现的关系。
    如下所示，
    + ![Beta 值的意义](resource/beta-meaning.jpg)
    + ![Beta 计算公式](resource/beta-formula.jpg)
  
  - Beta值的计算：
    + ![Beta formula](resource/beta_value.jpg)
    
  - CAPM计算公式：
      + ![CAPM return formula](resource/CAPM_return_value.jpg)
      + ![CAPM key parameter](resource/CAPM_key_para.jpg)
    - python程序的beta计算：
      + ![Python实现Beta和CAPMreturn](resource/Beta-CAPM-formula.jpg)

- Sharp Ratio： 用以评估回报和风险的比例
  - Sharp Ratio 的定义
    - 回报率越高，sharp ratio 值越大， 风险越高， sharp ratio 值越小
      + ![Sharp Ratio definition](resource/sharpRatio.jpg)
      + ![calculate sharp ratio](resource/sharpRatio_calc_python.jpg)  

- α值：   
  描述的是没有风险情况下的收益，通常α=1%是基金经理的投资基数，如果低于1%则基金无盈利，  
  α<0 的情况下投资收益较差
  ![α计算公式](resource/alpha-formula.jpg)

- Ref：
  - [多因子系列篇一 (上) -- 现代组合理论 (Modern Portfolio Theory)](https://zhuanlan.zhihu.com/p/82743646)
- 参考书：
  - 《主动投资组合管理》 
  - 《量化股票组合管理》
  - 参考公式
   ![Math formular of cov, var](resource/math_formula.jpg)
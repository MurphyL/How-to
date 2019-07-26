```
description: JUnit单元测试
```

> 单元测试中不准使用 System.out 来进行人肉验证，必须使用 assert 来验证。

单元测试必须遵守 `AIR` 原则。

- A：Automatic（自动化）
- I：Independent（独立性）
- R：Repeatable（可重复）

编写单元测试代码遵守 `BCDE` 原则，以保证被测试模块的交付质量。

- B：Border，边界值测试，包括循环边界、特殊取值、特殊时间点、数据顺序等。
- C：Correct，正确的输入，并得到预期的结果。
- D：Design，与设计文档相结合，来编写单元测试。
- E：Error，强制错误信息输入（如：非法数据、异常流程、非业务允许输入等），并得到预期的结果。


> 参考文档：《[阿里巴巴编码规范（JAVA）](https://edu.aliyun.com/course/417?spm=5176.165441.858711.1.449545f9xNGbsA)》
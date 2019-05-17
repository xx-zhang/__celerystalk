## 2019-5-17 

> 今天上午接触到这个开源的扫描工具; 觉得已经写了这么多非常有思想，
所以在这个基础上准备集成下自己的一些想法来继续完善。
**主要是提升到python3的版本并且修改数据库为其他的sqlachemy可以支持的**


### 当前修改部分
- 所有的python2 的 `exception,e` 修改为 `as e` 
- `urlparse` 修改为 `urllib.parse`
- 用python3的input替换原来的raw_input
- 增加了Dockerfile的简易部署







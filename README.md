# 逆波兰表达式

# 合作者：

1. 徐震 3180105504
2. 付仁泓  3180102072
3. 陈九润 3180105488



## ——钱徽C程序设计专题（2019-03-12创建）

组员：徐震，陈九润，付仁泓

## 03-26-16-30 内部测试完成，基本功能已具备
1. 整数的加减乘除运算
2. 带括号数字的运算
3. 浮点数运算的实现

## 静待九妹实现cos sin pow等简单函数的功能 手动滑稽.jpg

# 我好了我写完了函数

- 可以用程序里的套路，调用C里面有的所有函数了其实，就加一点判断的内容行了

- 成功实现了函数中只有一个参数不加括号的情况
- 成功实现了函数内的这个参数是另一个函数的情况

- 并对程序结构进行了重构，增加了func()函数

## 现在需要数据来测验功能的完整性

- hhh行吧我测试完了，修改了……hin多hin多bug，包括但不限于

  - 调整了stdin的清空方式（用fflush不知道为啥总有些奇奇怪怪的错误，劳资直接用宏了）

  - 读入无法识别函数的错误处理机制
  - 读入无法识别字符的错误处理机制
  - 错误出现时的堆栈处理方式（考虑过goto汇编最后还是选择一层层退出）
  - 更改并调试然后更改并调试main以满足错误处理机制
  - 增加部分内容的注释，便于理解程序逻辑
  - 修剪了不合适的代码行
  - ——以上——徐震

- 其实叭好像仍旧需要更多的测试点进行功能检验
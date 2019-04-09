# 逆波兰表达式

# 合作者：

1. 徐震 3180105504
2. 付仁泓  3180102072
3. 陈九润 3180105488



# LOG

## ——钱徽C程序设计专题（2019-03-12创建）

组员：徐震，陈九润，付仁泓

## 03-26-16-30 内部测试完成，基本功能已具备
1. 整数的加减乘除运算
2. 带括号数字的运算
3. 浮点数运算的实现

## 静待九妹实现cos sin pow等简单函数的功能 手动滑稽.jpg

## 我好了我写完了函数

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

## 更新

- 增加了历史记录功能（需要CTRL+C来结束程序）
- 增加了对e和pi的支持



## 无论是对于函数，还是像e，pi一样的内容，只需要按照程序内的套路进行极为方便的添加。





# 内容简述（部分内容的解释留在程序的注释中）

**url: https://github.com/dendenxu/npl**
**git command: git clone https://github.com/dendenxu/npl.git**

为了后期方便调试，在最后的几个版本中将stack.c stack.h
main.c几个文件进行了合并，内容没有发生实际变动。

此项目
1. 通过将用户输入的中缀表达式转换为后缀表达式
2. 计算后缀表达式的值来实现简单的计算器功能（因此，对于不加括号的除法，会先进行后面的乘法运算）

注意：
1. 一切计算都是在假定用户输入格式正确的情况下进行的，如果输入的格式不是严格的中缀表达式，谁知道会发生什么
2. 支持的运算符：+、 -、 *、 /、 =       =代表运算的结束以及     （左括号     和
）右括号
3. 支持的数据类型：双精度浮点类型（注意不可以将0.3写成.3，但是可以将3.0写成3.）
4. 栈大小：10000*sizeof(char)，浮点数组大小：10000*sizeof(double)，用户需保证输入的计算式不会超出两者的限制，否则谁知道会发生什么
5. 用户输入的数据中可以在任意地方放入空白字符，比如用户输入1+1=或者1 + 1 =
都可以得到正确的结果（当然，不可以在原本应连续输入的函数中插入奇怪的空白字符，例如s
i n）
6. 所有运算都是浮点运算，所以最终结果可能与实际结果有微小的差异，但这也是不可避免的……，最终的运算结果输出形式与最终结果有关，有可能为E型或浮点型
7. 为了方便使用，开启死循环模式，如果不手动ctrl+c，会一直运行下去

项目分工：
- 架构设计及实现：徐震
- 主函数设计及实现：徐震
- stack.h设计及实现：徐震
- 部分stack.c函数设计及实现：徐震
- stack.c主体设计及实现：付仁泓
- 项目总体调试及初步测试运行：徐震
- 简单函数计算功能设计及实现：陈九润（待完成）
- 我好了，我递归了简单函数功能-徐震
- 我把不加括号的单值函数也实现了下（暂时是只能对单独的一个数进行操作）...-徐震
- 现在能对单独参数是一个函数的情况进行处理-徐震
- 现在可以对e,pi,Pi,PI进行处理-徐震
- 现在增加了历史记录功能，可以用ans,ANS,Ans调用，未计算出有效结果时请勿使用-徐震







# 测试样例

```c
1+1=
1 + 1 =
1 + sin     (    pi    )          =
1 + sin sin sin (pow(sqrt(pi)            ,              2)) *   10000 + 1 / 2 /     3=
ans + 1 =
fabs ans =
    
// output
// 1+1=
// 2
// 1 + 1 =
// 2
// 1 + sin     (    pi    )          =
// 1
// 1 + sin sin sin (pow(sqrt(pi)            ,              2)) *   10000 + 1 / 2 /     3=
// 2.5
// ans + 1 =
// 3.5
// fabs ans =
// 3.5
// ^C


```
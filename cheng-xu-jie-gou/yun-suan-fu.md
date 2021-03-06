# 运算符

## **算术运算符**

| 运算符 | 描述 |
| :--- | :--- |
| + | 相加 |
| - | 相减 |
| \* | 相乘 |
| / | 相除 |
| % | 求余 |
| ++ | 自增，只支持x++，即x=x+1 |
| -- | 自减，只支持x--，即x=x-1 |

补充，+ 和 - 也可以作为一元的加法和减法运算符。

## **关系运算符**

| 运算符 | 描述 |
| :--- | :--- |
| == | 检查两个值是否相等，如果相等返回 True 否则返回 False |
| != | 检查两个值是否不相等，如果不相等返回 True 否则返回 False |
| &gt; | 检查左边值是否大于右边值，如果是返回 True 否则返回 False |
| &lt; | 检查左边值是否小于右边值，如果是返回 True 否则返回 False |
| &gt;= | 检查左边值是否大于等于右边值，如果是返回 True 否则返回 False |
| &lt;= | 检查左边值是否小于等于右边值，如果是返回 True 否则返回 False |

## **逻辑运算符**

| 运算符 | 描述 |
| :--- | :--- |
| && | 逻辑 AND 运算符。 如果两边的操作数都是 True，则条件 True，否则为 Fals |
| \|\| | 逻辑 OR 运算符。 如果两边的操作数有一个 True，则条件 True，否则为 False |
| ！ | 逻辑 NOT 运算符。 如果条件为 True，则逻辑 NOT 条件 False，否则为 True |

⚠️注意：逻辑运算符&&和\|\|可能有短路行为：若运算符左侧的结果已能确定整个表达式的结果时，右侧不会进行求值。

## **位运算符**

下表列出了位运算符 &, \|, 和 ^ 的计算：

| p | q | p & q | p \| q | p ^ q |
| :--- | :--- | :--- | :--- | :--- |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 | 1 |

Go 语言支持的位运算符如下表所示:

| 运算符 | 描述 |  |
| :--- | :--- | :--- |
| & | 按位与运算符"&"是双目运算符。 其功能是参与运算的两数各对应的二进位相与 |  |
| \| | 按位或运算符" | "是双目运算符。 其功能是参与运算的两数各对应的二进位相或 |
| ^ | 运算符"^"作为双目运算符时，其功能是参与运算的两数各对应的二进位相异或，当两对应的二进位相异时，结果为1；但当用作一元运算符时，则表示按位取反 |  |
| &^ | 运算符"&^"用于按位置零（AND NOT）：表达式z = x &^ y结果z的bit位为0，如果对应y中bit位为1的话，否则对应的bit位等于x相应的bit位的值 |  |
| &lt;&lt; | 左移运算符"&lt;&lt;"是双目运算符。左移n位就是乘以2的n次方。 其功能把"&lt;&lt;"左边的运算数的各二进位全部左移若干位，高位丢弃，低位补0 |  |
| &gt;&gt; | 右移运算符"&gt;&gt;"是双目运算符。右移n位就是除以2的n次方。 其功能是把"&gt;&gt;"左边的运算数的各二进位全部右移若干位，无符号数的右移运算用0填充左边空缺的bit位，但是有符号数的右移运算会用符号位的值填充左边空缺的bit位 |  |

位运算符的详细介绍及使用场景参考笔记 [Understanding Bitwise Operators](https://app.yinxiang.com/shard/s64/nl/13796945/7ede0391-8312-45d5-86ce-b7aaee5bbbeb/)

## **赋值运算符**

| 运算符 | 描述 |
| :--- | :--- |
| = | 简单的赋值运算符，将一个表达式的值赋给一个左值 |
| += | 相加后再赋值 |
| -= | 相减后再赋值 |
| \*= | 相乘后再赋值 |
| /= | 相除后再赋值 |
| %= | 求余后再赋值 |
| &lt;&lt;= | 左移后赋值 |
| &gt;&gt;= | 右移后赋值 |
| &= | 按位与后赋值 |
| ^= | 按位异或后赋值 |
| \|= | 按位或后赋值 |

## **运算符优先级**

下面是Go语言中关于算术运算、逻辑运算和比较运算的二元运算符，它们按照先级递减的顺序的排列：

| 优先级 | 运算符 |
| :--- | :--- |
| 1 | \*      /      %      &lt;&lt;       &gt;&gt;     &       &^ |
| 2 | +      -      \|      ^ |
| 3 | ==     !=     &lt;      &lt;=       &gt;      &gt;= |
| 4 | && |
| 5 | \|\| |

二元运算符有五种优先级。在同一个优先级，使用左优先结合规则，但是使用括号可以明确优先顺序，使用括号也可以用于提升优先级


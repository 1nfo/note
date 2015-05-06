title 效果和‘#’相同
=
subtitle 和‘##’相同
-
[markdown/basic](http://www.appinn.com/markdown/basic.html)
星期三, 06. 五月 2015 11:16上午 

# 1#
## 2
### 3
#### 4
##### 5 
###### 6
####### 7（并没有7级）
**bo**__ld__
*ita*_lic_
~~test~~
==highlight==
___
[baidu](https://www.baidu.com 'baidu') 
[baidu][1]
[baidu][]
[1]:https://www.baidu.com 'baidu'
[baidu]:https://www.baidu.com 'baidu'

	a code block, backgrond is different
	python:
	
`a code sting, backgrond is different
	python:`
***
`&=&amp;`&=&amp;
'&'='&amp;', what if &amp;amp;
<=&lt; and &lt;works when it in&ltstring;(letter only)&gtendwitha; but ';'will display

html tags <xxx> works here but not <> when nothing in it  

This is a paragraph.前后有一个以上的空行（\s+）
newline

>quato
>>quato    in  quato
>
>
>
>multi space and empty line will be treated as single one just like html
no need to type > at the start of every newline when you input without empty line
it still works

until a empty newline
>* list()
>+ list
>-  list
>* *+- is same. btw, 分割线can interupt quato directly

1. 有序list
1. 无所谓‘.’ 之前什么，不过第一行最好是1
8. 突然变多
3. 或者变少
0. 只要是  **(\d+\. )**有空格
-6. 5 负数可不行，我又想多了。。。
所以段落都被包含进来了
	
    多段用tab或space{4}

直接emptyline开始其他内容
+ 无序list
就不行
---
##转义
\\\   反斜线
\`   反引号`
\*   星号*
\_   底线 _
\{花括号}  
\[方括号] 
\( 括弧) 
\#   井字号

\+ 加号
\-   减号
\.   英文句点
\!   惊叹号
---
test area
***
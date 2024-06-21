# Assignment #1: 拉齐大家Python水平

Updated 0940 GMT+8 Feb 19, 2024

2024 spring, Complied by ==胡登科、生命科学学院==



**说明：**

1）数算课程的先修课是计概，由于计概学习中可能使用了不同的编程语言，而数算课程要求Python语言，因此第一周作业练习Python编程。如果有同学坚持使用C/C++，也可以，但是建议也要会Python语言。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知3月1日导入选课名单后启用。**作业写好后，保留在自己手中，待3月1日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



**编程环境**

==（Microsoft Windows 11 家庭中文版、Python 3.7, PyCharm 2023.1.4）==

## 1. 题目

### 20742: 泰波拿契數

http://cs101.openjudge.cn/practice/20742/



思路：利用列表写递推式，然后生成这个数列的list，然后打表。

用时：30min

##### 代码

```python
# 
def tribonacci(n):
    if n == 0:
        return 0
    elif n <= 2:
        return 1
    trib = [0, 1, 1] + [0] * (n - 2)
    for i in range(3, n + 1):
        trib[i] = trib[i - 1] + trib[i - 2] + trib[i - 3]
    return trib[n]
n = int(input())
print(tribonacci(n))
```



代码运行截图 ==（至少包含有"Accepted"）==

![image-20240301220136122](C:\Users\胡登科\AppData\Roaming\Typora\typora-user-images\image-20240301220136122.png)

### 58A. Chat room

greedy/strings, 1000, http://codeforces.com/problemset/problem/58/A



思路：将hello转化为列表，然后依次寻找，当找到5后结束。

用时：10min



##### 代码

```python
# 
# 聊天室
word = [str(i) for i in str(input())]
Sum = 0
x = ['h', 'e', 'l', 'l', 'o']
t = 0
k=0
for i in word:
    if i == x[t]:
        Sum += 1
        t += 1
    if t == 5:
        k=1
        break
if k:
    print("YES")
else:
    print("NO")

```



代码运行截图 ==（至少包含有"Accepted"）==![image-20240227150527785](C:\Users\胡登科\AppData\Roaming\Typora\typora-user-images\image-20240227150527785.png)





### 118A. String Task

implementation/strings, 1000, http://codeforces.com/problemset/problem/118/A



思路：存字然后判断不是元音。

min:10



##### 代码

```python
# 

word = [str(i) for i in str(input())]
prt = ''
for letters in word:
    if letters != 'A' and letters != 'a' and letters != 'E' and letters != 'e' and letters != 'I' and letters != 'i' and letters != 'O' and letters != 'o' and letters != 'U' and letters != 'u' and letters != 'Y' and letters != 'y':
        letters = letters.lower()
        prt = prt +'.'+ letters
print(prt)
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240227151758566](C:\Users\胡登科\AppData\Roaming\Typora\typora-user-images\image-20240227151758566.png)



### 22359: Goldbach Conjecture

http://cs101.openjudge.cn/practice/22359/



思路：

先写一个判断素数的函数，然后枚举判断拆分开的两个数是否为素数。

用时：15min

##### 代码

```python
# 
import math
def is_prime(n):
    k = math.sqrt(n)
    if n < 2:
        return False
    for i in range(2, int(k) + 1):
        if n % i == 0:
            return False
    return True


def goldbach(n):
    for i in range(2, n):
        if is_prime(i) and is_prime(n - i):
            return i, n - i


n = int(input())
a, b = goldbach(n)
print(a, b)
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240227144103846](C:\Users\胡登科\AppData\Roaming\Typora\typora-user-images\image-20240227144103846.png)



### 23563: 多项式时间复杂度

http://cs101.openjudge.cn/practice/23563/



思路：将算式处理为字符串，然后统计指数，找到最大的指数。

用时：15min

##### 代码

```python
# 
ps = input().split('+') 
ns = [(i.split('n^')) for i in ps]
result = 0 
for i in ns:
    if int(i[1]) > result and i[0] != '0': 
        result = int(i[1]) 
print('n^{}'.format(result)) 
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240227144637916](C:\Users\胡登科\AppData\Roaming\Typora\typora-user-images\image-20240227144637916.png)



### 24684: 直播计票

http://cs101.openjudge.cn/practice/24684/



思路：本题不咋会做，参考了答案。思路题目中的注释部分详尽地做了解释。

用时：30+min



##### 代码

```python
# 
from collections import defaultdict

# 读取输入并转换成整数列表
votes = list(map(int, input().split()))

# 使用字典统计每个选项的票数
# default 自身创建一个字典并加入value值
vote_counts = defaultdict(int)
for vote in votes:
    vote_counts[vote] += 1

# 找出得票最多的票数
max_votes = max(vote_counts.values())

# 按编号顺序收集得票最多的选项
lst = [item for item in vote_counts.items() if item[1] == max_votes]
winners = sorted(lst)

# 输出得票最多的选项，如果有多个则并列输出
# 此处 winner 的类型为元组， winner[0]表示元组中的序号
print(' '.join(str(winner[0]) for winner in winners))
```



代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

![image-20240227144601771](C:\Users\胡登科\AppData\Roaming\Typora\typora-user-images\image-20240227144601771.png)



## 2. 学习总结和收获

==如果作业题目简单，有否额外练习题目，比如：OJ“数算pre每日选做”、CF、LeetCode、洛谷等网站题目。==

作业题目思维难度较为简单，主要掌握字符串的处理以及相关的函数运用。

OJ“数算pre每日选做''每天做三道题 大致用时1小时。

希望能跟闫老师学习到熟练运用python 成绩乃身外之物。




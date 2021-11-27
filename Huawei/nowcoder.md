# HJ1 字符串最后一个单词的长度
## 描述
计算字符串最后一个单词的长度，单词以空格隔开，字符串长度小于5000。
（注：字符串末尾不以空格为结尾）

## 输入描述：
输入一行，代表要计算的字符串，非空，长度小于5000。

## 输出描述：
输出一个整数，表示输入字符串最后一个单词的长度。

## 示例
### 输入：
hello nowcoder
### 输出：
8

## 题解
```python3
import sys

for line in sys.stdin:
    a = line.split()
    print(len(a[-1]))
```

# HJ2 计算某字符出现次数

## 描述
写出一个程序，接受一个由字母、数字和空格组成的字符串，和一个字符，然后输出输入字符串中该字符的出现次数。（不区分大小写字母）

## 数据范围
[1，200]，输入的数据有可能包含大小写字母、数字和空格

## 输入描述
第一行输入一个由字母和数字以及空格组成的字符串，第二行输入一个字符。

## 输出描述
输出输入字符串中含有该字符的个数。（不区分大小写字母）

## 示例
### 输入
ABCabc
A
### 输出
2

## 题解
```python3
import sys
 
a=input().strip().lower()
b=input().strip().lower()
print(a.count(b))
```

# HJ3 明明的随机数
## 描述
明明想在学校中请一些同学一起做一项问卷调查，为了实验的客观性，他先用计算机生成了 N 个 1 到 1000 之间的随机整数（ N≤1000 ），对于其中重复的数字，只保留一个，把其余相同的数去掉，不同的数对应着不同的学生的学号。然后再把这些数从小到大排序，按照排好的顺序去找同学做调查。请你协助明明完成“去重”与“排序”的工作(同一个测试用例里可能会有多组数据(用于不同的调查)，希望大家能正确处理)。

注：测试用例保证输入参数的正确性，答题者无需验证。测试用例不止一组。
当没有新的输入时，说明输入结束。

数据范围： n[1,1000] ，输入的数字大小满足 [1,500]

## 输入描述
注意：输入可能有多组数据(用于不同的调查)。每组数据都包括多行，第一行先输入随机整数的个数 N ，接下来的 N 行再输入相应个数的整数。具体格式请看下面的"示例"。


## 输出描述
返回多行，处理后的结果

## 示例
### 输入
3
2
2
1
11
10
20
40
32
67
40
20
89
300
400
15

### 输出
1
2
10
15
20
32
40
67
89
300
400

说明：
示例1包含了两个小样例！！  
输入解释：
第一个数字是3，也即这个小样例的N=3，说明用计算机生成了3个1到1000之间的随机整数，接下来每行一个随机数字，共3行，也即这3个随机数字为：
2
1
1
所以第一个小样例的输出为：
1
2
第二个小样例的第一个数字为11，也即...(类似上面的解释)...
所以第二个小样例的输出为：
10
15
20
32
40
67
89
300
400  

```python3
data=[]
while True:
    try:
        n=input()
        arr=[]
        for i in range(int(n)):
            arr.append(int(input()))
        uniq_arr=set(arr)
        for j in sorted(uniq_arr):
            print(j)
    except (EOFError, KeyboardInterrupt):
        break
```

# HJ4 字符串分隔

## 描述
•连续输入字符串，请按长度为8拆分每个输入字符串并进行输出； 
•长度不是8整数倍的字符串请在后面补数字0，空字符串不处理。

## 输入描述
连续输入字符串(输入多次,每个字符串长度小于等于100)

## 输出描述
依次输出所有分割后的长度为8的新字符串

## 示例
### 输入
abc
123456789
### 输出
abc00000
12345678
90000000

```python3
while True:
    try:
        l=input().strip()
        for i in range(0,len(l),8):
            print("{0:0<8s}".format(l[i:i+8]))
    except (EOFError,KeyboardInterrupt):
        break
```

# HJ5 进制转换
## 描述
写出一个程序，接受一个十六进制的数，输出该数值的十进制表示。

## 数据范围
保证结果在 [2,2**31-1]

注意本题有多组输入

## 输入描述
输入一个十六进制的数值字符串。注意：一个用例会同时有多组输入数据，请参考帖子https://www.nowcoder.com/discuss/276处理多组输入的问题。

## 输出描述
输出该数值的十进制字符串。不同组的测试用例用\n隔开。


## 示例
### 输入
0xA
0xAA

### 输出
10
170

```python3
while True:
    try:
        s=input()
        print(int(s,16))
    except:
        break
```

# HJ6 质数因子
## 描述
功能:输入一个正整数，按照从小到大的顺序输出它的所有质因子（重复的也要列举）（如180的质因子为2 2 3 3 5 ）

## 数据范围
[2,2**9+14]

## 输入描述
输入一个整数

## 输出描述
按照从小到大的顺序输出它的所有质数的因子，以空格隔开。最后一个数后面也要有空格。

## 示例
### 输入
180
### 输出
2 2 3 3 5

```python3
import math
n=int(input())
for i in range(2,int(math.sqrt(n))+1):
    while n%i==0:
        print(i,end=' ')
        n=n//i
if n>2:
    print(n)
```

# HJ7 取近似值
## 描述
写出一个程序，接受一个正浮点数值，输出该数值的近似整数值。如果小数点后数值大于等于 0.5 ,向上取整；小于 0.5 ，则向下取整。

## 数据范围
保证输入的数字在 32 位浮点数范围内

## 输入描述
输入一个正浮点数值

## 输出描述
输出该数值的近似整数值

## 示例
### 输入
5.5

### 输出
6

### 说明
0.5>=0.5，所以5.5需要向上取整为6   

```python3
print(int(float(input())+0.5))
```

# HJ8 合并表记录
## 描述
数据表记录包含表索引和数值（int范围的正整数），请对表索引相同的记录进行合并，即将相同索引的数值进行求和运算，输出按照key值升序进行输出。

## 提示
0 <= index <= 11111111
1 <= value <= 100000

## 输入描述
先输入键值对的个数n（1 <= n <= 500）
然后输入成对的index和value值，以空格隔开

## 输出描述
输出合并后的键值对（多行）

## 示例
### 输入
4
0 1
0 2
1 2
3 4

### 输出
0 3
1 2
3 4

```python3
n=int(input())
dic={}

for i in range(n):
    line=input().split()
    key=int(line[0])
    value=int(line[1])
    dic[key]=dic.get(key,0)+value

for each in sorted(dic):
    print(each,dic[each])
```

# HJ9 提取不重复的整数
## 描述
输入一个 int 型整数，按照从右向左的阅读顺序，返回一个不含重复数字的新的整数。
保证输入的整数最后一位不是 0 。

## 数据范围
[1,10**8]

## 输入描述
输入一个int型整数

## 输出描述
按照从右向左的阅读顺序，返回一个不含重复数字的新的整数

## 示例
### 输入
9876673
### 输出
37689

```python3
arr=input()
arr=arr[::-1]
dup_arr=list()
for i in arr:
    if i in dup_arr:
        continue
    else:
        dup_arr.append(i)
        print(i,end='')
```

# HJ10 字符个数统计
## 描述
编写一个函数，计算字符串中含有的不同字符的个数。字符在 ASCII 码范围内( 0~127 ，包括 0 和 127 )，换行表示结束符，不算在字符里。不在范围内的不作统计。多个相同的字符只计算一次
例如，对于字符串 abaca 而言，有 a、b、c 三种不同的字符，因此输出 3 。

数据范围： 
输入描述：

输入一行没有空格的字符串。
输出描述：

输出 输入字符串 中范围在(0~127，包括0和127)字符的种数。

```python3
print(len(set(input())))
```

# HJ11 数字颠倒
描述

输入一个整数，将这个整数以字符串的形式逆序输出
程序不考虑负数的情况，若数字含有0，则逆序形式也含有0，如输入为100，则输出为001

数据范围： 
输入描述：

输入一个int整数
输出描述：

将这个整数以字符串的形式逆序输出
示例1

输入：
1516000
复制
输出：
0006151
复制
示例2

输入：
0
复制
输出：
0

```python3
print(input()[::-1])
```

# HJ12 字符串反转
描述

接受一个只包含小写字母的字符串，然后输出该字符串反转后的字符串。（字符串长度不超过1000）
输入描述：

输入一行，为一个只包含小写字母的字符串。
输出描述：

输出该字符串反转后的字符串。
示例1

输入：
abcd
复制
输出：
dcba

```python3
print(input()[::-1])
```

# HJ13 句子逆序
描述

将一个英文语句以单词为单位逆序排放。例如“I am a boy”，逆序排放后为“boy a am I”
所有单词之间用一个空格隔开，语句中除了英文字母外，不再包含其他字符

数据范围：输入的字符串长度满足 

注意本题有多组输入
输入描述：

输入一个英文语句，每个单词用空格隔开。保证输入只包含空格和字母。
输出描述：

得到逆序的句子
示例1

输入：
I am a boy
复制
输出：
boy a am I
复制
示例2

输入：
nowcoder
复制
输出：
nowcoder

```python3
print(' '.join(input().split()[::-1]))
```

# HJ14 字符串排序
描述

给定 n 个字符串，请对 n 个字符串按照字典序排列。

数据范围：  ，字符串长度满足 
输入描述：

输入第一行为一个正整数n(1≤n≤1000),下面n行为n个字符串(字符串长度≤100),字符串中只含有大小写字母。
输出描述：

数据输出n行，输出结果为按照字典序排列的字符串。
示例1

输入：
9
cap
to
cat
card
two
too
up
boat
boot
复制
输出：
boat
boot
cap
card
cat
to
too
two
up

```python3
n=int(input())
arr=[]
for i in range(n):
    arr.append(input())
for i in sorted(arr):
    print(i)
```

# HJ15 求int型正整数在内存中存储时1的个数
描述

输入一个 int 型的正整数，计算出该 int 型数据在内存中存储时 1 的个数。

数据范围：保证在 32 位整型数字范围内
输入描述：

 输入一个整数（int类型）
输出描述：

 这个数转换成2进制后，输出1的个数
示例1

输入：
5
复制
输出：
2
复制
示例2

输入：
0
复制
输出：
0

```python3
print(bin(int(input())).count('1'))
```

# HJ16 购物单
描述

王强今天很开心，公司发给N元的年终奖。王强决定把年终奖用于购物，他把想买的物品分为两类：主件与附件，附件是从属于某个主件的，下表就是一些主件与附件的例子：

主件	附件
电脑	打印机，扫描仪
书柜	图书
书桌	台灯，文具
工作椅	无

如果要买归类为附件的物品，必须先买该附件所属的主件。每个主件可以有 0 个、 1 个或 2 个附件。附件不再有从属于自己的附件。王强想买的东西很多，为了不超出预算，他把每件物品规定了一个重要度，分为 5 等：用整数 1 ~ 5 表示，第 5 等最重要。他还从因特网上查到了每件物品的价格（都是 10 元的整数倍）。他希望在不超过 N 元（可以等于 N 元）的前提下，使每件物品的价格与重要度的乘积的总和最大。
    设第 j 件物品的价格为 v[j] ，重要度为 w[j] ，共选中了 k 件物品，编号依次为 j 1 ， j 2 ，……， j k ，则所求的总和为：
v[j 1 ]*w[j 1 ]+v[j 2 ]*w[j 2 ]+ … +v[j k ]*w[j k ] 。（其中 * 为乘号）
    请你帮助王强设计一个满足要求的购物单。
 

输入描述：

输入的第 1 行，为两个正整数，用一个空格隔开：N m
（其中 N （ <32000 ）表示总钱数， m （ <60 ）为希望购买物品的个数。）

从第 2 行到第 m+1 行，第 j 行给出了编号为 j-1 的物品的基本数据，每行有 3 个非负整数 v p q

（其中 v 表示该物品的价格（ v<10000 ）， p 表示该物品的重要度（ 1 ~ 5 ）， q 表示该物品是主件还是附件。如果 q=0 ，表示该物品为主件，如果 q>0 ，表示该物品为附件， q 是所属主件的编号）
 

输出描述：

 输出文件只有一个正整数，为不超过总钱数的物品的价格与重要度乘积的总和的最大值（ <200000 ）。
示例1

输入：
1000 5
800 2 0
400 5 1
300 5 1
400 3 0
500 2 0
复制
输出：
2200

```python3
from collections import defaultdict
 
# 处理输入
n, m = map(int, input().split())
n //= 10  # 价格总为 10 的倍数，优化空间复杂度
prices = defaultdict(lambda: [0, 0, 0])  # 主从物品的价格
values = defaultdict(lambda: [0, 0, 0])  # 主从物品的价值
 
for i in range(m):      # i 代表第 i + 1 个物品
    v, p, q = map(int, input().split())
    v //= 10            # 价格总为 10 的倍数，优化空间复杂度
    if q == 0:          # 追加主物品
        prices[i + 1][0] = v
        values[i + 1][0] = v * p
    elif prices[q][1]:  # 追加从物品
        prices[q][2] = v
        values[q][2] = v * p
    else:
        prices[q][1] = v
        values[q][1] = v * p
 
# 处理输出
dp = [0] * (n + 1)  # 初始化 dp 数组
 
for i, v in prices.items():
    for j in range(n, v[0] - 1, -1):
        p1, p2, p3 = v
        v1, v2, v3 = values[i]
        # 处理主从组合的四种情况
        dp[j] = max(dp[j], dp[j - p1] + v1)
        dp[j] = max(dp[j], dp[j - p1 - p2] + v1 + v2) if j >= p1 + p2 else dp[j]
        dp[j] = max(dp[j], dp[j - p1 - p3] + v1 + v3) if j >= p1 + p3 else dp[j]
        dp[j] = max(dp[j], dp[j - p1 - p2 - p3] + v1 + v2 + v3) if j >= p1 + p2 + p3 else dp[j]
 
print(dp[n] * 10)
```

# HJ17 坐标移动
描述

开发一个坐标计算工具， A表示向左移动，D表示向右移动，W表示向上移动，S表示向下移动。从（0,0）点开始移动，从输入字符串里面读取一些坐标，并将最终输入结果输出到输出文件里面。
输入：
合法坐标为A(或者D或者W或者S) + 数字（两位以内）
坐标之间以;分隔。
非法坐标点需要进行丢弃。如AA10;  A1A;  $%$;  YAD; 等。
下面是一个简单的例子 如：
A10;S20;W10;D30;X;A1A;B10A11;;A10;
处理过程：
起点（0,0）
+   A10   =  （-10,0）
+   S20   =  (-10,-20)
+   W10  =  (-10,-10)
+   D30  =  (20,-10)
+   x    =  无效
+   A1A   =  无效
+   B10A11   =  无效
+  一个空 不影响
+   A10  =  (10,-10)
结果 （10， -10）

数据范围：每组输入的字符串长度满足  ，坐标保证满足  ，且数字部分仅含正数

注意请处理多组输入输出
输入描述：

一行字符串
输出描述：

最终坐标，以逗号分隔
示例1

输入：
A10;S20;W10;D30;X;A1A;B10A11;;A10;
复制
输出：
10,-10
复制

```python3
import re
x,y=0,0
cmd=input().strip().split(';')
fun={
    'A':lambda a,b,p:(a-p,b),
    'D':lambda a,b,p:(a+p,b),
    'W':lambda a,b,p:(a,b+p),
    'S':lambda a,b,p:(a,b-p)
}
for ins in cmd:
    if re.match(r'[A|S|D|W]\d\d?$',ins):
        x,y=fun[ins[0]](x,y,int(ins[1:]))
print(f'{x},{y}')
```

# HJ18 识别有效的IP地址和掩码并进行分类统计
描述

请解析IP地址和对应的掩码，进行分类识别。要求按照A/B/C/D/E类地址归类，不合法的地址和掩码单独归类。
所有的IP地址划分为 A,B,C,D,E五类
A类地址1.0.0.0~126.255.255.255;
B类地址128.0.0.0~191.255.255.255;
C类地址192.0.0.0~223.255.255.255;
D类地址224.0.0.0~239.255.255.255；
E类地址240.0.0.0~255.255.255.255

私网IP范围是：
10.0.0.0-10.255.255.255
172.16.0.0-172.31.255.255
192.168.0.0-192.168.255.255

子网掩码为二进制下前面是连续的1，然后全是0。（例如：255.255.255.32就是一个非法的掩码）
注意二进制下全是1或者全是0均为非法

注意：
1. 类似于【0.*.*.*】和【127.*.*.*】的IP地址不属于上述输入的任意一类，也不属于不合法ip地址，计数时请忽略
2. 私有IP地址和A,B,C,D,E类地址是不冲突的

输入描述：

多行字符串。每行一个IP地址和掩码，用~隔开。
输出描述：

统计A、B、C、D、E、错误IP地址或错误掩码、私有IP的个数，之间以空格隔开。
示例1

输入：
10.70.44.68~255.254.255.0
1.0.0.1~255.0.0.0
192.168.0.2~255.255.255.0
19..0.~255.255.255.0
复制
输出：
1 0 1 0 0 2 1
复制
说明：
10.70.44.68~255.254.255.0的子网掩码非法，19..0.~255.255.255.0的IP地址非法，所以错误IP地址或错误掩码的计数为2；
1.0.0.1~255.0.0.0是无误的A类地址；
192.168.0.2~255.255.255.0是无误的C类地址且是私有IP；
所以最终的结果为1 0 1 0 0 2 1 

```python3
import re
res=[0,0,0,0,0,0,0]
def toBin(str_list):
    return ''.join(str(j) for j in [bin(int(i))[2:].rjust(8,'0') for i in str_list])

def mask_val(mask):
    mask_str=mask.split('.')
    if '' not in mask_str:
        mask_bin = toBin(mask_str)
        if (re.search("[0][1]",mask_bin) or '1' not in mask_bin or '0' not in mask_bin):
            return False
    return True
try:
    while True:
        raw=input().split('~')
        ip=raw[0]
        mask=raw[1]
        ip_str=ip.split('.')
        if '' not in ip_str:
            if not (ip.startswith('127') or ip.startswith('0')):
                if mask_val(mask):
                    ip_bin=toBin(ip_str)
                    if ip_bin.startswith('0'):
                        res[0]+=1
                    elif ip_bin.startswith('10'):
                        res[1]+=1
                    elif ip_bin.startswith('110'):
                        res[2]+=1
                    elif ip_bin.startswith('1110'):
                        res[3]+=1
                    elif ip_bin.startswith('1111'):
                        res[4]+=1
                    if (ip_str[0]=='10' and 0<=int(ip_str[1])<=255 and 0<=int(ip_str[2])<=255 and 0<=int(ip_str[3])<=255) or (ip_str[0]=='172' and 16<=int(ip_str[1])<=31 and 0<=int(ip_str[2])<=255 and 0<=int(ip_str[2])<=255) or (ip_str[0]=='192' and ip_str[1]=='168' and 0<=int(ip_str[2])<=255 and 0<=int(ip_str[3])<=255):
                        res[-1]+=1
                else:
                    res[-2]+=1
        else:
            res[-2]+=1
except EOFError:
    print(" ".join(str(i) for i in res))
```

# HJ19 简单错误记录
描述

开发一个简单错误记录功能小模块，能够记录出错的代码所在的文件名称和行号。

处理：

1、 记录最多8条错误记录，循环记录，最后只用输出最后出现的八条错误记录。对相同的错误记录只记录一条，但是错误计数增加。最后一个斜杠后面的带后缀名的部分（保留最后16位）和行号完全匹配的记录才做算是”相同“的错误记录。
2、 超过16个字符的文件名称，只记录文件的最后有效16个字符；
3、 输入的文件可能带路径，记录文件名称不能带路径。也就是说，哪怕不同路径下的文件，如果它们的名字的后16个字符相同，也被视为相同的错误记录
4、循环记录时，只以第一次出现的顺序为准，后面重复的不会更新它的出现时间，仍以第一次为准

数据范围：错误记录数量满足  ，每条记录长度满足 
输入描述：

每组只包含一个测试用例。一个测试用例包含一行或多行字符串。每行包括带路径文件名称，行号，以空格隔开。
输出描述：

将所有的记录统计并将结果输出，格式：文件名 代码行数 数目，一个空格隔开，如：
示例1

输入：
D:\zwtymj\xccb\ljj\cqzlyaszjvlsjmkwoqijggmybr 645
E:\je\rzuwnjvnuz 633
C:\km\tgjwpb\gy\atl 637
F:\weioj\hadd\connsh\rwyfvzsopsuiqjnr 647
E:\ns\mfwj\wqkoki\eez 648
D:\cfmwafhhgeyawnool 649
E:\czt\opwip\osnll\c 637
G:\nt\f 633
F:\fop\ywzqaop 631
F:\yay\jc\ywzqaop 631
D:\zwtymj\xccb\ljj\cqzlyaszjvlsjmkwoqijggmybr 645
复制
输出：
rzuwnjvnuz 633 1
atl 637 1
rwyfvzsopsuiqjnr 647 1
eez 648 1
fmwafhhgeyawnool 649 1
c 637 1
f 633 1
ywzqaop 631 2
复制
说明：
输出中的第五行记录，由于文件名长度超过了16个字符，达到了17，所以第一个字符'c'应该被忽略。
最后两条记录由于文件名和行号相同，因此被视为同一个错误记录。哪怕它们的路径是不同的。 

```python3
import sys
errors=[]
count=[]
for line in sys.stdin:
    error=line.split()[0].split('\\')[-1][-16:]+" "+line.split()[1]
    if error not in errors:
        errors.append(error)
        count.append(1)
    else:
        count[errors.index(error)]+=1
for i in range(len(errors[-8:])):
    print(errors[-8:][i],count[-8:][i])
```

# HJ20 密码验证合格程序
描述

密码要求:
1.长度超过8位
2.包括大小写字母.数字.其它符号,以上四种至少三种
3.不能有长度大于2的不含公共元素的子串重复 （注：其他符号不含空格或换行）

数据范围：输入的字符串长度满足 

本题有多组输入
输入描述：

一组或多组字符串。每组占一行
输出描述：

如果符合要求输出：OK，否则输出NG
示例1

输入：
021Abc9000
021Abc9Abc1
021ABC9000
021$bc9000
复制
输出：
OK
NG
NG
OK

```python3
while True:
    try:
        psw=input()
        if len(psw)<=8:
            print('NG')
        else:
            sub=[]
            for i in range(len(psw)-2):
                sub.append(psw[i:i+3])
            if len(set(sub))<len(sub):
                print('NG')
            else:
                type_=0
                import re
                Upper='[A-Z]'
                Lower='[a-z]'
                num='\d'
                chars='[^A-Za-z0-9]'
                pattern=[Upper,Lower,num,chars]
                for pat in pattern:
                    pw=re.search(pat,psw)
                    if pw:
                        type_+=1
                if type_>=3:
                    print('OK')
                else:
                    print('NG')
    except:
        break
```

# HJ21 简单密码
描述

密码是我们生活中非常重要的东东，我们的那么一点不能说的秘密就全靠它了。哇哈哈. 接下来渊子要在密码之上再加一套密码，虽然简单但也安全。

假设渊子原来一个BBS上的密码为zvbo9441987,为了方便记忆，他通过一种算法把这个密码变换成YUANzhi1987，这个密码是他的名字和出生年份，怎么忘都忘不了，而且可以明目张胆地放在显眼的地方而不被别人知道真正的密码。

他是这么变换的，大家都知道手机上的字母： 1--1， abc--2, def--3, ghi--4, jkl--5, mno--6, pqrs--7, tuv--8 wxyz--9, 0--0,就这么简单，渊子把密码中出现的小写字母都变成对应的数字，数字和其他的符号都不做变换，

声明：密码中没有空格，而密码中出现的大写字母则变成小写之后往后移一位，如：X ，先变成小写，再往后移一位，不就是 y 了嘛，简单吧。记住，Z 往后移是 a 哦。

数据范围： 输入的字符串长度满足 

本题有多组样例输入
输入描述：

输入包括多个测试数据。输入是一个明文，密码长度不超过100个字符，输入直到文件结尾
输出描述：

输出渊子真正的密文
示例1

输入：
YUANzhi1987
复制
输出：
zvbo9441987

```python3
while True:
    try:
        s = input()
        res = []
        for i in s:
            if i.isdigit():
                res.append(i)
            elif i.isupper() and i != 'Z':
                res.append(chr(ord(i.lower()) + 1))
            elif i == 'Z':
                res.append('a')
            else:
                if i in 'abc':
                    res.append('2')
                elif i in 'def':
                    res.append('3')
                elif i in 'ghi':
                    res.append('4')
                elif i in 'jkl':
                    res.append('5')
                elif i in 'mno':
                    res.append('6')
                elif i in 'pqrs':
                    res.append('7')
                elif i in 'tuv':
                    res.append('8')
                else:
                    res.append('9')
        print(''.join(res))
    except:
        break
```

# HJ22 汽水瓶
描述

有这样一道智力题：“某商店规定：三个空汽水瓶可以换一瓶汽水。小张手上有十个空汽水瓶，她最多可以换多少瓶汽水喝？”答案是 5 瓶，方法如下：先用 9 个空瓶子换3瓶汽水，喝掉 3 瓶满的，喝完以后 4 个空瓶子，用 3 个再换一瓶，喝掉这瓶满的，这时候剩 2 个空瓶子。然后你让老板先借给你一瓶汽水，喝掉这瓶满的，喝完以后用 3 个空瓶子换一瓶满的还给老板。如果小张手上有 n 个空汽水瓶，最多可以换多少瓶汽水喝？

数据范围：输入的正整数满足 

注意：本题存在多组输入。
允许如题面所述向老板借汽水。
输入的 0 仅表示输入结束，并不用输出结果
输入描述：

输入文件最多包含 10 组测试数据，每个数据占一行，仅包含一个正整数 n（ 1<=n<=100 ），表示小张手上的空汽水瓶数。n=0 表示输入结束，你的程序不应当处理这一行。
输出描述：

对于每组测试数据，输出一行，表示最多可以喝的汽水瓶数。如果一瓶也喝不到，输出0。
示例1

输入：
3
10
81
0
复制
输出：
1
5
40
复制
说明：
样例 1 解释：用三个空瓶换一瓶汽水，剩一个空瓶无法继续交换
样例 2 解释：用九个空瓶换三瓶汽水，剩四个空瓶再用三个空瓶换一瓶汽水，剩两个空瓶，向老板借一瓶汽水喝完得三个空瓶换一瓶汽水还给老板 

```python3
while True:
    try:
        n=int(input())
        if n!=0:print(n//2)
    except:
        break
```

# HJ23 删除字符串中出现次数最少的字符
描述

实现删除字符串中出现次数最少的字符，若多个字符出现次数一样，则都删除。输出删除这些单词后的字符串，字符串中其它字符保持原来的顺序。
注意每个输入文件有多组输入，即多个字符串用回车隔开

数据范围：输入的字符串长度满足  ，保证输入的字符串中仅出现小写字母
输入描述：

字符串只包含小写英文字母, 不考虑非法输入，输入的字符串长度小于等于20个字节。
输出描述：

删除字符串中出现次数最少的字符后的字符串。
示例1

输入：
abcdd
aabcddd
复制
输出：
dd
aaddd

```python3
while True:
    try:
        arr=input()
        dic,res={},''
        for c in arr:
            if c not in dic:
                dic[c]=1
            else:
                dic[c]+=1
        min_value=min(dic.values())
        for c in arr:
            if dic[c]!=min_value:
                res+=c
        print(res)
    except:
        break
```

# HJ24 合唱队
描述

计算最少出列多少位同学，使得剩下的同学排成合唱队形
说明：
N 位同学站成一排，音乐老师要请其中的 (N - K) 位同学出列，使得剩下的 K 位同学排成合唱队形。 
合唱队形是指这样的一种队形：设K位同学从左到右依次编号为 1，2…，K ，他们的身高分别为 T1，T2，…，TK ，   则他们的身高满足存在 i （1<=i<=K） 使得 T1<T2<......<Ti-1<Ti>Ti+1>......>TK 。 
你的任务是，已知所有N位同学的身高，计算最少需要几位同学出列，可以使得剩下的同学排成合唱队形。

注意：不允许改变队列元素的先后顺序 且 不要求最高同学左右人数必须相等
请注意处理多组输入输出！

数据范围： 

输入描述：

有多组用例，每组都包含两行数据，第一行是同学的总数 N ，第二行是 N 位同学的身高，以空格隔开
输出描述：

最少需要几位同学出列
示例1

输入：
8
186 186 150 200 160 130 197 200
复制
输出：
4
复制
说明：
由于不允许改变队列元素的先后顺序，所以最终剩下的队列应该为186 200 160 130或150 200 160 130       
```python3
import bisect
def inc_max(l):
    dp = [1]*len(l) # 初始化dp，最小递增子序列长度为1
    arr = [l[0]] # 创建数组
    for i in range(1,len(l)): # 从原序列第二个元素开始遍历
        if l[i] > arr[-1]:
            arr.append(l[i])
            dp[i] = len(arr)
        else:
            pos = bisect.bisect_left(arr, l[i]) # 用二分法找到arr中第一个比ele_i大（或相等）的元素的位置
            arr[pos] = l[i]
            dp[i] = pos+1
    return dp
 
while True:
    try:
        N = int(input())
        s = list(map(int, input().split()))
        left_s = inc_max(s) # 从左至右
        right_s = inc_max(s[::-1])[::-1] # 从右至左
        sum_s = [left_s[i]+right_s[i]-1 for i in range(len(s))] # 相加并减去重复计算
        print(str(N-max(sum_s)))
    except:
        break
```

# HJ25 数据分类处理
描述

信息社会，有海量的数据需要分析处理，比如公安局分析身份证号码、 QQ 用户、手机号码、银行帐号等信息及活动记录。
采集输入大数据和分类规则，通过大数据分类处理程序，将大数据分类输出。

请注意本题有多组输入用例。

数据范围： ，输入的整数大小满足 
输入描述：

﻿一组输入整数序列I和一组规则整数序列R，I和R序列的第一个整数为序列的个数（个数不包含第一个整数）；整数范围为0~(2^31)-1，序列个数不限
输出描述：

﻿从R依次中取出R<i>，对I进行处理，找到满足条件的I： 
I整数对应的数字需要连续包含R<i>对应的数字。比如R<i>为23，I为231，那么I包含了R<i>，条件满足 。 
按R<i>从小到大的顺序:
(1)先输出R<i>； 
(2)再输出满足条件的I的个数； 
(3)然后输出满足条件的I在I序列中的位置索引(从0开始)； 
(4)最后再输出I。 
附加条件： 
(1)R<i>需要从小到大排序。相同的R<i>只需要输出索引小的以及满足条件的I，索引大的需要过滤掉 
(2)如果没有满足条件的I，对应的R<i>不用输出 
(3)最后需要在输出序列的第一个整数位置记录后续整数序列的个数(不包含“个数”本身)
 
序列I：15,123,456,786,453,46,7,5,3,665,453456,745,456,786,453,123（第一个15表明后续有15个整数） 
序列R：5,6,3,6,3,0（第一个5表明后续有5个整数） 
输出：30, 3,6,0,123,3,453,7,3,9,453456,13,453,14,123,6,7,1,456,2,786,4,46,8,665,9,453456,11,456,12,786
说明：
30----后续有30个整数
3----从小到大排序，第一个R<i>为0，但没有满足条件的I，不输出0，而下一个R<i>是3
6--- 存在6个包含3的I 
0--- 123所在的原序号为0 
123--- 123包含3，满足条件 
示例1

输入：
15 123 456 786 453 46 7 5 3 665 453456 745 456 786 453 123
5 6 3 6 3 0
复制
输出：
30 3 6 0 123 3 453 7 3 9 453456 13 453 14 123 6 7 1 456 2 786 4 46 8 665 9 453456 11 456 12 786

```python3
while True:
    try:
        I = [x for x in input().split()[1:]]
        R = sorted([int(x) for x in set(input().split()[1:]) if x > '0']) # R的序列要求是去除首位，且后续数字大于0，且要按照数字排序
        R = [str(x) for x in R] # 需要R数组从int转换为str，才方便进行比较
        result = []
        for r_index in range(len(R)):
            tmp_list = []
            for i_index in range(len(I)):
                if R[r_index] in I[i_index] and I[i_index] not in tmp_list:#当R元素字符串包含在I元素且tmp_list中没有该字符串时，加入到临时字符串，不然就会出现重复的I元素和其索引
                    tmp_list.append(i_index)
                    tmp_list.append(I[i_index])
            tmp_list.insert(0, len(tmp_list)//2) # 因为index+value到时数组长度乘2了，这个地方需要除2
            tmp_list.insert(0, R[r_index])
            if len(tmp_list) > 2:
                result += tmp_list
            tmp_list.clear()
        result.insert(0, len(result))
        for num in result:
            print(num,end=' ')
        print()
    except EOFError:
        break
```

# HJ26 字符串排序
描述

编写一个程序，将输入字符串中的字符按如下规则排序。

规则 1 ：英文字母从 A 到 Z 排列，不区分大小写。

如，输入： Type 输出： epTy

规则 2 ：同一个英文字母的大小写同时存在时，按照输入顺序排列。

如，输入： BabA 输出： aABb

规则 3 ：非英文字母的其它字符保持原来的位置。

如，输入： By?e 输出： Be?y


注意有多组测试数据，即输入有多行，每一行单独处理（换行符隔开的表示不同行）

数据范围：输入的字符串长度满足  
输入描述：

输入字符串
输出描述：

输出字符串
示例1

输入：
A Famous Saying: Much Ado About Nothing (2012/8).
复制
输出：
A aaAAbc dFgghh: iimM nNn oooos Sttuuuy (2012/8).

```python3
while True:
    try:
        s=input()
        a=''
        for i in s:
            if i.isalpha():
                a+=i
        b=sorted(a,key=str.upper)
        index=0
        d=''
        for i in range(len(s)):
            if s[i].isalpha():
                d+=b[index]
                index+=1
            else:
                d+=s[i]
        print(d)
    except:
        break
```

# HJ27 查找兄弟单词
描述

定义一个单词的“兄弟单词”为：交换该单词字母顺序（注：可以交换任意次），而不添加、删除、修改原有的字母就能生成的单词。
兄弟单词要求和原来的单词不同。例如： ab 和 ba 是兄弟单词。 ab 和 ab 则不是兄弟单词。
现在给定你 n 个单词，另外再给你一个单词 str ，让你寻找 str 的兄弟单词里，按字典序排列后的第 k 个单词是什么？
注意：字典中可能有重复单词。本题含有多组输入数据。

数据范围：，输入的字符串长度满足  ， 
输入描述：

先输入单词的个数n，再输入n个单词。 再输入一个单词，为待查找的单词x 最后输入数字k
输出描述：

输出查找到x的兄弟单词的个数m 然后输出查找到的按照字典顺序排序后的第k个兄弟单词，没有符合第k个的话则不用输出。
示例1

输入：
3 abc bca cab abc 1
复制
输出：
2
bca
复制

```python3
while True:
    try:
        data=input().split()
        n=int(data[0])
        k=int(data[-1])
        arr=data[1:-2]
        tar=data[-2]
        m=0
        bro=[]
        for word in arr:
            if word == tar:
                continue
            elif sorted(word) == sorted(tar):
                m+=1
                bro.append(word)
        print(m)
        print(sorted(bro)[k-1])
    except:
        break
```

# HJ28 素数伴侣
描述

题目描述
若两个正整数的和为素数，则这两个正整数称之为“素数伴侣”，如2和5、6和13，它们能应用于通信加密。现在密码学会请你设计一个程序，从已有的 N （ N 为偶数）个正整数中挑选出若干对组成“素数伴侣”，挑选方案多种多样，例如有4个正整数：2，5，6，13，如果将5和6分为一组中只能得到一组“素数伴侣”，而将2和5、6和13编组将得到两组“素数伴侣”，能组成“素数伴侣”最多的方案称为“最佳方案”，当然密码学会希望你寻找出“最佳方案”。
输入:
有一个正偶数 n ，表示待挑选的自然数的个数。后面给出 n 个具体的数字。
输出:
输出一个整数 K ，表示你求得的“最佳方案”组成“素数伴侣”的对数。

数据范围：  ，输入的数据大小满足 

本题有多组输入
输入描述：

输入说明
1 输入一个正偶数 n 
2 输入 n 个整数
题目有多组输入
输出描述：

求得的“最佳方案”组成“素数伴侣”的对数。
示例1

输入：
4
2 5 6 13
2
3 6
复制
输出：
2
0
```python3
def get_primenum(s):
    if s<4:
        return True
    #通过从2到它的平方根之间没有可除尽的数来判断这个数是否为素数。原理：一个数与另一个数能除尽则也能除尽这个数的2倍数。若直接判断从2到这个数之间的数则会耗费大量的时间来计算导致超时。
    for i in range(2,int(s**0.5)+1):
        if s%i==0:
            return False
    return True
    
def find_even(evens,previous_select,final_select,odd):
    for i, even in enumerate(evens):
        if get_primenum(even+odd) and previous_select[i]==0:
            previous_select[i]=1
            #判断第i位偶数是否被匹配或者它的匹配奇数是否有其他选择，如果有其他选择，则当前的奇数匹配第i位偶数
            if final_select[i]==0 or find_even(evens, previous_select, final_select, final_select[i]):
                final_select[i]=odd
                return True
    return False

while True:
    try:
        N=int(input())
        list0=list(map(int,input().split(' ')))
        count0=0
        evens,odds=[],[]
        for list1 in list0:
            if list1%2==0:
                evens.append(list1)
            else:
                odds.append(list1)
        final_select=[0]*len(evens)
        for odd in odds:
            previous_select=[0]*len(evens)
            if find_even(evens, previous_select, final_select, odd):
                count0 +=1
        print(count0)
    except:
        break
```

# HJ29 字符串加解密
描述

1、对输入的字符串进行加解密，并输出。
2、加密方法为：
当内容是英文字母时则用该英文字母的后一个字母替换，同时字母变换大小写,如字母a时则替换为B；字母Z时则替换为a；
当内容是数字时则把该数字加1，如0替换1，1替换2，9替换0；
其他字符不做变化。
3、解密方法为加密的逆过程。

本题含有多组样例输入。

数据范围：输入的两个字符串长度满足  ，保证输入的字符串都是大小写字母或者数字
输入描述：

输入说明
输入一串要加密的密码
输入一串加过密的密码
输出描述：

输出说明
输出加密后的字符
输出解密后的字符
示例1

输入：
abcdefg
BCDEFGH
复制
输出：
BCDEFGH
abcdefg

```python3
def check(a,b):
    L1 = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
    L2 = "BCDEFGHIJKLMNOPQRSTUVWXYZAbcdefghijklmnopqrstuvwxyza1234567890"
    result = ""
    if b == 1:
        for i in a:
            result += L2[L1.index(i)]
    elif b == -1:
        for i in a:
            result += L1[L2.index(i)]
    return result
while True:
    try:
        print(check(input(),1))
        print(check(input(), -1))

    except:
        break
```

# HJ30 字符串合并处理
描述

按照指定规则对输入的字符串进行处理。
详细描述：
第一步：将输入的两个字符串str1和str2进行前后合并。如给定字符串 "dec" 和字符串 "fab" ， 合并后生成的字符串为 "decfab"

第二步：对合并后的字符串进行排序，要求为：下标为奇数的字符和下标为偶数的字符分别从小到大排序。这里的下标的意思是字符在字符串中的位置。注意排序后在新串中仍需要保持原来的奇偶性。例如刚刚得到的字符串“decfab”，分别对下标为偶数的字符'd'、'c'、'a'和下标为奇数的字符'e'、'f'、'b'进行排序（生成 'a'、'c'、'd' 和 'b' 、'e' 、'f'），再依次分别放回原串中的偶数位和奇数位，新字符串变为“abcedf”

第三步：对排序后的字符串中的'0'~'9'、'A'~'F'和'a'~'f'字符，需要进行转换操作。
转换规则如下：
对以上需要进行转换的字符所代表的十六进制用二进制表示并倒序，然后再转换成对应的十六进制大写字符（注：字符 a~f 的十六进制对应十进制的10~15，大写同理）。
如字符 '4'，其二进制为 0100 ，则翻转后为 0010 ，也就是 2 。转换后的字符为 '2'。
如字符 ‘7’，其二进制为 0111 ，则翻转后为 1110 ，对应的十进制是14，转换为十六进制的大写字母为 'E'。
如字符 'C'，代表的十进制是 12 ，其二进制为 1100 ，则翻转后为 0011，也就是3。转换后的字符是 '3'。
根据这个转换规则，由第二步生成的字符串 “abcedf” 转换后会生成字符串 "5D37BF"

注意本题含有多组样例输入。

数据范围：输入的字符串长度满足 

输入描述：

本题含有多组样例输入。每组样例输入两个字符串，用空格隔开。
输出描述：

输出转化后的结果。每组样例输出一行。
示例1

输入：
dec fab
复制
输出：
5D37BF

```python3
import re
def encrypt(x):
    if re.search(r'[0-9A-Fa-f]', x):
        return hex(int(bin(int(x, 16))[2:].rjust(4, '0')[::-1], 2))[2:].upper()
    else:
        return x

while True:
    try:
        a = list(input().replace(" ", "")) 
        a[::2] = sorted(a[::2])  
        a[1::2] = sorted(a[1::2]) 
        res = ""
        for i in a:
            res += encrypt(i) 
        print(res)
    except:
        break

```

# HJ31 单词倒排
描述

对字符串中的所有单词进行倒排。
说明：
1、构成单词的字符只有26个大写或小写英文字母；
2、非构成单词的字符均视为单词间隔符；
3、要求倒排后的单词间隔符以一个空格表示；如果原字符串中相邻单词间有多个间隔符时，倒排转换后也只允许出现一个空格间隔符；
4、每个单词最长20个字母；

数据范围：字符串长度满足 
输入描述：

输入一行以空格来分隔的句子
输出描述：

输出句子的逆序
示例1

输入：
I am a student
复制
输出：
student a am I
复制
示例2

输入：
$bo*y gi!r#l
复制
输出：
l r gi y bo

```python3
while True:
    try:
        a=input().strip()
        for i in range(len(a)):
            if not a[i].isalpha():
                a=a.replace(a[i],' ')
        b=a..strip().split(' ')
        b.reverse()
        print(' '.join(b))
    except:
        break
```

# HJ32 密码截取
描述

Catcher是MCA国的情报员，他工作时发现敌国会用一些对称的密码进行通信，比如像这些ABBA，ABA，A，123321，但是他们有时会在开始或结束时加入一些无关的字符以防止别国破解。比如进行下列变化 ABBA->12ABBA,ABA->ABAKK,123321->51233214　。因为截获的串太长了，而且存在多种可能的情况（abaaab可看作是aba,或baaab的加密形式），Cathcer的工作量实在是太大了，他只能向电脑高手求助，你能帮Catcher找出最长的有效密码串吗？

数据范围：字符串长度满足 
输入描述：

输入一个字符串（字符串的长度不超过2500）
输出描述：

返回有效密码串的最大长度
示例1

输入：
ABBA
复制
输出：
4

```python3
while True:
    try:
        a=input()
        bc=0
        if a==a[::-1]:
            print(len(a))
        else:
            for i in range(len(a)):
                if i-bc>1 and a[i-bc-1:i+1]==a[i-bc-1:i+1][::-1]:
                    bc+=2
                elif i-bc>=0 and a[i-bc:i+1]==a[i-bc:i+1][::-1]:
                    bc+=1
            print(bc)
    except:
        break
```

# HJ33 整数与IP地址间的转换
描述

原理：ip地址的每段可以看成是一个0-255的整数，把每段拆分成一个二进制形式组合起来，然后把这个二进制数转变成
一个长整数。
举例：一个ip地址为10.0.3.193
每段数字             相对应的二进制数
10                   00001010
0                    00000000
3                    00000011
193                  11000001
组合起来即为：00001010 00000000 00000011 11000001,转换为10进制数就是：167773121，即该IP地址转换后的数字就是它了。

本题含有多组输入用例，每组用例需要你将一个ip地址转换为整数、将一个整数转换为ip地址。

数据范围：保证输入的是合法的 IP 序列

输入描述：

输入 
1 输入IP地址
2 输入10进制型的IP地址
输出描述：

输出
1 输出转换成10进制的IP地址
2 输出转换后的IP地址
示例1

输入：
10.0.3.193
167969729
复制
输出：
167773121
10.3.3.193

```python3
while True:
    try:
        ip = input()
        num = input()
    except:
        break
    else:
        # ip to num
        ip_list = ip.split('.')
        ip2num = str()
        for i in ip_list:
            a = bin(int(i,10))[2:]
            a = '0'*(8-len(a)) + a if len(a)<8 else a
            ip2num += a
        print(int(ip2num,2))
        # num to ip
        num2ip = []
        num2 = bin(int(num,10))[2:]
        num2 = '0'*(32-len(num2)) + num2 if len(num2)<32 else num2
        for i in range(4):
            b = num2[8*i:8*i+8]
            b = str(int(b,2))
            num2ip.append(b)
        print('.'.join(num2ip))
```

# HJ34 图片整理
描述

Lily上课时使用字母数字图片教小朋友们学习英语单词，每次都需要把这些图片按照大小（ASCII码值从小到大）排列收好。请大家给Lily帮忙，通过C语言解决。

本题含有多组样例输入。

数据范围：每组输入的字符串长度满足 
输入描述：

Lily使用的图片包括"A"到"Z"、"a"到"z"、"0"到"9"。输入字母或数字个数不超过1024。
输出描述：

Lily的所有图片按照从小到大的顺序输出
示例1

输入：
Ihave1nose2hands10fingers
复制
输出：
0112Iaadeeefghhinnnorsssv

```python3
while True:
    try:
        print(''.join(sorted(input)))
    except:
        break
```

# HJ35 蛇形矩阵
描述

蛇形矩阵是由1开始的自然数依次排列成的一个矩阵上三角形。
例如，当输入5时，应该输出的三角形为：
1 3 6 10 15
2 5 9 14
4 8 13
7 12
11

请注意本题含有多组样例输入。

输入描述：

输入正整数N（N不大于100）
输出描述：

输出一个N行的蛇形矩阵。
示例1

输入：
4
复制
输出：
1 3 6 10
2 5 9
4 8
7

```python3
while True:
    try:
        m=int(input())
        for i in range(1,m+1):
            for j in range(1,m-i+2):
                if j==m-i+1:
                    print((i+j-2)*(i+j-1)//2+j)
                else:
                    print((i+j-2)*(i+j-1)//2+j,end=' ')
    except:
        break
```

# HJ36 字符串加密
```python3
描述

有一种技巧可以对数据进行加密，它使用一个单词作为它的密匙。下面是它的工作原理：首先，选择一个单词作为密匙，如TRAILBLAZERS。如果单词中包含有重复的字母，只保留第1个，将所得结果作为新字母表开头，并将新建立的字母表中未出现的字母按照正常字母表顺序加入新字母表。如下所示：
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
T R A I L B Z E S C D F G H J K M N O P Q U V W X Y (实际需建立小写字母的字母表，此字母表仅为方便演示）
上面其他用字母表中剩余的字母填充完整。在对信息进行加密时，信息中的每个字母被固定于顶上那行，并用下面那行的对应字母一一取代原文的字母(字母字符的大小写状态应该保留)。因此，使用这个密匙， Attack AT DAWN (黎明时攻击)就会被加密为Tpptad TP ITVH。
请实现下述接口，通过指定的密匙和明文得到密文。

本题有多组输入数据。

数据范围： ，保证输入的字符串中仅包含小写字母
输入描述：

先输入key和要加密的字符串
输出描述：

返回加密后的字符串
示例1

输入：
nihao
ni
复制
输出：
le

```python3
letter=[chr((ord('a')+i)) for i in range(26)]

while True:
    try:
        key,encoder=input(),input()
        newkey=[]
        for s in key:
            if s not in newkey:
                newkey.append(s)
        for s in letter:
            if s not in newkey:
                newkey.append(s)
        encodeDic={}
        for i in range(len(newkey)):
            encodeDic[letter[i]]=newkey[i]
        newencoder=''
        for s in encoder:
            newencoder+=encodeDic[s]
        print(newencoder)
    except:
        break
```

# HJ37 统计每个月兔子的总数
描述

有一只兔子，从出生后第3个月起每个月都生一只兔子，小兔子长到第三个月后每个月又生一只兔子，假如兔子都不死，问第n个月的兔子总数为多少？

本题有多组数据。

数据范围：每组输入满足 
输入描述：

多行输入，一行输入一个int型整数表示第n个月
输出描述：

每一行输出对应的兔子总数
示例1

输入：
1
2
3
4
5
9
复制
输出：
1
1
2
3
5
34

```python3
def func(n):
    if n<2:
        return 1
    else:
        return func(n-1)+func(n-2)
            
while True:
    try:
        month=int(input())
        n=month-1
        print(func(n))
    except:
        break
```

# HJ38 求小球落地5次后所经历的路程和第5次反弹的高度
描述

假设一个球从任意高度自由落下，每次落地后反跳回原高度的一半; 再落下, 求它在第5次落地时，共经历多少米?第5次反弹多高？
最后的误差判断是小数点6位

数据范围：输入的小球初始高度满足  ，且保证是一个整数
输入描述：

输入起始高度，int型
输出描述：

分别输出第5次落地时，共经过多少米第5次反弹多高
示例1

输入：
1
复制
输出：
2.875
0.03125

```python3
while True:
    try:
        n=int(input())
        print(n*2.875)
        print(n*0.03125)
    except:
        break
```

# HJ39 判断两个IP是否属于同一子网
描述

子网掩码是用来判断任意两台计算机的IP地址是否属于同一子网络的根据。
子网掩码与IP地址结构相同，是32位二进制数，其中网络号部分全为“1”和主机号部分全为“0”。利用子网掩码可以判断两台主机是否中同一子网中。若两台主机的IP地址分别与它们的子网掩码相“与”后的结果相同，则说明这两台主机在同一子网中。
示例：
I P 地址　 192.168.0.1
子网掩码　 255.255.255.0
转化为二进制进行运算：
I P 地址　  11000000.10101000.00000000.00000001
子网掩码　11111111.11111111.11111111.00000000
AND运算   11000000.10101000.00000000.00000000
转化为十进制后为：
192.168.0.0

I P 地址　 192.168.0.254
子网掩码　 255.255.255.0

转化为二进制进行运算：
I P 地址　11000000.10101000.00000000.11111110
子网掩码  11111111.11111111.11111111.00000000
AND运算  11000000.10101000.00000000.00000000
转化为十进制后为：
192.168.0.0
通过以上对两台计算机IP地址与子网掩码的AND运算后，我们可以看到它运算结果是一样的。均为192.168.0.0，所以这二台计算机可视为是同一子网络。

输入一个子网掩码以及两个ip地址，判断这两个ip地址是否是一个子网络。
若IP地址或子网掩码格式非法则输出1，若IP1与IP2属于同一子网络输出0，若IP1与IP2不属于同一子网络输出2。

注:
有效掩码与IP的性质为：
1. 掩码与IP每一段在 0 - 255 之间
2. 掩码的二进制字符串前缀为网络号，都由‘1’组成；后缀为主机号，都由'0'组成

本题有多组输入

输入描述：

多组输入，一组3行，第1行是输入子网掩码、第2，3行是输入两个ip地址
输出描述：

若IP地址或子网掩码格式非法则输出1，若IP1与IP2属于同一子网络输出0，若IP1与IP2不属于同一子网络输出2
示例1

输入：
255.255.255.0
192.168.224.256
192.168.10.4
255.0.0.0
193.194.202.15
232.43.7.59
255.255.255.0
192.168.0.254
192.168.0.1
复制
输出：
1
2
0
复制
说明：
对于第一个例子:
255.255.255.0
192.168.224.256
192.168.10.4
其中IP:192.168.224.256不合法，输出1

对于第二个例子:
255.0.0.0
193.194.202.15
232.43.7.59
2个与运算之后，不在同一个子网，输出2

对于第三个例子，2个与运算之后，如题目描述所示，在同一个子网，输出0

```python3
while True:
    try:
        x=list(map(int,input().split('.')))
        y=list(map(int,input().split('.')))
        z=list(map(int,input().split('.')))
        m,n=[],[]
        if x[0]!=255 or x[3]!=0 or max(x+y+z)>255 or min(x+y+z)<0:
            print('1')
        else:
            for i in range(len(x)):
                x[i]=bin(x[i]).replace('0b','')
                y[i]=bin(y[i]).replace('0b','')
                z[i]=bin(z[i]).replace('0b','')
                m.append(int(x[i],2)&int(y[i],2))
                n.append(int(x[i],2)&int(z[i],2))
            if n==m:
                print('0')
            else:
                print('2')
    except:
        break
```

# HJ40 统计字符
描述

输入一行字符，分别统计出包含英文字母、空格、数字和其它字符的个数。
本题包含多组输入。
数据范围：输入的字符串长度满足 
输入描述：

输入一行字符串，可以有空格
输出描述：

统计其中英文字符，空格字符，数字字符，其他字符的个数
示例1

输入：
1qazxsw23 edcvfr45tgbn hy67uj m,ki89ol.\\/;p0-=\\][
复制
输出：
26
3
10
12

```python3
while True:
    try:
        s=input()
        l=[0,0,0]
        for i in s:
            l[0]+=int(i.isalpha())
            l[1]+=int(i==' ')
            l[2]+=int(i.isnumeric())
        print(l[0])
        print(l[1])
        print(l[2])
        print(len(s)-l[0]-l[1]-l[2])
    except:
        break
```
# HJ41 称砝码
描述

现有一组砝码，重量互不相等，分别为 m1,m2,m3…mn ；
每种砝码对应的数量为 x1,x2,x3...xn 。现在要用这些砝码去称物体的重量(放在同一侧)，问能称出多少种不同的重量。
注：
称重重量包括 0 

本题有多组输入

数据范围：每组输入数据满足  ，  ， 
输入描述：

输入包含多组测试数据。
对于每组测试数据：
第一行：n --- 砝码数(范围[1,10])
第二行：m1 m2 m3 ... mn --- 每个砝码的重量(范围[1,2000])
第三行：x1 x2 x3 .... xn --- 每个砝码的数量(范围[1,6])
输出描述：

利用给定的砝码可以称出的不同的重量数
示例1

输入：
2
1 2
2 1
10
4 185 35 191 26 148 149 3 172 147
3 5 2 1 5 5 3 1 4 2
复制
输出：
5
3375

```python3
while True:
    try:
        n = int(input())
        m = list(map(int,input().split()))
        x = list(map(int,input().split()))
    except:
        break
    else:
        amount = []
        weights = {0,}
        for i in range(n):
            for j in range(x[i]):
                amount.append(m[i])
                
        for i in amount:
            for j in list(weights):
                weights.add(i+j)
        print(len(weights))
```

# HJ42 学英语
描述

Jessi初学英语，为了快速读出一串数字，编写程序将数字转换成英文：

具体规则如下:
1.在英语读法中三位数字看成一整体，后面再加一个计数单位。从最右边往左数，三位一单位，例如12,345 等
2.每三位数后记得带上计数单位 分别是thousand, million, billion.
3.公式：百万以下千以上的数 X thousand X, 10亿以下百万以上的数：X million X thousand X, 10 亿以上的数：X billion X million X thousand X. 每个X分别代表三位数或两位数或一位数。
4.在英式英语中百位数和十位数之间要加and，美式英语中则会省略，我们这个题目采用加上and，百分位为零的话，这道题目我们省略and

下面再看几个数字例句：
22: twenty two
100:  one hundred 
145:  one hundred and forty five
1,234:  one thousand two hundred and thirty four
8,088:  eight thousand (and) eighty eight (注:这个and可加可不加，这个题目我们选择不加)
486,669:  four hundred and eighty six thousand six hundred and sixty nine
1,652,510:  one million six hundred and fifty two thousand five hundred and ten

说明：
数字为正整数，不考虑小数，转化结果为英文小写；
保证输入的数据合法
关键字提示：and，billion，million，thousand，hundred。

数据范围：

本题含有多组输入数据。

输入描述：

输入多行long型整数
输出描述：

输出相应的英文写法
示例1

输入：
22
100
145
1234
8088
486669
1652510
复制
输出：
twenty two
one hundred
one hundred and forty five
one thousand two hundred and thirty four
eight thousand eighty eight
four hundred and eighty six thousand six hundred and sixty nine
one million six hundred and fifty two thousand five hundred and ten

```python3
num1 = ['zero','one','two','three','four','five','six',
       'seven','eight','nine','ten','eleven','twelve',
       'thirteen','fourteen','fifteen','sixteen',
       'seventeen','eighteen','nineteen']
num2 = [0,0,'twenty','thirty','forty','fifty','sixty',
       'seventy','eighty','ninety']

# 100以内转英文
def n2w(n):
    if n > 0:
        if n < 20:
            word.append(num1[n])
        else:
            word.append(num2[n//10])
            if n%10 != 0:
                word.append(num1[n%10])

# 1000以内转英文
def hun(n):
    if n >= 100:
        word.append(num1[n//100])
        word.append('hundred')
        if n % 100 != 0:
            word.append('and')
    n2w(n%100)

while True:
    try:
        n = int(input())
    except:
        break
    else:
        word = []
        a = n % 1000  # 个十百位
        b = (n//1000) % 1000  # 个十百千
        c = (n//1000000) % 1000  #个十百m
        d = n // 1000000000    # 个十百b
        
        if d > 0:
            hun(d)
            word.append('billion')
        if c > 0 :
            hun(c)
            word.append('million')
        if b > 0:
            hun(b)
            word.append('thousand')
        if a > 0 :
            hun(a)
        print(' '.join(word))
```

# HJ43 迷宫问题
描述

定义一个二维数组 N*M ，如 5 × 5 数组下所示：

int maze[5][5] = {
0, 1, 0, 0, 0,
0, 1, 1, 1, 0,
0, 0, 0, 0, 0,
0, 1, 1, 1, 0,
0, 0, 0, 1, 0,
};

它表示一个迷宫，其中的1表示墙壁，0表示可以走的路，只能横着走或竖着走，不能斜着走，要求编程序找出从左上角到右下角的路线。入口点为[0,0],既第一格是可以走的路。

本题含有多组数据。

数据范围：  ， 输入的内容只包含 
输入描述：

输入两个整数，分别表示二维数组的行数，列数。再输入相应的数组，其中的1表示墙壁，0表示可以走的路。数据保证有唯一解,不考虑有多解的情况，即迷宫只有一条通道。
输出描述：

左上角到右下角的最短路径，格式如样例所示。
示例1

输入：
5 5
0 1 0 0 0
0 1 1 1 0
0 0 0 0 0
0 1 1 1 0
0 0 0 1 0
复制
输出：
(0,0)
(1,0)
(2,0)
(2,1)
(2,2)
(2,3)
(2,4)
(3,4)
(4,4)

```python3
def sol43():
    W = lambda x, y: (x - 1, y)
    S = lambda x, y: (x + 1, y)
    A = lambda x, y: (x, y - 1)
    D = lambda x, y: (x, y + 1)
    [N, M] = map(int, input().strip().split(' '))
    end = (N - 1, M - 1)

    def start2end(m, s, p):
        # find child
        child, v = [], list(p)
        for F in [W, A, S, D]:
            t = (F(s[0],s[1]))
            if not (0 <= t[0] < N and 0 <= t[1] < M):
                continue
            if not m[t[0]][t[1]] and (t not in v):
                if t == end:
                    p.append(end)
                    for pp in p:
                        print('(%d,%d)' %(pp[0],pp[1]))
                    return
                else:  # Enter the child node
                    child.append(t)
        if not child:
            # no child exit
            return
        for t in child:
            p_old = p.copy()
            p_old.append(t)
            start2end(m, t, p_old)

    maze = []
    for i in range(N):
        maze.append(list(map(int, input().strip().split(' '))))
    paths = [(0,0)]
    start2end(maze, (0,0), paths)
    return


if __name__ == '__main__':
    while True:
        try:
            sol43()
        except EOFError as e:
            # print(e)
            break
```

# HJ44 Sudoku
描述

问题描述：数独（Sudoku）是一款大众喜爱的数字逻辑游戏。玩家需要根据9X9盘面上的已知数字，推算出所有剩余空格的数字，并且满足每一行、每一列、每一个3X3粗线宫内的数字均含1-9，并且不重复。
例如：
输入

输出


数据范围：输入一个 9*9 的矩阵
输入描述：

包含已知数字的9X9盘面数组[空缺位以数字0表示]
输出描述：

完整的9X9盘面数组
示例1

输入：
0 9 2 4 8 1 7 6 3
4 1 3 7 6 2 9 8 5
8 6 7 3 5 9 4 1 2
6 2 4 1 9 5 3 7 8
7 5 9 8 4 3 1 2 6
1 3 8 6 2 7 5 9 4
2 7 1 5 3 8 6 4 9
3 8 6 9 1 4 2 5 7
0 4 5 2 7 6 8 3 1
复制
输出：
5 9 2 4 8 1 7 6 3
4 1 3 7 6 2 9 8 5
8 6 7 3 5 9 4 1 2
6 2 4 1 9 5 3 7 8
7 5 9 8 4 3 1 2 6
1 3 8 6 2 7 5 9 4
2 7 1 5 3 8 6 4 9
3 8 6 9 1 4 2 5 7
9 4 5 2 7 6 8 3 1

```python3
import copy

class Solution:
    def __init__(self):
        self.matrix = []
        self.queue = []
        self.matrix_bk = []
        self.init_matrix()
    
    def init_matrix(self):
        for _ in range(9):
            self.matrix.append(list(map(int, input().strip().split())))
        self.update_queue()
    
    def get_candidates(self, i, j):
        assert self.matrix[i][j] == 0
        cand0 = set(list(range(10))) - set(self.matrix[i])
        cand1 = set(list(range(10))) - set([self.matrix[k][j] for k in range(9)])
        cand2 = set(list(range(10))) - set([self.matrix[p][q] \
                                            for p in range(i // 3 * 3, i // 3 * 3 + 3) \
                                            for q in range(j // 3 * 3, j // 3 * 3 + 3)])
        return list(cand0 & cand1 & cand2)
    
    def update_queue(self):
        self.queue.clear()
        for i in range(9):
            for j in range(9):
                if self.matrix[i][j] == 0:
                    self.queue.append(((i, j), self.get_candidates(i, j)))
        self.queue.sort(key=lambda item : len(item[1]))
    
    def print_matrix(self):
        for line in self.matrix:
            print(' '.join(list(map(str, line))))
            
    def reload(self):
        self.matrix = self.matrix_bk
        self.update_queue()
    
    def dfs(self):
        while len(self.queue) > 0 and len(self.queue[0][1]) == 1:
            i, j = self.queue[0][0]
            self.matrix[i][j] = self.queue[0][1][0]
            self.queue.pop(0)
        self.update_queue()
        if len(self.queue) == 0:
            self.print_matrix()
            return True
        if len(self.queue[0][1]) == 0:
            return False
        queue_item = copy.deepcopy(self.queue[0])
        self.matrix_bk = copy.deepcopy(self.matrix)
        for cand in queue_item[1]:
            i, j = queue_item[0]
            self.matrix[i][j] = cand
            self.update_queue()
            if self.dfs():
                return True
            else:
                self.reload()
                
Solution().dfs()
```

# HJ45 名字的漂亮度
描述

给出一个名字，该名字有26个字符组成，定义这个字符串的“漂亮度”是其所有字母“漂亮度”的总和。 
每个字母都有一个“漂亮度”，范围在1到26之间。没有任何两个不同字母拥有相同的“漂亮度”。字母忽略大小写。
给出多个名字，计算每个名字最大可能的“漂亮度”。

本题含有多组数据。

数据范围：输入的名字长度满足 

输入描述：

整数N，后续N个名字
输出描述：

每个名称可能的最大漂亮程度
示例1

输入：
2
zhangsan
lisi
复制
输出：
192
101

```python3
while True:
    try:
        n = int(input())
        for i in range(n):
            s = input().strip()
            d = {}
            for i in s:
                if i in d.keys():
                    d[i]+=1
                else:
                    d[i]=1
            l = sorted(d.values(),reverse=True)
        #     print(l)
            Sum = 0
            a = 26
            for i in l:
                Sum += a*i
                a -= 1
            print(Sum)
    except:
        break
```

# HJ46 截取字符串
描述

输入一个字符串和一个整数 k ，截取字符串的前k个字符并输出

本题输入含有多组数据

数据范围：字符串长度满足  ， 
输入描述：

1.输入待截取的字符串
2.输入一个正整数k，代表截取的长度
输出描述：

截取后的字符串
示例1

输入：
abABCcDEF
6
复制
输出：
abABCc

```python3
while True:
    try:
        #获取输入字符
        data1 = input()
        #获取正整数k
        k = int(input())
        list1 = []
        for i in range(k):
            list1.append(data1[i])
        print(''.join(list1))
    except:
        break

```

# HJ48 从单向链表中删除指定值的节点
描述

输入一个单向链表和一个节点的值，从单向链表中删除等于该值的节点，删除后如果链表中无节点则返回空指针。
链表的值不能重复。
构造过程，例如输入一行数据为:
6 2 1 2 3 2 5 1 4 5 7 2 2
则第一个参数6表示输入总共6个节点，第二个参数2表示头节点值为2，剩下的2个一组表示第2个节点值后面插入第1个节点值，为以下表示:
1 2 表示为
2->1
链表为2->1

3 2表示为
2->3
链表为2->3->1

5 1表示为
1->5
链表为2->3->1->5

4 5表示为
5->4
链表为2->3->1->5->4

7 2表示为
2->7
链表为2->7->3->1->5->4

最后的链表的顺序为 2 7 3 1 5 4

最后一个参数为2，表示要删掉节点为2的值
删除 结点 2
则结果为 7 3 1 5 4

数据范围：链表长度满足  ，节点中的值满足 

测试用例保证输入合法

输入描述：

输入一行，有以下4个部分：
1 输入链表结点个数
2 输入头结点的值
3 按照格式插入各个结点
4 输入要删除的结点的值
输出描述：

输出一行
输出删除结点后的序列，每个数后都要加空格
示例1

输入：
5 2 3 2 4 3 5 2 1 4 3
复制
输出：
2 5 4 1
复制
说明：
形成的链表为2->5->3->4->1
删掉节点3，返回的就是2->5->4->1 
```python3
while True:
    try:
        s=input().split()
        mm,l,k=int(s.pop(0)),[s.pop(0)],s.pop(-1)
        for i in range(0,2*mm-2,2):
            n,m=s[i],s[i+1]
            l.insert(l.index(m)+1,n) 
        l.remove(k)
        print(" ".join(l)+" ")
    except:
        break
```

# HJ50 四则运算
描述

输入一个表达式（用字符串表示），求这个表达式的值。
保证字符串中的有效字符包括[‘0’-‘9’],‘+’,‘-’, ‘*’,‘/’ ,‘(’， ‘)’,‘[’, ‘]’,‘{’ ,‘}’。且表达式一定合法。

数据范围：表达式计算结果和过程中满足  ，字符串长度满足 
输入描述：

输入一个算术表达式
输出描述：

得到计算结果
示例1

输入：
3+2*{1+2*[-4/(8-6)+7]}
复制
输出：
25

```python3
while True:
    try:
        s=input()
        s=s.replace('{', '(')
        s=s.replace("}",")")
        s=s.replace("[","(")
        s=s.replace("]",")")
        print(int(eval(s)))
    except:
        break
```




























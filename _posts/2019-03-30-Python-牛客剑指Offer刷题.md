---
layout:     post
title:      刷题 牛客剑指Offer
subtitle:   刷题 牛客剑指Offer刷题Python
date:       2019-3-30
author:     Hugo Yu
header-img: 
catalog: true
tags:
    - Python
    - 刷题
---
# 题目
数组 	二维数组中的查找 	110385 	23.35%
## 题目描述
在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    # array 二维列表
    def Find(self, target, array):
        flag = False
        for i in range(len(array)):
            if target in array[i]:
                flag = True
                break
        return flag

```
# 题目
字符串 	替换空格 	102326 	24.00%
## 题目描述
请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    # s 源字符串
    def replaceSpace(self, s):
        # write code here
        return s.replace(" ","%20")
```
# 题目 
链表 	从尾到头打印链表 	88420 	23.73%
## 题目描述
输入一个链表，按链表值从尾到头的顺序返回一个ArrayList。
## 答案

```
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # 返回从尾部到头部的列表值序列，例如[1,2,3]
    def printListFromTailToHead(self, listNode):
        # write code here
        result = []
        while listNode!=None:
            result.insert(0,listNode.val)
            listNode = listNode.next
        return result
```


# 题目
树 	重建二叉树 	61351 	22.29%
## 题目描述
输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，则重建二叉树并返回。
## 答案

```
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    # 返回构造的TreeNode根节点
    def reConstructBinaryTree(self, pre, tin):
        # write code here
        if len(pre) == 0:
            return None
        elif len(pre) == 1:
            return TreeNode(pre[0])
        else:
            Node = TreeNode(pre[0])
            Node.left = self.reConstructBinaryTree(pre[1:tin.index(pre[0])+1],tin[:tin.index(pre[0])])
            Node.right = self.reConstructBinaryTree(pre[tin.index(pre[0])+1:],tin[tin.index(pre[0])+1:])
        return Node
            
```
# 题目
栈和队列 	用两个栈实现队列 	69627 	35.67%
## 题目描述
用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。
## 答案


```
# -*- coding:utf-8 -*-
class Solution:
    def __init__(self):
        self.stack1 = []
        self.stack2 = []
    def push(self, node):
        # write code here
        self.stack1.append(node)
    def pop(self):
        # return xx
        if self.stack2 == []:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
            return self.stack2.pop()
        return self.stack2.pop()
```
# 题目
查找和排序 	旋转数组的最小数字 	65770 	31.41%
## 题目描述
把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。 输入一个非减排序的数组的一个旋转，输出旋转数组的最小元素。 例如数组{3,4,5,1,2}为{1,2,3,4,5}的一个旋转，该数组的最小值为1。 NOTE：给出的所有元素都大于0，若数组大小为0，请返回0。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def minNumberInRotateArray(self, rotateArray):
        # write code here
        if len(rotateArray)>1:
            for i in range(len(rotateArray)-1):
                if rotateArray[i] > rotateArray[i+1]:
                    return rotateArray[i+1]
        elif len(rotateArray)>0:
            return rotateArray[0]
        else:
            return 0
```
# 题目
递归和循环 	斐波那契数列 	73386 	28.13%

## 题目描述
大家都知道斐波那契数列，现在要求输入一个整数n，请你输出斐波那契数列的第n项（从0开始，第0项为0）。

n<=39 
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def Fibonacci(self, n):
        # write code here
        a = 0
        b = 1
        for i in range(n):
            a,b = b,a+b
        return a

```
# 题目
递归和循环 	跳台阶 	73755 	33.67%
## 题目描述
一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法（先后次序不同算不同的结果）。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def jumpFloor(self, number):
        # write code here
        a = 1
        b = 1
        for i in range(number):
            a,b = b,a+b
        return a

```
## 解析
 对于本题,前提只有 一次 1阶或者2阶的跳法。

a.如果两种跳法，1阶或者2阶，那么假定第一次跳的是一阶，那么剩下的是n-1个台阶，跳法是f(n-1);

b.假定第一次跳的是2阶，那么剩下的是n-2个台阶，跳法是f(n-2)

c.由a\b假设可以得出总跳法为: f(n) = f(n-1) + f(n-2) 

d.然后通过实际的情况可以得出：只有一阶的时候 f(1) = 1 ,只有两阶的时候可以有 f(2) = 2

e.可以发现最终得出的是一个斐波那契数列：


# 题目
递归和循环 	变态跳台阶 	66474 	39.71%
## 题目描述
一只青蛙一次可以跳上1级台阶，也可以跳上2级……它也可以跳上n级。求该青蛙跳上一个n级的台阶总共有多少种跳法。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def jumpFloorII(self, number):
        # write code here
        if number > 0:
            return (pow(2,number-1))

```
## 解析
 关于本题，前提是n个台阶会有一次n阶的跳法。分析如下:

f(1) = 1

f(2) = f(2-1) + f(2-2)         //f(2-2) 表示2阶一次跳2阶的次数。

f(3) = f(3-1) + f(3-2) + f(3-3) 

...

f(n) = f(n-1) + f(n-2) + f(n-3) + ... + f(n-(n-1)) + f(n-n) 

 

说明： 

1）这里的f(n) 代表的是n个台阶有一次1,2,...n阶的 跳法数。

2）n = 1时，只有1种跳法，f(1) = 1

3) n = 2时，会有两个跳得方式，一次1阶或者2阶，这回归到了问题（1） ，f(2) = f(2-1) + f(2-2) 

4) n = 3时，会有三种跳得方式，1阶、2阶、3阶，

    那么就是第一次跳出1阶后面剩下：f(3-1);第一次跳出2阶，剩下f(3-2)；第一次3阶，那么剩下f(3-3)

    因此结论是f(3) = f(3-1)+f(3-2)+f(3-3)

5) n = n时，会有n中跳的方式，1阶、2阶...n阶，得出结论：

    f(n) = f(n-1)+f(n-2)+...+f(n-(n-1)) + f(n-n) => f(0) + f(1) + f(2) + f(3) + ... + f(n-1)

    

6) 由以上已经是一种结论，但是为了简单，我们可以继续简化：

    f(n-1) = f(0) + f(1)+f(2)+f(3) + ... + f((n-1)-1) = f(0) + f(1) + f(2) + f(3) + ... + f(n-2)

    f(n) = f(0) + f(1) + f(2) + f(3) + ... + f(n-2) + f(n-1) = f(n-1) + f(n-1)

    可以得出：

    f(n) = 2*f(n-1)

    

7) 得出最终结论,在n阶台阶，一次有1、2、...n阶的跳的方式时，总得跳法为：
f(n) = 1         (n=0)
     = 1         (n=1)
     = 2*f(n-1)  (n>=2)
# 题目
递归和循环 	矩形覆盖 	59126 	34.42%
## 题目描述
我们可以用2\*1的小矩形横着或者竖着去覆盖更大的矩形。请问用n个2\*1的小矩形无重叠地覆盖一个2*n的大矩形，总共有多少种方法？
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def rectCover(self, number):
        # write code here
        if number<=0:
            return 0
        else:
            a=0
            b=1
            for i in range(number):
                a,b = b,a+b
            return b

```
## 解析
![image](https://uploadfiles.nowcoder.com/images/20170718/3614591_1500381257269_B18DB55610F4CC5E67C96674FE51EBDC)
# 题目
位运算 	二进制中1的个数 	63607 	34.15%
## 题目描述
输入一个整数，输出该数二进制表示中1的个数。其中负数用补码表示。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def NumberOf1(self, n):
        # write code here
        return bin(n).count("1") if n>=0 else bin(2**32+n).count("1")

```
## 解析：
python中的三目运算符为：x if expr else y
# 题目
代码的完整性 	数值的整数次方 	58055 	30.95%
## 题目描述
给定一个double类型的浮点数base和int类型的整数exponent。求base的exponent次方。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def Power(self, base, exponent):
        # write code here
        return base**exponent
```

# 题目
代码的完整性 	调整数组顺序使奇数位于偶数前面 	58479 	25.32%
## 题目描述
输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前半部分，所有的偶数位于数组的后半部分，并保证奇数和奇数，偶数和偶数之间的相对位置不变。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def reOrderArray(self, array):
        # write code here
        odd = []
        even = []
        for num in array:
            if num % 2 == 0:
                even.append(num)
            else:
                odd.append(num)
        return odd+even
```

```
# -*- coding:utf-8 -*-
class Solution:
    def reOrderArray(self, array):
        # write code here
        for i in range(0,len(array)):
            for j in range(len(array)-1,i,-1):
                if array[j-1]%2 ==0 and array[j]%2==1:
                    temp = array[j-1]
                    array[j-1] = array[j]
                    array[j] = temp
        return array
```

# 题目
代码的完整性 	调整数组顺序使奇数位于偶数前面 	58479 	25.32%
## 题目描述
输入一个链表，输出该链表中倒数第k个结点。
## 答案

```
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def FindKthToTail(self, head, k):
        # write code here
        
        stack = []
        while head!=None:
            stack.append(head)
            head=head.next
        if k<=len(stack) and k>=1:
            return stack[-k]
```

# 题目
代码的鲁棒性 	链表中倒数第k个结点 	59925 	20.33%
## 题目描述
输入一个链表，输出该链表中倒数第k个结点。
## 答案

```
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def FindKthToTail(self, head, k):
        # write code here
        stack = []
        while head!=None:
            stack.append(head)
            head=head.next
        if k<=len(stack) and k>=1:
            return stack[-k]
```


```
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def FindKthToTail(self, head, k):
        # write code here
        if k >0 and head != None:
            first = head
            second = head
            for i in range(k-1):
                if second.next != None:
                    second = second.next
                else:
                    return None
            while second.next!=None:
                second = second.next
                first = first.next
            return first
                
```


# 题目
代码的鲁棒性 	反转链表 	58251 	28.36%
## 题目描述
输入一个链表，反转链表后，输出新链表的表头。
## 答案

```
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    # 返回ListNode
    def ReverseList(self, pHead):
        # write code here
        if pHead == None or pHead.next == None:
            return pHead
        last = None
        while pHead:
            temp = pHead.next
            pHead.next = last
            last = pHead
            pHead = temp
        return last
```

# 题目
代码的鲁棒性 	合并两个排序的链表 	53937 	26.77%
## 题目描述
输入两个单调递增的链表，输出两个链表合成后的链表，当然我们需要合成后的链表满足单调不减规则。
## 答案

```
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    # 返回合并后列表
    def Merge(self, pHead1, pHead2):
        # write code here
        mergeNode = ListNode(0)
        listNOde = mergeNode
        while pHead1 and pHead2:
            if pHead1.val <= pHead2.val:
                mergeNode.next = pHead1
                pHead1 = pHead1.next
            else:
                mergeNode.next = pHead2
                pHead2 = pHead2.next
            mergeNode = mergeNode.next
        if pHead1:
            mergeNode.next = pHead1
        if pHead2:
            mergeNode.next =  pHead2
        return listNOde.next
            
```
# 题目
代码的鲁棒性 	树的子结构 	46285 	22.72%
## 题目描述
输入两棵二叉树A，B，判断B是不是A的子结构。（ps：我们约定空树不是任意一个树的子结构）
## 答案

```
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    def HasSubtree(self, pRoot1, pRoot2):
        # write code here
        result = False
        if pRoot1 and pRoot2:
            if pRoot1.val == pRoot2.val:
                result = self.F(pRoot1,pRoot2)
            if not result:
                result = self.HasSubtree(pRoot1.left,pRoot2)
            if not result:
                result = self.HasSubtree(pRoot1.right,pRoot2)
        return result
    def F(self,node1,node2):
        if node2==None:
            return True
        elif node1==None:
            return False
        elif node1.val != node2.val:
            return False
        return self.F(node1.left,node2.left) and self.F(node1.right,node2.right)
```

# 题目
面试思路 	二叉树的镜像 	51123 	42.34%
## 题目描述
操作给定的二叉树，将其变换为源二叉树的镜像。
<br>二叉树的镜像定义：源二叉树 
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;8
<br/>&nbsp;&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;&nbsp;&nbsp;\\
<br/>&nbsp;&nbsp;&nbsp;6&nbsp;&nbsp;&nbsp;10
<br/>&nbsp;&nbsp;/&nbsp;&nbsp;\\&nbsp;&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;\\
<br/>5&nbsp;&nbsp;7&nbsp;&nbsp;9&nbsp;&nbsp;11
<br/>镜像二叉树
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;8
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;&nbsp;&nbsp;\\
<br/>&nbsp;&nbsp;&nbsp;&nbsp;10&nbsp;&nbsp;&nbsp;&nbsp;6
<br/>&nbsp;&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;\\&nbsp;&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;\\
<br/>11&nbsp;&nbsp;9&nbsp;&nbsp;7&nbsp;&nbsp;&nbsp;&nbsp;5

## 答案

```
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    # 返回镜像树的根节点
    def Mirror(self, root):
        # write code here
        if root == None:
            return None
        if root.left or root.right:
            tmp = root.left
            root.left = root.right
            root.right = tmp
            self.Mirror(root.left)
            self.Mirror(root.right)
        
```


# 题目
画图让抽象形象化 	顺时针打印矩阵 	41807 	17.27%
## 题目描述
输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字，例如，如果输入如下4 X 4矩阵： 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 则依次打印出数字1,2,3,4,8,12,16,15,14,13,9,5,6,7,11,10.
## 答案

# 题目
举例让抽象具体化 	包含min函数的栈 	42835 	30.90%
## 题目描述
定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def __init__(self):
        self.stack = []
        self.min_stack = []
    def push(self, node):
        # write code here
        if not self.min_stack or node < self.min_stack[-1]:
            self.min_stack.append(node)
        self.stack.append(node)
    def pop(self):
        # write code here
        if self.stack[-1] == self.min_stack[-1]:
            self.min_stack.pop()
        self.stack.pop()
    def top(self):
        # write code here
        return self.stack[-1]
    def min(self):
        # write code here
        return self.min_stack[-1]
```


# 题目
举例让抽象具体化 	栈的压入、弹出序列 	43534 	28.37%
## 题目描述
输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否可能为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如序列1,2,3,4,5是某栈的压入顺序，序列4,5,3,2,1是该压栈序列对应的一个弹出序列，但4,3,5,1,2就不可能是该压栈序列的弹出序列。（注意：这两个序列的长度是相等的）
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def IsPopOrder(self, pushV, popV):
        # write code here
        if len(pushV) != len(popV):
            return False
        stack = []
        j = 0
        for i in range(len(pushV)):
            stack.append(pushV[i])
            while stack and popV[j] == stack[-1]:
                j+=1
                stack.pop()
        if stack:
            return False
        else:
            return True
                
            
```

# 题目
举例让抽象具体化 	从上往下打印二叉树 	44789 	26.24%
## 题目描述
从上往下打印出二叉树的每个节点，同层节点从左至右打印。
## 答案

```
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    # 返回从上到下每个节点值列表，例：[1,2,3]
    def PrintFromTopToBottom(self, root):
        # write code here
        queue = []
        valList = []
        if not root:
            return valList
        queue.append(root)
        while queue:
            root = queue.pop(0)
            valList.append(root.val)
            if root.left:
                queue.append(root.left)
            if root.right:
                queue.append(root.right)
        return valList
```
# 题目
举例让抽象具体化 	二叉搜索树的后序遍历序列 	39061 	23.35%
## 题目描述
输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历的结果。如果是则输出Yes,否则输出No。假设输入的数组的任意两个数字都互不相同。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def VerifySquenceOfBST(self, sequence):
        # write code here
        if not sequence:
            return False
        if len(sequence) == 1:
            return True
        root = sequence[-1]
        i = 0 
        while sequence[i] < root:
            i+=1
        k = i
        for j in range(i,len(sequence)-1):
            if sequence[j] < root:
                return False
        left_sequence = sequence[0:k]
        right_sequence = sequence[k:-1]
        left = True
        right = True
        if len(left_sequence) > 0:
            left = self.VerifySquenceOfBST(left_sequence)
        if len(right_sequence) > 0:
            right = self.VerifySquenceOfBST(right_sequence)
        return left and right
           
```


# 题目
举例让抽象具体化 	二叉树中和为某一值的路径 	36466 	25.85%
## 题目描述
输入一颗二叉树的跟节点和一个整数，打印出二叉树中结点值的和为输入整数的所有路径。路径定义为从树的根结点开始往下一直到叶结点所经过的结点形成一条路径。(注意: 在返回值的list中，数组长度大的数组靠前)
## 答案

```
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    # 返回二维列表，内部每个列表表示找到的路径
    def FindPath(self, root, expectNumber):
        # write code here
        if not root:
            return []
        if root and not root.left and not root.right and expectNumber == root.val:
            return [[root.val]]
        res = []
        left = self.FindPath(root.left,expectNumber-root.val)
        right = self.FindPath(root.right,expectNumber-root.val)
        for i in left + right:
            res.append([root.val]+i)
        return res
```


# 题目
分解让复杂问题简单 	复杂链表的复制 	30698 	20.58%
## 题目描述
输入一个复杂链表（每个节点中有节点值，以及两个指针，一个指向下一个节点，另一个特殊指针指向任意一个节点），返回结果为复制后复杂链表的head。（注意，输出结果中请不要返回参数中的节点引用，否则判题程序会直接返回空）
## 答案

# 题目
分解让复杂问题简单 	二叉搜索树与双向链表 	28666 	27.41%
## 题目描述
输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的双向链表。要求不能创建任何新的结点，只能调整树中结点指针的指向。
## 答案

```
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    def Convert(self, pRootOfTree):
        # write code here
        if not pRootOfTree:
            return pRootOfTree
        if not pRootOfTree.left and not pRootOfTree.right:
            return pRootOfTree
        self.Convert(pRootOfTree.left)
        left = pRootOfTree.left
        if left:
            while left.right:
                left = left.right
            pRootOfTree.left,left.right = left,pRootOfTree
        self.Convert(pRootOfTree.right)
        right = pRootOfTree.right
        if right:
            while right.left:
                right = right.left
            pRootOfTree.right,right.left = right,pRootOfTree
        
        while pRootOfTree.left:
            pRootOfTree = pRootOfTree.left
        return pRootOfTree
        
```


# 题目
分解让复杂问题简单 	字符串的排列 	32172 	19.66%
## 题目描述
输入一个字符串,按字典序打印出该字符串中字符的所有排列。例如输入字符串abc,则打印出由字符a,b,c所能排列出来的所有字符串abc,acb,bac,bca,cab和cba。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def Permutation(self, ss):
        # write code here
        if not ss:
            return 
        return sorted(list(set(map(''.join,itertools.permutations(ss)))))
```

# 题目
时间效率 	数组中出现次数超过一半的数字 	39158 	26.56%
## 题目描述
数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。例如输入一个长度为9的数组{1,2,3,2,2,2,5,4,2}。由于数字2在数组中出现了5次，超过数组长度的一半，因此输出2。如果不存在则输出0。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def MoreThanHalfNum_Solution(self, numbers):
        # write code here
        
        for i in set(numbers):
            if numbers.count(i) > (len(numbers)/2):
                return i
        return 0
```

# 题目
时间效率 	最小的K个数 	38592 	21.10%
## 题目描述
输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def GetLeastNumbers_Solution(self, tinput, k):
        # write code here
        if k > len(tinput):
            return []
        return sorted(tinput)[:k]
```

# 题目
时间效率 	连续子数组的最大和 	37253 	34.85%
## 题目描述
HZ偶尔会拿些专业问题来忽悠那些非计算机专业的同学。今天测试组开完会后,他又发话了:在古老的一维模式识别中,常常需要计算连续子向量的最大和,当向量全为正数的时候,问题很好解决。但是,如果向量中包含负数,是否应该包含某个负数,并期望旁边的正数会弥补它呢？例如:{6,-3,-2,7,-15,1,2,2},连续子向量的最大和为8(从第0个开始,到第3个为止)。给一个数组，返回它的最大连续子序列的和，你会不会被他忽悠住？(子向量的长度至少是1)
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def FindGreatestSumOfSubArray(self, array):
        # write code here
        pos = 0
        while pos < (len(array)) and array[pos] <0:
            pos += 1
        if pos ==len(array):
            return max(array)
        biggest = 0
        for i in range(0,len(array)):
            maxx = 0
            current = 0
            for j in range(i,len(array)):
                current += array[j]
                if maxx < current:
                    maxx = current
            if biggest <= maxx:
                biggest = maxx
        return biggest
            
```
# 题目
时间效率 	整数中1出现的次数（从1到n整数中1出现的次数） 	29760 	32.48%
## 题目描述
求出1~13的整数中1出现的次数,并算出100~1300的整数中1出现的次数？为此他特别数了一下1~13中包含1的数字有1、10、11、12、13因此共出现6次,但是对于后面问题他就没辙了。ACMer希望你们帮帮他,并把问题更加普遍化,可以很快的求出任意非负整数区间中1出现的次数（从1 到 n 中1出现的次数）。
## 答案

# 题目
时间效率 	把数组排成最小的数 	30220 	26.25%
## 题目描述
输入一个正整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。例如输入数组{3，32，321}，则打印出这三个数字能排成的最小数字为321323。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def PrintMinNumber(self, numbers):
        # write code here
        if not numbers:
            return ""
        lmb = lambda n1,n2:int(str(n1)+str(n2))-int(str(n2)+str(n1))
        array = sorted(numbers,cmp=lmb)
        return ''.join([str(i) for i in array])
```

# 题目
时间空间效率的平衡 	丑数 	30594 	21.16%
## 题目描述
把只包含质因子2、3和5的数称作丑数（Ugly Number）。例如6、8都是丑数，但14不是，因为它包含质因子7。 习惯上我们把1当做是第一个丑数。求按从小到大的顺序的第N个丑数。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def PrintMinNumber(self, numbers):
        # write code here
        if not numbers:
            return ""
        lmb = lambda n1,n2:int(str(n1)+str(n2))-int(str(n2)+str(n1))
        array = sorted(numbers,cmp=lmb)
        return ''.join([str(i) for i in array])
```

# 题目
时间空间效率的平衡 	第一个只出现一次的字符位置 	33093 	25.17%
## 题目描述
在一个字符串(0<=字符串长度<=10000，全部由字母组成)中找到第一个只出现一次的字符,并返回它的位置, 如果没有则返回 -1（需要区分大小写）.
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def FirstNotRepeatingChar(self, s):
        # write code here
        for i in s:
            if s.count(i) == 1:
                return s.index(i)
        return -1
```

# 题目
时间空间效率的平衡 	数组中的逆序对 	25287 	14.94%
## 题目描述
在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组,求出这个数组中的逆序对的总数P。并将P对1000000007取模的结果输出。 即输出P%1000000007
输入描述:

题目保证输入的数组中没有的相同的数字

数据范围：

	对于%50的数据,size<=10^4

	对于%75的数据,size<=10^5

	对于%100的数据,size<=2*10^5
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def InversePairs(self, data):
        # write code here
        return self.inverseCount(data[:], 0, len(data)-1, data[:])%1000000007
    def inverseCount(self, tmp, start, end, data):
        if end-start <1:
            return 0
        if end - start == 1:
            if data[start]<=data[end]:
                return 0
            else:
                tmp[start], tmp[end] = data[end], data[start]
                return 1
        mid = (start+end)//2
        cnt = self.inverseCount(data, start, mid, tmp) + self.inverseCount(data, mid+1, end, tmp)
        # print(start, mid, end, cnt, data)
        i = start
        j = mid + 1
        ind = start
          
        while(i <= mid and j <= end):
            if data[i] <= data[j]:
                tmp[ind] = data[i]
                i += 1
            else:
                tmp[ind] = data[j]
                cnt += mid - i + 1
                j += 1
            ind += 1
        while(i<=mid):
            tmp[ind] = data[i]
            i += 1
            ind += 1
        while(j<=end):
            tmp[ind] = data[j]
            j += 1
            ind += 1
        return cnt
```

# 题目
时间空间效率的平衡 	两个链表的第一个公共结点 	31304 	31.94%
## 题目描述
输入两个链表，找出它们的第一个公共结点。
## 答案
```
# -*- coding:utf-8 -*-
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    def FindFirstCommonNode(self, pHead1, pHead2):
        # write code here
        list1 = []
        list2 = []
        node1 = pHead1
        node2 = pHead2
        while node1:
            list1.append(node1.val)
            node1 = node1.next
        while node2:
            if node2.val in list1:
                return node2
            else:
                node2 = node2.next
```

# 题目
知识迁移能力 	数字在排序数组中出现的次数 	30993 	29.37%
## 题目描述
统计一个数字在排序数组中出现的次数。
## 答案

```
# -*- coding:utf-8 -*-
class Solution:
    def GetNumberOfK(self, data, k):
        # write code here
        return data.count(k)
        
```
# 题目
知识迁移能力 	二叉树的深度 	35717 	46.71%
## 题目描述
输入一棵二叉树，求该树的深度。从根结点到叶结点依次经过的结点（含根、叶结点）形成树的一条路径，最长路径的长度为树的深度。
## 答案
```
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    def TreeDepth(self, pRoot):
        # write code here
        if pRoot:
            return 1 + max(self.TreeDepth(pRoot.left),self.TreeDepth(pRoot.right))
        return 0
```
# 题目
知识迁移能力 	平衡二叉树 	29306 	33.53%
## 题目描述
输入一棵二叉树，判断该二叉树是否是平衡二叉树。
## 答案
```
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    def IsBalanced_Solution(self, pRoot):
        # write code here
        if not pRoot:
            return True
        leftHeight = self.getHeight(pRoot.left)
        rightHeight = self.getHeight(pRoot.right)
        if abs(leftHeight-rightHeight)>1:
            return False
        else:
            return True
    def getHeight(self,pRoot):
        if pRoot:
            return 1+max(self.getHeight(pRoot.left),self.getHeight(pRoot.right))
        return 0
        
```

# 题目
知识迁移能力 	数组中只出现一次的数字 	30804 	28.58%
## 题目描述
一个整型数组里除了两个数字之外，其他的数字都出现了偶数次。请写程序找出这两个只出现一次的数字。
## 答案
```
# -*- coding:utf-8 -*-
class Solution:
    # 返回[a,b] 其中ab是出现一次的两个数字
    def FindNumsAppearOnce(self, array):
        # write code here
        result = []
        for i in set(array):
            if array.count(i)%2:
                result.append(i)
        return result
```

# 题目
知识迁移能力 	和为S的连续正数序列 	27867 	26.14%
## 题目描述
小明很喜欢数学,有一天他在做数学作业时,要求计算出9~16的和,他马上就写出了正确答案是100。但是他并不满足于此,他在想究竟有多少种连续的正数序列的和为100(至少包括两个数)。没多久,他就得到另一组连续正数和为100的序列:18,19,20,21,22。现在把问题交给你,你能不能也很快的找出所有和为S的连续正数序列? Good Luck!
输出描述:
输出所有和为S的连续正数序列。序列内按照从小至大的顺序，序列间按照开始数字从小到大的顺序
## 答案
```
# -*- coding:utf-8 -*-
class Solution:
    def FindContinuousSequence(self, tsum):
        # write code here
        result = []
        if tsum < 3:
            return result
        i = 1
        while i<= tsum:
            tmp = []
            j = i
            while sum(tmp) < tsum:
                tmp.append(j)
                j+=1
            if sum(tmp) == tsum and len(tmp)>1:
                result.append(tmp)
            i+=1
        return result
            
```

# 题目
知识迁移能力 	和为S的两个数字 	30915 	28.52%
## 题目描述
输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。
输出描述:

对应每个测试案例，输出两个数，小的先输出。
## 答案
```
# -*- coding:utf-8 -*-
class Solution:
    def FindNumbersWithSum(self, array, tsum):
        # write code here
        ls = []
        if not isinstance(array, list):
            return ls
        for i, v in enumerate(array):
            for v1 in array[i:]:
                if (v + v1) == tsum:
                    ls.append([v, v1])
        if ls:
            return ls[0]
        else:
            return ls
```

# 题目
知识迁移能力 	左旋转字符串 	30425 	30.33%
## 题目描述
汇编语言中有一种移位指令叫做循环左移（ROL），现在有个简单的任务，就是用字符串模拟这个指令的运算结果。对于一个给定的字符序列S，请你把其循环左移K位后的序列输出。例如，字符序列S=”abcXYZdef”,要求输出循环左移3位后的结果，即“XYZdefabc”。是不是很简单？OK，搞定它！
## 答案
```
# -*- coding:utf-8 -*-
class Solution:
    def LeftRotateString(self, s, n):
        # write code here
        if len(s) < n:
            return s
        return s[n:]+s[:n]
```

# 题目
知识迁移能力 	翻转单词顺序列 	29929 	18.79%
## 题目描述
牛客最近来了一个新员工Fish，每天早晨总是会拿着一本英文杂志，写些句子在本子上。同事Cat对Fish写的内容颇感兴趣，有一天他向Fish借来翻看，但却读不懂它的意思。例如，“student. a am I”。后来才意识到，这家伙原来把句子单词的顺序翻转了，正确的句子应该是“I am a student.”。Cat对一一的翻转这些单词顺序可不在行，你能帮助他么？
## 答案
```
# -*- coding:utf-8 -*-
class Solution:
    def ReverseSentence(self, s):
        # write code here
        tmp = s.split(' ')
        return ' '.join(tmp[::-1])
```
# 题目
抽象建模能力 	扑克牌顺子 	23913 	24.97%
## 题目描述
LL今天心情特别好,因为他去买了一副扑克牌,发现里面居然有2个大王,2个小王(一副牌原本是54张^_^)...他随机从中抽出了5张牌,想测测自己的手气,看看能不能抽到顺子,如果抽到的话,他决定去买体育彩票,嘿嘿！！“红心A,黑桃3,小王,大王,方片5”,“Oh My God!”不是顺子.....LL不高兴了,他想了想,决定大\小 王可以看成任何数字,并且A看作1,J为11,Q为12,K为13。上面的5张牌就可以变成“1,2,3,4,5”(大小王分别看作2和4),“So Lucky!”。LL决定去买体育彩票啦。 现在,要求你使用这幅牌模拟上面的过程,然后告诉我们LL的运气如何， 如果牌能组成顺子就输出true，否则就输出false。为了方便起见,你可以认为大小王是0。
## 答案
```
# -*- coding:utf-8 -*-
class Solution:
    def IsContinuous(self, numbers):
        # write code here
        if not numbers:
            return False
        numbers.sort(reverse=True)
        joker = 0
        while numbers[-1] == 0:
            numbers.pop()
            joker += 1
        if len(set(numbers)) < 5-joker:
            return False
        if abs(numbers[0]-numbers[-1])>=5:
            return False
        return True
```




















































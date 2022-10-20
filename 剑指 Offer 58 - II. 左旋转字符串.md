## Description

     

字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"。

示例 1：

输入: s = "abcdefg", k = 2
输出: "cdefgab"
示例 2：

输入: s = "lrloseumgh", k = 6
输出: "umghlrlose"

限制：

1 <= k < s.length <= 10000

来源：力扣（LeetCode）
链接：[https://leetcode.cn/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof](https://leetcode.cn/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof)
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

## Solution

1. Algo#1

Idea

```
Main idea:
1) reverse 0-n-1 substring
2) reverse n-end substring
3) reverse total string     
```

Process:

![Untitled](https://code-thinking.cdn.bcebos.com/pics/%E5%89%91%E6%8C%87Offer58-II.%E5%B7%A6%E6%97%8B%E8%BD%AC%E5%AD%97%E7%AC%A6%E4%B8%B2.png)

There are 3 main solutions here

 1) using slicde arrary

 2) using reverse function

 3) self-define reverse function

Note: 

```
# 时间复杂度：O(n)
# 空间复杂度：O(n)，python的string为不可变，需要开辟同样大小的list空间来修改

```

Code:

```python
class Solution:
    def reverseLeftWords(self, s: str, n: int) -> str:
        # solution 1
        """
        arr = list(s)
        if n > len(arr):
            return s
        return ''.join(arr[n:] + arr[:n])
        """
        # solution #2
        # use reverse function
        """
        arr = list(s)
        arr[:n] = reversed(arr[:n])
        arr[n:] = reversed(arr[n:])
        arr.reverse()
        return ''.join(arr)
        """

        # solution # 3
        # use self-define reserver
        def reverse_sub(subarr, left, right):
            while left < right:
                subarr[left], subarr[right] = subarr[right], subarr[left]
                left += 1
                right -= 1
            

        arr = list(s)
        reverse_sub(arr, 0, n-1)       
        reverse_sub(arr,n,len(arr)-1)
        reverse_sub(arr,0,len(arr)-1)

        return ''.join(arr)
```


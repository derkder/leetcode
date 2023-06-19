292. Nim 游戏  
桌子上有一堆石头。你们轮流进行自己的回合， 你作为先手 。每一回合，轮到的人拿掉 1 - 3 块石头。拿掉最后一块石头的人就是获胜者。  
---

官解推导过程  
![](/一些奇妙的算法/Nim游戏官解思路.png)
  
'''
class Solution {
public:
    bool canWinNim(int n) {
        return n % 4 != 0;
    }
};
'''




## ！！要寻找任一个元素的右边&左边第一个比自己大或者小的元素的位置，此时我们就要想到可以用单调栈了  
//O(n)[小于对应递增栈，大于对应递减栈]！！  
    
##### ！！单调栈里存放的元素是什么？[坐标]    
  单调栈里只需要存放元素的下标i就可以了，如果需要使用对应的元素，直接T[i]就可以获取。    
      
##### 最纯正的单调栈：    
e.g.739. 每日温度https://programmercarl.com/0739.%E6%AF%8F%E6%97%A5%E6%B8%A9%E5%BA%A6.html#%E6%80%9D%E8%B7%AF   
返回的是一个记录每个元素左边/右边第一个比自己大的元素的数组    
   
##### 其他的经典例题：   
接雨水是找凹，最大矩形是找凸  


## 使得数组成为递增或递减，此时我们想到「单调栈」  
##### 经典例题：  2865美丽塔  
[https://leetcode.cn/problems/beautiful-towers-i/solutions/2614597/mei-li-ta-i-by-leetcode-solution-uqnf/]  

## 模板
```
// 递增栈
stack<int> st;
vector<int> result(T.size(), 0);
st.push(0);
for (int i = 1; i < T.size(); i++) {
    if (T[i] < T[st.top()]) {                       // 情况一
        st.push(i);
    } else if (T[i] == T[st.top()]) {               // 情况二
        st.push(i);
    } else {
        while (!st.empty() && T[i] > T[st.top()]) { // 情况三
            result[st.top()] = i - st.top();
            st.pop();
        }
        st.push(i);
    }
}
```

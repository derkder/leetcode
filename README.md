## leetcode  


没思路或许想想dp?  
一维dp不行再想想二维dp？  

还有二分【O(logn)】？[在一个范围内找一个满足条件的数]  









伟大的ak之神啊，庇佑一下下您虔诚的子民吧[机器猫抹眼泪]  

---

## 容易忘的且非常常用：O(logn)
### 优先队列：  
```
auto cmp = [&matrix](pair<int, int> & a, pair<int, int> & b) {//三个地址符号（除非不用传入参数）
            return matrix[a.first][a.second] > matrix[b.first][b.second];
        };
priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(cmp)> q(cmp);//!!!没有地址符号
```
```
q.top();//访问不到最后一位，只能访问到顶
```
### bfs：  
需要记录搜索层数： q.size()
### string api  
```
int a; string temp;
a = stoi(temp);
temp = to_string(a);
string temp = substr(int pos = 0, int n = npos);//返回由pos开始的n个字符组成的字符串
```
### 剪枝：  
一般是退出循环，并不是return false

### 二分法
```
//在这个范围内一定有，找符合条件的第一个
while (L < R){ 
    if (check(mid, time, m) == true)  R = mid;
    else  L = mid + 1;                 //标准的框架
}
return L;

////在这个范围内不一定有
while (L <= R){   
    if(mid==t) return nums[mid];
    if (check(mid, time, m) == true)  R = mid-1;
    else  L = mid + 1;                 
}
return -1;
```

### pair：  
p1 = make_pair(1, 1.2);

### 卡时
```
if((double)clock()/CLOCKS_PER_SEC>0.97) return;
```

---
## 容易忘的且没有非常常用：
### 双向bfs：
```
1、创建「两个队列」分别用于两个方向的搜索；  
2、创建「两个哈希表」用于「解决相同节点重复搜索」和「！！记录转换次数！！！」；  
3、为了尽可能让两个搜索方向“平均”，每次从队列中取值进行扩展时，先判断哪个队列容量较少；  
while(!d1.isEmpty() && !d2.isEmpty()) {
    if (d1.size() < d2.size()) {
        update(d1, m1, m2);
    } else {
        update(d2, m2, m1);
    }
}
// update 为将当前队列 d 中包含的元素取出，进行「一次完整扩展」的逻辑（按层拓展）
void update(Deque d, Map cur, Map other) {}//bfs
```
### 回溯
```
public void backtracking (此时已经走完的路径startIndex，此次可选择的选择列表n,终止条件){//！！！！！也不一定是startindex而是记录used
    if(判断出口的条件){
        存放结果;（结果大概是个全局变量）
        return;//递归的最深度，即终止
       }
    for(int i=();i<选择列表长度;i++){//列表长度是所有的选择长度
     处理节点;//！！！！！！！
     backtracking(此时已经走完的路径startIndex，此时的选择列表,终止条件)//此时列表是下一节点的列表
     撤销上一步的路径;//！！！！！！！，不一定有
    }
   }
}
```
### 最大公约数GCD和最小公倍数LCM
```
gcd(a, b)//Greatest Common Divisor
lcm(a, b)//Least Common Multip
** long ab = lcm<long>(a,b); **
```


### 背包问题（dp[j]：容量为j的背包所背的最大价值||能否凑出重量j）
#### 01背包
```
// 初始化
vector<int> dp(bagWeight + 1, 0);
##### 01背包：
第二层循环从大到小！！
for(int i = 0; i < weight.size(); i++) { // 遍历物品
    for(int j = bagWeight; j >= weight[i]; j--) { // 遍历背包容量
        dp[j] = max(dp[j], dp[j - weight[i]] + value[i]);
    }
}
```
##### 完全背包：
```
// 初始化
vector<int> dp(bagWeight + 1, 0);
//第二层循环从小到大
for(int i = 0; i < weight.size(); i++) { // 遍历物品
    for(int j = weight[i]; j <= bagWeight ; j++) { // 遍历背包容量
        dp[j] = max(dp[j], dp[j - weight[i]] + value[i]);

    }
}
```

### 输入输出专场
`while(cin>>a && cin>>b)`

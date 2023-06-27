## leetcode  


没思路或许想想dp?  
一维dp不行再想想二维dp？  

还有二分【O(logn)】？[在一个范围内找一个满足条件的数]  









伟大的ak之神啊，庇佑一下下您虔诚的子民吧[机器猫抹眼泪]  

---

## 容易忘的且非常常用：
### 优先队列：  
```
static bool cmp(pair<int, int>& m, pair<int, int>& n) {//不加static报错
        return m.second > n.second;
    }
priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(&cmp)> q(cmp);//!!!
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

### pair：  
p1 = make_pair(1, 1.2);

### 卡时
```
if((double)clock()/CLOCKS_PER_SEC>0.97) return;
```

---
## 容易忘的且没有非常常用：
#### 双向bfs：
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
#### 回溯
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

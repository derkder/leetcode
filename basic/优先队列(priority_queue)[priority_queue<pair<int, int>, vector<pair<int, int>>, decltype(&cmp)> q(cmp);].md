## 简介
把元素放进去，元素就自动排队了【所以priority_queue才是小根堆，set不是嘞】  
```
//升序队列（小顶堆），把最小的放在队首top上（也就是优先会被弹出的位置）  
priority_queue <int,vector<int>,greater<int> > q;  
//降序队列 
priority_queue <int,vector<int>,less<int> >q;
```
改变排序使用的函数：
```
static bool cmp(pair<int, int>& m, pair<int, int>& n) {//不加static报错
        return m.second > n.second;
    }
priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(&cmp)> q(cmp);
```
```
q.top()    //访问队首元素不是.front
q.empty() //判断队列是否为空
q.push()   //插入元素到队尾
q.pop()    //出队队首元素
q.size()   //返回队列中元素的个数
```

---

## 例题
#### 703.数据流中的第 K 大元素
设计一个找到数据流中第 k 大元素的类（class）。注意是排序后的第 k 大元素，不是第 k 个不同的元素。
```
class KthLargest {
public:
    priority_queue<int, vector<int>, greater<int>> q;
    int k;
    KthLargest(int k, vector<int>& nums) {
        this->k = k;
        for (auto& x: nums) {//!!!!!
            add(x);
        }
    }
    
    int add(int val) {
        q.push(val);
        if (q.size() > k) {
            q.pop();
        }
        return q.top();
    }
};
```
其实这题核心是用堆，小根堆。
还有个知识点就是数据流，所谓数据流，即是说我们写的算法需要支持 add() 函数；在力扣后台评测程序中会多次调用add()函数，每次调用都会向我们写的算法中添加一个元素。
#### 优先队列的优化：  373. 查找和最小的 K 对数字  
//如果无脑把所有数字对放在优先队列里会超时，因此  
先把所有的 nums1 的索引入队，即入队的元素有 [0, 0]、[1, 0]、[2, 0]、[3, 0]、......  
首次弹出的肯定是 [0, 0]，再把 [0, 1] 入队；  
这样就可以通过优先级队列比较 [0, 1] 和 [1, 0] 的结果，再弹出较小者；  
依次进行，进行 k 轮。  
[https://leetcode.cn/problems/find-k-pairs-with-smallest-sums/solution/tong-ge-lai-shua-ti-la-you-xian-ji-dui-l-fw7y/]
```
class Solution {
public:
    vector<vector<int>> kSmallestPairs(vector<int>& nums1, vector<int>& nums2, int k) {
        auto cmp = [&nums1, &nums2](const pair<int, int> & a, const pair<int, int> & b) {
            return nums1[a.first] + nums2[a.second] > nums1[b.first] + nums2[b.second];
        };

        int m = nums1.size();
        int n = nums2.size();
        vector<vector<int>> ans;   
        priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(cmp)> pq(cmp);
        for (int i = 0; i < min(k, m); i++) {
            pq.emplace(i, 0);
        }
        while (k-- > 0 && !pq.empty()) {
            auto [x, y] = pq.top(); 
            pq.pop();
            ans.emplace_back(initializer_list<int>{nums1[x], nums2[y]});
            if (y + 1 < n) {
                pq.emplace(x, y + 1);
            }
        }

        return ans;
    }
};
```

---
## 详述
priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(&cmp)> q(cmp);//declear type?


## 使……最大值尽可能小」是二分搜索题目常见的问法（410）
[https://github.com/derkder/leetcode/blob/main/%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92/%E4%B8%80%E4%BA%9B%E9%A2%98/410%E5%88%86%E5%89%B2%E6%95%B0%E7%BB%84%E7%9A%84%E6%9C%80%E5%A4%A7%E5%80%BC.md]

##其他：  
大部分此问题的终止条件都是left>right//！！！！    
   
while里面是left=mid+1；right=mid-1;（这个不一定的）    
    
**通常当题目要求时间复杂度为O(logn)或者自底向上递推显然超时**  
**即空间复杂度为O(1)或者是常数，以及需要一个一个遍历的题目就可以用二分优化**  
[https://yuguang.blog.csdn.net/article/details/111935019]  
  
常和前缀和结合  

---

模板：  (这模板可能是错的，l < r还是 l <= r取决于mid是怎么挪动的，是 = l还是 = l- 1， 我感觉就是无所谓是不是一定有， <= 应该都不会错，最多多比一个)
原来的模板  
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

////l和r两个元素可以都进行变化的，返回的东西也可以加减1的
```

---

一般说常数的空间复杂度都是二分，但是也不一定，例如73.矩阵置0
是利用在原来的空间上标记

大部分此问题的终止条件都是left>right//！！！！  
 
while里面是left=mid+1；right=mid-1;（这个不一定的）  
  
**通常当题目要求时间复杂度为O(logn)或者自底向上递推显然超时**  
**即空间复杂度为O(1)或者是常数，以及需要一个一个遍历的题目就可以用二分优化**  
[https://yuguang.blog.csdn.net/article/details/111935019]  
  
常和前缀和结合  

---

模板：  
  
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

////找一个数组里第一个大于target的数，l和r都要变，而且返回的也是r否则就不对
while (l < r) {
   int mid = l + (r - l) / 2;
   if (nums[mid] >= target) {
       r = mid - 1;
   } else {
       l = mid + 1;
   }
}
return r;
```

---

一般说常数的空间复杂度都是二分，但是也不一定，例如73.矩阵置0
是利用在原来的空间上标记

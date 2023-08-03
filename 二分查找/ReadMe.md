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

////找一个数组里第一个小于target的数，就是说l和r两个元素可以都进行变化的，返回的东西也可以加减1的
while(l < r){
     mid = l + ((r - l)>>1);
     if(matrix[mid][n-1] <= target){
         l = mid+1;
     }
     else{
         r = mid - 1;
     }
 }
 int y = r + 1;
```

---

一般说常数的空间复杂度都是二分，但是也不一定，例如73.矩阵置0
是利用在原来的空间上标记

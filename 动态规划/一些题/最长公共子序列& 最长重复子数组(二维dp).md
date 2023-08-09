## 数组是连续的，序列可以不是连续的
## 1143最长公共子序列  
#### 题目
输入：text1 = "abcde", text2 = "ace"   
输出：3    
解释：最长公共子序列是 "ace" ，它的长度为 3 。  
#### 解：
```
class Solution {
public:
    int longestCommonSubsequence(string text1, string text2) {
        //dp[i][j] 表示 text1[0:i - 1]和 text2[0:j]- 1的最长公共子序列的长度。
        //之所以 dp[i][j] 的定义不是 text1[0:i] 和 text2[0:j] ，是为了方便当 i = 0 或者 j = 0 的时候，dp[i][j]表示的为空字符串和另外一个字符串的匹配，这样 dp[i][j] 可以初始化为 0.
        //递推公式：
        //if (text1[i - 1] == text2[j - 1]) dp[i][j] = dp[i - 1][j - 1] + 1;合理
        //else dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);//hum....,能理解但有点怪，可能要多做攒感觉吧
        int n1 = text1.length();
        int n2 = text2.length();
        vector<vector<int>> dp(n1 + 1, vector<int>(n2 + 1, 0));
        for(int i = 0; i < n1; ++i){
            dp[i][0] = 0;
        }
        for(int i = 0; i < n2; ++i){
            dp[0][i] = 0;
        }
        for(int i = 1; i <= n1; ++i){
            for(int j = 1; j <= n2; ++j){
                if(text1[i - 1] == text2[j - 1]) dp[i][j] = dp[i - 1][j - 1] + 1;
                else dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
            }
        }
        return dp[n1][n2];
    }
};
// @lc code=end
```



## 718最长重复子数组
#### 题目
输入：A: [1,2,3,2,1],B: [3,2,1,4,7]       
输出：3    
解释：长度最长的公共子数组是 [3, 2, 1] 。
#### 醍醐灌顶的图图：
![718dp](/动态规划/一些题/imgs/718dp图解.png)
#### 解：
```
int findLength(vector<int>& nums1, vector<int>& nums2) {
        //嗨呀，知道是dp（因为在这个专题找de）
        //难不成用二分？嗨呀，已经很努力地想了
        //dp[i][j] ：以i-1结尾的A子数组和以j-1结尾的B子数组的最长!!公共后缀长度!!而不是最长子数组长度
        //这个公共后缀就很难想
        int n = nums1.size();
        int m = nums2.size();
        int ans = 0;
        vector<vector<int>> dp(n + 1, vector<int>(m + 1, 0));
        for(int i = 1; i < n + 1; ++i){
            for(int j = 1; j < n + 1; ++j){
                if(nums[i-1] == nums[j - 1]){
                    dp[i][j] = dp[i -1][j - 1] + 1;
                }
                ans = max(ans,  dp[i][j])
            }
        }
        return ans;
    }
```

# Longest Common Substring

## Problem

Find longest common *substring* of two inputs
- Definition of substring: 連續的 chars
    - Example: Longest Common Substring of `"abcde"` and `"aaafcdgg"` is `"cd"`

## Dynamic Programming Approach

- 建立 DP table, `dp[0, 0]` 為 0
  - 只要 `word1[i] == word2[j]`
    - `dp[i, j] = d[i-1, j-1] + 1`
    - 左上格 + 1，儲存在 `dp[i, j]`

-  例如 `word1` = `"abcde"`, `word2` = `"bcaa"`
   -  LCS = `bc`
 
![](2021-05-07-21-31-38.png)

- 例如 `word1` = `"abcd"`, `word2` = `"bcdfg"`
  - LCS = `bcd`

![](2021-05-07-21-35-47.png)

## Tips

- word1/word2 在 row 或在 column 都沒差，table 建好就好
- 記得 `dp[0,0]` 是 0，要從 `dp[0,1]` 或 `dp[1,0]` 開始建 table
  - 第一個 row/column 都會是 `0`
- LCS 的長度: 設變數 `lcs`，當 `word1[i] == word2[j]` 建立 dp table 的時候，將該格的數值跟 `lcs` 比較
  - `lcs = max(lcs, dp[i,j])`
- 追蹤 LCS: 從最大那格往左上追蹤，直到遇到 `0`

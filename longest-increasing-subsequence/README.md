# 300. Longest Increasing Subsequence - Média

<div align="center"><img src= "./result.png"/></div>

---

## Vídeo Explicação

https://youtu.be/6MIfTR7_aEs

---

## Link Questão

https://leetcode.com/problems/longest-increasing-subsequence/description/

---

## *Código*

```c 
int lengthOfLIS(int* nums, int numsSize) {
    int l[2500];
    l[0] = 1;

    for (int i=1; i<numsSize; i++) {
        l[i] = 1;
        for (int j=0; j<i; j++) {
            if (nums[j] < nums[i] && 1+l[j] > l[i]) {
                l[i] = 1+l[j];
            }
        }
    }

    int max = l[0];
    for (int i=1; i<numsSize; i++) {
        if (l[i] > max) max = l[i];
    }
    
    return max;
}
```

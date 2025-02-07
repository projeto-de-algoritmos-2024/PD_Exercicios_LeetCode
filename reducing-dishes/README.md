# 1402. Reducing Dishes

<div align="center"><img src= "https://github.com/projeto-de-algoritmos-2024/PD_Exercicios_LeetCode/raw/refs/heads/master/reducing-dishes/result"/></div>

---

## Vídeo Explicação

https://youtu.be/

---

## Link Questão

https://leetcode.com/problems/reducing-dishes/

---

## *Código*

```c 
int compar(const void *a, const void *b) {
    int ia = *(int *)a;
    int ib = *(int *)b;
    return (ia > ib) - (ia < ib);
}          

int **mem;
int getSatisfaction(int *sv, int idx, int count, int max) {
    if (idx >= max) return 0;
    if (mem[idx][count-1] != -1) return mem[idx][count-1];

    int take = count*sv[idx]+getSatisfaction(sv, idx+1, count+1, max);
    int no_take = getSatisfaction(sv, idx+1, count, max);
    
    mem[idx][count-1] = take > no_take ? take : no_take;
    return mem[idx][count-1];
}

void initmem(int max) {
  mem = malloc(max*sizeof(int *));
  for (int i=0; i<max; i++) {
    mem[i] = malloc(max*sizeof(int));
    for (int j=0; j<max; j++) {
      mem[i][j] = -1;
    }
  }
}

int maxSatisfaction(int* satisfaction, int satisfactionSize) {
    initmem(satisfactionSize);
    qsort(satisfaction, satisfactionSize, sizeof(int), compar);
    int s = getSatisfaction(satisfaction, 0, 1, satisfactionSize);
    return s > 0 ? s : 0;
}
```

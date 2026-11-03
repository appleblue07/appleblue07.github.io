---
title: "유니온 파인드(Union find)"
date: 2026-11-01
categories: [ps 개념]
---

# 유니온 파인드 (Union find) 알고리즘 기본 템블릿입니다

```cpp

int parent[100005];

void init(int n) {
    for(int i = 1; i <= n; i++)
        parent[i] = i;
}

int find(int x) {
    if(parent[x] == x) return x;
    return parent[x] = find(parent[x]);
}

void unite(int a, int b) {
    a = find(a);
    b = find(b);

    if(a != b)
        parent[b] = a;
}


```

여담 <br>
설명은 나중에 추가하겠습니다.
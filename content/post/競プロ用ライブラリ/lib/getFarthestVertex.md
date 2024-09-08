+++
title = 'getFarthestVertex(最遠頂点を求める)'
date = 2024-07-30T22:01:37+09:00
description = "romophic-library"
categories = [
  "c++",
  "competitive programming"
]
+++
## 用途
指定した頂点からもっとも遠い頂点を得る.

## 計算量
$ O(n) $

## Depends
- **[DirectedGraph]({{< ref "post/競プロ用ライブラリ/lib/DirectedGraph" >}})**

## 使い方
### 宣言
```cpp
auto res = dijkstra(g,s);
```
`res.v`で最も遠い頂点の頂点番号を得る. `res.cost`で最も遠い頂点までの距離を得る.

## 実装
```cpp
struct getFarthestVertex_return {
  int v, cost;
};
getFarthestVertex_return getFarthestVertex(DirectedGraph &_g, int _v) {
  queue<pair<int, int>> q;
  vector<int> t(_g.n, -1);
  q.push({_v, 0});
  getFarthestVertex_return res = {-1, -1};
  while (!q.empty()) {
    auto p = q.front();
    q.pop();
    bool tr = true;
    for (auto &i : _g.g[p.first])
      if (t[i.to] == -1) {
        tr = false;
        q.push({i.to, p.second + i.cost});
        t[i.to] = p.second + i.cost;
      }
    if (tr)
      res = {p.first, p.second};
  }
  return res;
}
```
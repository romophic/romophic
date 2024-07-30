+++
title = 'chmax/chmin'
date = 2024-07-29T22:01:37+09:00
description = "romophic-library"
categories = [
  "c++",
  "competitive programming"
]
+++
## 使い方
`chmax(a,b)`で`a=max(a,b)`の更新をする. 更新があった場合はtrueを返す. `chmin`も同様:
## 実装
```cpp
template <class T>
bool chmax(T &a, const T &b) { return a < b ? a = b, true : false; }
template <class T>
bool chmin(T &a, const T &b) { return a > b ? a = b, true : false; }
```
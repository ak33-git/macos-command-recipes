# MacOSでbits/stdc++.hのエイリアスを作成

## ディレクトリ作成（include 置き場）
```bash
cd ~
mkdir -p cpp_include/bits
```

## bits/stdc++.hを作成
```bash
nano cpp_include/bits/stdc++.h
```
中身に以下を書き込む
```cpp
#pragma once
#include <iostream>
#include <vector>
#include <algorithm>
#include <string>
#include <queue>
#include <stack>
#include <map>
#include <set>
```

## 動作をテスト
```bash
cd ~/Desktop
nano test.cpp
```
中身に以下を書き込む
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    cout << "OK" << endl;
    return 0;
}
```

## コンパイルして実行
```bash
clang++ -std=c++17 -I/Users/ユーザ名/cpp_include test.cpp
./a.out
```
ユーザ名は自分の名前に変更する

## VScode設定(include pathを以下に変更)
```text
${workspaceFolder}/**
/Users/ユーザ名/cpp_include
```
ユーザ名は自分の名前に変更する

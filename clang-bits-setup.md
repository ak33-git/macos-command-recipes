# MacOSでbits/stdc++.hのエイリアスを作成

macOS の標準 C++ コンパイラでは<bits/stdc++.h> を include することができません。
以下の手順で、元のコンパイラに変更を加えずローカル環境上で <bits/stdc++.h> を扱えるようにします。

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
コンパイルは通るがVScode上でエラー表記が出るので設定を変更  
VScodeの画面でcmd + Shift + P  

C/C++ Edit Configurations(UI)を選択し  
Include Pathに以下を追加
```text
${workspaceFolder}/**
/Users/ユーザ名/cpp_include
```
ユーザ名は自分の名前に変更する

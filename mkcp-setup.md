# MacOSでAtCoderのコンテスト回のディレクトリ作成

以下の手順により、コマンド一つで
A.cpp, B.cpp, C.cpp, ... を作成

## ディレクトリ作成（コマンド置き場）
```bash
mkdir -p ~/bin
```

## PATHを通す
~/binがPATHに入っていない時は以下の手順でPATHに追加してください
```bash
nano ~/.zshrc
```
~/.zshrcはzshの設定ファイルです。
中に次の文を追加してください。
```bash
export PATH="$HOME/bin:$PATH"
```
control+xでExit
書き込むかどうか聞かれたらyを押してEnter


PATHの設定を反映
```bash
source ~/.zshrc
```

## mkcpを作成
```bash
touch ~/bin/mkcp
nano ~/bin/mkcp
```
mkcpの中身に以下を書き込む
```bash
#!/bin/sh
[ $# -ge 1 ] && [ -n "$1" ] || { echo "Usage: mkcp <dir>"; exit 2; }

mkdir "$1"
cd "$1" || exit 1
touch test.cpp
touch {A..G}.cpp

for f in test {A..G}; do
    cat << 'EOF' > "$f.cpp"
#include <bits/stdc++.h>
using namespace std;
using ll = long long;
using ld = long double;
using i128 = __int128_t;

int main()
{

}
EOF
done
```

## コマンドの権限確認
もし作成したコマンドの実行権限がない場合、以下の手順で権限を変更できる
```bash
ls -l ~/bin/mkcp
chmod +x ~/bin/mkcp
```

## 動作をテスト
```bash
cd ~/Desktop
mkcp test
```
Desktop直下にtestディレクトリが作成されていればOK

もし、makefileやtest.cppなどを追加したい場合はmkcpの中身を変更してください

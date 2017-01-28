# コマンドを作って手軽に使えるようにする（PATHを通す）

自分で作ったコマンドやスクリプトをターミナルで使えるようにするためには、登録が必要。分かりやすく同じ場所に保存するようにし、そのディレクトリへのPATHを通しておけば、毎回パスを書かずに呼び出せるようになる。（ここでは自分のホームディレクトリに「mybin」ディレクトリを作り、そこに格納していくこととする）
例：
`/usr/local/bin/atom` ← `atom` で呼び出せる（これはatomインストール時に作られたもの）
`/Users/konaho/mybin/hello.sh` ← `hoge.sh` で呼び出せる（これは自分で作ったもの）


## 現在有効になっているPATHを確かめる
`echo $PATH`  → `/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin`

## PATHを追加する（自分で作ったシェル等が通るように）※ただし、登録セッションのみ有効
`export PATH=$PATH:~/mybin/`
→常時利用できるようにするためには `.bashrc` に追記して保存（セッション起動時に自動で実行されるようになる）
`vi ~/.bashrc` , `atom ~/.bashrc` などで編集＆保存

## 自分のコマンドを作る
`atom ~/mybin/hello.sh`

## 作ったコマンドに実行権限をつける（自分のみ）
`chmod u+x ~/mybin/hello.sh`

## [参考] 権限を確かめてみる
`ls -l mybin/hello.sh`
→ `-rwxr--r--  1 konaho  staff  34  1  9 17:32 mybin/hello.sh`
→ ownerに `rwx` がついているのでOK（2文字目から3つずつowner-group-everyone）

これにより、以下のどの呼び出しをしても実行できるようになった
`/Users/konaho/mybin/hello.sh`
`~/mybin/hello.sh`
`hello.sh`

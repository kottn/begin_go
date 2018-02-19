# begin_go
:beginner: はじめてのgo

## 環境
Debian 9

## アンインストール
* 古いバージョンがある場合はgoディレクトリを消す（普通は`/usr/local/go`にある）
```
$ su -
# cd /usr/local
# rm -rf go/
```
* `~/.profile`や`~/.bash_profile`に古い`$GOPATH`があったら消す

## インストール
* `apt`で入る golang は古いので [golang公式](https://golang.org/dl/) へ
* Stable versions から`goX.X.X.linux-amd64.tar.gz`をダウンロード
* `/usr/local/go`に解凍
```
$ cd ~/Downloads
$ sudo tar -C /usr/local -zxf go*.tar.gz
```

* `~/.profile`にパスを通す
	* `$PATH`に`/usr/local/go/bin`を追加
	* `$GOROOT`は`/usr/local/go`に解凍したら設定しなくていい
	* `$GOPATH`は適当に作った一箇所（例えば`~/.go`）に設定
	* `$PATH`に`$GOPATH/bin`を追加
	* :point_right: つまり`~/.profile`に以下を追加
```
export PATH=/usr/local/go/bin:$PATH
export GOPATH=$HOME/.go
export PATH=$GOPATH/bin:$PATH
```
* 読み込む
```
$ source ~/.profile
```
* バージョン確認
```
$ source ~/.profile
$ go version
```

## 実行テスト
* `hello_barabara.go`の中身はとってもバラバラ:

```go
package  main

import     "fmt"

func main()    {
fmt.Printf("hello, world\n")
}
```

* `gofmt`コマンドを使ってインデントのこだわりから開放される
```
$ gofmt hello_barabara.go > hello.go
$ cat hello.go
```

```go
package main

import "fmt"

func main() {
	fmt.Printf("hello, world\n")
}
```

* 走らせてみる
```
$ go run hello.go
hello, world
```

* ビルドも可能
```
$ go build hello.go
$ ./hello
hello, world
```

# kickoff_go
はじめてのgo

## 環境
Debian 9

## インストール
* 古いバージョンがある場合はgoディレクトリを削除．`~/.profile`などに古い`$GOPATH`があったら消す．
```
su -
cd /usr/local
rm -rf go
```

* https://golang.org/dl/ にアクセス
* Stable versions から`go*.linux-amd64.tar.gz`をダウンロード
* `/usr/local/go`に解凍
```
cd ~/Downloads
sudo tar -C /usr/local -zxf go*.tar.gz
```

* `~/.profile`にパスを通す
	* `$PATH`に`/usr/local/go/bin`を追加
	* `$GOROOT`は`/usr/local/go`に解凍したら設定しなくていい
	* `$GOPATH`は適当に決めた一箇所（例えば`~/.go`）に設定
	* `$PATH`に`$GOPATH/bin`を追加

つまり`~/.profile`に以下を追加
```
export PATH=/usr/local/go/bin:$PATH
export GOPATH=$HOME/.go
export PATH=$GOPATH/bin:$PATH
```

* バージョン確認
```
source ~/.profile
go version
```

* テストプログラム
`hello_barabara.go`の中身はとってもバラバラ
```go
package  main

import     "fmt"

func main()    {
fmt.Printf("hello, world\n")
}
```
`gofmt`コマンドを使ってインデントのこだわりから開放される
```
gofmt hello_barabara.go > hello.go
cat hello.go
```
結果
```go
package main

import "fmt"

func main() {
	fmt.Printf("hello, world\n")
}
```
走らせてみる
```
go run hello.go
```
ビルドも可能
```
go build hello.go
./hello
```

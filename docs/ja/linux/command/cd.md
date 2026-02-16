---
tags:
    - Linux
    - Command
---


# CD / チェンジディレクトリ

このコマンドはディレクトリを移動するときに用います。

<br>

## 基本

`~/`ホームディレクトリにあるabcというディレクトリにアクセスする場合はこの様になります。<br>
```
# /home/user から /home/user/abcにアクセスしたい

user@machine:~$  cd abc
```
では確認してみましょう。<br>

```
user@machine:~/abc$  pwd
/home/user/abc
```
しっかり`/home/user/abc`に移動できていますね。
<br><br>

では次はホームディレクトリからドキュメントにあるtxtディレクトリに行くとします。<br>
```
# /home/user から /home/user/Documents/testにアクセスしたい

user@machine:~$  cd Documents/text
```
では確認してみましょう。<br>
```
user@machine:~/Documents/text$  pwd
/home/user/Documents/text
```
しっかり`/home/user/Documents/txt`に移動できていますね。<br>
ディレクトリの中のディレクトリに行くときは`/`で区切ります。
<br><br>


## ホームディレクトリに移動
上で`/home/user/Documents/txt`に移動しました。<br>
ここから`~$`ホームディレクトリに戻ろうと思います。<br>

### 方法１　"~/" を使う
```
# /home/user/Documents/txt から /home/userに
user@machine: ~/Documents/text$ cd ~/
```
では確認してみましょう。<br>
```
user@machine:~$  pwd
/home/user
```
しっかり`/home/user`に移動できていますね。<br>

### 方法2 "../../" を使う
```
# /home/user/Documents/txt から /home/userに
user@machine: ~/Documents/text$ cd ../../
```
では確認してみましょう。<br>
```
user@machine:~$  pwd
/home/user
```
しっかり`/home/user`に移動できていますね。<br>
<br><br>


### "~/" と "../../" の違い
"~/" と "../../"どちらもちゃんとホームディレクトリに戻ってこられました。<br>
ではどんな違いがあるのでしょうか？<br>

{++**・"~/"**++}<br>
"~/"はホームディレクトリを表しています。<br>
なので、どんなディレクトリにいようと`cd ~/`と打てば、ホームディレクトリに速攻で戻ってこられます。<br><br>

{++**・"../../"**++}<br>
"../../"はそもそも`../`を二つ並べただけです。<br>
では、`../`はなんでしょう？<br>
答えは、 ==一つ前のディレクトリに戻る== でした。<br><br>
そのため、`/home/user/Documents/txt`で一度しか打たないと`/home/user/Documents`で止まってしまいます。<br>
また、`/home/user/Documents/txt`で三度打つと`/home`まで戻ってしまいます。<br><br>



## 絶対pathで移動
さっきまでは`xxx/yyy`の様な感じでpathを指定していました。<br>
このやり方は ==**相対path**== といいます。<br>
相対pathは今いる位置（directory）からみた相対位置を指定します。<br>
例えば...<br>

```
# /home/user から /home/user/Documents/text/minecraft

user@machine:~$  cd Documents/text/minecraft
user@machine:~/Documents/text/minecraft$  pwd
/home/user/Documents/text/minecraft



# /home/user/Documents/text/minecraft から /home/user/Documents/logs

user@machine:~/Documents/text/minecraft$  cd ../../logs
user@machine:~/Documents/logs$  pwd
/home/user/Documents/logs
```
しかし、`/home/user/aaa/bbb/ccc/ddd`から`/usr/local/bin`に移動したいとすると、最短でも`cd ~/../../usr/local/bin`と長くなってしまいます。<br>
これでは間違えてしまうと地獄なので、こういう時は下記のやり方をやります。<br><br>


頭に`/`をつけた`/xxx/yyy`これを ==**絶対path**==　といいます。<br>
絶対pathではこの様に移動します。<br>

```
# /home/user/aaa/bbb/ccc/ddd から /usr/local/bin

user@machine:~/aaa/bbb/ccc/ddd$  cd /usr/local/bin
user@machine:/usr/local/bin$  pwd
/usr/local/bin
```
とてもスッキリした移動方法になりましたね〜<br>
これが絶対pathでの移動方法です。<br><br>

ちなみに、`cd /`と打つとどこにいてもルートディレクトリ（root directory）に連れて行かれます。<br>

```
user@machine:~/aaa/bbb/ccc/ddd$  cd /
user@machine:/$  pwd
/

user@machine:~/Documents/text$  cd /
user@machine:/$  pwd
/
```
# T540 ubuntu16のインストール
## ライブCDの準備
Ubuntu Desktop 日本語 Remixをダウンロードし、CDにISOイメージで焼く
（T510のBraseroで焼いた）
Ubuntu 16.04 LTS - 2021年4月までサポート
ubuntu-ja-16.04-desktop-amd64.iso

## ライブCDから起動してインストール
### LAN接続
  途中ネットからダウンロードするため確実に繋がるLAN接続に
### インストールの種類
  全削除し全てUbuntuに
　　LVMモード
###　スーパーユーザーとしてインストール
　　ユーザはインストール後に作成する
  あなたの名前 : hamaguchi
  コンピューター名 : hamaguchi-ThinkPad-T540p
  usr name : hamaguchi
  pass : Uu@b724i[]r
### オプション
　アップデートしながらインストール
　サードパーティ製ドライバ、ソフトを有効

## インストール後の設定
###　ユーザ作成
 $ sudo usradd -m hiroshi
 $ sudo passwd hiroshi
     Uu@b724i[]u
###　ユーザがsudoコマンド使える設定
 $ sudo visudo
  rootと同じようにhiroshiの行を追加してsudoresを上書き保存

  su で root になろうとしたら、どんなパスワードを入れても認証失敗になってしまう。
  Ubuntu ではそもそも root のパスワードは設定されていない
  su と同じ操作をするためには、
  sudo -i

### システムのアップグレード
　再起動してhiroshiでログイン
　無線がうまくつながらない

apt-get updateが途中で失敗していることが原因

Error in appstreamcli: double free or corruption (fasttop): 0x00000000012f1fe0

Ubuntu 16.04のapt updateでappstreamcliが固まりアップデートができない問題
2016年5月20日現在、apt updateで処理が進まなくなる問題が発生しています。
この問題は「ソフトウェアの更新」からは発生しないようです。
appstream 0.9.4-1パッケージに問題があるようです。
Ubuntu 16.04でも修正版がリリースされました。
問題はパッケージが修正されてもapt updateで固まってインストールできない点です。
ここでは修正されたappstreamをインストールする手順を記載します。

#### 回避方法
```
$ sudo mv /etc/apt/apt.conf.d/50appstream /etc/apt/apt.conf.d/50appstream.disable
$ sudo apt update -y
$ sudo apt upgrade -y
$ sudo mv /etc/apt/apt.conf.d/50appstream.disable /etc/apt/apt.conf.d/50appstream
$ sudo apt update -y
```

## ネットワーク設定
上記のアップデート、アップグレードにより自動的につながる。
Debian87のようにドライバの別途インストール不要
以下不要
hamaguchi@debian871:~/00_HD-PCTU3/00buckup$ su -
パスワード:Uu@b724i[]r
root@debian871:~# ls
root@debian871:~# cd /home/hamaguchi/00_HD-PCTU3/00buckup/
root@debian871:/home/hamaguchi/00_HD-PCTU3/00buckup# ls
firmware-realtek_0.43_all.deb  sources.list
iwlwifi-6000-4.ucode	       sources.list.save
root@debian871:/home/hamaguchi/00_HD-PCTU3/00buckup# cp iwlwifi-6000-4.ucode /lib/firmware/

Debian desktopの右上をクリックしてWi-Fiを選択
Buffalo-G-1AB0を選択し、パスワード入力 : buwadt4ti5hf3

## Tweak toolによるデスクトプ周りの基本設定
ubuntuのデスクトップはUnity、Tweak toolは入ってない
Ubuntuソフトウェアでインストール

* ウィンドウ：最大化、最小化をオン
* デスクトップ：アイコン表示
* トップバー：日付表示
* 外観：ウィンドウをブライト（最大、最小の部分が見やすい）
* 拡張機能：ほとんどオンに
* 電源：ラップトップを閉じた時の挙動をNothingに

## インストール後の必要ファイルをPCにコピー
外付けハードディスク00_HD-PCTU3からコピー

## 日本語入力メソッドの設定（Google入力のオープンソース版Mozc）
以下不要
hamaguchi@debian871:/etc/apt$ sudo apt-get install mozc-utils-gui
hamaguchi@debian871:/etc/apt$ sudo apt-get install mozc-server
hamaguchi@debian871:/etc/apt$ sudo apt-get install ibus-mozc
hamaguchi@debian871:/etc/apt$ sudo apt-get install uim-mozc

## aplicationが暴走した時の終了の方法
端末を開いて
hamaguchi@debian871:~$ ps aux | grep qgis
hamaguc+ 11927  5.3 11.5 604788 359364 ?       Sl   18:03   0:44 /usr/bin/qgis.bin
hamaguc+ 12531  0.0  0.0   4056  2392 pts/0    S+   18:17   0:00 grep qgis
hamaguchi@debian871:~$ sudo kill 11927

## 設定関連
/etc/ 設定ファイルは通常ここにある。
/usr/local/ のサブディレクトリ(パッケージではなくソースコードを使ってインストールした場合、このディレクトリは手作業でコンパイルおよびインストールされたプログラムを収めるための場所)
/opt/ にある場合もある
インストールされた Debian システムのバージョン番号
hamaguchi@debian871:~$ cat /etc/debian_version
8.7

## 有用アプリのインストール
TREE ディレクトリ構成の視覚化
VIM,ATOM,medit,hexedit
python(pyenv,ANACONDA3(spyder含む))
QGIS
この時点でpythonは２と３が入っている
ANACONDA3(Spyder含む)
MuseScore2
LaTeX
R,Rstudio,VSC,Chrome,EclipseIDE（JAVA,C++）,

## printer E879ABの設定
### ドライバのダウンロード
epson-inkjet-printer-escpr2_1.0.9-1lsb3.2_amd64.deb
### ドライバのインストール
上記ファイルをクリックするだけでインストールOK
### プリンタの設定
設定/プリンタ/ネットワークでEP-879を選択

### man の日本語化
hiroshi@hamaguchi-ThinkPad-T540p:~$ sudo apt install manpages-ja
パッケージリストを読み込んでいます... 完了
依存関係ツリーを作成しています                
状態情報を読み取っています... 完了
以下のパッケージが新たにインストールされます:
  manpages-ja
アップグレード: 0 個、新規インストール: 1 個、削除: 0 個、保留: 83 個。
3,571 kB のアーカイブを取得する必要があります。
この操作後に追加で 4,098 kB のディスク容量が消費されます。
取得:1 http://jp.archive.ubuntu.com/ubuntu xenial/universe amd64 manpages-ja all 0.5.0.0.20140515+dfsg-2 [3,571 kB]
3,571 kB を 3秒 で取得しました (1,163 kB/s)
以前に未選択のパッケージ manpages-ja を選択しています。
(データベースを読み込んでいます ... 現在 272778 個のファイルとディレクトリがインストールされています。)
.../manpages-ja_0.5.0.0.20140515+dfsg-2_all.deb を展開する準備をしています ...
manpages-ja (0.5.0.0.20140515+dfsg-2) を展開しています...
man-db (2.7.5-1) のトリガを処理しています ...
manpages-ja (0.5.0.0.20140515+dfsg-2) を設定しています ...

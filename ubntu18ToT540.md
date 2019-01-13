# T540 ubuntu18.04LTSのインストール  
## ライブDVDの準備  
日経Linux20187月号の付録DVD　Ubuntu18.04LTS 日本語 Remix　- 2023年4月までサポート  
## ライブDVDから起動してインストール  
### 無線LAN接続  
  インストール中にかってに接続設定メニューが表示される。  
  Buffalo-G-1ABOを選択肢し、PASSワードを入力すれば接続成功  
### インストールの種類  
  全削除し全てUbuntuに、最小インストール、自動アップデート、サードパーティ製ソフト、暗号化しない、LVMモード、アキディスクスペース上書きにチェック
  
### スーパーユーザーとしてインストール  
  あなたの名前 : xxxxx  
  コンピューター名 : xxxxx-ThinkPad-T540p  
  usr name : xxxxx  
  pass : xxxxxxxxxx  
  ログイン時にパスワードを要求にチェック  
### アカウント登録
  メールソフトを登録してないせいか、うまくいかなかった。
## インストール後の設定
### ユーザ作成
 $ sudo usradd -m hiroshi
 $ sudo passwd hiroshi
     xxxxxxxxxxx
### ユーザがsudoコマンド使える設定
 $ sudo visudo
  rootと同じようにhiroshiの行を追加してsudoresを上書き保存

  su で root になろうとしたら、どんなパスワードを入れても認証失敗になってしまう。
  Ubuntu ではそもそも root のパスワードは設定されていない
  su と同じ操作をするためには、
  sudo -i
### システムのアップグレード
apt-get update
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

### man の日本語化
hiroshi@hamaguchi-ThinkPad-T540p:~$ sudo apt install manpages-ja

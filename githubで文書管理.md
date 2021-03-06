# githubで文書管理
## githubのアカウント作成
## 新規リポジトリ作成(web上のリモートリポジトリ)
  +CLICK new repositoryを選択  
  repository nameを入力  
  initialize this repository with a READMEにチェック  
  create repository
## clone
  clone or downloadをclick
  urlをcopy
  リモートリポジトリと同期するローカルリポジトリのフォルダを作成し、そこで端末を開く
  ``` bash
  hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env$ git clone https://github.com/hamakan2/howtoLinux.git
Cloning into 'howtoLinux'...
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), done.
```
## ファイルを追加してコミット
あらかじめ、ローカルリポジトリに登録したいファイルをコピーするなど作成しておく。
``` bash
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env$ cd howtoLinux/

hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ ls
01linux.md  02ubuntu16T540.md  README.md

hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git add 02ubuntu16T540.md 

hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git commit -m "T540にubuntu18をインストールする方法を記載するためにubuntu16の方法のファイルを 追加"
[master 0fc679e] T540にubuntu18をインストールする方法を記載するためにubuntu16の方法のファイルを追加
 1 file changed, 151 insertions(+)
 create mode 100644 02ubuntu16T540.md
```
## 履歴をみる
``` bash
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git log
commit 0fc679e56af8ba8c4874cea6f29e3f39150ecdac (HEAD -> master)
Author: hamakan2 <baavv914@jttk.zaq.ne.jp>
Date:   Sun Jan 13 17:50:49 2019 +0900

    T540にubuntu18をインストールする方法を記載するためにubuntu16の方法のファイルを追加

commit 29f6d165ee98384cf12a04cc147363329698bb17 (origin/master, origin/HEAD)
Author: hamakan2 <hamakan2@users.noreply.github.com>
Date:   Sun Jan 13 17:27:45 2019 +0900

    Update README.md
    
    PC thinkpadにLinuxをインストールして環境構築する概要を記載

commit fcb21372fc36e7d4d42dba2e34713b6c26797255
Author: hamakan2 <hamakan2@users.noreply.github.com>
Date:   Sun Jan 13 16:57:41 2019 +0900

    Initial commit
```
## push(ローカルリポジトリで行った変更をリモートリポジトリに反映させる)
``` bash
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git push origin master 
Username for 'https://github.com': hamakan2
Password for 'https://hamakan2@github.com': 
Counting objects: 3, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 3.41 KiB | 1.71 MiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/hamakan2/howtoLinux.git
   29f6d16..0fc679e  master -> master
```
## ファイル名の変更
``` bash
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git mv 02ubuntu16T540.md ubntu18ToT540.md
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ ls
01linux.md  README.md  ubntu18ToT540.md
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git push origin master 
Username for 'https://github.com': hamakan2
Password for 'https://hamakan2@github.com': 
Everything up-to-date
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git commit -m "ubuntu18用のファイル名に変更"
[master 5fd09be] ubuntu18用のファイル名に変更
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename 02ubuntu16T540.md => ubntu18ToT540.md (100%)
 
 hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git push origin master 
Username for 'https://github.com': hamakan2
Password for 'https://hamakan2@github.com': 
Counting objects: 2, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 314 bytes | 314.00 KiB/s, done.
Total 2 (delta 0), reused 0 (delta 0)
To https://github.com/hamakan2/howtoLinux.git
   0fc679e..5fd09be  master -> master
```

## リモートリポジトリ上で何か変更を加えたら、再度ローカルリポジトリにClone
``` bash
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git clone https://github.com/hamakan2/howtoLinux.git
Cloning into 'howtoLinux'...
remote: Enumerating objects: 14, done.
remote: Counting objects: 100% (14/14), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 14 (delta 1), reused 5 (delta 0), pack-reused 0
Unpacking objects: 100% (14/14), done.
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git log
commit 5fd09bee73518d6bc62e0bb85373424b9c6820f7 (HEAD -> master, origin/master, origin/HEAD)
Author: hamakan2 <baavv914@jttk.zaq.ne.jp>
Date:   Sun Jan 13 18:05:22 2019 +0900

    ubuntu18用のファイル名に変更

commit 0fc679e56af8ba8c4874cea6f29e3f39150ecdac
Author: hamakan2 <baavv914@jttk.zaq.ne.jp>
Date:   Sun Jan 13 17:50:49 2019 +0900

    T540にubuntu18をインストールする方法を記載するためにubuntu16の方法のファイルを追加

commit 29f6d165ee98384cf12a04cc147363329698bb17
Author: hamakan2 <hamakan2@users.noreply.github.com>
Date:   Sun Jan 13 17:27:45 2019 +0900

    Update README.md
    
    PC thinkpadにLinuxをインストールして環境構築する概要を記載

commit fcb21372fc36e7d4d42dba2e34713b6c26797255
Author: hamakan2 <hamakan2@users.noreply.github.com>
Date:   Sun Jan 13 16:57:41 2019 +0900

    Initial commit
```
## git pushが失敗した時
``` bash
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git add githubで文書管理.md 
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git commit -m "github使用法のファイルを追加"
[master ebd76ad] github使用法のファイルを追加
 1 file changed, 133 insertions(+)
 create mode 100644 "github\343\201\247\346\226\207\346\233\270\347\256\241\347\220\206.md"
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git push origin master
Username for 'https://github.com': hamakan2
Password for 'https://hamakan2@github.com': 
To https://github.com/hamakan2/howtoLinux.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/hamakan2/howtoLinux.git'
ヒント: Updates were rejected because the remote contains work that you do
ヒント: not have locally. This is usually caused by another repository pushing
ヒント: to the same ref. You may want to first integrate the remote changes
ヒント: (e.g., 'git pull ...') before pushing again.
ヒント: See the 'Note about fast-forwards' in 'git push --help' for details.
```

## 解決方法
### プルして最新の変更履歴をマージしてから、またプッシュし直せばOKです。
``` bash
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git pull origin master
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/hamakan2/howtoLinux
 * branch            master     -> FETCH_HEAD
   5fd09be..134f9a8  master     -> origin/master
Merge made by the 'recursive' strategy.
 ubntu18ToT540.md | 135 +++++++++----------------------------------------------
 1 file changed, 22 insertions(+), 113 deletions(-)
```
### マージで競合したのでコミットし直します。(たぶんVimが立ち上がります。:qでvimからぬける)
``` bash
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git commit -m "競合解決"
ブランチ master
このブランチは 'origin/master' よりも2コミット進んでいます。
  (use "git push" to publish your local commits)

追跡されていないファイル:
	01linux.md
	howtoLinux/
```
### あとは今まで通りプッシュするだけです。
``` bash
hamaguchi@hamaguchi-ThinkPad-T540p:~/Github/howto/env/howtoLinux$ git push
Username for 'https://github.com': hamakan2
Password for 'https://hamakan2@github.com': 
Counting objects: 5, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 2.18 KiB | 2.18 MiB/s, done.
Total 5 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/hamakan2/howtoLinux.git
   134f9a8..6429d8c  master -> master

追跡されていないファイル:
	01linux.md
	howtoLinux/

これでエラーなく無事プッシュできました。


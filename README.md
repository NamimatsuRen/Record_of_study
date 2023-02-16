# 勉強の記録

Markdown記法に慣れるため，リポジトリに勉強の記録を行う．

***

## 2023/02/10

### 豆知識

- VScodeでMarkdownのプレビューを見る方法 Windows [Ctrl] + [Shift]+[V]
>
### gitのリポジトリ作成，ローカルとリモートの紐付け

- gitの超基本的な使い方
  - 初期設定
    - ユーザ名を登録`git config --global user.name ユーザ名`
        メールアドレスを登録`git config --global user.email メールアドレス`
        登録されているかの確認`git config --list`
        確認を止めたい時は`q`
>
- リモートリポジトリの作成
  - github上で作成
>
- ローカルリポジトリの作成
  - 作業するディレクトリ上で`git init`することで，そのディレクトリをgitリポジトリにする．
>
- リモートリポジトリとローカルリポジトリを紐付ける
  - ローカルリポジトリのターミナルで
        `git remote add origin https://github.com/user/repositori.git`
>
### 読書

**世界で闘うプログラミング力を鍛える本**をちょっぴり読んだ．
作者いわくコーディング面接はめちゃやばだからしっかり対策が必要．
アルゴリズム・コーディング・設計に標準が置かれている．
面接担当者は次のような軸に基づいて評価を下している．

- **分析スキル:** 導かれた方法は最適であったか？複数の選択肢を検討できていたか？
- **コーディングスキル:** 考えたアルゴリズムを適切なプログラムにへんかんできたか？潜在的なエラーに対処しているか？
- **技術知識/コンピュータ・サイエンスの基礎知識:** コンピュータ・サイエンスや関連技術について，基礎的な知識をしっかりと持っているか？
- **経験:** 難易度が高く，面白いプロジェクトを経験してきたか？プロジェクトの後押しや先導を行ってきたか？
- **企業文化との相性/コミュニケーションスキル:** 性格や価値観が自社や配属予定のチームに合っているか？

***

## 2023/02/11

### gitにファイルの変更を保存する

- ローカルリポジトリにコミットする
  - コミットとはファイルの追加・変更をリポジトリに反映する操作
  - まず，`git add 任意のファイル or ディレクトリ`を入力し，インデックスにファイルを追加する．
  - `git add`を取り消すには，
    - ファイルを削除する場合`git rm --cached ファイル名`
    - ディレクトリを削除する場合`git rm --cached -r ディレクトリ名`
    - インデックスに追加した全ての修正を取り消す場合`git rm --cached -r .`
  - インデックスとは，変更内容を一時的に保存する領域である．
  - インデックスに追加されたファイルのみがコミットの対象となる．

***

## 2023/02/12

### リモートリポジトリにpushする

***

## 2023/02/15

### 三日坊主になってしまっている件について

三日坊主と書いているが、実質2日坊主である．
githubに上手くREADME.mdをアップロード出来ずに萎えてしまった．
また，その日に何をするか不明確であるため，パソコンを開いても何もせずに1日が終わってしまう．
その対策としてREADME.mdの編集の際に明日やることを書いておくことにする．
README.mdの編集を通じて，継続するコツをつかむことが出来れば，万々歳である．
今日は夜遅いので寝ます．
明日は最初に**世界で闘うプログラミング力を鍛える本**を読み進めたい．
コーディングテスト対策本だが，純粋にコーディング力を鍛えるために進めていきたい．
また，このファイルの編集記録をgithubに載せたい(草を生やしたい)ので**YouTubeでgitとGitHubについて学習する．** だいぶ初歩的なところで躓いているが，諦めず続けたい．

***

## 2023/02/16

### ファイルの変更をgithubに反映できなかった理由

**ファイルの構成ミス**という超初歩的なミスが原因だった．
フォルダの下にファイルがあると思い込んでいたが，フォルダの下に無駄にフォルダを作成していた．

### 知らぬ間にブランチが切られている

一人で編集しているはずなのに，ブランチが切られている．
README.mdの変更が反映されない．githubぐらい上手く使えるようになりたい

### gitの使い方

ブランチ名がmasterからmainに切り替わっていたことが原因でブランチが切られていた．
リポジトリ作成後に`master`にプッシュしてしまい，initial commitが上手くいかなかった．
対処法を以下に示す．

1. ブランチ名を変更する

   - `git branch -m 変更するブランチ名 変更後のブランチ名`
2. 強制的にプッシュする
   - `git push -f origin main`


- 発生したエラー

```bash
$ git push origin main
To リポジトリHTTPS
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'リポジトリHTTPS'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

エラーの内容について，`non-fast-forward`は`main`ブランチのローカルとリモートの最新情報が異なっていることを示している．そのため，通常のプッシュが行えず，`reject`が表示される．
以下の記事のおかげで解決しました．非常に感謝
[Qita](https://qiita.com/Takao_/items/5e563d5ea61d2829e497 "git pushがreject（拒否）されたときの対処法")  , [Hatena Blog](https://chiroru-memo.hatenablog.com/entry/2020/10/12/234906 "Githubのデフォルトブランチがmainになった")

### 今日の反省と明日やること

コーディング本は結局進められなかった．明日は読み進めたい．コーディングだけでなく，就活でも使えそうなことが載っていて良い．TOEICも近づいているので，英語の勉強も進めたい．

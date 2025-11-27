# HTMLファイルを作って GitHub にアップする手順書（初心者向け）

この手順書では、**ローカルPCで HTML ファイルを作成し、それを GitHub のリポジトリに push するまで**の一連の流れを説明します。

想定している環境・前提は以下です。

- GitHub アカウント：`Kengo55555`
- 例として作るリポジトリ名：`news-dashboard`
- すでに GitHub アカウントは作成済み
- PC にターミナル（またはコマンドプロンプト）とエディタ（VS Code など）がある

---

## 1. GitHub に新しいリポジトリを作成する

1. ブラウザで GitHub にログインする  
   - URL: `https://github.com/`

2. 右上の **「＋」アイコン → *New repository*** をクリック

3. リポジトリ作成画面で、次のように入力する
   - **Repository name**：`news-dashboard`（好きな名前でOK）
   - **Description**：任意（空でもOK）
   - **Public / Private**：どちらでもよい（公開したくなければ Private）
   - 他の項目（Initialize this repository with…）は **何もチェックしない**（空のリポジトリにする）

4. 一番下の **「Create repository」** をクリック

これで `https://github.com/Kengo55555/news-dashboard` のような空リポジトリができる。

---

## 2. ローカルPCにリポジトリをクローンする

### 2-1. ターミナルを開く

- macOS：Launchpad → Terminal
- Windows：スタートメニュー → 「ターミナル」 or 「コマンドプロンプト」 or 「PowerShell」

### 2-2. 作業用フォルダへ移動

好きなフォルダでOK。例として `~/workspace` を使う。

```bash
cd ~
mkdir -p workspace
cd workspace

2-3. GitHub からクローンする

ブラウザで、さきほど作ったリポジトリページを開く
例：https://github.com/Kengo55555/news-dashboard

緑の 「Code」 ボタンをクリック
→ HTTPS タブの URL（https://github.com/Kengo55555/news-dashboard.git）をコピー

ターミナルで以下を実行

git clone https://github.com/Kengo55555/news-dashboard.git
cd news-dashboard


これで、ローカルPC上に news-dashboard フォルダが作成され、その中がリポジトリになる。

3. HTML ファイル（index.html）を作成する
3-1. エディタでファイルを作る

VS Code などのエディタで news-dashboard フォルダを開く

新規ファイルを作成して ファイル名を index.html にする

中身に使いたい HTML コード（今回作ったニュースダッシュボードのコード）を貼り付ける

保存する

例：この手順書で一緒に作った「ニュース収集＋お気に入り＋カスタマイズ」の HTML をそのまま入れる

4. Git に変更を登録してコミットする
4-1. 変更状況を確認

ターミナルで、リポジトリのフォルダ内にいることを確認してから：

cd ~/workspace/news-dashboard   # すでに移動済みなら不要
git status


index.html が赤文字で Untracked file と表示されればOK（まだ Git に登録されていない状態）

4-2. 変更をステージング（git add）
git add index.html


もう一度 git status をすると、index.html が緑色になり、コミット待ちの状態になる。

4-3. コミットを作成する
git commit -m "Add news dashboard index.html"


ここでの "Add news dashboard index.html" はコミットメッセージ（好きなコメントでOK）。

5. GitHub に push するための認証（Personal Access Token）

git push すると、初回は GitHub の認証が必要になる。

5-1. Personal Access Token（PAT）を作成する

ブラウザで GitHub を開きログインする

右上のアイコン → 「Settings」 をクリック

左メニュー一番下あたりの 「Developer settings」 をクリック

左メニューから 「Personal access tokens」 → 「Tokens (classic)」 を選択

右上の 「Generate new token (classic)」 をクリック

フォームを入力する

Note：news-dashboard token など、用途がわかる名前

Expiration：任意（日数が過ぎるとトークンが使えなくなる）

Scopes：最低限 repo にチェックを入れる

一番下の 「Generate token」 をクリック

表示された 長い英数字のトークンをコピー する
→ この画面を閉じると再表示できないので、メモ帳などに控えておくと安心

6. GitHub に push する
6-1. push コマンドを実行

ターミナルで以下を実行：

git push origin main


※ ブランチ名が master の場合は main → master に読み替える。

実行すると、以下のように聞かれる：

Username for 'https://github.com':


GitHub のユーザー名 を入力（例：Kengo55555）して Enter

続いて、

Password for 'https://github.com':


が出るので、さきほど作成した Personal Access Token をパスワードとして貼り付けて Enter

入力中は画面に何も表示されないが正常な動作

エラーが出ずに処理が終了すれば push 成功。

7. GitHub 上で index.html を確認する

ブラウザでリポジトリを開く
例：https://github.com/Kengo55555/news-dashboard

ページをリロード（再読み込み）する

ファイル一覧に index.html が表示されていれば OK

8. ローカルで HTML を動かして確認する
8-1. ダブルクリックで開く（簡単な方法）

news-dashboard フォルダから index.html をダブルクリックすると、ブラウザで開ける。
ただし、一部のブラウザ環境では fetch の制限がかかる場合がある。

8-2. 簡易ローカルサーバーで動かす（おすすめ）

Python が入っている場合：

cd ~/workspace/news-dashboard
python -m http.server 8000


ブラウザで以下の URL を開く：

http://localhost:8000/index.html

これで、HTML 内の JS が http:// 経由で正しく動きやすくなる。

9. その後の更新フロー（運用イメージ）

HTML を修正して、また GitHub に反映したい場合は、次の流れを繰り返す。

index.html を編集して保存

ターミナルで変更を確認

git status


変更をステージング & コミット

git add index.html
git commit -m "◯◯のレイアウトを修正"


GitHub にプッシュ

git push origin main


GitHub のリポジトリページを開いて、変更が反映されていることを確認

10. （オプション）GitHub Pages で Web 公開する

HTML をインターネット越しに見られるようにしたい場合は、GitHub Pages を使う。

GitHub で news-dashboard リポジトリを開く

上部タブから 「Settings」 をクリック

左メニューから 「Pages」 をクリック

Build and deployment セクションで以下を設定

Source: Deploy from a branch

Branch: main（または master） / フォルダ: / (root)

「Save」ボタンを押す

数十秒〜数分後、同じページに公開URLが表示される
例：https://kengo55555.github.io/news-dashboard/

その URL をブラウザで開くと、index.html が Web 上で表示される

よくあるつまずきポイントと対処
Q1. git push origin main のあとに何も返ってこない

多くの場合、ユーザー名 / トークン入力待ち になっているだけ。

ターミナルをよく見ると Username for 'https://github.com': と表示されているはず。

Q2. GitHub パスワードを入れたら怒られた
remote: Support for password authentication was removed on August 13, 2021.


これは正常メッセージ

Personal Access Token をパスワードの代わりに使う必要がある

この手順書の「5. Personal Access Token を作成する」に戻
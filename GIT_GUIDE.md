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

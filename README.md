# News Dashboard（Google News RSS 自動収集）

このプロジェクトは、**指定したキーワードのGoogleニュースを定期収集し表示するWebアプリ**です。  
記事のお気に入り保存、検索テーマの変更、ページネーションなどの機能を備えています。

---

## 🚀 主な機能

### 🔹 1. GoogleニュースRSSの自動取得  
- キーワードに基づきニュースを自動収集  
- 3時間ごとに自動更新  
- 手動更新（再読み込み）も可能

### 🔹 2. カスタムカテゴリ設定  
- 4カテゴリそれぞれに  
  - タイトル  
  - 検索キーワード  
  を自由に設定できる

### 🔹 3. お気に入り機能  
- 記事にチェックするとお気に入りに保存  
- LocalStorage を使用して永続化

### 🔹 4. ページネーション  
- 各カテゴリ20件ごとにページを分割

---

## 📦 リポジトリ構成

├─ index.html # メインアプリ
├─ README.md # このドキュメント
├─ docs/ # GitHub Pages用
│ ├─ index.html
│ └─ style.css
├─ guide/ # 手順書
│ ├─ GIT_GUIDE.md
│ └─ SETUP_GUIDE.md
└─ assets/
└─ img/ # 手順書用画像

---

## 🌐 公開URL（GitHub Pages）

**URL は以下になります：**
https://kengo55555.github.io/news-dashboard/


（※ GitHub Pages が有効化されていない場合は Settings → Pages → Enable してください）

---

## 🛠 使用技術

- HTML / CSS / JavaScript (Vanilla)
- Google News RSS（rss2json API）
- LocalStorage
- GitHub Pages

---

## 📚 セットアップ手順

ローカルで動かす場合：

```bash
python -m http.server 8000


ブラウザで：
http://localhost:8000/index.html

📃 手順書

guide/GIT_GUIDE.md — Git に push するまで
guide/SETUP_GUIDE.md — 画像付きセットアップ手順

🧑‍💻 作者
GitHub: https://github.com/Kengo55555


---

# ✅ **2. GitHub Pages 用デザイン（docs/ 配下）**

👇 最低限の公開ページテンプレートです。  
見栄えよく配置し、スマホでも見やすいデザインにしてあります。

---

## **📄 docs/index.html**

```html
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<title>News Dashboard | GitHub Pages</title>
<link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>News Dashboard</h1>
    <p>カスタマイズ可能な Google ニュース収集ダッシュボード</p>
  </header>

  <main>
    <section>
      <h2>アプリ本体</h2>
      <p>下記リンクからアプリを起動できます。</p>
      <a class="btn" href="../index.html">▶ アプリを開く</a>
    </section>

    <section>
      <h2>ドキュメント</h2>
      <ul>
        <li><a href="../guide/GIT_GUIDE.md">Git 操作手順書</a></li>
        <li><a href="../guide/SETUP_GUIDE.md">セットアップガイド（画像付き）</a></li>
      </ul>
    </section>
  </main>

  <footer>
    <p>© 2025 News Dashboard</p>
  </footer>
</body>
</html>

📄 docs/style.css

body {
  margin: 0;
  padding: 0;
  font-family: "Segoe UI", sans-serif;
  background: #f7f7f7;
  color: #333;
}

header {
  background: #4c6ef5;
  color: white;
  text-align: center;
  padding: 2rem 1rem;
}

main {
  max-width: 900px;
  margin: 2rem auto;
  padding: 0 1rem;
}

section {
  background: white;
  padding: 1.5rem;
  border-radius: 10px;
  margin-bottom: 2rem;
  box-shadow: 0 0 10px rgba(0,0,0,0.05);
}

.btn {
  display: inline-block;
  background: #4c6ef5;
  color: white;
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  text-decoration: none;
  font-weight: bold;
}
.btn:hover {
  background: #3b5bdb;
}

footer {
  text-align: center;
  padding: 1rem;
  color: #888;
}




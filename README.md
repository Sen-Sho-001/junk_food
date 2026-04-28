# JUNK FOOD お気に入り (PWA版)


ジャンクフード（toylure.com）の中古ルアー用お気に入り管理ツール。
PC・スマホ両対応の Progressive Web App として動作します。

## 特徴

- 📱 **スマホで「共有」ボタンから1タップ追加**（PWA share_target）
- ☁️ **GitHub Gist でPC・スマホ間自動同期**
- 📷 **QRコードで他端末に同期設定を1秒で共有**
- 💻 **PCでブックマークレットからワンクリック追加**
- 🌐 **オフライン対応**（Service Worker）
- 🔒 **データは自分のGitHub Gistに保存**（プライベート可）

---

## 🚀 GitHub Pages へのデプロイ手順

### 1. GitHubリポジトリを作る

[github.com/new](https://github.com/new) で新しいリポジトリを作成:

- **Repository name**: 何でもOK（例: `junkfood-favorites`）
- **Public** または **Private** どちらでもOK（Pages設定で対応）
- **Add a README file** にチェック（任意）

### 2. このフォルダの全ファイルをアップロード

GitHubリポジトリのページで「**Add file → Upload files**」をクリックし、以下を全部ドロップ:

```
index.html
manifest.json
sw.js
icon-192.png
icon-512.png
icon-maskable.png
favicon.png
README.md（このファイル・任意）
```

「**Commit changes**」をクリック。

### 3. GitHub Pages を有効化

1. リポジトリの **Settings** タブを開く
2. 左メニューの **Pages** をクリック
3. **Source** で「**Deploy from a branch**」を選択
4. **Branch** で「**main**」「**/(root)**」を選んで **Save**
5. 1〜2分待つと、上部に `https://<ユーザー名>.github.io/<リポジトリ名>/` が表示される

これがあなた専用のお気に入りツールのURLです。

### 4. ブックマーク・ホーム画面に追加

- **PC**: そのURLをブックマーク
- **スマホ (iOS)**: SafariでURLを開いて、共有 → ホーム画面に追加
- **スマホ (Android)**: ChromeでURLを開いて、メニュー → アプリをインストール

---

## 🔄 同期の設定（PC↔スマホでデータ共有したい場合）

### 1台目（メイン端末）で

1. アプリを開いて「**⚡ クイック追加・同期設定**」を展開
2. 「**☁️ 同期**」タブをクリック
3. 「**GitHub Token を発行**」リンクをクリック → GitHubで Token を作成（scopes は `gist` のみでOK）
4. 発行された Token をコピー
5. 「**Token を設定**」ボタンをクリック → 貼り付け → 接続
6. 自動で Gist が作成され、データがクラウドに保存されます

### 2台目以降の端末で

1. アプリを開いて、同じく「**☁️ 同期**」タブを開く
2. 1台目の端末で「**📱 QR共有**」ボタンをクリックしてQRコードを表示
3. 2台目で「**📦 データ**」タブ → 「**📷 QRコードで読み込み**」
4. 2台目のカメラで1台目のQRをスキャン → 自動で同じGistに繋がります

これで **どの端末で追加しても全端末で同期** されます。

---

## 📱 スマホでの使い方（PWAインストール後）

1. ジャンクフード（toylure.com）で欲しい商品ページを開く
2. ブラウザの**共有ボタン**をタップ
3. 共有先一覧から「**JF お気に入り**」を選択
4. アプリが起動して自動でお気に入りに追加される ✨

PWAをインストールしていない場合は、URLをコピー → アプリのページに戻る → クリップボードから自動検出されます。

---

## 💻 PCでの使い方（ブックマークレット）

1. アプリを開いて「**⚡ クイック追加・同期設定**」→「**💻 PC**」タブ
2. 「**＋ JUNK FOOD 追加**」ボタンをブックマークバーにドラッグ
3. 「**ショップを開く**」ボタンで toylure.com を別タブで開く
4. 商品ページでブックマークバーの「**＋ JUNK FOOD 追加**」をクリック
5. 各商品の右上に出る **+** ボタンをクリック → アプリに自動追加

---

## ⚠️ 注意

- **GitHub Token はあなたの端末内のみ**に保存されます（GitHub APIへの認証以外には送信されません）
- Token は `gist` scopeのみで発行することを強く推奨（他のスコープは不要）
- QR共有には Token が含まれるので、人目にさらさないでください
- Gist は private にしていても、Gist URL を知っている人なら閲覧可能です（推測困難なIDですが）

---

## 🛠️ ローカルで動作確認したい場合

```bash
cd /path/to/this/folder
python3 -m http.server 8000
```

ブラウザで `http://localhost:8000` を開く。
（PWA機能は HTTPS または localhost でのみ動作します）

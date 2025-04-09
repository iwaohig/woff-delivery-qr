# LINE WORKS WOFF Demo - Delivery QR App

このリポジトリは、LINE WORKS の WOFF（Worksmobile OpenFrame Framework）を利用した**納品伝票の QR 表示および受領確認のデモアプリケーション**です。配送担当者が QR コードを提示し、受領者が読み取って受領処理を行うという流れを模擬体験できます。

> ⚠️ 本アプリケーションは **デモ用モックアップ**です。一部データはランダム生成されており、実際の配送データではありません。

---

## 📦 アプリ概要

- 配送担当者が自分の LINE WORKS アカウントでログインし、QR コードを生成
- QR に含まれる納品 ID / 納品先名 / 担当者名などをエンコード
- 受領者は LINE WORKS アカウントでログインして QR をスキャン
- 明細確認と受領ボタンをタップして完了

---

## 🚀 デモ手順

1. **LINE WORKS モバイルアプリでトークルームを開く**
2. トークルームの **固定メニューから**
   - 配送担当者は「納品 QR 表示」
   - 受領者は「受領 QR 読取」
3. 配送担当者が QR を表示し、受領者がスキャン
4. スキャン結果が画面に表示され、「受領」ボタンをタップ
5. 「納品明細を見る」リンクからダミー明細を別ウィンドウで確認
6. 納品明細画面の「閉じる」で元の画面に戻る

---

## 🖥 画面構成

### qr-display.html
- 配送担当者用 QR 表示アプリ
- LINE WORKS WOFF SDK を使ってログイン情報を取得し、QR に反映
- QR に含まれるデータ
  - 納品 ID（固定）
  - 納品先名（固定：「ワークス中央病院」）
  - 配送担当者名 / ID
  - 有効期限（5分）

### qr-reader.html
- 受領者用 QR 読取アプリ
- LINE WORKS アカウントで初期化後、QR をスキャン
- 内容確認後、受領ボタンをタップするとデモ用エンドポイントに JSON 送信
- 「納品明細を見る」リンクで delivery-details.html を新しいタブで表示

### delivery-details.html
- ダミー納品明細表示画面
- 納品日（今日の日付）と医薬品の品目をランダム表示
- 「閉じる」ボタンでウィンドウを閉じる設計

---

## 🔧 使用技術

| 技術 | 用途 |
|------|------|
| HTML / CSS / JavaScript | フロントエンド開発 |
| [LINE WORKS WOFF SDK](https://developers.worksmobile.com/jp/docs/woff-guide) | LINE WORKS 認証・プロフィール取得・QR スキャン |
| [qrcodejs](https://github.com/davidshimjs/qrcodejs) | QR コードの生成 |
| Azure Logic Apps (Webhook) | 受領情報の送信先（モック） |

---

## 📂 ファイル構成（抜粋）

```
├── qr-display.html          # 配送担当者用 QR 表示画面
├── qr-reader.html           # 受領者用 QR スキャン + 送信画面
├── delivery-details.html    # ダミー納品明細画面（医薬品データはランダム生成）
├── README.md                # 本ファイル
```

---

## 📎 注意事項

- このアプリは LINE WORKS WOFF に対応した **モバイル環境内ブラウザでのみ動作確認されています**。
- モバイルアプリ以外のブラウザでは初期化に失敗する可能性があります。

---

## 👤 制作

このデモは社内勉強会・展示用に作成されたものであり、商用利用を目的としたものではありません。

ご質問・フィードバックは Issue またはプルリクエストにてお知らせください。

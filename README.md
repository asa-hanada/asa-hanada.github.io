# asa-hanada.github.io

制作物、公開日記、自作PDFをまとめる個人サイトです。

## ファイル構成

- `index.html`: トップページ
- `projects/`: 制作物・コード
- `writings/`: 書き物の入口
- `writings/diary/`: 日ごとの日記
- `pdf/`: PDF一覧
- `pdf/files/`: 公開するPDFファイル
- `assets/`: CSSとJavaScript

## 更新方法

### 日記を書く

日記は `writings/diary/YYYY/MM/DD.md` に、一日一ファイルで置きます。
たとえば2026年11月18日の日記は `writings/diary/2026/11/18.md` です。

```markdown
---
title: 日記の題名
date: 2026-11-18
description: 日記の短い説明。
permalink: /writings/diary/2026/11/18/
---

ここに本文をMarkdownで書きます。
```

日記を追加すると、`writings/diary/` の一覧へ日付順に自動で表示されます。

### 自分でGitHubへ反映する

VS Codeでこのフォルダを開き、メニューの「ターミナル」→「新しいターミナル」を選びます。
ターミナルで次のコマンドを上から順番に実行します。

1. 変更されたファイルを確認します。

   ```powershell
   git status
   ```

2. 変更をコミットの対象に追加します。

   ```powershell
   git add .
   ```

3. 変更内容に短い名前を付けて保存します。引用符の中は変更内容に合わせて書き換えます。

   ```powershell
   git commit -m "日記を追加"
   ```

4. GitHubの`main`ブランチへ送ります。

   ```powershell
   git push origin main
   ```

プッシュ後、通常は1〜2分ほどでGitHub Pagesへ反映されます。
途中でエラーや競合が表示された場合は、`--force`を付けて無理にプッシュせず、作業を止めてエラー内容を確認してください。

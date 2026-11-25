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

### 編集した内容をGitHubにプッシュする

VS Codeでサイトのフォルダを開き、「ターミナル」→「新しいターミナル」を選びます。
PowerShellを別に開いた場合は、最初に`cd`でサイトのフォルダへ移動します。`Projects`に置いている場合の例です。

```powershell
cd "$env:USERPROFILE\Projects\asa-hanada.github.io"
```

以下は`README.md`を編集したときの例です。日記やCSSを更新したときは、ファイル名とコミットメッセージを変更内容に合わせます。

1. `git status`で、変更したファイルと現在のブランチを確認します。このサイトでは`main`にプッシュすると公開サイトが更新されます。

   ```powershell
   git status --short --branch
   ```

2. `git add`で、次のコミットに入れる変更を選びます。`git diff --cached`で、選んだ差分を確認できます。

   ```powershell
   git add -- README.md
   git diff --cached
   ```

3. `git commit`で、選んだ変更に短いメッセージを付けて手元のGit履歴に記録します。

   ```powershell
   git commit -m "GitHubへの更新手順を追記"
   ```

4. `git push`で、手元の`main`のコミットをGitHubに送ります。送る変更がコミット済みなら、ここから実行できます。

   ```powershell
   git push origin main
   ```

GitHub Pagesの更新が終わったら、[公開サイト](https://asa-hanada.github.io/)をブラウザで再読み込みして確認します。
途中でエラーや競合が表示された場合は、`--force`を付けて無理にプッシュせず、作業を止めてエラー内容を確認してください。

#### コミットに入れる変更を選ぶ

- **変更したファイルを全部入れる**なら、`git status`の一覧を確認してから、手順2の`git add -- README.md`を`git add -A`に置き換えます。新規ファイルや削除も対象です。
- **同じファイルの一部だけ入れる**なら、たとえば`git add -p -- assets/styles.css`を使います。差分ごとに`y`で選ぶ、`n`で見送る、`q`で選択を終了します。
- コミットは「背景色を変える」「日記を追加する」のように、目的がひとまとまりになったところで作ります。いくつかコミットを作ってから、公開したいときにまとめてプッシュできます。

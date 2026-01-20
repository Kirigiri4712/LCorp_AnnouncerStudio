# AnnouncerTool

LobotomyCorp の Announcers MOD を簡単に作成するための Windows Forms GUI ツールです。

## ダウンロード

**一般ユーザーの方はビルド不要です。** [Releases](../../releases) ページからビルド済みの実行ファイルをダウンロードしてください。

## 使い方（GUI）

1. ダウンロードした `AnnouncerTool.exe` を実行します。

2. アプリでできること:
   - `Select Save Folder...` で出力先フォルダを選択します（このフォルダに `AnnouncersImage_LEB` 等が作成されます）。
   - `Add` でアナウンサーを追加し、リストから選択します。
   - 言語を選び、タグ（例: `AgentDie_TEXT`）ごとにセリフを入力します。
   - `Assign Image...` でタグに紐づける PNG を選べます（保存時にコピーされます）。
   - `Save Mod` で指定フォルダへエクスポートします。
   - `Load Existing` で既存の `AnnouncersXML_LEB.xml` を読み込み、既存テキストや画像を参照できます。

注意:
- 音声ファイルの自動生成は行いません（音声が無くてもゲームは再生しないだけで動作します）。
- 保存時、各アナウンサーの `Announcer.png` と `UI.png` が存在しない場合はプレースホルダを自動生成します。

詳しい作り方は添付の `HowToUse_en.txt` を参照してください。

---

## 開発者向け情報

### ブランチ運用

このリポジトリでは全ての開発を `main` ブランチで直接行っています（機能ブランチは使用していません）。

### 必要環境

- .NET 8.0 SDK
- Windows（Windows Forms を使用）

### ビルド

```bash
cd AnnouncerTool
dotnet build -c Release
```

### 実行

```bash
dotnet run --project AnnouncerTool
```

# AnnouncerTool

日本語: このツールは LobotomyCorp の Announcers MOD フォルダ構成を解析し、テキストタグから期待される画像/音声ファイル名を出力します。オプションでプレースホルダの PNG/WAV を生成できます。

dotnet build -c Release
## ビルド

.NET 7 SDK が必要です。

```bash
cd AnnouncerTool
dotnet build -c Release
```

## 使い方（GUI）

1. ビルド後、実行します:

```bash
dotnet run --project AnnouncerTool
```

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
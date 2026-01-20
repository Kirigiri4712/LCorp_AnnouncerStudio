# アナウンサー作成ツール

Lobotomy Corporation用のアナウンサーMODを作成するためのGUIツールです。

## 機能

- 複数のアナウンサーの作成・管理
- 16種類のトリガーシナリオに対応したセリフ編集
- セリフの多言語対応（jp、enなど）
- 各アナウンスへのポートレート画像の割り当て
- 各アナウンスへの音声ファイル（WAV）の割り当て
- 音声ノーマライズ機能
- 音声プレビュー再生
- サイズが異なる画像のリサイズ（縮小/切り抜き）
- ランダムアナウンス機能
- ポートレート差分（Expression）機能
- 枠線色のカスタマイズ（透明度対応）

## 動作環境

- Windows 10/11（64ビット）
- .NET 8.0 ランタイム（自己完結型ビルドに同梱）

## インストール

1. zipファイルを任意のフォルダに解凍
2. `Languages`フォルダがexeと同じディレクトリにあることを確認
3. `AnnouncerTool.exe`を実行

## 使い方

### 新しいアナウンサーの作成

1. ツールを起動
2. テキストフィールドにアナウンサー名を入力（英語推奨）
3. セリフの言語を選択（デフォルト：jp）
4. リストの各タグをクリックしてセリフを入力
5. 画像を割り当て：
   - **Announcer.png**：デフォルトのポートレート（512x512必須）
   - **UI.png**：選択ボタンのアイコン（345x213推奨）
   - **タグ画像**：特定のアナウンス用ポートレート
6. （オプション）WAV音声ファイルを割り当て
7. 保存先フォルダを選択して「MODを保存」をクリック

### タグの説明

| タグ | トリガー |
|------|----------|
| Click | アナウンサー選択時 |
| StartWork | 業務開始時（音声のみ） |
| HalfOverWork | エネルギー目標の半分達成時 |
| OverWork | エネルギー目標達成時 |
| AgentDie | エージェント死亡時 |
| AgentPanic | エージェントパニック時 |
| OnAgentPanicReturn | パニック回復時 |
| AllDie | 全エージェント死亡時 |
| OnGetEGOgift | E.G.Oギフト獲得時 |
| CounterToZero | アブノーマリティ脱走時 |
| Suppress | アブノーマリティ鎮圧時 |
| QliphothMeltdown | クリフォトメルトダウン発生時 |
| Rabbit | ラビットチーム派遣時 |
| RabbitReturn | ラビットチーム帰還時 |
| Idle | 65-90秒間アナウンスがない時 |
| OnOverWork | 管理終了ボタン押下時（音声のみ） |

### プレースホルダー

- `#0` - エージェント名（AgentDie、AgentPanic、OnAgentPanicReturn、OnGetEGOgiftで使用可）
- `$0` - アブノーマリティ名（CounterToZero、Suppressで使用可）

### ランダムアナウンス

1. 「ランダム」チェックボックスをオン
2. 「数量」を設定（タグごとの最大バリエーション数、1-10）
3. 「追加」ボタンで番号付きバリエーションを作成（例：AgentDie_1、AgentDie_2）

### 既存MODの読み込み

「既存を読込」をクリックし、既存MODの`AnnouncersXML_LEB.xml`ファイルを選択してください。

## 出力構造

```
YourMod/
├── AnnouncersXML_LEB.xml
├── AnnouncersImage_LEB/
│   └── [アナウンサー名]/
│       ├── Announcer.png
│       ├── UI.png
│       └── Announcer[タグ名].png
├── AnnouncersTEXT_LEB/
│   └── [アナウンサー名]/
│       └── [言語]/
│           └── [言語].xml
└── AnnouncersSounds_LEB/
    └── [アナウンサー名]/
        └── [タグ名].wav
```

## ツール言語の追加

`Languages`フォルダにJSONファイルを追加することで、UIの言語を追加できます。
テンプレートとして`en.json`または`ja.json`を参照してください。

## ライセンス

このツールはLobotomy CorporationのMOD作成用として提供されています。

## クレジット

Claude Codeで作成

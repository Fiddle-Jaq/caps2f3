# caps2f3 - CapsLock to F3 Remapper

CapsLock キーを F3 キーに変換する AutoHotkey v2 スクリプトです。

## 特徴

- **JIS / US キーボード両対応** — スキャンコード (`sc03A`) で指定しているため、キーボードレイアウトに依存しません
- **修飾キー対応** — Shift + CapsLock → Shift + F3 など、修飾キーとの組み合わせがそのまま動作します
- **軽量** — 常駐メモリ使用量はごくわずかです

## 必要環境

- Windows 10 / 11
- [AutoHotkey v2.0](https://www.autohotkey.com/) 以上（`.ahk` から実行する場合）

`.exe` 版はAutoHotkey のインストール不要で動作します。

## インストール

### exe 版

1. [Releases](../../releases) から `caps2f3.exe` をダウンロード
2. ダブルクリックで実行

### ahk 版

1. [AutoHotkey v2](https://www.autohotkey.com/) をインストール
2. [Releases](../../releases) から `caps2f3.ahk` をダウンロード
3. ダブルクリックで実行

## Windows 起動時に自動実行する

1. `Win + R` を押して `shell:startup` と入力し、スタートアップフォルダを開く
2. `caps2f3.exe`（または `.ahk`）のショートカットをフォルダに配置する

## スクリプトの内容

```ahk
#Requires AutoHotkey v2.0
#SingleInstance Force
InstallKeybdHook()

; CapsLock(sc03A) -> F3
; スキャンコード指定によりJIS/USキーボード両対応
*sc03A::F3
```

| 記述 | 説明 |
|------|------|
| `#Requires AutoHotkey v2.0` | AHK v2.0 以上を要求 |
| `#SingleInstance Force` | 再実行時に旧インスタンスを自動で置換 |
| `InstallKeybdHook()` | キーボードフックを有効化し、確実にキーを捕捉 |
| `*sc03A::F3` | CapsLock（スキャンコード `03A`）を F3 にリマップ。`*` により修飾キー併用時も動作 |

## 動作仕様

| 入力 | 出力 |
|------|------|
| CapsLock | F3 |
| Shift + CapsLock | Shift + F3 |
| Ctrl + CapsLock | Ctrl + F3 |

## アンインストール

タスクトレイの AutoHotkey アイコンを右クリック → **Exit** で停止します。スタートアップに登録している場合はショートカットも削除してください。

## ライセンス

[MIT](LICENSE)

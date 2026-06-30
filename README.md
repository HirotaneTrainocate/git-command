# .gitignore サンプル

このリポジトリは `.gitignore` の基本動作を確認するための最小サンプルです。

## 目的

- 追跡されるファイルと無視されるファイルの違いを確認する
- 例外ルール（`!`）の動きを確認する

## サンプル構成

- `src/app.txt` : 追跡対象
- `.env` : 無視対象（機密ファイル例）
- `logs/app.log` : 無視対象（ログ例）
- `tmp/cache.tmp` : 無視対象（`*.tmp`）
- `build/output.txt` : 無視対象（ビルド成果物）
- `logs/.gitkeep` : 例外ルールで追跡対象

## 手順

1. 現在の状態を確認

```bash
git status --short
```

2. 無視ルールに一致するか確認

```bash
git check-ignore -v .env logs/app.log tmp/cache.tmp build/output.txt
```

3. 追跡対象だけを追加

```bash
git add .
git status --short
```

期待される結果:

- `src/app.txt` と `logs/.gitkeep` は `A` で表示される
- `.env` / `logs/app.log` / `tmp/cache.tmp` / `build/output.txt` は表示されない

4. 例外ルールを説明

`.gitignore` では `logs/*.log` を無視していますが、`!logs/.gitkeep` で例外的に `.gitkeep` を追跡できます。

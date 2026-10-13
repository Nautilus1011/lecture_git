# CLAUDE.md

講義「人工知能応用特論Ⅰ」の演習用リポジトリ。**コミット履歴は課題として提出する可能性がある**ため、履歴の綺麗さを最優先する。

## ディレクトリ構成

| パス | 用途 |
| --- | --- |
| `src/` | 再利用するPythonモジュール（例: `dataloader.py`） |
| `scripts/` | 単体で実行するスクリプト（例: `hello.py`） |
| `tests/` | pytest のテスト（`src/` に対応させる） |
| `experiment/` | 実験ごとの設定・ログ・結果のまとめ |
| `notebooks/` | Jupyter Notebook |
| `docs/` | 講義メモ・ドキュメント |
| `data/` | データセット置き場（**中身はGit管理しない**） |
| `models/` | 学習済みモデル置き場（**中身はGit管理しない**） |

- ルート直下にスクリプトを置かない。講義資料がルートに置く手順でも、上の表に合わせて適切なディレクトリに配置する。
- 空ディレクトリには `.gitkeep` を置く。ファイルが入ったら `.gitkeep` は削除してよい。

## Git 運用ルール（GitHub flow）

- 作業は必ず `main` から feature ブランチを切って行う（`git switch -c add_<内容>`）。
- `main` への統合は **Squash merge**（`git merge --squash <branch>` → `git commit`）。
- マージ後はローカル・リモートの作業ブランチを削除する。
- リモートの取り込みは `git pull` を使わず、`git fetch origin` → `git merge origin/main` と分けて行う。
- 手順の詳細は `/github-flow` スキルを参照。

### コミット

- メッセージは講義資料に合わせ、英語の短い命令形・小文字始まり（例: `add hello.py`, `implement dummy dataloader`）。
- **`Co-Authored-By` などのAI共著表記は付けない。**
- `git add .` / `git add -A` は使わず、パスを明示して add する。
- 強制プッシュや履歴の書き換えは、ユーザーの明示的な指示がある場合のみ行う（`--force-with-lease` を使う）。

### コミットしないもの

- `tmp-*.md` などの作業メモ
- データセット、学習済みモデル（`.pth`, `.pt`, `.onnx`, `.ckpt`）、50MB以上のファイル
- `.venv/`, `__pycache__/`, `.DS_Store`, `.claude/settings.local.json`

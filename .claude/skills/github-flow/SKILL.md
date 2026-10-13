---
name: github-flow
description: このリポジトリのGitHub flow（featureブランチ作成 → コミット → Squash merge → ブランチ削除）を講義の手順どおりに実行する。新しい演習や機能を追加してmainに取り込むときに使う。
---

# GitHub flow（Squash merge）

引数としてブランチ名（例: `add_dataloader`）とSquash後のコミットメッセージを受け取る。不明ならユーザーに確認する。

## 手順

1. 事前確認
   ```bash
   git status            # 作業ツリーが綺麗か
   git fetch origin
   git switch main
   git merge origin/main # git pull は使わない
   ```
2. featureブランチを作成する
   ```bash
   git switch -c <branch>
   ```
3. 実装し、パスを明示してコミットする（必要なら複数コミットに分けてよい）
   ```bash
   git add <paths>
   git commit -m "<english imperative message>"
   git push -u origin <branch>
   ```
4. mainにSquash mergeしてプッシュする
   ```bash
   git switch main
   git merge --squash <branch>
   git commit -m "<summary message>"
   git push origin main
   ```
5. 作業ブランチを削除する
   ```bash
   git branch -D <branch>
   git push origin --delete <branch>
   ```
6. 結果を確認する
   ```bash
   git log --oneline --graph
   git ls-remote origin
   ```

## 注意

- コミットメッセージに `Co-Authored-By` などのAI共著表記を付けない。
- `tmp-*.md`、データ、モデル重みなど `.gitignore` 対象のファイルを add しない。
- ファイルはルート直下ではなく `src/` や `scripts/` などの適切なディレクトリに置く（`CLAUDE.md` 参照）。

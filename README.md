# lecture_git

東京農工大学大学院 先進学際科学府  
講義「**人工知能応用特論Ⅰ：機械学習・データサイエンスのためのプログラミング**」演習用リポジトリ

---

## 概要 (Overview)
本リポジトリは、「人工知能応用特論Ⅰ」におけるGit/GitHubの実践、開発環境構築、Pythonコーディング、テスト駆動開発、および深層学習の実験管理に関する演習コードを管理するリポジトリです。

* **受講者**: [氏名] ([学籍番号])
* **担当教員**: 山田宏樹 先生

---

## 開発環境 (Development Environment)
講義資料で推奨・指定されているツール群を中心に構成しています。

* **OS**: [macOS / Windows 11 (WSL2) / Ubuntu など]
* **Editor**: Visual Studio Code (VS Code)
* **Version Control**: Git / GitHub CLI (`gh`)
* **Container**: Docker Desktop
* **Language**: Python 3.x

---

## 講義スケジュールと対応進捗 (Progress)
- [x] **第1回：Gitの基礎** (環境構築、ローカルリポジトリ初期化)
- [x] **第2回：Git・GitHubの実践** (GitHub flow、ブランチ運用、リモート同期、Docker Desktop導入)
- [ ] **第3回：Pythonの環境構築**
- [ ] **第4回：Dev Containerによる開発環境の構築**
- [ ] **第5回：Visual Studio Code (VS Code) を活用した開発**
- [ ] **第6回：読みやすいPythonコードの書き方**
- [ ] **第7回：pytestを使ったテスト駆動開発**
- [ ] **第8回：機械学習のプロジェクトにおける実験管理**

---

## ブランチ運用方針 (Branch Strategy)
講義方針に則り、個人開発および研究開発に適した **GitHub flow** を採用して運用します。

1. **`main` ブランチ**: 動作確認済みの安定状態のみを保持。直接の開発・コミットは行わない。
2. **Feature ブランチ (`add_*` / `feature/*`)**: 
   * 機能追加や演習ごとに `main` からブランチを切って作業 (`git switch -c <branch_name>`)
   * 実装・検証完了後、`main` に戻り **Squash merge** (`git merge --squash <branch_name>`) を実行して履歴を集約
   * マージ完了後は作業ブランチを削除 (`git branch -D <branch_name>`)

---

## リポジトリ運用上のルール (.gitignore & Data Policy)
講義資料の指示に基づき、以下の管理ルールを徹底します。

* **大容量ファイル・成果物の管理除外**:
  * 100MB以上のファイルはGit管理禁止（50MB以上で警告対象）。
  * データセット、学習済みモデルの重み（`.pth`, `.pt`, `.onnx` 等）はコミットせず、ローカルまたは外部ストレージで管理する。
* **中間ファイル・環境の除外**:
  * 仮想環境（`.venv/`）、キャッシュ（`__pycache__/`）、OS生成ファイル（`.DS_Store`）は `.gitignore` により追跡対象から除外。

---

## ディレクトリ構成 (Repository Structure)
```text
lecture_git/
├── README.md          # 本ドキュメント
├── .gitignore         # Python / 環境用除外設定
├── hello.py           # 第2回：リモート同期確認用スクリプト
└── (今後の演習ファイル群)
```

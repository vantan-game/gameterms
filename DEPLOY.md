# DEPLOY — GameTerms 学習ダッシュボード

GitHub Pages による静的サイト公開のメモ。

## 公開URL

https://vantan-game.github.io/gameterms/

メインページは `study_dashboard.html`。ルートアクセス時は `index.html` から自動リダイレクト。

## 構成

| ファイル | 役割 |
|---|---|
| `index.html` | `study_dashboard.html` へのリダイレクト |
| `study_dashboard.html` | 学習ダッシュボード（メインページ） |
| `terms_master.html` | 全875語マスター一覧 |
| `category_index.html` | カテゴリ別索引 |
| `importance_index.html` | 重要度別索引（A→B→C） |
| `study_plan_A_rank_30days.html` | 重要度A 83語 30日学習プラン |
| `study_plan.html` | 旧版ダッシュボード（v1）|
| `terms_data.js` | 索引・ダッシュボード共有データ |
| `study_plan_A_rank_30days.csv` | 30日プラン CSV版 |
| `.nojekyll` | GitHub Pages の Jekyll 処理を無効化 |
| `README.md` | プロジェクト概要 |

## デプロイ操作（参考）

このディレクトリの中で：

```bash
git init
git add .
git commit -m "Initial commit: GameTerms learning dashboard"
git branch -M main
git remote add origin https://github.com/vantan-game/gameterms.git
git push -u origin main

gh api -X POST /repos/vantan-game/gameterms/pages \
  -f source[branch]=main -f source[path]=/
```

## データ更新時

`terms_data.js` は `tools/build_terms_data.js`（ソースリポジトリ側）で自動生成されたファイル。中身を直接編集しないこと。更新が必要な場合はソース側で再生成してから本リポジトリにコピーする。

## 注意

- ローカルストレージで学習状態を保存（`gameterms_v2` キー）
- 印刷時は各ページの「印刷」ボタンを使用（A4最適化済み）
- 学習シート PDF（`output/pdf/`）は本リポジトリには含めない（容量のため別管理）
